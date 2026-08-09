# Claude Opus 5 API production notes

## Confirmed contract

- Endpoint: `POST /v1/messages`
- Model ID: `claude-opus-5`
- Authentication: `x-api-key: <POYO_API_KEY>`

## Input limits

| Field | Requirement | Constraint |
| --- | --- | --- |
| model | required | claude-opus-5. |
| max_tokens | required | Maximum generated tokens. |
| system | optional | System prompt. |
| messages | required | Anthropic-style role/content messages. |
| stream | optional | Enable streaming when supported by the client. |

## Operational checklist

- Keep API keys in a server-side secret manager.
- Validate user input before calling the API.
- Apply request timeouts and retry only rate limits or transient 5xx responses.
- Bound output tokens and log usage for cost control.
- Redact sensitive prompt and response content from logs.
- Recheck the live model page before hard-coding prices.

## Failure handling

Treat non-2xx HTTP responses and non-success API `code` values as errors. Preserve the HTTP status, API code, request ID when present, and a redacted response body for debugging.

Schema: [PoYo API documentation](https://docs.poyo.ai/api-manual/chat-series/claude-messages)

