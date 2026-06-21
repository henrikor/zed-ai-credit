# zed-ai-credit

Show how much AI credit you have left from your AI provider.

This repository tracks the design and upstream work for a **built-in Zed status bar indicator**. The implementation lives in a fork of [zed-industries/zed](https://github.com/zed-industries/zed) as the `ai_credit_status` crate.

## Status

- Upstream implementation: [henrikor/zed `ai-credit-status-bar`](https://github.com/henrikor/zed/tree/ai-credit-status-bar)
- Pull request: https://github.com/zed-industries/zed/pull/59655
- Feature discussion: https://github.com/zed-industries/zed/discussions/59656
- Docs: `docs/src/ai/ai-credit-status.md` in the Zed fork
- Issue draft: [UPSTREAM_ISSUE.md](./UPSTREAM_ISSUE.md)

## Settings (in Zed)

```json
"ai_credit_status": {
  "enabled": true,
  "refresh_seconds": 60,
  "monthly_budget_usd": null
}
```

## Supported providers (v1)

| Provider | Support |
| --- | --- |
| Zed Pro | When cloud API returns `token_spend_cents` |
| GitHub Copilot Chat | Premium request quota |
| OpenRouter | Credit limit via `/api/v1/key` |
| OpenAI | Monthly usage API + optional budget |
| Anthropic / Mistral | API key check + optional budget (no remaining-credit API) |

## Why not a Zed extension?

The extension API has no status bar primitive. A persistent indicator requires a core change or waiting for [RFC #53403](https://github.com/zed-industries/zed/discussions/53403).
