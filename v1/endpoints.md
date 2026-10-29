# FlexDeploy v1 REST endpoint index

Base: `https://<host>/flexdeploy/rest` + path. Grouped by tag.

## Contents
- Administration - Security Group
- Administration - User
- Approval Tasks
- Current User Profile
- Folder
- Project
- Project - Branch
- Project - Package
- Project - Properties
- Project - Version
- Release
- Release Gates
- Release Snapshots
- Scheduled Tasks API
- Topology - Integration CMSInstance
- Topology - Integrations Account
- Topology - Integrations Issue Tracking System Instance
- Topology - Integrations SCMInstance
- Topology - Targets API
- Workflow Execution
- Workflow Request

## Administration - Security Group
- `GET /v1/administration/security/group` — This GET service will return a list of groups in the form of JSON objects based on the query parameters group name. Groups are only returned if they match all of the specified query parameters. If no query parameters are given this request will return the entire list of groups. (query: groupName)
- `POST /v1/administration/security/group` — This POST service will create a new group with the same attributes as the given JSON object.
- `GET /v1/administration/security/group/{Id}` — This GET service will find a group with the given Id and return the JSON representation of the object.
- `PUT /v1/administration/security/group/{Id}` — This PUT service will update all attributes of a group with the given Id based on the attributes of a JSON object parameters.
- `PATCH /v1/administration/security/group/{Id}` — This PATCH service will update an existing group with the information passed through a JSON object. If an attribute of the JSON is null it will not be updated in the group.

## Administration - User
- `GET /v1/administration/security/user` — This GET service will return a list of users in the form of JSON objects based on the query parameters user name, first name, last name and group id. Users are only returned if they match all of the specified query parameters. Maximum of 50 items will be returned if limit is not provided. (query: userName, lastName, firstName, groupId, limit, offset)
- `POST /v1/administration/security/user` — This POST service will create a new user with the same attributes as the given JSON object.
- `GET /v1/administration/security/user/{Id}` — This GET service will find a user with the given Id and return the JSON representation of the object.
- `PUT /v1/administration/security/user/{Id}` — This PUT service will update all attributes of a user with the given Id based on the attributes of a JSON object parameters. Attributes that are not provided will become their default values.
- `PATCH /v1/administration/security/user/{Id}` — This PATCH service will update an existing user with the information passed through a JSON object. If an attribute of the JSON is null it will not be updated in the user. Groups that are included in a PATCH will be added, but existing groups will still remain.

## Approval Tasks
- `PUT /v1/tasks/approval/approve` — Approve Task by the given attributes (query: workflowRequestId, folderRequestId, pipelineStageExecId, projectId, applicationId, environmentId, externalId, externalSystemType, externalSystemId, notes)
- `PUT /v1/tasks/approval/approve/{Id}` — Approve Task by Id (query: notes)
- `GET /v1/tasks/approval/{Id}` — Find an Approval Task with the given Task Id
- `PUT /v1/tasks/approval/reject` — Reject Task by the given attributes (query: workflowRequestId, folderRequestId, pipelineStageExecId, projectId, applicationId, environmentId, externalId, externalSystemType, externalSystemId, notes)
- `PUT /v1/tasks/approval/reject/{Id}` — Reject Task by Id (query: notes)
- `GET /v1/tasks/approval` — Search Approval Tasks (query: workflowRequestId, folderRequestId, pipelineStageExecId, projectId, applicationId, environmentId, externalId, externalSystemType, externalSystemId, notes)

## Current User Profile
- `GET /v1/self` — This service will give information about current user. It returns the userName, roles,firstName,lastName and other information about the user.

## Folder
- `GET /v1/folder/{Id}` — Find a Folder with the given Id
- `GET /v1/folder` — Search Folders (query: folderName)

## Project
- `POST /v1/project/{Id}/build` — Builds a Project
- `GET /v1/project` — Search Projects (query: projectName, folderId, isActive, limit, offset)
- `POST /v1/project` — Creates a new Project with attributes from the given JSON body
- `POST /v1/project/{Id}/deploy` — Deploys a Project
- `POST /v1/project/{Id}/execute` — Executes a Utility Project
- `GET /v1/project/{id}` — Find a Project with the given Id
- `PATCH /v1/project/{Id}` — Updates provided attributes of a Project with the given Id based on a JSON object

## Project - Branch
- `GET /v1/project/{projectId}/stream` — Returns a list of branches that match the criteria (query: streamName, isActive)
- `POST /v1/project/{projectId}/stream` — Creates a Branch (previously called a project stream)
- `GET /v1/project/{projectId}/stream/{streamId}` — Returns a JSON representation of the branch
- `PUT /v1/project/{projectId}/stream/{streamId}` — Updates a project Branch, replacing all attributes with those given.
- `PATCH /v1/project/{projectId}/stream/{streamId}` — Updates a project Branch, replacing only non-null attributes from the given object.
- `POST /v1/project/{projectId}/stream/{streamId}/populate` — Discovers files for a project Branch. Returns an integer which is the number of new files populated.
- `POST /v1/project/{projectId}/stream/{streamId}/populate/salesforce` — Discovers Salesforce files for a project Branch

## Project - Package
- `POST /v1/project/{projectId}/package` — Creates a Project Package
- `GET /v1/project/{projectId}/package/{packageName}` — Find a Project Package with the given Name for a given projectId
- `PUT /v1/project/{projectId}/package/{packageName}` — Updates a Project Package - replacing any previous content with the new contents
- `DELETE /v1/project/{projectId}/package/{packageName}` — Deletes a Project Package
- `PATCH /v1/project/{projectId}/package/{packageName}` — Patches a Project Package - appending any provided files to the existing package

## Project - Properties
- `GET /v1/project/{projectid}/property` — Gets the Project Properties for a project
- `PUT /v1/project/{projectid}/property` — Replaces the Project Properties for a project
- `PATCH /v1/project/{projectid}/property` — Updates the Project Properties for a project

## Project - Version
- `GET /v1/project/{projectid}/version/{versionid}/artifact` — Download zipped Artifacts for a Project Version
- `GET /v1/project/{projectid}/version/{versionid}` — Gets a project Version
- `GET /v1/project/{projectid}/version` — Searches Project Versions (query: projectVersionName, projectStreamId, packageName, requestAllFiles, scmRevision, limit, offset)

## Release
- `GET /v1/releases` — Search releases (query: releaseName, releaseStatus, limit, offset)
- `POST /v1/releases` — Creates a new release
- `GET /v1/releases/{releaseId}` — Find a release with the given id
- `PUT /v1/releases/{releaseId}` — Updates the release
- `PATCH /v1/releases/{releaseId}` — Updates/Append to an existing release

## Release Gates
- `POST /v1/releases/{releaseId}/gate/approval` — Completes an Approval Gate with attributes from the given JSON body. (query: snapshotId)
- `POST /v1/releases/{releaseId}/gate/externalApproval` — Completes an External Gate with attributes from the given JSON body (query: snapshotId)

## Release Snapshots
- `GET /v1/releases/{releaseId}/snapshot` — Search Snapshots (query: snapshotName, snapshotStatus, limit)
- `POST /v1/releases/{releaseId}/snapshot` — Creates a new snapshot or Promotes a Project to a Release
- `GET /v1/releases/{releaseId}/snapshot/{snapshotId}/execution` — Find the Snapshot Execution with the given snapshot id (query: environmentId, stepName, gateName)
- `GET /v1/releases/{releaseId}/snapshot/{snapshotId}` — Find the Snapshot with the given release id

## Scheduled Tasks API
- `PUT /v1/tasks/scheduled/cancel/{taskId}` — This PUT service will reject a scheduled task with the given Id. (query: notes)
- `PUT /v1/tasks/scheduled/cancel` — This PUT service will cancel a scheduled task with the given attributes. (query: workflowRequestId, folderRequestId, pipelineStageGateExecId, pipelineStageStepExecId, projectId, applicationId, environmentId, notes)
- `GET /v1/tasks/scheduled/{taskId}` — This GET service will find a scheduled task with the given task Id and return the JSON representation of the object.
- `PUT /v1/tasks/scheduled/runnow/{taskId}` — This PUT service will run a scheduled task with the given Id. (query: notes)
- `PUT /v1/tasks/scheduled/runnow` — This PUT service will run a scheduled task with the given attributes. (query: workflowRequestId, folderRequestId, pipelineStageGateExecId, pipelineStageStepExecId, projectId, applicationId, environmentId, notes)
- `GET /v1/tasks/scheduled` — This GET service will return a list of scheduled tasks in the form of JSON objects based on a query parameter for the display name. (query: workflowRequestId, folderRequestId, pipelineStageGateExecId, pipelineStageStepExecId, projectId, applicationId, environmentId, notes)

## Topology - Integration CMSInstance
- `GET /v1/topology/integrations/cmsinstance` — This GET service will return a list of Change Management Systems in the form of JSON objects based on the query parameters code, name, and Change Management System type. (query: instanceName, instanceCode, cmsSystemName)
- `POST /v1/topology/integrations/cmsinstance` — The POST service will create a new change management system with the same attributes as the given JSON object.
- `GET /v1/topology/integrations/cmsinstance/{Id}` — This GET service will find a Change Management System with the given Id and return the JSON representation of the object.
- `PUT /v1/topology/integrations/cmsinstance/{Id}` — This PUT service will update all attributes of an Change Management System with the given Id based on the attributes of the supplied JSON object.
- `PATCH /v1/topology/integrations/cmsinstance/{Id}` — This PATCH service will update the information of the Change Management System of the specified Id with the non-null parameters of the JSON.

## Topology - Integrations Account
- `GET /v1/topology/integrations/account/{accountType}` — This GET service will return a list of account instances in the form of JSON objects based on the query parameters code, name, and provider. (query: instanceName, instanceCode, provider)
- `POST /v1/topology/integrations/account/{accountType}` — This POST service will create a new account instance with the same attributes as the given JSON object.
- `GET /v1/topology/integrations/account/{accountType}/{Id}` — This GET service will find an account instance with the given Id and return the JSON representation of the object.
- `PUT /v1/topology/integrations/account/{accountType}/{Id}` — This PUT service will update all attributes of an account instance with the given Id based on the attributes of a JSON object parameters.
- `PATCH /v1/topology/integrations/account/{accountType}/{Id}` — This PATCH service will update an existing account instance with the information passed through a JSON object.

## Topology - Integrations Issue Tracking System Instance
- `GET /v1/topology/integrations/itsinstance` — This GET service will return a list of Issue Tracking Systems in the form of JSON objects based on the query parameters code, name, and issue tracking system type. (query: instanceCode, instanceName, issueTrackingSystemName)
- `POST /v1/topology/integrations/itsinstance` — The POST service will create a new issue tracking system with the same attributes as the given JSON object.
- `GET /v1/topology/integrations/itsinstance/{Id}` — This GET service will find an Issue Tracking System with the given Id and return the JSON representation of the object.
- `PUT /v1/topology/integrations/itsinstance/{Id}` — This PUT service will update all attributes of an issue tracking system with the given Id based on the attributes of the supplied JSON object.
- `PATCH /v1/topology/integrations/itsinstance/{Id}` — This PATCH service will update the information of the Issue Tracking System of the specified Id with the non-null parameters of the JSON.

## Topology - Integrations SCMInstance
- `GET /v1/topology/integrations/scminstance` — This GET service will find a SCM instance by querying based on a name, code, and/or type of the SCM and return the JSON representations of the objects. (query: instanceName, instanceCode, scmType, isActive)
- `POST /v1/topology/integrations/scminstance` — This POST service will create a new SCM instance with the same attributes as the given JSON object.
- `GET /v1/topology/integrations/scminstance/{Id}` — This GET service will find a SCM instance with the given Id and return the JSON representation of the object.
- `PUT /v1/topology/integrations/scminstance/{Id}` — This PUT service will update all attributes of a SCM instance with the given Id based on the attributes of a JSON object parameters.
- `PATCH /v1/topology/integrations/scminstance/{Id}` — This PATCH service will update an existing SCM instance with the information passed through a JSON object. If an attribute of the JSON is null it will not be updated in the SCM instance.
- `POST /v1/topology/integrations/scminstance/test` — This POST service will test the connection.

## Topology - Targets API
- `GET /v1/topology/environmentinstance/{envId}/{instId}` — This GET service will find a target  with the given environment id and target group id. It returns the JSON representation of the target.
- `PUT /v1/topology/environmentinstance/{envId}/{instId}` — This PUT service will replace all attributes of a target with the given target corresponding to the environment id and target group id provided in the url.
- `PATCH /v1/topology/environmentinstance/{envId}/{instId}` — This PATCH service will update an existing target with the information passed through a JSON object. If an attribute of the JSON is null it will not be updated in the target.
- `POST /v1/topology/environmentinstance/{envId}/{instId}/initiatepostrefresh` — This POST service will perform the same action found on the Post Refresh requests form off of the target page.

## Workflow Execution
- `GET /v1/workflowexecution/{workflowExecutionId}/logs` — Download zipped logs for a Workflow Execution with the given Id
- `GET /v1/workflowexecution/{workflowExecutionId}` — Find a Workflow Execution with the given Id
- `GET /v1/workflowexecution` — Search Workflow Executions (query: workflowExecutionId, workflowRequestId, parentWorkflowRequestId, projectId, projectVersionId, projectWorkflowId, workflowVersionId, environmentId, instanceId, predeployWorkflowExecId, executionStatus, dockerImageName, workflowId, workflowType, reviewStatus, limit, offset)

## Workflow Request
- `GET /v1/workflowrequest/{workflowRequestId}` — Finds a Workflow Request with the given Id.

