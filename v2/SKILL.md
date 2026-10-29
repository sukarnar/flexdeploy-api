---
name: flexdeploy-api
description: Work with the Flexagon FlexDeploy 9.0 REST v2 API — write curl/Python/PowerShell/pipeline scripts or answer questions that call FlexDeploy endpoints (projects, versions, builds, deploys, releases, snapshots, environments, targets, workflows, workflow executions, credentials, users, work items, webhooks, config import/export). Use this whenever the user mentions FlexDeploy, Flexagon, /flexdeploy/rest, or wants to automate FlexDeploy builds/deployments/releases from CI, scripts or another tool, even if they don't say "API".
---

# FlexDeploy REST v2 API (9.0)

Source spec: https://flexagon.com/api-spec/9.0/v2/ (OpenAPI 3.0.1, 161 paths). A copy is bundled so you never need to guess field names.

## Basics
- **Base URL**: `https://<server>/flexdeploy/rest` + path, e.g. `GET https://fd.example.com/flexdeploy/rest/v2/project?projectName=MyApp`. Ask for the host if unknown; use a variable/placeholder rather than inventing one.
- **Auth**: HTTP Basic (a FlexDeploy user). Read credentials from env vars (e.g. `FD_USER`, `FD_PASSWORD`) or the CI secret store — never hard-code them in scripts.
- **JSON** in/out: send `Content-Type: application/json`, `Accept: application/json`. File uploads (`/attachment/upload`, project templates) are `multipart/form-data` with a `file` field.
- **CRUD pattern** (most resources): `GET /v2/<res>` search with query filters + `limit`/`offset`; `POST /v2/<res>` create; `GET|PUT|PATCH|DELETE /v2/<res>/{Id}`. `PUT` replaces all attributes; `PATCH` only updates non-null fields — prefer PATCH for partial edits.
- IDs are numeric (`int64`). Look things up by name via the search endpoint first, then use the returned id.

## Common workflows
- **Trigger a build/deploy/test/utility/rollback**: `POST /v2/workflowrequest/{build|deploy|test|utility|rollback}` → returns a workflow request; poll `GET /v2/workflowrequest/{Id}` and/or the workflow execution (`/v2/workflowexecution/...`) until a terminal status, with a sleep between polls and a timeout.
- **Releases**: `/v2/release`, release content, properties and snapshots tags — create/start a release, add projects, create a snapshot.
- **Topology**: environments, targets, target groups, endpoints, and their properties under the `Topology - *` tags.
- **Approvals / tasks**: `Tasks` tag.
- **Logs & artifacts**: plugin execution logs, `Project - Artifact`, `Project - Backup`, workflow execution reports.

## Finding the exact endpoint and body
1. Skim `references/endpoints.md` (all operations grouped by tag, with query params). Grep it rather than reading the whole file.
2. Get the full request/response schema with `$ref`s resolved:
   ```
   python scripts/fd_schema.py find release            # paths containing a word
   python scripts/fd_schema.py op POST /v2/workflowrequest/deploy
   python scripts/fd_schema.py schema <SchemaName>
   ```
   (Needs PyYAML. In Git Bash prefix with `MSYS_NO_PATHCONV=1` so `/v2/...` isn't rewritten into a Windows path.) Fall back to grepping `references/openapi.yaml` if Python isn't available.
3. Build the request from the schema — use the real field names and enum values; mark required fields; don't invent fields the spec lacks. If something genuinely isn't in v2, say so (older v1 endpoints exist but are separate).

## Writing scripts
- Fail loudly: check HTTP status (`curl --fail-with-body`, `raise_for_status()`), print the response body on error — FlexDeploy errors usually explain the problem.
- Paginate searches with `limit`/`offset` when the user wants "all".
- For polling, show the status transitions and exit non-zero on failure so CI pipelines stop.
- Be careful with destructive calls (DELETE, PUT replacing objects, config import) — call them out to the user.
