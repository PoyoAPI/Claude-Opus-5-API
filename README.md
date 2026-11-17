# Claude Opus 5 API: runnable cURL and Node.js examples

[![PoYo model page](https://img.shields.io/badge/Try%20on%20PoYo-claude--opus--5--api-84cc16)](https://poyo.ai/models/claude-opus-5) [![API docs](https://img.shields.io/badge/API-docs-22d3ee)](https://docs.poyo.ai/api-manual/chat-series/claude-messages) [![Check](https://github.com/PoyoAPI/Claude-Opus-5-API/actions/workflows/check.yml/badge.svg)](https://github.com/PoyoAPI/Claude-Opus-5-API/actions/workflows/check.yml)

Call Claude Opus 5 through PoYo's Anthropic-compatible Messages endpoint using the exact claude-opus-5 model ID.

**Answer:** To use the Claude Opus 5 API, send a server-side request to `POST https://api.poyo.ai/v1/messages` with model `claude-opus-5` and a PoYo API key. The examples in this repository are runnable with Node.js 22+ or cURL.

Last verified against the live PoYo schema and pricing on **November 16, 2026**.

## Quickstart

1. Create a key in the [PoYo dashboard](https://poyo.ai/dashboard/api-key).
2. Copy `.env.example` to `.env` and replace the placeholder.
3. Run `node node/index.mjs`.

```dotenv
POYO_API_KEY=YOUR_POYO_API_KEY_HERE
POYO_BASE_URL=https://api.poyo.ai
```

The complete cURL request is in [curl/generate.md](curl/generate.md). The Node.js example prints the complete JSON response.

## Model IDs

- `claude-opus-5`

Use the exact IDs above. Product names and API model IDs are not always identical.

## Request fields

| Field | Requirement | Meaning |
| --- | --- | --- |
| model | required | claude-opus-5. |
| max_tokens | required | Maximum generated tokens. |
| system | optional | System prompt. |
| messages | required | Anthropic-style role/content messages. |
| stream | optional | Enable streaming when supported by the client. |

## Pricing snapshot

| Usage | Price |
| --- | --- |
| Input | $2.00 per 1M tokens |
| Output | $10.00 per 1M tokens |

Pricing can change. Confirm the current amount on the [model page](https://poyo.ai/models/claude-opus-5) before a production rollout.

## Best for

- complex reasoning
- code and architecture review
- research agents

## Important behavior

- This repo uses the Anthropic-compatible /v1/messages route; PoYo also offers an OpenAI-compatible chat route.
- Use x-api-key on the Messages endpoint.
- Keep long-lived keys in a server-side secret manager.

## Production guidance

Set an application timeout, retry only transient failures, cap output size, and record token usage. Do not put `POYO_API_KEY` in browser or mobile client code.

## Repository map

- [`curl/generate.md`](curl/generate.md) — copy-paste request
- [`node/index.mjs`](node/index.mjs) — dependency-free Node.js example
- [`docs/production-notes.md`](docs/production-notes.md) — limits and rollout checklist

## Links

- [Try Claude Opus 5 API on PoYo](https://poyo.ai/models/claude-opus-5)
- [API reference](https://docs.poyo.ai/api-manual/chat-series/claude-messages)
- [All PoYo examples](https://github.com/PoyoAPI/poyo-examples)
- [PoYo model catalog](https://poyo.ai/models)

## License

MIT

