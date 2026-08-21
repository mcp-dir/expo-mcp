# Expo

### Expo for Claude, ChatGPT and AI agents

Your Expo and EAS project in natural language: up to date SDK docs, cloud builds (status, logs, trigger and cancel), EAS CI workflows, store submission and TestFlight data (crashes and feedback). Connect your Expo account in one click, no key or token.

- 📊 **19 tools**
- ✏️ **Read and write**
- 💬 **Works with any MCP client**: Claude Desktop, Cursor, VS Code, Cline, Continue
- 🔑 **Magic-link login (no password)**

[Portuguese version](README.md) · [Full docs (PT-BR)](docs/)

---

## One-click install

### Claude (Web and Desktop)

[➕ Open in Claude and connect](https://claude.ai/new?modal=add-custom-connector#settings/customize-connectors)

Manual: [claude.ai/customize/connectors](https://claude.ai/customize/connectors?surface=cowork) → **+** → **Add custom connector** → name `Expo`, URL `https://api.mcp.ai/p_expo`.

### Cursor

[➕ Install in Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=expo&config=eyJ1cmwiOiJodHRwczovL2FwaS5tY3AuYWkvcF9leHBvIn0=)

### VS Code (Copilot Chat)

[➕ Install in VS Code](vscode:mcp/install?name=expo&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapi.mcp.ai%2Fp_expo%22%7D)

### Any other MCP-over-HTTP client

```
https://api.mcp.ai/p_expo
```

---

## 19 tools

| Tool | Description |
|---|---|
| `expo_add_library` | Add an Expo library to the project using expo install and attach usage instructions when available |
| `expo_read_documentation` | Fetch a single Expo documentation page and return its content as markdown. |
| `expo_search_documentation` | Search the official Expo documentation and return page URLs ranked by relevance for a user query. |
| `expo_learn` | Learn Expo how-to for a specific topic and remember it for future conversations. |
| `expo_workflow_create` | Creates a new EAS workflow YAML file for Expo projects or fetches workflow syntax documentation. |
| `expo_workflow_info` | Fetches detailed information about a specific EAS workflow run by ID. |
| `expo_workflow_list` | Lists recent EAS workflow runs for a project. |
| `expo_workflow_logs` | Fetches logs for a specific job in an EAS workflow run. |
| `expo_workflow_run` | Triggers an EAS workflow run from a git reference. |
| `expo_workflow_cancel` | Cancels a running EAS workflow. |
| `expo_workflow_validate` | Validates EAS workflow YAML syntax and configuration. |
| `expo_build_list` | Lists EAS builds for a project. |
| `expo_build_info` | Fetches the status and detailed information about a specific EAS build by ID. |
| `expo_build_logs` | Fetches the logs for a specific EAS build. |
| `expo_build_submit` | Submits an EAS build to the app store (Google Play Store for Android, App Store for iOS). |
| `expo_build_run` | Triggers a new EAS build using a build profile from eas.json. |
| `expo_build_cancel` | Cancels an EAS build that is queued or in progress. |
| `expo_testflight_crashes` | Fetch TestFlight crash data. Without crashId, lists recent crashes. With crashId, returns the full crash log with stack trace. |
| `expo_testflight_feedback` | Fetch screenshot feedback from TestFlight. |

---

## Pricing

Free.

---

## License

MIT — see [LICENSE](LICENSE). The MCP server at `api.mcp.ai/p_expo` is proprietary (hosted); this repo (manifests, docs, skills) is MIT.
