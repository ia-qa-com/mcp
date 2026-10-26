# IA-QA MCP server

Free QA and LLM-testing tools for AI agents, served over MCP (Streamable HTTP). **No account, no API key.** Every tool returns a verdict an agent can act on: pass/fail, a score, a diff.

- Website: https://www.ia-qa.com · MCP page: https://www.ia-qa.com/mcp-server · `llms.txt`: https://www.ia-qa.com/llms.txt
- Official MCP Registry: `io.github.JcJamet/ia-qa-toolbox` and the three packs below

This repository **describes** the hosted server; it holds no server code. The live tool list is always `GET https://www.ia-qa.com/mcp`.

## Endpoints

| Endpoint | Tools listed | For |
|---|---|---|
| `https://www.ia-qa.com/mcp` | all 152 | clients with no tool limit |
| `https://www.ia-qa.com/mcp/security` | 30 | prompt injection, PII and secret scans, TLS/header/CORS audits, MCP server checks |
| `https://www.ia-qa.com/mcp/eval` | 38 | hallucination, eval contracts, semantic and RAG tests, tokens and models |
| `https://www.ia-qa.com/mcp/data` | 36 | JSON/YAML/CSV, schema validation, encoding, text and time utilities |

Clients cap how many tools they load (VS Code Copilot 128 per request, Cursor about 40). A pack lists only its tools; for a tool outside it, add the full server or the pack that lists it — `find_tool` searches everything and says which pack lists each tool.

## Install

**Claude Code**
```sh
claude mcp add --transport http ia-qa https://www.ia-qa.com/mcp
# or one pack:
claude mcp add --transport http ia-qa-security https://www.ia-qa.com/mcp/security
```

**Cursor** — `.cursor/mcp.json (this project) or ~/.cursor/mcp.json (all projects)` (use a pack: Cursor loads about 40 tools)
```json
{
  "mcpServers": {
    "ia-qa-security": {
      "url": "https://www.ia-qa.com/mcp/security"
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

**Claude Desktop** — Settings → Connectors → Add custom connector, URL `https://www.ia-qa.com/mcp` (or a pack URL).

**Any other MCP client** — Streamable HTTP at one of the URLs above. More clients, and a prompt you can paste into any agent: https://www.ia-qa.com/mcp-server

## What leaves your machine

Every call runs on ia-qa.com: whatever you pass to a tool is sent there — including a provider API key given to one of the few bring-your-own-key tools. The call journal stores **no IP address**: a monthly pseudonym (an HMAC, not reversible) to count distinct callers within a month, and each entry is deleted 400 days after the call. Rate limit: 60 requests per minute per IP.

For tools that must run next to your app (selector self-healing, app discovery), use the local packages instead — nothing is sent to ia-qa.com: [`@ia-qa/pal`](https://www.npmjs.com/package/@ia-qa/pal), [`@ia-qa/self-healing`](https://www.npmjs.com/package/@ia-qa/self-healing), [`@ia-qa/qa-discovery`](https://www.npmjs.com/package/@ia-qa/qa-discovery).

## Packs

### `security` — https://www.ia-qa.com/mcp/security

`prompt_injection_scan` · `shield_analyze` · `guardrail_test` · `toxicity_scan` · `bias_detect` · `redact_pii` · `secret_scan` · `detect_secrets` · `security_headers_check` · `ssl_certificate_check` · `cors_test` · `cors_checker` · `cookie_security_audit` · `web_security_audit` · `validate_url` · `decode_jwt` · `generate_hmac` · `hash_text` · `generate_password` · `mcp_server_evaluate` · `mcp_server_health_check` · `mcp_schema_lint` · `validate_mcp_response` · `function_call_validate` · `validate_agent_trajectory` · `latency_benchmark` · `parse_http_headers` · `http_status_lookup` · `find_tool` · `rate_tool`

### `eval` — https://www.ia-qa.com/mcp/eval

`get_testing_guidelines` · `run_eval_contract` · `run_semantic_tests` · `generate_eval_yaml` · `generate_ci_workflow` · `metamorphic_check` · `needle_haystack_generate` · `test_skill` · `hallucination_check` · `similarity_score` · `consistency_check` · `llm_output_validator` · `llm_format_check` · `llm_json_schema_check` · `response_quality_score` · `compare_responses` · `analyze_responses` · `prompt_test_suite` · `cot_analyzer` · `conversation_analyze` · `ab_test_report` · `embedding_similarity` · `rag_relevance_rank` · `rerank_evaluate` · `bm25_score` · `build_rag_prompt` · `count_tokens` · `token_budget_calculator` · `context_window_check` · `list_llm_models` · `model_info` · `compare_models` · `estimate_llm_cost` · `llm_generate` · `run_vlm_test_suite` · `extract_json_from_text` · `find_tool` · `rate_tool`

### `data` — https://www.ia-qa.com/mcp/data

`format_json` · `json_schema_validate` · `json_diff` · `extract_json_path` · `flatten_json` · `json_to_yaml` · `yaml_to_json` · `xml_to_json` · `parse_csv` · `json_to_csv` · `mock_from_schema` · `json_schema_generate` · `openapi_validate` · `timestamp_convert` · `cron_parse` · `validate_email` · `regex_test` · `diff_text` · `text_stats` · `case_convert` · `generate_slug` · `base64_encode` · `base64_decode` · `url_encode` · `url_decode` · `generate_uuid` · `hash_text` · `number_base_convert` · `color_convert` · `lorem_ipsum` · `decode_jwt` · `env_parse` · `count_code_lines` · `lint_commit_message` · `find_tool` · `rate_tool`

All 152 tools, by category: [TOOLS.md](TOOLS.md).

---

Generated from the server's own definitions on 2026-10-26. The live list (`GET https://www.ia-qa.com/mcp`) wins if this page disagrees.
