# Crisp

### Crisp for Claude, ChatGPT and AI agents

Customer support, live chat, CRM and helpdesk on Crisp with the full official REST API v1 (api.crisp.chat), conversations and messages, contacts/people, knowledge base (articles, categories, locales), campaigns, operators, visitors and website settings. Read and write. Auth via a token keypair (generated in Crisp, under Settings, Workspace settings, Advanced configuration).

- 📊 **1 tool**
- 🔒 **Read-only**
- 💬 **Works with any MCP client**: Claude Desktop, Cursor, VS Code, Cline, Continue
- 🔑 **Magic-link login (no password)**

[Portuguese version](README.md) · [Full docs (PT-BR)](docs/)

---

## One-click install

### Claude (Web and Desktop)

[➕ Open in Claude and connect](https://claude.ai/new?modal=add-custom-connector#settings/customize-connectors)

Manual: [claude.ai/customize/connectors](https://claude.ai/customize/connectors?surface=cowork) → **+** → **Add custom connector** → name `Crisp`, URL `https://api.mcp.ai/p_crisp`.

### Cursor

[➕ Install in Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=crisp&config=eyJ1cmwiOiJodHRwczovL2FwaS5tY3AuYWkvcF9jcmlzcCJ9)

### VS Code (Copilot Chat)

[➕ Install in VS Code](vscode:mcp/install?name=crisp&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapi.mcp.ai%2Fp_crisp%22%7D)

### Any other MCP-over-HTTP client

```
https://api.mcp.ai/p_crisp
```

---

## 1 tool

| Tool | Description |
|---|---|
| `search_tools` | Single entrypoint for MCP catalog. |

---

## Pricing

Free.

---

## License

MIT — see [LICENSE](LICENSE). The MCP server at `api.mcp.ai/p_crisp` is proprietary (hosted); this repo (manifests, docs, skills) is MIT.
