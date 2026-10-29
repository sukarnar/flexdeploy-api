---
name: flexdeploy-graphql-v2
description: Build a GraphQL API for Flexagon FlexDeploy on top of its REST v2 API (9.0) — generate a GraphQL schema (SDL) from the FlexDeploy OpenAPI spec, stand up a GraphQL gateway/server (graphql-yoga, Apollo or similar) whose resolvers call /flexdeploy/rest/v2, trim it to chosen areas (projects, releases, workflow requests, environments...), and write GraphQL queries/mutations against it. Use this whenever the user mentions GraphQL together with FlexDeploy or Flexagon, wants a GraphQL layer, schema, gateway, federation subgraph or BFF for FlexDeploy, or asks to "convert"/"wrap" the FlexDeploy REST API as GraphQL — even if they just say "graphql for flexdeploy".
---

# GraphQL for FlexDeploy REST v2

FlexDeploy itself only exposes REST (`/flexdeploy/rest/v2`, HTTP Basic auth). GraphQL is built as a **gateway in front of it**: a generated schema plus generic resolvers that turn each GraphQL field into one REST call. Don't hand-write the 280 fields — generate them from the bundled spec so names and types match FlexDeploy exactly.

## What's bundled
- `references/openapi.yaml` — FlexDeploy 9.0 REST v2 spec (from https://flexagon.com/api-spec/9.0/v2/).
- `scripts/gen_graphql.py` — OpenAPI → GraphQL generator (needs Python + PyYAML). Writes:
  - `schema.graphql`: object types, `...Input` input types, enums, `Query` (every GET) and `Mutation` (POST/PUT/PATCH/DELETE). Field names are the spec's `operationId`s (e.g. `searchProject`, `deployWorkflowRequest`); each field's doc string shows its REST method and path.
  - `operations.json`: field → `{method, path, pathParams, queryParams, body, response}` — the resolver map.
  - `skipped.json`: operations left out and why (12 by default: file downloads/uploads, multipart, text/plain bodies).
- `assets/server/` — ready-to-run Node gateway (`server.mjs` + `package.json`, graphql-yoga 5) that builds every resolver from `operations.json`.

## Mapping rules (so you can explain the schema)
- int64 → custom scalar `Long` (FlexDeploy ids exceed GraphQL `Int`); free-form objects/maps → scalar `JSON`.
- Path params → required args; query params → optional args (same names, e.g. `limit`, `offset`, `isActive`).
- JSON request body → a single `input:` argument of the matching `...Input` type.
- Responses: JSON → typed object (search results are `Paginated*` types with `items`, `totalCount`, `hasMore`); text → `String`; no body → `Boolean` (true on success).
- Spec enums with valid GraphQL names become enums (e.g. `searchProject_ScmType`); others stay `String`.

## Workflow
1. **Ask (briefly) only what changes the build**: which areas they need (all, or certain tags like `Project`, `Release`, `Workflow Request`), read-only or with mutations, and their stack if not Node. Default: everything, Node + graphql-yoga.
2. **Generate**:
   ```
   python scripts/gen_graphql.py --out <project>/generated
   python scripts/gen_graphql.py --out <project>/generated --tags "Project,Project - Version,Workflow Request,Workflow Execution,Topology - Environment"
   python scripts/gen_graphql.py --out <project>/generated --only-queries
   ```
   Tag names are the `## headings` you'd see in the spec (e.g. `Release Snapshots`, `Security - User`). The script prints counts; mention `skipped.json` if the user needs any of those operations (they need plain REST).
3. **Server** (Node default): copy `assets/server/*` into the project, put the generated files in `generated/`, then `npm install` and run with `FD_URL=https://<host>/flexdeploy/rest node server.mjs` (GraphiQL at `http://localhost:4000/graphql`).
   - **Auth**: the gateway forwards the caller's `Authorization` header, so each user acts with their own FlexDeploy permissions; `FD_USER`/`FD_PASSWORD` env vars are only a fallback service account. Keep that design unless the user asks otherwise, and never put credentials in code.
   - REST errors become GraphQL errors with `extensions.code` (`UNAUTHENTICATED`, `FORBIDDEN`, `FLEXDEPLOY_ERROR`) and the HTTP status.
   - Other stacks (Apollo Server, Python Strawberry/Ariadne, Java/Spring GraphQL, a federation subgraph): reuse `schema.graphql` as-is and port the ~30-line generic resolver in `server.mjs` — it's just path substitution, query string, JSON body, fetch.
4. **Validate** before handing over: build the schema (e.g. `buildSchema` from `graphql`, or start the server) and run at least one query and one mutation; if no FlexDeploy server is reachable, point `FD_URL` at a tiny mock and check the REST calls it receives.
5. **Show example operations** using real field names from the generated schema, e.g.:
   ```graphql
   query { searchProject(isActive: false, scmType: GIT, limit: 50) { totalCount hasMore items { projectId projectName } } }
   mutation { deployWorkflowRequest(input: { projectId: 10234, projectVersionId: 88123, environmentId: 501 }) { workflowRequestId requestStatus } }
   ```
   Look up arguments/fields with `grep -n "<fieldName>(" generated/schema.graphql`.

## Going further (only if asked)
- **Nicer graph**: add hand-written relationship fields on top (e.g. `WorkflowRequestDataObject.execution` resolving via `searchWorkflowExecution(workflowRequestId)`), via `extend type` in a separate SDL file merged with the generated one. Keep generated files untouched so they can be regenerated.
- **Renaming**: rename `operationId`-style fields (e.g. `searchProject` → `projects`) in a thin layer, not by editing the generator output.
- **Performance**: add a per-request cache/DataLoader for repeated `get...ById` calls.
- Flag that mutations hit the real FlexDeploy (deploys, deletes, config import) — suggest `--only-queries` for dashboards and reporting.
