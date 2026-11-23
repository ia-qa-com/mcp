# IA-QA MCP server

17 QA judges for AI agents, served over MCP (Streamable HTTP). **No account.** Every tool returns a verdict an agent can act on and `gate: pass | review | fail`, the one field to branch a CI step on; the few tools that call a model use your own key.

- Website: https://www.ia-qa.com · MCP page: https://www.ia-qa.com/mcp-server · `llms.txt`: https://www.ia-qa.com/llms.txt
- Official MCP Registry: `io.github.JcJamet/ia-qa-toolbox`

This repository **describes** the hosted server; it holds no server code. The live tool list is always `GET https://www.ia-qa.com/mcp`.

## Endpoints

| Endpoint | Tools listed | For |
|---|---|---|
| `https://www.ia-qa.com/mcp` | all 17 | every client |
| `https://www.ia-qa.com/mcp/security`, `/mcp/eval`, `/mcp/data` | 17 | kept for clients configured on them: since MCP V2 they serve the same list as `/mcp` |

## Tools that left the list (MCP V2, November 2026)

The server went from 156 listed tools to 17: each tool kept absorbed its neighbours, with the same engines, and the utilities stay on the website. An old tool name still answers until **2027-05-22**; its answer carries a `deprecated` field naming the tool that replaces it and its page on the site, and `@ia-qa/cli` still finds those names. Some clients (the MCP Inspector) refuse a tool their list does not hold: call the tool named in `deprecated.use`.

## Install

**Claude Code**
```sh
claude mcp add --transport http ia-qa https://www.ia-qa.com/mcp
```

**Cursor** — `.cursor/mcp.json (this project) or ~/.cursor/mcp.json (all projects)`
```json
{
  "mcpServers": {
    "ia-qa": {
      "url": "https://www.ia-qa.com/mcp"
    }
  }
}
```

**VS Code (GitHub Copilot, agent mode)** — `.vscode/mcp.json`
```json
{
  "servers": {
    "ia-qa": {
      "type": "http",
      "url": "https://www.ia-qa.com/mcp"
    }
  }
}
```

**Claude Desktop** — Settings → Connectors → Add custom connector, URL `https://www.ia-qa.com/mcp`.

**Any other MCP client** — Streamable HTTP at one of the URLs above. More clients, and a prompt you can paste into any agent: https://www.ia-qa.com/mcp-server

## What leaves your machine

Every call runs on ia-qa.com: whatever you pass to a tool is sent there — including a provider API key given to one of the few bring-your-own-key tools. The call journal stores **no IP address**: a monthly pseudonym (an HMAC, not reversible) to count distinct callers within a month, and each entry is deleted 400 days after the call. Rate limit: 60 requests per minute per IP.

For tools that must run next to your app (selector self-healing, app discovery), use the local packages instead — nothing is sent to ia-qa.com: [`@ia-qa/pal`](https://www.npmjs.com/package/@ia-qa/pal), [`@ia-qa/self-healing`](https://www.npmjs.com/package/@ia-qa/self-healing), [`@ia-qa/qa-discovery`](https://www.npmjs.com/package/@ia-qa/qa-discovery).

## Tools

`get_testing_guidelines` · `run_pr_gate_pipeline` · `generate_test_cases` · `analyze_test_results` · `web_security_audit` · `run_eval_contract` · `agent_checkout_eval` · `mcp_server_evaluate` · `test_skill` · `generate_ci_workflow` · `package_check` · `rate_tool` · `screen_text` · `evaluate_llm_output` · `evaluate_agent_run` · `check_api_contract` · `model_catalogue`

All 17 tools, by category: [TOOLS.md](TOOLS.md).

---

Generated from the server's own definitions on 2026-11-23. The live list (`GET https://www.ia-qa.com/mcp`) wins if this page disagrees.
