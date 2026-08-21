# Ferramentas

Expo expõe 19 ferramentas.

### 1. `expo_add_library`
**Input**: `projectRoot`, `libraryName`

Add an Expo library to the project using expo install and attach usage instructions when available

### 2. `expo_read_documentation`
**Input**: `url`, `offset` (opcional)

Fetch a single Expo documentation page and return its content as markdown.

### 3. `expo_search_documentation`
**Input**: `query`

Search the official Expo documentation and return page URLs ranked by relevance for a user query.

### 4. `expo_learn`
**Input**: `topic`

Learn Expo how-to for a specific topic and remember it for future conversations.

### 5. `expo_workflow_create`
**Input**: `action`, `projectRoot` (opcional), `fileName` (opcional), `workflowYaml` (opcional)

Creates a new EAS workflow YAML file for Expo projects or fetches workflow syntax documentation.

### 6. `expo_workflow_info`
**Input**: `workflowRunId`

Fetches detailed information about a specific EAS workflow run by ID.

### 7. `expo_workflow_list`
**Input**: `appId` (opcional), `appFullName` (opcional), `status` (opcional), `limit` (opcional)

Lists recent EAS workflow runs for a project.

### 8. `expo_workflow_logs`
**Input**: `workflowRunId`, `jobKey`, `sectionIndex` (opcional), `phase` (opcional)

Fetches logs for a specific job in an EAS workflow run.

### 9. `expo_workflow_run`
**Input**: `appId` (opcional), `appFullName` (opcional), `fileName`, `gitRef`

Triggers an EAS workflow run from a git reference.

### 10. `expo_workflow_cancel`
**Input**: `workflowRunId`

Cancels a running EAS workflow.

### 11. `expo_workflow_validate`
**Input**: `appId` (opcional), `appFullName` (opcional), `workflowYaml`

Validates EAS workflow YAML syntax and configuration.

### 12. `expo_build_list`
**Input**: `appId` (opcional), `appFullName` (opcional), `platform` (opcional), `status` (opcional), `limit` (opcional)

Lists EAS builds for a project.

### 13. `expo_build_info`
**Input**: `buildId`

Fetches the status and detailed information about a specific EAS build by ID.

### 14. `expo_build_logs`
**Input**: `buildId`

Fetches the logs for a specific EAS build.

### 15. `expo_build_submit`
**Input**: `appId` (opcional), `appFullName` (opcional), `buildId`, `platform`, `track` (opcional), `ascAppIdentifier` (opcional)

Submits an EAS build to the app store (Google Play Store for Android, App Store for iOS).

### 16. `expo_build_run`
**Input**: `appId` (opcional), `appFullName` (opcional), `platform`, `buildProfile`, `gitRef`, `baseDirectory` (opcional), `autoSubmit` (opcional), `submitProfile` (opcional)

Triggers a new EAS build using a build profile from eas.json.

### 17. `expo_build_cancel`
**Input**: `buildId`

Cancels an EAS build that is queued or in progress.

### 18. `expo_testflight_crashes`
**Input**: `bundleId`, `crashId` (opcional), `limit` (opcional)

Fetch TestFlight crash data. Without crashId, lists recent crashes. With crashId, returns the full crash log with stack trace.

### 19. `expo_testflight_feedback`
**Input**: `bundleId`, `limit` (opcional)

Fetch screenshot feedback from TestFlight.

## Prompts de exemplo

```
Qual o status do meu último build no EAS?
Mostre os logs do build que falhou
Liste os crashes recentes do meu app no TestFlight
```
