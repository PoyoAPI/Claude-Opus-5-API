# Claude Opus 5 API: cURL quickstart

Call `/v1/messages` with model `claude-opus-5`:

```bash
export POYO_API_KEY="your-api-key"
export POYO_BASE_URL="https://api.poyo.ai"

curl -X POST "$POYO_BASE_URL/v1/messages" \
  -H "x-api-key: $POYO_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
  "model": "claude-opus-5",
  "max_tokens": 900,
  "system": "You are a rigorous research and engineering assistant.",
  "messages": [
    {
      "role": "user",
      "content": "Review this rollout strategy: canary 5%, then 25%, then 100%. List missing safety checks."
    }
  ]
}'
```

Keep the API key on your server. Add timeouts, bounded retries, and usage logging before production.

See the [full README](../README.md) and [production notes](../docs/production-notes.md).

