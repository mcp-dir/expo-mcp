# Expo

### Expo para Claude, ChatGPT e agentes de IA

Seu projeto Expo e EAS por linguagem natural: documentação atualizada do SDK, builds na nuvem (status, logs, disparar e cancelar), workflows EAS de CI, envio pras lojas e dados de TestFlight (crashes e feedback). Conecte sua conta Expo em um clique, sem chave nem token.

- 📊 **19 ferramentas**
- ✏️ **Leitura e escrita**
- 💬 **Funciona com qualquer cliente MCP**: Claude Desktop, Cursor, VS Code, Cline, Continue
- 🔑 **Login via magic-link (sem senha)**

[English version](README.en.md) · [Documentação completa](docs/) · [Skill pra agentes](skills/)

---

## Instalar em 1 clique

### Claude (Web e Desktop)

A Anthropic unificou a instalação de MCPs em `claude.ai/customize/connectors`. **O mesmo link serve pra Claude Web e Claude Desktop** (basta estar logado):

[➕ Abrir no Claude e conectar](https://claude.ai/new?modal=add-custom-connector#settings/customize-connectors)

**Manual** (se o deeplink não abrir): [claude.ai/customize/connectors](https://claude.ai/customize/connectors?surface=cowork) → **+** → **Adicionar conector personalizado** → cole **Nome** `Expo` e **URL** `https://api.mcp.ai/p_expo`.

### Cursor

[➕ Instalar Expo no Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=expo&config=eyJ1cmwiOiJodHRwczovL2FwaS5tY3AuYWkvcF9leHBvIn0=)

### VS Code (Copilot Chat)

[➕ Instalar Expo no VS Code](vscode:mcp/install?name=expo&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapi.mcp.ai%2Fp_expo%22%7D)

### ChatGPT, Manus, OpenClaw e mais 40+ clientes

Funciona em qualquer cliente MCP que suporte **MCP over HTTP**. A URL do servidor é sempre:

```
https://api.mcp.ai/p_expo
```

Detalhes por cliente: [INSTALL.md](INSTALL.md).

---

## Exemplos de uso

```
Qual o status do meu último build no EAS?
Mostre os logs do build que falhou
Liste os crashes recentes do meu app no TestFlight
```

---

## 19 ferramentas disponíveis

| Tool | Descrição |
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

Detalhe de cada tool: [docs/ferramentas.md](docs/ferramentas.md)

---

## Preços

Grátis.

---

## Privacidade & LGPD

- **Sub-processadores**: Expo, o LLM host que você escolher (Claude, ChatGPT, Cursor, agente próprio). Lista completa em [docs/privacidade-lgpd.md](docs/privacidade-lgpd.md).
- Os dados retornados pelas tools são enviados ao **LLM host que você escolher**, sub-processador fora do nosso controle. Recomendamos planos com opt-out de treinamento.

---

## Perguntas frequentes

**O servidor é open source?**
O servidor é proprietário (hosted). Este repositório é o wrapper público com manifestos, docs e skills — tudo MIT.

**Posso usar com agente próprio (não Claude/Cursor)?**
Sim — qualquer cliente que suporte MCP over HTTP. URL: `https://api.mcp.ai/p_expo`.


---

## Suporte

- 📧 [expo@mcp.ai](mailto:expo@mcp.ai)
- 🐛 [GitHub Issues](https://github.com/mcp-dir/expo-mcp/issues)
- 📄 [docs/](docs/)

---

## Licença

MIT — veja [LICENSE](LICENSE). O servidor MCP em `api.mcp.ai/p_expo` é proprietário (hosted); este repositório (manifestos, docs, skills) é MIT.
