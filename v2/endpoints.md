# FlexDeploy v2 REST endpoint index

Base: `https://<host>/flexdeploy/rest` + path. Grouped by tag.

## Contents
- Administration - Admin Operations
- Administration - Incoming Webhook Function
- Administration - Incoming Webhook Message
- Administration - Incoming Webhook Provider
- Administration - Outgoing Webhook Event Listener
- Administration - Outgoing Webhook Event Message Listener
- Administration - Property Key Definition
- Administration - Property Set
- Administration - Resource Type
- Administration - Scheduled Event Function
- Administration - Scheduled Event Message Function
- Attachment
- Change Ticket
- Configuration
- Flex Work Item
- Folder
- Group
- Integration AccountProvider
- Pipeline Attachment
- Plugin Execution
- Project
- Project - Artifact
- Project - Backup
- Project - Branch
- Project - Execution
- Project - Files
- Project - Package
- Project - Template
- Project - Test Configuration
- Project - Version
- Release
- Release Content
- Release Property
- Release Snapshots
- SCM Revisions
- Search
- Security - Credential
- Security - Credential Store
- Security - Credential Store Provider
- Security - Group Member
- Security - User
- Tasks
- Topology - Endpoint
- Topology - Environment
- Topology - Integration Instance
- Topology - Integration Instance Properties
- Topology - Target
- Topology - Target Group
- Topology - Target Properties
- Topology - Test Instance
- Topology - Test Instance Properties
- Work Item
- Workflow
- Workflow Execution
- Workflow Execution - Report
- Workflow Request
- Workflow Version

## Administration - Admin Operations
- `GET /v2/administration/adminoperations/logFileDownload` — Download a single log file for the given fileName (query: fileName, numberOfLines)
- `GET /v2/administration/adminoperations/logFileDownloadAll` — Download all the Logs in zip format (query: withThreadDumps)

## Administration - Incoming Webhook Function
- `GET /v2/administration/incomingwebhooks/function/{Id}` — Find an Incoming Webhook Function with the given Id
- `PUT /v2/administration/incomingwebhooks/function/{Id}` — Updates all attributes of an Incoming Webhook Function with the given Id based on the attributes of a JSON object parameters
- `DELETE /v2/administration/incomingwebhooks/function/{Id}` — Deletes an existing Incoming Webhook Function.
- `PATCH /v2/administration/incomingwebhooks/function/{Id}` — Updates an existing Incoming Webhook Function with the information passed through a JSON object. If an attribute of the JSON is null it will not be updated.
- `GET /v2/administration/incomingwebhooks/function` — Returns a list of Incoming Webhook Functions in the form of JSON objects based on the query parameters functionId, name, isActive, uri, and providerId. Does not return Function Script. (query: functionId, name, isActive, uri, providerId, limit, offset)
- `POST /v2/administration/incomingwebhooks/function` — Creates a new Incoming Webhook Function with attributes from the given JSON body

## Administration - Incoming Webhook Message
- `GET /v2/administration/incomingwebhooks/message/{Id}` — Find an Incoming Webhook Message with the given Id
- `POST /v2/administration/incomingwebhooks/message/{Id}` — Resubmits an Incoming Webhook Message and payload from the given Id
- `GET /v2/administration/incomingwebhooks/message` — Returns a list of Incoming Webhook Messages in the form of JSON objects based on the query parameters webhookMessageId, providerId, message, status and incomingUri. Does not return Functions, Logs, and Payload. (query: webhookMessageId, providerId, message, status, incomingURI, limit, offset)

## Administration - Incoming Webhook Provider
- `GET /v2/administration/incomingwebhooks/provider/{Id}` — Find an Incoming Webhook Provider with the given Id
- `PUT /v2/administration/incomingwebhooks/provider/{Id}` — Updates all attributes of an Incoming Webhook Provider with the given Id based on the attributes of a JSON object parameters
- `DELETE /v2/administration/incomingwebhooks/provider/{Id}` — Deletes an existing Incoming Webhook Provider.
- `PATCH /v2/administration/incomingwebhooks/provider/{Id}` — Updates an existing Incoming Webhook Provider with the information passed through a JSON object. If an attribute of the JSON is null it will not be updated.
- `GET /v2/administration/incomingwebhooks/provider` — Returns a list of Incoming Webhook Providers in the form of JSON objects based on the query parameters providerId, name, isActive, and sequenceNumber. Does not return Functions, Properties, and Match Script. (query: providerId, name, isActive, sequenceNumber, limit, offset)
- `POST /v2/administration/incomingwebhooks/provider` — Creates a new Incoming Webhook Provider with attributes from the given JSON body

## Administration - Outgoing Webhook Event Listener
- `GET /v2/administration/outgoingwebhooks/listener/{Id}` — Find an Event Listener with the given Id
- `PUT /v2/administration/outgoingwebhooks/listener/{Id}` — Updates all attributes of an Event Listener with the given Id based on the attributes of a JSON object parameters
- `PATCH /v2/administration/outgoingwebhooks/listener/{Id}` — Updates an existing Event Listener with the information passed through a JSON object. If an attribute of the JSON is null it will not be updated.
- `GET /v2/administration/outgoingwebhooks/listener` — Returns a list of Event Listeners in the form of JSON objects based on the query parameters EventListenerId, EventListenerName, isActive, and description. (query: eventListenerId, eventListenerName, isActive, description, limit, offset)
- `POST /v2/administration/outgoingwebhooks/listener` — Creates a new Event Listener with attributes from the given JSON body

## Administration - Outgoing Webhook Event Message Listener
- `GET /v2/administration/outgoingwebhooks/eventmessagelistener/{Id}` — Find an Outgoing Webhook Event Message Listener with the given Id
- `POST /v2/administration/outgoingwebhooks/eventmessagelistener/{Id}` — Resubmits an Outgoing Webhook Event Message and payload from the given Id
- `GET /v2/administration/outgoingwebhooks/eventmessagelistener` — Returns a list of Outgoing Webhook Event Message Listeners in the form of JSON objects based on the query parameters eventMessageListenerId, eventListenerId, message and status. (query: eventMessageListenerId, eventListenerId, message, status, limit, offset)

## Administration - Property Key Definition
- `GET /v2/administration/propertykeydefinition` — Search Property Key Definitions (query: propertyDefinitionId, propertyKeyName, displayName, isActive, propertyScope, isCustom, description, isMultiSelect, isAllowsVariant, IsDefaultExpression, limit, offset)
- `POST /v2/administration/propertykeydefinition` — Creates a new Property Key Definition with attributes from the given JSON body
- `GET /v2/administration/propertykeydefinition/{Id}` — Find a Property Key Definition with the given Id
- `PUT /v2/administration/propertykeydefinition/{Id}` — Updates an existing Property Key Definition with the information passed through a JSON object
- `PATCH /v2/administration/propertykeydefinition/{Id}` — Updates an existing Property Key Definition with the information passed through a JSON object. If an attribute of the JSON is null, it will not be updated.

## Administration - Property Set
- `GET /v2/administration/propertyset/{Id}` — Find a Property Set with the given Id
- `PUT /v2/administration/propertyset/{Id}` — Updates an existing Workflow Property Set with the information passed through a JSON object
- `GET /v2/administration/propertyset` — Search Property Sets (query: propertySetId, propertySetName, ownerId, isActive, ownerType, limit, offset)

## Administration - Resource Type
- `GET /v2/administration/resourcetype/{Id}` — 
- `PUT /v2/administration/resourcetype/{Id}` — 
- `DELETE /v2/administration/resourcetype/{Id}` — 
- `PATCH /v2/administration/resourcetype/{Id}` — 
- `GET /v2/administration/resourcetype` — Search Resource Types (query: resourceTypeId, resourceTypeName, description, isActive, ownerType, limit, offset)
- `POST /v2/administration/resourcetype` — Create Resource Type

## Administration - Scheduled Event Function
- `GET /v2/administration/scheduledevents/function/{Id}` — Find a Scheduled Event Function with the given Id
- `PUT /v2/administration/scheduledevents/function/{Id}` — Updates all attributes of a Scheduled Event Function with the given Id based on the attributes of a JSON object parameters
- `PATCH /v2/administration/scheduledevents/function/{Id}` — Updates an existing Scheduled Event Function with the information passed through a JSON object. If an attribute of the JSON is null it will not be updated.
- `GET /v2/administration/scheduledevents/function` — Returns a list of Scheduled Event Functions in the form of JSON objects based on the query parameters eventListenerId, eventListenerName, isActive, description, and cronExpression. (query: eventListenerId, eventListenerName, isActive, description, cronExpression, limit, offset)
- `POST /v2/administration/scheduledevents/function` — Creates a new Scheduled Event Function with attributes from the given JSON body

## Administration - Scheduled Event Message Function
- `GET /v2/administration/scheduledevents/messagefunction/{Id}` — Find an Scheduled Event Message Function with the given Id
- `POST /v2/administration/scheduledevents/messagefunction/{Id}` — Resubmits an Scheduled Event Message and payload from the given Id
- `GET /v2/administration/scheduledevents/messagefunction` — Returns a list of Scheduled Event Message Functions in the form of JSON objects based on the query parameters eventMessageListenerId, eventListenerId, message and status. (query: eventMessageListenerId, eventListenerId, message, status, limit, offset)

## Attachment
- `DELETE /v2/attachment/{attachmentId}` — Deletes an attachment using the given id
- `GET /v2/attachment/download/{attachmentId}` — Download an attachment using the given id (query: inline)
- `POST /v2/attachment/upload` — Uploads an attachment. The file should be specified in the 'file' field in a multipart form data post.

## Change Ticket
- `GET /v2/changeticket/{Id}` — Find an Change Ticket with the given Id
- `PUT /v2/changeticket/{Id}` — Updates all attributes of an Change Ticket with the given Id based on the attributes of a JSON object parameters
- `DELETE /v2/changeticket/{Id}` — Deletes an existing Change Ticket.
- `PATCH /v2/changeticket/{Id}` — Updates an existing Change Ticket with the information passed through a JSON object. If an attribute of the JSON is null it will not be updated.
- `GET /v2/changeticket` — Search Change Tickets (query: cmsTicketId, ticketNumber, ticketType, description, cmsId, instanceId, limit, offset)
- `POST /v2/changeticket` — Creates a new Change Ticket with attributes from the given JSON body

## Configuration
- `GET /v2/configuration/export/{token}` — Download an export zip file for a given token.
- `GET /v2/configuration/export/{token}/status` — Returns the status of the export request for a given token.
- `GET /v2/configuration/import/{token}/status` — Returns the status of the import request for a given token.
- `POST /v2/configuration/export` — Submits an export request.
- `POST /v2/configuration/import` — Submits an import request.

## Flex Work Item
- `POST /v2/flexworkitem/{flxWorkItemId}/comment` — add a Flex Work Item Comment with attributes from the given JSON body
- `GET /v2/flexworkitem` — Returns a list of Flex Work Items in the form of JSON objects based on the query parameters code and name. (query: flexWorkItemId, status, title, type, limit, offset)
- `POST /v2/flexworkitem` — Creates a new Flex Work Item with attributes from the given JSON body
- `GET /v2/flexworkitem/field` — Returns a list of Flex Work Item Fields in the form of JSON objects based on the query parameters code and name. (query: propertyDefinitionId, isActive, code, displayName, isRequired, propertyKeyDatatype, flxWorkItemType, groupKey, limit, offset)
- `POST /v2/flexworkitem/field` — Creates a new Flex Work Item Field with attributes from the given JSON body
- `GET /v2/flexworkitem/fieldgroup` — Returns a list of Flex Work Item Groups in the form of JSON objects based on the query parameters code and name. (query: groupKey, name, isActive, sortNumber, limit, offset)
- `POST /v2/flexworkitem/fieldgroup` — Creates a new Flex Work Item Field Group with attributes from the given JSON body
- `GET /v2/flexworkitem/{flxWorkItemId}` — Find a Flex Work Item with the given Id
- `PUT /v2/flexworkitem/{flxWorkItemId}` — Updates all attributes of a Flex Work Item with the given Id based on the attributes of a JSON object parameters
- `DELETE /v2/flexworkitem/{flxWorkItemId}` — Deletes an existing Flex Work Item.
- `PATCH /v2/flexworkitem/{flxWorkItemId}` — Updates an existing Flex Work Item with the information passed through a JSON object. If an attribute of the JSON is null it will not be updated.
- `GET /v2/flexworkitem/field/{flxWorkItemFieldId}` — Find a Flex Work Item Field with the given Id
- `PUT /v2/flexworkitem/field/{flxWorkItemFieldId}` — Updates all attributes of a Flex Work Item Field with the given Id based on the attributes of a JSON object parameters
- `DELETE /v2/flexworkitem/field/{flxWorkItemFieldId}` — Deletes an existing Flex Work Item Field.
- `PATCH /v2/flexworkitem/field/{flxWorkItemFieldId}` — Updates an existing Flex Work Item Field with the information passed through a JSON object. If an attribute of the JSON is null it will not be updated.
- `GET /v2/flexworkitem/fieldgroup/{flxWorkItemFieldGroupCode}` — Find a Flex Work Item Field Group with the given Code
- `PUT /v2/flexworkitem/fieldgroup/{flxWorkItemFieldGroupCode}` — Updates all attributes of a Flex Work Item Group with the given Id based on the attributes of a JSON object parameters
- `DELETE /v2/flexworkitem/fieldgroup/{flxWorkItemFieldGroupCode}` — Deletes an existing Flex Work Item Field Group.
- `PATCH /v2/flexworkitem/fieldgroup/{flxWorkItemFieldGroupCode}` — Updates an existing Flex Work Item Field Group with the information passed through a JSON object. If an attribute of the JSON is null it will not be updated.
- `GET /v2/flexworkitem/status/{statusId}` — Find a Flex Work Item Status with the given Id
- `GET /v2/flexworkitem/type/{code}` — Find a Flex Work Item Type with the given Id
- `GET /v2/flexworkitem/{flxWorkItemId}/field` — Gets the fields of a Flex Work Item given the Flex Work Item id.
- `PATCH /v2/flexworkitem/{flxWorkItemId}/comment/{flxWorkItemCommentId}` — update an existing Flex Work Item Comment with the information passed through a JSON object. If an attribute of the JSON is null it   will not be updated.
- `PUT /v2/flexworkitem/fields/{flxWorkItemFieldGroupCode}` — Updates all attributes of all Flex Work Item Fields within a Field Group with the given key based on the attributes of a JSON object parameters
- `PATCH /v2/flexworkitem/{flxWorkItemId}/field/{fieldName}` — Updates an existing Flex Work Item field with the information passed through a JSON object. If an attribute of the JSON is null it will not be updated.
- `GET /v2/flexworkitem/status` — Returns a list of Flex Work Item Statuses in the form of JSON objects based on the query parameters code and name. (query: statusId, name, isActive, limit, offset)
- `GET /v2/flexworkitem/type` — Returns a list of Flex Work Item Types in the form of JSON objects based on the query parameters code and name. (query: code, color, isActive, name, limit, offset)
- `POST /v2/flexworkitem/{flxWorkItemId}/attachment/upload` — 

## Folder
- `GET /v2/folder/{Id}` — Find a Folder with the given Id
- `PUT /v2/folder/{Id}` — Updates all attributes of a Folder with the given Id based on the attributes of a JSON object parameters
- `DELETE /v2/folder/{Id}` — Deletes an existing Folder.
- `PATCH /v2/folder/{Id}` — Updates an existing Folder with the information passed through a JSON object. If an attribute of the JSON is null it will not be updated.
- `GET /v2/folder` — Search Folders (query: folderId, folderName, description, isActive, parentFolderId, limit, offset)
- `POST /v2/folder` — Creates a new Folder with attributes from the given JSON body

## Group
- `GET /v2/administration/security/group/{Id}` — Find a Group with the given Id
- `PUT /v2/administration/security/group/{Id}` — Updates all attributes of a Group with the given Id based on the attributes of a JSON object parameters
- `PATCH /v2/administration/security/group/{Id}` — Updates an existing Group with the information passed through a JSON object. If an attribute of the JSON is null it will not be updated.
- `GET /v2/administration/security/group` — Search Groups (query: groupId, groupName, isActive, description, limit, offset)
- `POST /v2/administration/security/group` — Creates a new Group from the given JSON body

## Integration AccountProvider
- `POST /v2/integrations/account` — Creates a new account provider with attributes from the given JSON body
- `GET /v2/integrations/account/{accountProviderId}` — Find an account provider detail with the given id
- `PUT /v2/integrations/account/{accountProviderId}` — Updates all attributes of a Account Provider with the given Id based on the attributes of a JSON object parameters
- `DELETE /v2/integrations/account/{accountProviderId}` — Deletes an existing Account Provider.
- `PATCH /v2/integrations/account/{accountProviderId}` — Updates an existing Account Provider with the information passed through a JSON object. If an attribute of the JSON is null it will not be updated.

## Pipeline Attachment
- `GET /v2/pipeline/attachment/download/{attachmentId}` — Download an attachment using the given id (query: inline)

## Plugin Execution
- `GET /v2/pluginexecution/{pluginExecutionId}/{endpointId}/logs` — Find the logs for a given pluginExecutionId and endpointId

## Project
- `GET /v2/project/{Id}` — Find a Project with the given Id
- `PUT /v2/project/{Id}` — Updates all attributes of a Project with the given Id based on the attributes of a JSON object parameters
- `DELETE /v2/project/{Id}` — Deletes an existing Project.
- `PATCH /v2/project/{Id}` — Updates an existing Project with the information passed through a JSON object. If an attribute of the JSON is null it will not be updated.
- `GET /v2/project` — Search Projects (query: projectId, projectName, projectType, isActive, projectClassification, folderId, packageBuildType, packageNameSyntax, scmType, webhooksEnabled, limit, offset)
- `POST /v2/project` — Creates a new Project with attributes from the given JSON body

## Project - Artifact
- `GET /v2/project/{projectId}/version/{projectVersionId}/artifact/file` — Download a single artifact file for the given ProjectId and ProjectVersionId (query: relativeFilePath)
- `GET /v2/project/{projectId}/version/{projectVersionId}/artifact/all` — Download the artifacts in zip format for the given ProjectId and ProjectVersionId
- `GET /v2/project/{projectId}/version/{projectVersionId}/artifact` — List the artifacts for the given ProjectId and ProjectVersionId

## Project - Backup
- `GET /v2/workflowexecution/{workflowExecutionId}/backup/file` — Download a single backup file for the given WorkflowExecutionId (query: relativeFilePath)
- `GET /v2/workflowexecution/{workflowExecutionId}/backup/all` — Download the backups in zip format for the given WorkflowExecutionId
- `GET /v2/workflowexecution/{workflowExecutionId}/backup` — List the backups for the given WorkflowExecutionId

## Project - Branch
- `GET /v2/project/{projectId}/branch/{branchId}` — Find a Project Branch with the given Id
- `PUT /v2/project/{projectId}/branch/{branchId}` — Updates all attributes of a Project Branch with the given Id based on the attributes of a JSON object parameters
- `PATCH /v2/project/{projectId}/branch/{branchId}` — Updates an existing Project Branch with the information passed through a JSON object. If an attribute of the JSON is null it will not be updated.
- `GET /v2/project/{projectId}/branch` — Search Project Branches (query: branchId, branchName, isActive, mainBranchFlag, versionSyntax, attribute1, attribute2, attribute3, description, limit, offset)
- `POST /v2/project/{projectId}/branch` — Creates a new Project Branch with attributes from the given JSON body

## Project - Execution
- `GET /v2/projectworkflowexecution/{executionId}` — Find a Workflow Execution with the given Id
- `GET /v2/projectworkflowexecution` — Search Workflow Executions (query: projectId, packageName, environmentId, relDefinitionId, projectBranchId, workflowType, limit, offset)

## Project - Files
- `GET /v2/project/{projectId}/projectobject` — Search Project Objects by project id, project object id, active status, object path, and object type id. Project Object attributes are not returned. Use the GET by id method to retrieve attributes. (query: projectObjectId, isActive, objectPath, objectTypeId, offset, limit)
- `POST /v2/project/{projectId}/projectobject` — Creates a new Project Object with attributes from the given JSON body
- `POST /v2/project/{projectId}/projectobject/environment/{environmentId}/discoverfrombackend` — Discover files (synchronous) from a backend system for the given EnvironmentId based on the attributes of a JSON object parameters
- `POST /v2/project/{projectId}/projectobject/environment/{environmentId}/discoverfrombackendasync` — Discover files (asynchronous) from a backend system for the given EnvironmentId based on the attributes of a JSON object parameters
- `GET /v2/project/{projectId}/projectobject/discoverfromsap` — Discover files (synchronous) from SAP.
- `POST /v2/project/{projectId}/projectobject/stream/{branchId}/discoverfromscm` — Discover files (synchronous) from SCM for the given BranchId based on the attributes of a JSON object parameters
- `POST /v2/project/{projectId}/projectobject/stream/{branchId}/discoverfromscmasync` — Discover files (asynchronous) from SCM for the given BranchId based on the attributes of a JSON object parameters
- `POST /v2/project/{projectId}/projectobject/evaluateone` — ReEvaluate a project file based on the attributes of a JSON object parameters
- `POST /v2/project/{projectId}/projectobject/evaluatemany` — ReEvaluate many project files based on the attributes of a JSON object parameters
- `GET /v2/project/{projectId}/projectobject/discoverstatus` — Refresh SAP Change Request (synchronous).
- `GET /v2/project/{projectId}/projectobject/{projectObjectId}` — Find a Project Object with the given Id
- `PUT /v2/project/{projectId}/projectobject/{projectObjectId}` — Updates all attributes of an Project Object with the given Id based on the attributes of a JSON object parameters
- `PATCH /v2/project/{projectId}/projectobject/{projectObjectId}` — Updates an existing Project Object with the information passed through a JSON object. If an attribute of the JSON is null it will not be updated. The projectObjectAttributes list values will be replaced by the given projectObjectAttributes list if one is provided. If projectObjectAttributes is not provided, then the existing list will be retained.
- `GET /v2/project/{projectId}/projectobject/refreshsapchangerequest/{changeRequestNumber}` — Refresh SAP Change Request (synchronous).

## Project - Package
- `GET /v2/project/{projectId}/package` — Search Project Packages (query: projectPackageId, description, excludePath, includePath, packageName, packagePath, packageStatus, packageType, tests, testLevel, versionSyntax, limit, offset)
- `POST /v2/project/{projectId}/package` — Creates a new Project Package with attributes from the given JSON body in the given Project
- `GET /v2/project/{projectId}/package/{packageId}` — Find a Project Package with the given Id
- `PUT /v2/project/{projectId}/package/{packageId}` — Updates all attributes of a Project Package with the given Id based on the attributes of a JSON object parameters
- `DELETE /v2/project/{projectId}/package/{packageId}` — Deletes an existing Project Package.
- `PATCH /v2/project/{projectId}/package/{packageId}` — Updates an existing Project Package with the information passed through a JSON object. If an attribute of the JSON is null it will not be updated in the environment.

## Project - Template
- `POST /v2/projecttemplate/create` — Creates Projects, Git SCM Instances, and Folders as applicable based on input parsed Project Template objects.
- `POST /v2/projecttemplate/download` — Downloads a template csv based on the data provided. Information can be added to the template to be used in parse and create methods.
- `POST /v2/projecttemplate/parse` — Parses and validates CSV file input, and returns a list of the parsed Project Template objects.

## Project - Test Configuration
- `GET /v2/project/{projectId}/testconfig/{projectTestConfigId}` — Find a Project Test Configuration with the given Id
- `PUT /v2/project/{projectId}/testconfig/{projectTestConfigId}` — Updates all attributes of a Project Test Configuration with the given Id based on the attributes of a JSON object parameters
- `DELETE /v2/project/{projectId}/testconfig/{projectTestConfigId}` — Deletes an existing Project Test Configuration.
- `PATCH /v2/project/{projectId}/testconfig/{projectTestConfigId}` — Updates an existing Project Test Configuration with the information passed through a JSON object. If an attribute of the JSON is null it will not be updated.
- `GET /v2/project/{projectId}/testconfig` — Search Project Test Configurations (query: projectTestConfigId, isActive, limit, offset)
- `POST /v2/project/{projectId}/testconfig` — Creates a new Project Test Configuration with attributes from the given JSON body

## Project - Version
- `POST /v2/project/{projectId}/version/{versionId}/activate` — Activates a project version that was inactivated previously.
- `POST /v2/project/{projectId}/version/{versionId}/workitem/{workItemId}` — Adds a work item to a project version.
- `DELETE /v2/project/{projectId}/version/{versionId}/workitem/{workItemId}` — Removes a work item from a project version.
- `GET /v2/project/{projectId}/version/{versionId}` — Find a Project Version with the given Id
- `POST /v2/project/{projectId}/version/{versionId}/inactivate` — Inactivates an active project version.
- `POST /v2/project/{projectId}/version/{versionId}/promote` — Promotes a project version to create a release snapshot.
- `GET /v2/project/{projectId}/version` — Search Project Versions (query: projectVersionName, projectStreamId, packageName, scmRevision, limit, offset)

## Release
- `GET /v2/release` — Search releases (query: releaseId, releaseName, releaseStatus, pipelineId, limit, offset)
- `POST /v2/release` — Creates a new release with attributes from the given JSON body
- `GET /v2/release/{Id}` — Find a release with the given id
- `PUT /v2/release/{Id}` — Updates all attributes of a release with the given id based on the attributes of the provided JSON object
- `PATCH /v2/release/{Id}` — Updates an existing release with the information passed through a JSON object. If an attribute of the provided JSON is null, it will not be updated.

## Release Content
- `GET /v2/release/{releaseId}/content` — Returns a list of Release Projects in the form of JSON objects based on the query parameters relProjectId, projectId, projectBranchId, packageName, and projectGroups. (query: relProjectId, projectId, projectBranchId, packageName, projectGroups, limit, offset)
- `POST /v2/release/{releaseId}/content` — Creates a new release project with attributes from the given JSON body
- `GET /v2/release/{releaseId}/content/{releaseProjectId}` — Find a Release Project with given releaseId and releaseProjectId
- `PUT /v2/release/{releaseId}/content/{releaseProjectId}` — Updates all attributes of a release project with the given id based on the attributes of the provided JSON object
- `DELETE /v2/release/{releaseId}/content/{releaseProjectId}` — Deletes an existing Release Project.
- `PATCH /v2/release/{releaseId}/content/{releaseProjectId}` — Updates an existing release project with the information passed through a JSON object. If an attribute of the provided JSON is null, it will not be updated.

## Release Property
- `GET /v2/release/{releaseId}/property` — Find Release Properties for given releaseId
- `PUT /v2/release/{releaseId}/property` — Updates all properties of a Release with the given id based on the attributes of a list of JSON object parameters. Properties not passed in will have value defaulted.
- `PATCH /v2/release/{releaseId}/property` — Updates all properties of a Release with the given id based on the attributes of a list of JSON object parameters. Properties not passed in will be ignored.

## Release Snapshots
- `GET /v2/release/{releaseId}/snapshot` — Search Snapshots (query: snapshotName, snapshotStatus, limit, offset)
- `POST /v2/release/{releaseId}/snapshot` — Creates a new snapshot for a Release
- `GET /v2/release/{releaseId}/snapshot/{snapshotId}` — Find a snapshot with the given releaseId and snapshotId

## SCM Revisions
- `GET /v2/project/{projectId}/branch/{branchId}/revision/file/{projectObjectId}` — Search SCM Revisions for related to a given ProjectObjectId (query: limit)
- `GET /v2/project/{projectId}/branch/{branchId}/revision` — Search SCM Revisions for a given ProjectId and BranchId (query: limit)

## Search
- `POST /v2/search` — Global Search API (query: limit, offset)

## Security - Credential
- `DELETE /v2/administration/security/credential/{credentialId}` — Deletes an existing Credential.
- `POST /v2/administration/security/credential/downloadPublicKey` — Downloads a public key based on the information passed through a JSON object. Credential id must be of type SSH Key, and private key must be encoded to Base64 if passed.
- `GET /v2/administration/security/credential/downloadPublicKey/{credentialId}` — Downloads a public key based on the credential id. Credential must be of type SSH Key.
- `GET /v2/administration/security/credential/{Id}` — Find a Credential with the given Id
- `PUT /v2/administration/security/credential/{Id}` — Updates all attributes of an Credential with the given Id based on the attributes of a JSON object parameters
- `PATCH /v2/administration/security/credential/{Id}` — Updates an existing Credential with the information passed through a JSON object. If an attribute of the JSON is null it will not be updated.
- `GET /v2/administration/security/credential` — Search Credentials (query: credentialId, credentialName, credentialScope, credentialStoreId, limit, offset)
- `POST /v2/administration/security/credential` — Creates a new Credential with attributes from the given JSON body
- `POST /v2/administration/security/credential/test` — Test Credential using JDBC or basic authentication

## Security - Credential Store
- `GET /v2/administration/security/credentialstore/{Id}` — Find a Credential Store with the given Id
- `PUT /v2/administration/security/credentialstore/{Id}` — Updates all attributes of a Credential Store with the given Id based on the attributes of a JSON object parameters
- `PATCH /v2/administration/security/credentialstore/{Id}` — Updates an existing Credential Store with the information passed through a JSON object. If an attribute of the JSON is null it will not be updated.
- `GET /v2/administration/security/credentialstore` — Search Credential Stores (query: credentialStoreId, credentialStoreDefId, credentialStoreName, description, isActive, limit, offset)
- `POST /v2/administration/security/credentialstore` — Creates a new Credential Store with attributes from the given JSON body

## Security - Credential Store Provider
- `GET /v2/administration/security/credentialstoreprovider/{Id}` — Find a Credential Store Provider with the given Id
- `PUT /v2/administration/security/credentialstoreprovider/{Id}` — Updates all attributes of a Credential Store Provider with the given Id based on the attributes of a JSON object parameters
- `PATCH /v2/administration/security/credentialstoreprovider/{Id}` — Updates an existing Credential Store Provider with the information passed through a JSON object. If an attribute of the JSON is null it will not be updated.
- `GET /v2/administration/security/credentialstoreprovider` — Search Credential Store Providers (query: credentialStoreProviderId, credentialStoreProviderName, implementationClass, isActive, isCustom, limit, offset)
- `POST /v2/administration/security/credentialstoreprovider` — Creates a new Credential Store Provider with attributes from the given JSON body

## Security - Group Member
- `POST /v2/administration/security/groupmember/{GroupId}/{UserId}` — Assigns Group to User with the provided data.
- `DELETE /v2/administration/security/groupmember/{GroupId}/{UserId}` — Unassigns Group from User with the provided data.

## Security - User
- `GET /v2/administration/security/user/{Id}` — Find a User with the given Id
- `PUT /v2/administration/security/user/{Id}` — Updates all attributes of a User with the given Id based on the attributes of a JSON object parameters
- `PATCH /v2/administration/security/user/{Id}` — Updates an existing User with the information passed through a JSON object. If an attribute of the JSON is null it will not be updated.
- `GET /v2/administration/security/user` — Search Users (query: userId, userName, firstName, lastName, email, isActive, localUser, limit, offset)
- `POST /v2/administration/security/user` — Creates a new User with attributes from the given JSON body

## Tasks
- `PUT /v2/tasks/approve/{Id}` — Approves a Task with the given taskId
- `PUT /v2/tasks/assign/{Id}` — Assign a Task with the given taskId
- `GET /v2/tasks/{Id}` — Find a Task with given taskId
- `PUT /v2/tasks/reject/{Id}` — Rejects a Task with the given taskId
- `GET /v2/tasks` — Returns a list of Tasks in the form of JSON objects based on the query parameters. (query: taskId, myTasksOnly, taskStatus, taskNotes, taskType, workflowRequestId, workflowFolderId, pipelineStageExecId, projectId, projectName, pipelineStageStepExecId, environmentId, environmentName, projectVersionName, externalId, externalSystemId, externalSystemType, packageName, groupName, gateName, pipelineStageGateExecId, stageName, stepName, relSnapshot, relName, relSnapshotId, pipelineName, relDefinitionId, pipelineDefinitionId, groupId, workflowExecutionId, limit, offset)
- `PUT /v2/tasks/unassign/{Id}` — Unssign a Task with the given taskId

## Topology - Endpoint
- `DELETE /v2/topology/endpoint/{endpointId}` — Deletes an existing Endpoint.
- `GET /v2/topology/endpoint/{Id}` — Get Endpoint by ID
- `PUT /v2/topology/endpoint/{Id}` — Updates all attributes of an Endpoint with the given Id based on the attributes of a JSON object parameters
- `PATCH /v2/topology/endpoint/{Id}` — Updates an existing Endpoint with the information passed through a JSON object. If an attribute of the JSON is null it will not be updated.
- `GET /v2/topology/endpoint` — Search Endpoints (query: endpointId, baseDirectory, isBaseDirectoryExpr, connectionType, description, endpointAddress, endpointPort, endpointGroup, endpointSubgroup, endpointName, isActive, javaPath, isJavaPathExpr, osType, privateKeyCredentialId, username, passwordCredentialId, privilegeEscalation, runAsUsername, limit, offset, transferProtocol)
- `POST /v2/topology/endpoint` — Creates a new Endpoint with attributes from the given JSON body
- `POST /v2/topology/endpoint/test` — Test Endpoint
- `GET /v2/topology/endpoint/{Id}/test` — Test Endpoint

## Topology - Environment
- `GET /v2/topology/environment/{Id}` — Find an Environment with the given Id
- `PUT /v2/topology/environment/{Id}` — Updates all attributes of an Environment with the given Id based on the attributes of a JSON object parameters
- `DELETE /v2/topology/environment/{Id}` — Deletes an existing Environment.
- `PATCH /v2/topology/environment/{Id}` — Updates an existing Environment with the information passed through a JSON object. If an attribute of the JSON is null it will not be updated.
- `GET /v2/topology/environment` — Returns a list of Environments in the form of JSON objects based on the query parameters code and name. (query: environmentId, environmentCode, environmentName, isActive, isBuildEnvironment, sortNumber, limit, offset)
- `POST /v2/topology/environment` — Creates a new Environment with attributes from the given JSON body

## Topology - Integration Instance
- `GET /v2/topology/integrationinstance/{Id}` — Find an Integration Instance with the given Id
- `PUT /v2/topology/integrationinstance/{Id}` — Updates all attributes of an Integration Instance with the given Id based on the attributes of a JSON object parameters
- `DELETE /v2/topology/integrationinstance/{Id}` — Deletes an existing Integration Instance.
- `PATCH /v2/topology/integrationinstance/{Id}` — Updates an existing Integration Instance with the information passed through a JSON object. If an attribute of the JSON is null it will not be updated.
- `GET /v2/topology/integrationinstance` — Search Integration Instances (query: instanceId, instanceCode, instanceName, type, subType, isActive, limit, offset)
- `POST /v2/topology/integrationinstance` — Creates a new Integration Instance with attributes from the given JSON body
- `POST /v2/topology/integrationinstance/test` — Tests an existing Integration Instance with the information passed through a JSON object. (query: type, subType)

## Topology - Integration Instance Properties
- `GET /v2/topology/integrationinstance/{id}/property` — Find Properties for a given IntegrationInstanceId
- `PUT /v2/topology/integrationinstance/{id}/property` — Updates all attributes of an Integration Instance with the given Id based on the attributes of a JSON object parameters
- `PATCH /v2/topology/integrationinstance/{id}/property` — Updates an existing environment with the information passed through a JSON object. If an attribute of the JSON is null it will not be updated.

## Topology - Target
- `GET /v2/topology/target` — Search Targets (query: targetGroupId, environmentId, createdBy, updatedBy, limit, offset)
- `POST /v2/topology/target` — Creates a new Target with attributes from the given JSON body
- `GET /v2/topology/target/{Id}` — Get Target by id
- `PUT /v2/topology/target/{Id}` — Updates all attributes of a Target with the given Id based on the attributes of a JSON object parameters
- `PATCH /v2/topology/target/{Id}` — Updates an existing Target with the information passed through a JSON object. If an attribute of the JSON is null, it will not be updated.
- `POST /v2/topology/target/{Id}/initiatepostrefresh` — This POST service will perform the same action found on the Post Refresh Requests form on the target page.

## Topology - Target Group
- `DELETE /v2/topology/targetgroup/{targetGroupId}` — Deletes an existing TargetGroup.
- `GET /v2/topology/targetgroup/{Id}` — Get Target Group by ID
- `PUT /v2/topology/targetgroup/{Id}` — Updates all attributes of a Target Group with the given Id based on the attributes of a JSON object parameters
- `PATCH /v2/topology/targetgroup/{Id}` — Updates an existing Target Group with the information passed through a JSON object. If an attribute of the JSON is null it will not be updated.
- `GET /v2/topology/targetgroup` — Search Target Groups (query: targetGroupId, targetGroupCode, targetGroupName, groupCode, subGroupCode, isActive, limit, offset)
- `POST /v2/topology/targetgroup` — Creates a new Target Group with attributes from the given JSON body

## Topology - Target Properties
- `GET /v2/topology/target/{id}/property` — Get Target properties by id
- `PUT /v2/topology/target/{id}/property` — Updates all properties of a Target with the given id based on the attributes of a list of JSON object parameters
- `PATCH /v2/topology/target/{id}/property` — Updates properties of a Target with the given id based on the attributes of a list of JSON object parameters. Only properties passed in will be updated. If an attribute within the property JSON is null, it will not be updated.

## Topology - Test Instance
- `GET /v2/topology/testinstance/{Id}` — Find a Test Instance with the given Id
- `PUT /v2/topology/testinstance/{Id}` — Updates all attributes of a Test Instance with the given Id based on the attributes of a JSON object parameters
- `DELETE /v2/topology/testinstance/{Id}` — Deletes an existing Test Instance.
- `PATCH /v2/topology/testinstance/{Id}` — Updates an existing Test Instance with the information passed through a JSON object. If an attribute of the JSON is null it will not be updated.
- `GET /v2/topology/testinstance` — Search Test Instances (query: instanceId, instanceCode, instanceName, subType, isActive, limit, offset)
- `POST /v2/topology/testinstance` — Creates a new Test Instance with attributes from the given JSON body

## Topology - Test Instance Properties
- `GET /v2/topology/testinstance/{id}/property` — Find Properties for a Test Instance with the given Id
- `PUT /v2/topology/testinstance/{id}/property` — Updates all Properties of a Test Instance with the given Id based on the attributes of a JSON object parameters
- `PATCH /v2/topology/testinstance/{id}/property` — Updates some Properties of a Test Instance with the given Id based on the attributes of a JSON object parameters. Properties that are not in the incoming list will not be modified.

## Work Item
- `GET /v2/workitem/{Id}` — Find an Work Item with the given Id
- `PUT /v2/workitem/{Id}` — Updates all attributes of an Work Item with the given Id based on the attributes of a JSON object parameters
- `DELETE /v2/workitem/{Id}` — Deletes an existing Work Item.
- `PATCH /v2/workitem/{Id}` — Updates an existing Work Item with the information passed through a JSON object. If an attribute of the JSON is null it will not be updated.
- `GET /v2/workitem` — Search Work Items (query: workItemId, workItemNumber, type, description, issueTrackingSystemId, instanceId, limit, offset)
- `POST /v2/workitem` — Creates a new Work Item with attributes from the given JSON body

## Workflow
- `GET /v2/workflow/{Id}` — Find a Workflow with the given Id
- `PUT /v2/workflow/{Id}` — Updates all attributes of a Workflow with the given Id based on the attributes of a JSON object parameters. Workflow versions are not updated.
- `DELETE /v2/workflow/{Id}` — Deletes an existing Workflow.
- `PATCH /v2/workflow/{Id}` — Updates an existing Workflow with the information passed through a JSON object. If an attribute of the JSON is null it will not be updated. Workflow versions are not updated.
- `GET /v2/workflow/{Id}/properties` — Find a Workflow's Properties with the given Workflow Id
- `PUT /v2/workflow/{Id}/properties` — Updates all properties belonging a Workflow with the given Id. All properties not provided will be removed from the Workflow.
- `GET /v2/workflow` — Search Workflows (query: workflowId, workflowName, activeWorkflowVersionId, isActive, workflowType, workflowGroup, workflowSubgroup, description, readOnly, internal, limit, offset)
- `POST /v2/workflow` — Creates a new Workflow with attributes from the given JSON body. It will have a 1.0 version with no steps in it.

## Workflow Execution
- `GET /v2/workflowexecution/{workflowExecutionId}` — Find a Workflow Execution with the given Id
- `GET /v2/workflowexecution/{workflowExecutionId}/logs` — Download zipped logs for a Workflow Execution with the given Id
- `GET /v2/workflowexecution` — Search Workflow Executions (query: workflowExecutionId, workflowRequestId, parentWorkflowRequestId, projectId, projectVersionId, projectWorkflowId, workflowVersionId, environmentId, instanceId, predeployWorkflowExecId, executionStatus, dockerImageName, workflowId, workflowType, reviewStatus, limit, offset)

## Workflow Execution - Report
- `GET /v2/workflowexecution/report/{workflowExecutionReportId}` — Download a Workflow Execution Report with the given Id (query: inline)

## Workflow Request
- `POST /v2/workflowrequest/build` — Builds a project (asynchronous)
- `POST /v2/workflowrequest/deploy` — Deploys a project (asynchronous)
- `GET /v2/workflowrequest/{Id}` — Finds a Workflow Execution Request with the given Id.
- `POST /v2/workflowrequest/rollback` — Rolls back a project deployment (asynchronous)
- `POST /v2/workflowrequest/test` — Tests a project (asynchronous)
- `POST /v2/workflowrequest/utility` — Executes a Utility project (asynchronous)

## Workflow Version
- `PUT /v2/workflow/{workflowId}/version/{workflowVersionId}/activate` — Activates the Workflow Version with the given Id
- `GET /v2/workflow/{workflowId}/version/{workflowVersionId}` — Find a Workflow Version with the given Id
- `PATCH /v2/workflow/{workflowId}/version/{workflowVersionId}` — Updates an existing Workflow Version with the information passed through a JSON object. If an attribute of the JSON is null it will not be updated. (query: activate)
- `GET /v2/workflow/{workflowId}/version` — Find a Workflow Version with the given Version Name (query: workflowVersionName)
- `POST /v2/workflow/{workflowId}/version` — Creates a new Workflow Version with attributes from the given JSON body (query: activate)
- `GET /v2/workflow/{workflowId}/version/{workflowVersionId}/inputs` — Find a Workflow Version with the given Id

