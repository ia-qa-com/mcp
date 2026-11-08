# IA-QA MCP tools (153)

Generated on 2026-11-08 from the server's definitions. Live list: `GET https://www.ia-qa.com/mcp` · full schemas: `GET https://www.ia-qa.com/mcp?full=1`.

## eval

| Tool | What it does | Packs |
|---|---|---|
| `get_testing_guidelines` | Query the IA-QA methodology knowledge base. | eval |
| `run_eval_contract` | Run an IA-EVAL test suite (.ia-eval.yaml contract): call the model per scenario; return passed (true, false, null if undecided) and a verdict (PASS, FAIL, PARTIAL). | eval |
| `run_semantic_tests` | Semantic assertion primitive: compare actual vs expected text pairs using cosine similarity + ROUGE-L. | eval |
| `generate_ci_workflow` | Generate a ready-to-commit GitHub Actions workflow that gates a build on IA-QA: "eval_contract" runs a .ia-eval.yaml through ia-qa-com/eval-action@v1 (needs a provider key as a repo secret), "cli_checks" runs deterministic tools via npx @ia-qa/cli and fails the build on their verdict, "selector_drift" gates E2E selectors with @ia-qa/self-healing. | eval |
| `needle_haystack_generate` | Generate a "needle in a haystack" test: embeds a target fact into a large block of filler text at a specified position. | eval |
| `list_local_tests` | Discover .ia-eval.yaml LLM test suite files in the project directory. | — |
| `generate_html_report` | Convert a run_eval_contract() LLM Test Runner JSON result into a fully self-contained dark-themed HTML report with Pass/Fail badges, side-by-side Input/Output/Ground-Truth panels, evaluator score bars, and a radar chart. | — |
| `generate_eval_yaml` | Generate a complete .ia-eval.yaml evaluation contract from a plain-language description of what your LLM should do. | eval |
| `validate_agent_trajectory` | Run declarative assertions on an agent trace (OpenAI tool calls, Anthropic tool_use, LangChain run trees, ReAct logs). | security |
| `metamorphic_check` | Reference-free stability check: does an assistant's answer stay the same when the QUESTION is transformed (case, typo, paraphrase, reorder, translation)? | eval |
| `test_skill` | Test a SKILL.md. | eval |
| `skill_interview` | Help a person write a SKILL.md they can test. | eval |

## meta

| Tool | What it does | Packs |
|---|---|---|
| `find_tool` | Search available MCP tools by keyword or category before calling them. | security, eval, data |
| `identify_caller` | Returns what the server knows about the current MCP client: clientInfo captured during initialize, User-Agent, and any _meta fields sent with this request. | — |
| `rate_tool` | Give honest usage feedback on an IA-QA MCP tool. | security, eval, data |

## qa

| Tool | What it does | Packs |
|---|---|---|
| `generate_test_cases` | Generate a set of test cases (valid, edge, invalid, pairwise) for a given feature description. | — |
| `analyze_diff_bugs` | Pattern-based diff linter: flags a fixed set of risky shapes in changed code — query-string interpolation (SQL/Cypher/Mongo injection shape), shell interpolation, eval/new Function, empty catch blocks, regex built from a variable, fewer catch blocks than before, and named authorization guards that disappeared. | — |
| `run_pr_gate_pipeline` | Review triage for a pull request. | — |
| `diff_mappings` | Diff a baseline page mapping against a current one and return a CI-style verdict: PASS / FIX / BLOCK, plus per-element drift (ok, renamed, healable, ambiguous, lost, added, rebound). | — |
| `sandbox_scenario` | Get a ready-made selector-drift test case with a known-correct answer, for testing this MCP server or an agent workflow end to end. | — |
| `prompt_injection_scan` | Scan user input or prompts for prompt injection patterns. | security |
| `hallucination_check` | Lexical hallucination check: verifies an LLM answer's words, numbers and polarity against the provided source/context. | eval |
| `guardrail_test` | Test an LLM response against a set of guardrail rules: must-include, must-not-include, max length, required format, language, forbidden patterns, and custom regex. | security |
| `diff_text` | Compute a unified line-by-line diff between two text strings (LCS algorithm). | data |
| `validate_mcp_response` | Validate that an MCP tool response conforms to expected format, schema, and content rules. | security |
| `llm_output_validator` | Validate an LLM response against QA criteria: format checks (JSON, code, markdown), content rules (must-include, must-not-include), length constraints, language detection, and safety patterns. | eval |
| `compare_responses` | Compare two ALREADY-PRODUCED outputs (e.g. | eval |
| `analyze_responses` | Semantically analyze N already-produced model outputs for the SAME task (the MCP counterpart to the LLM Sandbox). | eval |
| `prompt_test_suite` | Define a test suite for a prompt: provide the system prompt, user prompt, and expected output criteria. | eval |
| `mcp_server_health_check` | Check an MCP server's tool definitions without contacting it — for a server not deployed yet, a stdio server, or a CI gate. | security |
| `mcp_server_evaluate` | Check that a live MCP server over Streamable HTTP speaks the protocol, 2026-07-28 or earlier: handshake or server/discover, tools/list and its definitions, error codes, one tools/call, structuredContent against outputSchema, latency. | security |
| `llm_format_check` | Validate that an LLM output matches an expected format: JSON, Markdown, code block, bullet list, numbered list, table, YAML, XML, or custom regex. | eval |
| `consistency_check` | Compare multiple LLM responses to the same prompt and detect inconsistencies using Jaccard word-overlap similarity and fact drift (number comparison). | eval |
| `llm_json_schema_check` | Validate that an LLM JSON output matches a JSON Schema definition. | eval |
| `response_quality_score` | Score an LLM response against the criteria you pass: coverage of expected_keywords and compliance with max_length. | eval |
| `toxicity_scan` | Scan text for toxic language, hate speech, bias/stereotype framing, violence, sexual and self-harm content. | security |
| `function_call_validate` | Validate an LLM function call / tool_use output: check that function name is in allowed list, arguments match expected schema (types, enums, ranges), no extra/missing args. | security |
| `conversation_analyze` | Analyze a multi-turn conversation for context retention, topic drift, instruction following, and repetition. | eval |
| `mcp_schema_lint` | Lint one MCP tool definition with the same rules as mcp_server_health_check: errors break the MCP spec (FAIL), documentation_issues are what its strict mode refuses — a parameter without description or type (FIX, never an A) — and suggestions are style only (snake_case) and change nothing. | security |
| `cot_analyzer` | Analyze a Chain-of-Thought (CoT) or reasoning trace from an LLM. | eval |
| `ab_test_report` | Generate an A/B test report comparing two prompts or model configurations. | eval |
| `similarity_score` | Compute text similarity between reference and hypothesis using multiple metrics: Cosine (BoW, TF-IDF), Jaccard, ROUGE-1, ROUGE-2, ROUGE-L, and BLEU. | eval |
| `bias_detect` | Analyse a set of LLM responses generated from the same prompt template but with different demographic variants (gender, origin, age, tone). | security |
| `run_vlm_test_suite` | Test a vision model (OpenAI, Anthropic or Gemini) on one image: each test case asks a question and asserts on the answer (contains, not_contains, json_format, min_length, max_length, semantic_contains = TF-IDF cosine ≥ 0.4). | eval |
| `multimodal_eval_guide` | Multimodal evaluation: action=guide (default) interprets a CLIP/FID/VQA score against reference thresholds; clip_score, fid_score, vqa_accuracy compute the metric (HuggingFace, or your VLM key for VQA); pipeline runs all three. | — |
| `run_vlm_test_suite_batch` | Compare several vision models on the same image and test cases, in parallel (same assertions as run_vlm_test_suite). | — |

## integrations

| Tool | What it does | Packs |
|---|---|---|
| `jira_to_test_suite` | Turn a Jira ticket into a test suite: Gherkin scenarios, E2E steps, API tests, test data and the ambiguities to clarify. | — |
| `post_jira_comment` | Post the output of jira_to_test_suite as a formatted comment on the source Jira ticket. | — |
| `create_confluence_page` | Create a new Confluence page from the output of jira_to_test_suite. | — |
| `fetch_jira_issue` | Fetch a complete Jira issue: summary, description converted to Markdown, status, assignee, priority, labels, custom fields, and optionally comments and attachment metadata. | — |
| `search_jira_issues` | Search Jira using JQL (Jira Query Language). | — |
| `fix_gherkin` | Fix Gherkin syntax warnings from a jira_to_test_suite result. | — |
| `fetch_confluence_page` | Fetch a Confluence page and return its content as clean Markdown. | — |

## security

| Tool | What it does | Packs |
|---|---|---|
| `redact_pii` | Automatically detect and redact Personally Identifiable Information (PII) from text. | security |
| `secret_scan` | Scan text or code for leaked secrets: API keys (AWS, GCP, Azure, OpenAI, Anthropic, Stripe, GitHub, GitLab, Slack, Twilio, SendGrid, HuggingFace), Slack / Teams / Discord webhook URLs, private keys, JWTs, database connection strings, Bearer and Basic auth headers, and hard-coded values assigned to password/secret/token names (a value read at run time — Cypress.env(), os.getenv() — is not flagged). | security |
| `shield_analyze` | One-call safety gate for an LLM response: grounding (with source), prompt injection on the response AND the prompt (checks.injection / checks.injection_prompt), toxicity, PII, guardrail rules, quality, plus an LLM review on Groq (server key; model "none" skips it and sends nothing out). | security |
| `security_headers_check` | Analyse the HTTP security headers of a public URL OR of raw response headers you paste in. | security |
| `ssl_certificate_check` | Analyse the SSL/TLS certificate of any HTTPS host. | security |
| `cors_test` | Audit a URL for CORS misconfigurations across several origins: wildcard with credentials, reflected origin, null origin, subdomain bypass, missing Vary. | security |
| `cors_checker` | Would a browser on this origin be allowed to read this URL? | security |
| `cookie_security_audit` | Audit the security attributes of cookies set by any URL. | security |
| `web_security_audit` | Run a comprehensive web security audit combining headers, SSL, CORS, and cookies checks — then use an LLM to produce a prioritised remediation plan. | security |

## rag

| Tool | What it does | Packs |
|---|---|---|
| `embedding_similarity` | Compute text similarity using local algorithms (Bag of Words, TF-IDF, Character N-grams). | eval |
| `rag_relevance_rank` | Rank an array of text chunks by relevance to a query using TF-IDF scoring. | eval |
| `vector_similarity` | Compute similarity/distance between two float vectors: cosine similarity, dot product, Euclidean and Manhattan distance. | — |
| `normalize_vector` | L2-normalize a float vector (produce a unit vector with norm=1). | — |
| `vector_quantize` | Simulate int8 or int4 quantization of float32 embedding vectors. | — |
| `vector_stats` | Compute statistics for a float vector or matrix of vectors: mean, std, L2 norm, min, max, sparsity, top-K indices. | — |
| `bm25_score` | Compute BM25 relevance score between a query and one or more documents. | eval |
| `build_rag_prompt` | Assemble a complete RAG (Retrieval-Augmented Generation) prompt from retrieved context chunks and a user query. | eval |
| `prompt_template_fill` | Fill a prompt template with variables. | — |
| `few_shot_formatter` | Format few-shot examples for LLM prompts. | — |
| `system_prompt_builder` | Build a structured system prompt from components: role, task, constraints, output format, tone, language, and examples. | — |
| `rerank_evaluate` | Evaluate RAG retrieval: rank passages against a query, compute Precision@k / Recall@k and a PASS/FAIL verdict from your relevance labels. | eval |

## llm

| Tool | What it does | Packs |
|---|---|---|
| `count_tokens` | Estimate the token count of a text string using the cl100k_base approximation (~4 chars/token). | eval |
| `truncate_to_tokens` | Truncate text to at most N tokens (cl100k_base: ~4 chars/token) to avoid exceeding an LLM context window. | — |
| `split_chunks` | Split text into chunks of at most N tokens (cl100k_base: ~4 chars/token) with optional overlap. | — |
| `extract_json_from_text` | Extract the first valid JSON object or array embedded in chaotic LLM output (surrounded by markdown fences, prose, or explanatory text). | eval |
| `estimate_llm_cost` | Estimate the API cost in USD for a given model and token counts, at the price read daily from the provider's own pricing page (prices_as_of, price_status). | eval |
| `token_budget_calculator` | Plan token allocation across system prompt, user input, context/RAG chunks, and expected output. | eval |
| `context_window_check` | Given an array of message objects [{role, content}], estimate total token usage and check if it fits in the target model's context window. | eval |
| `model_info` | Get detailed specs for an AI model: context window, pricing per 1K tokens, knowledge cutoff, provider, multimodal support, reasoning capabilities, and feature list. | eval |
| `compare_models` | Put 2-5 AI models side by side: price per 1k tokens, context window, multimodal, reasoning, provider, pricing page. | eval |
| `list_llm_models` | List all LLM models available on ia-qa.com with their provider, API endpoint, and capabilities. | eval |
| `llm_generate` | Generate text with an open-source model hosted on Groq, on the server's key — no API key needed. | eval |
| `optimize_prompt_tokens` | Compress an LLM prompt by removing filler words, verbose phrases, duplicate sentences, and unnecessary whitespace. | — |
| `llm_fit_finder` | Shortlist LLMs on facts, no ranking: cloud models with the features you need within a monthly budget, cheapest first; or local models that fit your VRAM, largest first, with the ollama command. | — |

## dev

| Tool | What it does | Packs |
|---|---|---|
| `validate_email` | Validate an email address against RFC 5322 syntax before storing it, sending a transactional email, or adding it to a mailing list. | data |
| `minify_js` | Minify a JavaScript snippet, function, class, or module up to 50 KB using Terser. | — |
| `decode_jwt` | Decode a JWT (JSON Web Token) and return its header and payload without verifying the signature. | security, data |
| `timestamp_convert` | Convert between Unix timestamps (seconds or milliseconds) and ISO-8601 / UTC date strings. | data |
| `validate_url` | Parse and validate a URL. | security |
| `check_contrast_ratio` | Calculate WCAG 2.1 contrast ratio between two colors. | — |
| `cron_parse` | Parse a cron expression into a human-readable schedule description. | data |
| `cron_validator` | Validate a 5-field cron expression, explain the schedule, and preview the next execution times. | — |
| `http_status_lookup` | Look up detailed information about any HTTP status code: class, name, description, cacheability, typical causes, and handling best practices. | security |
| `parse_http_headers` | Parse a raw HTTP headers block into a structured JSON object. | security |
| `generate_curl` | Generate a curl command from request parameters. | — |
| `extract_todos` | Extract TODO, FIXME, HACK, BUG, NOTE, OPTIMIZE, and custom tags from any source code or text. | — |
| `detect_secrets` | Scan code or config files for hardcoded secrets: AWS keys, GitHub tokens, OpenAI/Anthropic API keys, Stripe secrets, JWTs, Slack/Teams/Discord webhook URLs, session cookies, database connection strings, and generic passwords. | security |
| `count_code_lines` | Count lines of code: total, code lines, comment lines, blank lines, and comment density. | data |
| `lint_commit_message` | Validate a git commit message against the Conventional Commits spec (feat, fix, docs, style, refactor, test, chore, ci, perf, build). | data |
| `format_bytes` | Convert raw byte counts to human-readable sizes in SI (KB=1000) or IEC (KiB=1024) units, or parse size strings back to bytes. | — |
| `pr_gatekeeper` | Compound quality gate for pull requests. | — |
| `webhook_endpoint_create` | Create a temporary webhook endpoint that captures incoming HTTP requests for one hour. | — |
| `webhook_endpoint_requests` | Fetch the requests captured by a webhook created with webhook_endpoint_create. | — |
| `env_parse` | Parse a .env file content into a JSON object. | data |
| `openapi_validate` | Validate the structure of an OpenAPI 3.x specification (JSON or YAML). | data |

## web

| Tool | What it does | Packs |
|---|---|---|
| `generate_slug` | Convert any string into a URL-friendly slug: lowercase, ASCII-normalized (é→e), special characters removed, spaces replaced with hyphens. | data |
| `fetch_veille_feed` | Fetch the latest QA & AI/LLM articles aggregated from curated RSS sources (Google Testing Blog, DEV.to Testing/QA/AI/LLM/Agents, Hugging Face Blog, Simon Willison). | — |
| `score_geo_signals` | Analyze a webpage <head> HTML (or full HTML) for GEO (Generative Engine Optimization) signals. | — |
| `latency_benchmark` | Measure response time of one or more HTTP endpoints (GET/POST). | security |

## data

| Tool | What it does | Packs |
|---|---|---|
| `format_json` | Validate and pretty-print a string that is ALREADY valid JSON. | data |
| `parse_csv` | Parse a CSV string into a JSON array of objects (or raw arrays). | data |
| `extract_json_path` | Extract a value from a JSON string using dot-notation path (e.g., "user.address.city", "items.0.name", "meta.tags"). | data |
| `generate_json_ld` | Generate a ready-to-paste <script type="application/ld+json"> snippet for GEO / structured data optimization. | — |
| `json_schema_validate` | Validate a JSON value against a JSON Schema (draft-07 subset). | data |
| `flatten_json` | Flatten a nested JSON object to single-level dot-notation keys (e.g. | data |
| `xml_to_json` | Convert an XML string to a JSON object. | data |
| `mock_from_schema` | Generate realistic mock data from a JSON Schema. | data |
| `transform_json_array` | Transform a JSON array using common operations: pluck (extract specific fields), filter (by field value), sort_by (field), group_by (field), count_by (field), uniq_by (field). | — |
| `json_to_csv` | Convert a JSON array of objects to CSV format. | data |
| `json_diff` | Compute a deep structural diff between two JSON values. | data |
| `merge_json` | Deep merge two JSON objects. | — |
| `json_to_yaml` | Convert a JSON object to clean, human-readable YAML. | data |
| `yaml_to_json` | Parse a YAML string and return the equivalent JSON value. | data |
| `json_schema_generate` | Infer a JSON Schema (draft-07) from a sample JSON value. | data |
| `format_table` | Convert a JSON array of objects into a Markdown table. | — |

## text

| Tool | What it does | Packs |
|---|---|---|
| `text_stats` | Compute comprehensive statistics for any text: character count (with and without spaces), word count, line count, sentence count, paragraph count, and estimated reading time in minutes. | data |
| `regex_test` | Test a regular expression pattern against an input string and return all matches with their index positions and named capture groups. | data |
| `lorem_ipsum` | Generate Lorem Ipsum placeholder text for UI mockups, design prototypes, or test data population. | data |
| `strip_markdown` | Strip all Markdown formatting (headers, bold, italic, code fences, links, lists) from text and return clean plain text. | — |
| `escape_html` | Escape HTML special characters (&, <, >, ", ') to their safe HTML entities. | — |
| `unescape_html` | Convert HTML entities (&amp;, &lt;, &gt;, &quot;, &#x27;, and numeric &#NNN;) back to plain characters. | — |
| `case_convert` | Convert a string between naming conventions: camelCase, PascalCase, snake_case, kebab-case, UPPER_SNAKE_CASE, dot.case, Title Case. | data |
| `sort_lines` | Sort, deduplicate, reverse, or filter lines of text. | — |
| `html_to_markdown` | Convert HTML to clean Markdown. | — |
| `calculate_readability` | Calculate readability scores: Flesch Reading Ease, Flesch-Kincaid Grade Level, Coleman-Liau Index, and Automated Readability Index. | — |
| `normalize_whitespace` | Normalize whitespace: trim trailing spaces, collapse blank lines, normalize line endings (LF/CRLF), convert tabs to spaces. | — |
| `word_frequency` | Analyze word frequency in text. | — |
| `extract_links` | Extract all URLs, email addresses, and domain names from text. | — |
| `levenshtein_distance` | Compute the Levenshtein (edit) distance and normalized similarity ratio between two strings. | — |
| `detect_language` | Detect the natural language of a text using n-gram frequency analysis and common word markers. | — |

## encoding

| Tool | What it does | Packs |
|---|---|---|
| `generate_uuid` | Generate one or more cryptographically random UUID v4 identifiers. | data |
| `hash_text` | Compute a cryptographic hash of a text string. | security, data |
| `base64_encode` | Encode a UTF-8 string to Base64. | data |
| `base64_decode` | Decode a Base64 string back to UTF-8 text. | data |
| `url_encode` | Percent-encode a string for safe use in URLs. | data |
| `url_decode` | Decode a percent-encoded URL string back to plain text. | data |
| `generate_password` | Generate a cryptographically secure random password using crypto.randomBytes. | security |
| `color_convert` | Convert a color between HEX, RGB, and HSL formats. | data |
| `number_base_convert` | Convert numbers between bases: decimal, binary, octal, hexadecimal, or any base 2–36. | data |
| `generate_hmac` | Compute an HMAC signature for a message using a secret key. | security |
