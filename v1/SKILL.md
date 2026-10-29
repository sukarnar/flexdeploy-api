---
name: flexdeploy-api-v1
description: Work with the Flexagon FlexDeploy 9.0 REST v1 API (paths under /flexdeploy/rest/v1/...) — write curl/Python/PowerShell/CI scripts or answer questions about v1 endpoints for projects (build, deploy, execute utility), branches/streams, packages, project properties and versions, releases, release snapshots and gates, approval tasks, security users/groups, folders, targets and integration instances (SCM, CMS, ITS, accounts). Use this whenever the user mentions FlexDeploy v1, a /v1/ FlexDeploy URL, an existing script that calls /flexdeploy/rest/v1, or a v1-only call like /v1/project/{id}/build, /v1/project/{id}/deploy or release gate approval. For new automation with no version stated, prefer the flexdeploy-api (v2) skill if it is installed, and use this one when v2 lacks the operation.
---

# FlexDeploy REST v1 API (9.0)

Source spec: https://flexagon.com/api-spec/9.0/v1/ (OpenAPI 3.0.1, 57 paths, 21 groups). A copy is bundled so field names come from the spec, not memory.

## Basics
- **Base URL**: `https://<server>/flexdeploy/rest` + path, e.g. `POST https://fd.example.com/flexdeploy/rest/v1/project/10234/deploy`. Ask for the host if unknown; use a variable rather than inventing one.
- **Auth**: HTTP Basic (a FlexDeploy user). Read credentials from env vars (`FD_USER`, `FD_PASSWORD`) or the CI secret store — never hard-code them.
- **JSON** in/out with `Content-Type: application/json`.
- v1 is the older API. It's smaller than v2 and its naming differs: branches are **streams** (`/v1/project/{projectId}/stream`, `streamId`), releases are plural (`/v1/releases`). Don't mix v1 and v2 paths or field names in one call.

## v1 vs v2 — when to use which
- Use v1 when the user asks for it, maintains scripts already on v1, or needs something v1 has that v2 doesn't (e.g. **release gate completion** `POST /v1/releases/{releaseId}/gate/approval|externalApproval`, **current user profile**, SCM instance **connection test**).
- Builds/deploys exist in both: v1 is project-centric (`POST /v1/project/{Id}/build|deploy|execute`), v2 uses `/v2/workflowrequest/...`. If the user has no preference, mention v2 is the newer, broader API.

## Common workflows
- **Build**: `POST /v1/project/{Id}/build` — body `BuildProjectRequestPojo` (`environmentId` = build environment, `streamId`, `packageName`, `forceBuild`, `inputs`, `flexFields`, `relatedTickets`, `releaseId`, `workflowVersionOverride`). Returns 201 with a workflow request.
- **Deploy**: `POST /v1/project/{Id}/deploy` — body `DeployProjectRequestPojo` (`projectVersionId` numeric id, `environmentId`, `instanceIds`, `streamId`, `packageName`, `forceDeploy`, `predeploy`, `startTime`, `changeTickets`, `inputs`, `flexFields`). Resolve a version name like "1.4.2" to its id with the Project - Version search first.
- **Wait for completion**: poll `GET /v1/workflowrequest/{workflowRequestId}` and `GET /v1/workflowexecution?workflowRequestId=...` (`executionStatus`); logs zip at `GET /v1/workflowexecution/{id}/logs`.
- **Releases**: `/v1/releases` (search/create/update), snapshots `POST /v1/releases/{releaseId}/snapshot` (also "promotes a project to a release"), gates as above.
- **Approvals**: `Approval Tasks` group.

## Finding the exact endpoint and body
1. Grep `references/endpoints.md` (all operations by group, with query params).
2. Get a full schema with `$ref`s resolved:
   ```
   python scripts/fd_schema.py find stream
   python scripts/fd_schema.py op POST /v1/project/{Id}/deploy
   python scripts/fd_schema.py schema DeployProjectRequestPojo
   ```
   Needs PyYAML. In Git Bash prefix with `MSYS_NO_PATHCONV=1` so `/v1/...` isn't turned into a Windows path. Without Python, grep `references/openapi.yaml`.
3. Use only field names and enum values in the schema. The spec often doesn't mark required fields or list status values — say so rather than guessing silently.

## Writing scripts
- Check HTTP status (`curl --fail-with-body`, `raise_for_status()`) and print the response body on error.
- Paginate with `limit`/`offset` where the search supports them (some v1 searches only take `limit`).
- When polling, print status changes, sleep between polls, time out, and exit non-zero on failure so CI stops.
- Flag destructive calls (DELETE, PUT that replaces an object) to the user.
