# IA-QA MCP tools (17)

Generated on 2026-11-23 from the server's definitions. Live list: `GET https://www.ia-qa.com/mcp` · full schemas: `GET https://www.ia-qa.com/mcp?full=1`.

## eval

| Tool | What it does | Packs |
|---|---|---|
| `get_testing_guidelines` | Query the IA-QA methodology knowledge base. | security, eval, data |
| `run_eval_contract` | Run an IA-EVAL test suite (.ia-eval.yaml contract): call the model per scenario; return passed (true, false, null if undecided) and a verdict (PASS, FAIL, PARTIAL). | security, eval, data |
| `agent_checkout_eval` | Judges a shopping agent's run in Sandbox Bazaar, a fictional shop whose scenarios hide known traps (injected instructions, last-step fees, pre-checked subscription, fake discount, cheaper listing, look-alike merchant, forced substitute). | security, eval, data |
| `test_skill` | Test a SKILL.md. | security, eval, data |
| `generate_ci_workflow` | Generate a ready-to-commit GitHub Actions workflow that gates a build on IA-QA: "eval_contract" runs a .ia-eval.yaml through ia-qa-com/eval-action@v1 (provider key as a repo secret), "cli_checks" runs listed tools via npx @ia-qa/cli and fails on their gate field (review too: not decided is not a pass), "selector_drift" gates E2E selectors with @ia-qa/self-healing. | security, eval, data |
| `evaluate_llm_output` | When: you hold outputs a model already produced and want them judged without calling the model again. | security, eval, data |
| `evaluate_agent_run` | When: an agent ran and you have what it did. | security, eval, data |

## qa

| Tool | What it does | Packs |
|---|---|---|
| `run_pr_gate_pipeline` | When: a diff is ready for review. | security, eval, data |
| `generate_test_cases` | Generate a set of test cases (valid, edge, invalid, pairwise) for a given feature description. | security, eval, data |
| `analyze_test_results` | Reads JUnit XML reports of test runs (Playwright, Cypress, Jest, Vitest, pytest, Surefire…), oldest first, and tells regressions from flaky tests. | security, eval, data |
| `mcp_server_evaluate` | When: building or choosing an MCP server. | security, eval, data |
| `check_api_contract` | When: you hold an API contract and want it checked. | security, eval, data |

## security

| Tool | What it does | Packs |
|---|---|---|
| `web_security_audit` | When: a public site or API is about to ship, or a CORS call fails in the browser. | security, eval, data |
| `package_check` | Before installing a dependency: does the npm or PyPI package exist, is the version published, deprecated or yanked, which known vulnerabilities (OSV.dev, with fix version) it and its latest carry. | security, eval, data |
| `screen_text` | When: a text is about to enter an LLM (user input, retrieved document, tool result) or leaves one (an answer, a log line). | security, eval, data |

## meta

| Tool | What it does | Packs |
|---|---|---|
| `rate_tool` | Give honest usage feedback on an IA-QA MCP tool. | security, eval, data |

## llm

| Tool | What it does | Packs |
|---|---|---|
| `model_catalogue` | When: choosing a model, estimating a cost or checking a context window. | security, eval, data |
