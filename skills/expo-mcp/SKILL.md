---
name: expo-mcp
description: Skill da REST API do Expo na MCP.AI: 19 endpoints em /api/expo. Seu projeto Expo e EAS por linguagem natural: documentação atualizada do SDK, builds na nuvem (status, logs, disparar e cancelar), workflows EAS de CI, envio pras lojas e dados de TestFlight (crashes e feedback). Conecte sua conta Expo em um clique, sem chave nem token. Autentique com workspace API key (sk_live) gerada em app.mcp.ai/settings/api-keys. Use quando o usuário pedir algo coberto pelos endpoints.
---

# Expo — REST API skill

Você tem acesso à **Expo** REST API na MCP.AI.

> Seu projeto Expo e EAS por linguagem natural: documentação atualizada do SDK, builds na nuvem (status, logs, disparar e cancelar), workflows EAS de CI, envio pras lojas e dados de TestFlight (crashes e feedback). Conecte sua conta Expo em um clique, sem chave nem token.

## Base URL

```
https://api.mcp.ai/api/expo
```

Todo endpoint é um **POST** na Base URL + o path abaixo. Os parâmetros vão no corpo JSON.

## Autenticação

Inclua em toda request:

```
Authorization: Bearer sk_live_...
Content-Type: application/json
```

> Gere sua chave em **https://app.mcp.ai/settings/api-keys** (workspace API key `sk_live_…`, não expira, revogável). Uma única chave serve pra todos os seus MCPs.

## Formato de resposta

```json
{ "ok": true, "tool": "<tool_id>", "result": <payload> }
```

## Exemplo cURL

```bash
curl -X POST https://api.mcp.ai/api/expo/add/library \
  -H "Authorization: Bearer sk_live_..." \
  -H "Content-Type: application/json" \
  -d '{"projectRoot":"...","libraryName":"..."}'
```

## Reportar problemas

Se um endpoint retornar erro, vazio ou dado inesperado, reporte (não desista calado): **POST /api/expo/report** com `{ "message": "...", "context"?: "...", "conversation"?: [...] }`. Isso notifica o time da MCP.AI.

## Endpoints (19)

#### `expo_add_library`

Add an Expo library to the project using expo install and attach usage instructions when available _(POST /api/expo/add/library)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `projectRoot` | string | Sim |  |
| `libraryName` | string | Sim |  |

#### `expo_build_cancel`

Cancels an EAS build that is queued or in progress. _(POST /api/expo/build/cancel)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `buildId` | string | Sim | The ID of the build to cancel |

#### `expo_build_info`

Fetches the status and detailed information about a specific EAS build by ID. _(POST /api/expo/build/info)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `buildId` | string | Sim | The ID of the build to fetch details for |

#### `expo_build_list`

Lists EAS builds for a project. _(POST /api/expo/build/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `appId` | string | Não | The Expo project/app ID (UUID). Get this from app.json at "extra.eas.projectId". Either appId or appFullName is required. |
| `appFullName` | string | Não | The full name of the app (e.g., "@owner/my-app"). Use this if you don't have access to app.json. Either appId or appFullName is required. |
| `platform` | string | Não | Filter builds by platform (ANDROID or IOS) (ANDROID, IOS) |
| `status` | string | Não | Filter builds by status (IN_QUEUE, IN_PROGRESS, FINISHED, ERRORED, CANCELED) (CANCELED, ERRORED, FINISHED, IN_PROGRESS, IN_QUEUE, NEW, PENDING_CANCEL) |
| `limit` | number | Não | Maximum number of builds to return (default: 10) |

#### `expo_build_logs`

Fetches the logs for a specific EAS build. _(POST /api/expo/build/logs)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `buildId` | string | Sim | The ID of the build to fetch logs for |

#### `expo_build_run`

Triggers a new EAS build using a build profile from eas.json. _(POST /api/expo/build/run)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `appId` | string | Não | The Expo project/app ID (UUID). Get this from app.json at "extra.eas.projectId". Either appId or appFullName is required. |
| `appFullName` | string | Não | The full name of the app (e.g., "@owner/my-app"). Use this if you don't have access to app.json. Either appId or appFullName is required. |
| `platform` | string | Sim | The platform to build for (ANDROID or IOS) (ANDROID, IOS) |
| `buildProfile` | string | Sim | The build profile name from eas.json (e.g., "development", "preview", "production") |
| `gitRef` | string | Sim | Git reference (branch name, tag, or commit SHA) to build from |
| `baseDirectory` | string | Não | Base directory for monorepos (e.g., "apps/mobile") |
| `autoSubmit` | boolean | Não | Whether to automatically submit the build after completion |
| `submitProfile` | string | Não | Submit profile to use if autoSubmit is true |

#### `expo_build_submit`

Submits an EAS build to the app store (Google Play Store for Android, App Store for iOS). _(POST /api/expo/build/submit)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `appId` | string | Não | The Expo project/app ID (UUID). Get this from app.json at "extra.eas.projectId". Either appId or appFullName is required. |
| `appFullName` | string | Não | The full name of the app (e.g., "@owner/my-app"). Use this if you don't have access to app.json. Either appId or appFullName is required. |
| `buildId` | string | Sim | The ID of the build to submit |
| `platform` | string | Sim | The platform to submit to (ANDROID or IOS) (ANDROID, IOS) |
| `track` | string | Não | For Android: The release track (internal, alpha, beta, production). Required for Android submissions. |
| `ascAppIdentifier` | string | Não | For iOS: The App Store Connect app identifier (Apple ID of the app). Required for iOS submissions. |

#### `expo_learn`

Learn Expo how-to for a specific topic and remember it for future conversations. _(POST /api/expo/learn)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `topic` | string | Sim |  (expo-router) |

#### `expo_read_documentation`

Fetch a single Expo documentation page and return its content as markdown. _(POST /api/expo/read/documentation)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `url` | string | Sim |  |
| `offset` | integer | Não | Character offset to start reading from. Defaults to 0. |

#### `expo_search_documentation`

Search the official Expo documentation and return page URLs ranked by relevance for a user query. _(POST /api/expo/search/documentation)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `query` | string | Sim |  |

#### `expo_testflight_crashes`

Fetch TestFlight crash data. Without crashId, lists recent crashes. With crashId, returns the full crash log with stack trace. _(POST /api/expo/testflight/crashes)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `bundleId` | string | Sim | The bundle ID of the app (e.g., com.example.myapp) |
| `crashId` | string | Não | Specific crash ID to fetch full details for. If omitted, lists recent crashes. |
| `limit` | number | Não | Maximum number of crashes to list (default: 20, ignored when crashId is provided) |

#### `expo_testflight_feedback`

Fetch screenshot feedback from TestFlight. _(POST /api/expo/testflight/feedback)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `bundleId` | string | Sim | The bundle ID of the app (e.g., com.example.myapp) |
| `limit` | number | Não | Maximum number of feedback submissions to return (default: 20) |

#### `expo_workflow_cancel`

Cancels a running EAS workflow. _(POST /api/expo/workflow/cancel)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `workflowRunId` | string | Sim | The ID of the workflow run to cancel |

#### `expo_workflow_create`

Creates a new EAS workflow YAML file for Expo projects or fetches workflow syntax documentation. _(POST /api/expo/workflow/create)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `action` | string | Sim | Action to perform: "create" to create a new EAS workflow YML file, "learn" to get EAS workflow syntax documentation and examples. Use "learn" first to get the syntax and examples before creating a new workflow (create, learn) |
| `projectRoot` | string | Não | Root directory of the project (required for create action) |
| `fileName` | string | Não | Workflow file name (e.g., "build-and-deploy.yml") (required for create action) |
| `workflowYaml` | string | Não | Complete YAML content for the EAS workflow (multi-line string, required for create action). EAS workflows must be formatted with jobs that have a "type:" (e.g., type: build, type: submit, type: fingerprint) and "params:" sections. When a job depends on another job, use "needs: [first_job]" Example job structure:  ```yaml jobs:   job_name:     name: Job Display Name     type: build  # or submit, fingerprint, build, etc.     params:       platform: ios  # or android       profile: production     depends_on: [job_name_of_dependent_job] ``` |

#### `expo_workflow_info`

Fetches detailed information about a specific EAS workflow run by ID. _(POST /api/expo/workflow/info)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `workflowRunId` | string | Sim | The ID of the workflow run to fetch details for |

#### `expo_workflow_list`

Lists recent EAS workflow runs for a project. _(POST /api/expo/workflow/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `appId` | string | Não | The Expo project/app ID (UUID). Get this from app.json at "extra.eas.projectId". Either appId or appFullName is required. |
| `appFullName` | string | Não | The full name of the app (e.g., "@owner/my-app"). Use this if you don't have access to app.json. Either appId or appFullName is required. |
| `status` | string | Não | Filter workflow runs by status (ACTION_REQUIRED, CANCELED, FAILURE, IN_PROGRESS, NEW, SUCCESS) |
| `limit` | number | Não | Maximum number of workflow runs to return (default: 10, max: 100) |

#### `expo_workflow_logs`

Fetches logs for a specific job in an EAS workflow run. _(POST /api/expo/workflow/logs)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `workflowRunId` | string | Sim | The ID of the workflow run |
| `jobKey` | string | Sim | The key or ID of the job to fetch logs for. Use workflow_info to see available job keys. |
| `sectionIndex` | integer | Não | 1-based index of a log section to fetch (from the summary). Omit to get a summary of sections first. |
| `phase` | string | Não | Phase name to fetch (e.g. RUN_GRADLEW, SPIN_UP_BUILDER). Omit to get a summary of sections first. |

#### `expo_workflow_run`

Triggers an EAS workflow run from a git reference. _(POST /api/expo/workflow/run)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `appId` | string | Não | The Expo project/app ID (UUID). Get this from app.json at "extra.eas.projectId". Either appId or appFullName is required. |
| `appFullName` | string | Não | The full name of the app (e.g., "@owner/my-app"). Use this if you don't have access to app.json. Either appId or appFullName is required. |
| `fileName` | string | Sim | Workflow file name (e.g., "build.yml") |
| `gitRef` | string | Sim | Git reference (branch, tag, or commit SHA) to run the workflow from. The workflow file must exist at this reference in the repository. |

#### `expo_workflow_validate`

Validates EAS workflow YAML syntax and configuration. _(POST /api/expo/workflow/validate)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `appId` | string | Não | The Expo project/app ID (UUID). Get this from app.json at "extra.eas.projectId". Either appId or appFullName is required. |
| `appFullName` | string | Não | The full name of the app (e.g., "@owner/my-app"). Use this if you don't have access to app.json. Either appId or appFullName is required. |
| `workflowYaml` | string | Sim | The YAML content to validate |

---

Este MCP também funciona via **conexão MCP** (Claude / Cursor) em `https://api.mcp.ai/p_expo` — veja o [README](../../README.md). A skill acima é pra consumir a **REST API** direto (agente próprio / código).
