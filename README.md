# intgetion-llm

The LLM layer of the INTGETION platform as a shared library (no database, no
HTTP). Used by the bot and by any module that writes text with a model
(briefs intro, freelance and UGC drafts).

- `anthropic`, `openrouter`: chat adapters with tool calls.
- `provider`, `select`: one `LLMProvider` interface; `llmFromEnv()` and
  `modelsFromEnv()` pick the provider and models from env.
- `budget`: token and cost accounting (`costMicroUsd`, `trimContext`,
  `MAX_OUTPUT_TOKENS`), cost anomaly check, circuit breaker.
- `redact`: `redactPii` for logs and model input.
- `untrusted`: `wrapUntrusted` for user text placed in prompts.
- `./jev`: the structured question format used by the bot evals.
- Test fakes: `fake`, `fakeText`.

Env names (values are never stored here): `ANTHROPIC_API_KEY`,
`OPENROUTER_API_KEY` and the model and provider switches read by
`select.ts`.

```bash
npm ci
npm test
```

Install by tag: `"@intgetion/llm": "github:theonyxiesss/intgetion-llm#v0.1.0"`.
