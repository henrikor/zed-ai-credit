# Upstream issue draft: AI credit status bar

Use this when opening a GitHub Discussion or Issue on [zed-industries/zed](https://github.com/zed-industries/zed).

## Title

Status bar: show AI credit / quota usage for active LLM provider

## Summary

Users want an always-visible indicator of how much AI credit or quota remains for whichever provider powers the Zed Agent (Zed Pro, Copilot, OpenRouter, BYOK, etc.). Today this information is scattered across web dashboards or slash commands, and is easy to miss until limits are hit.

Related requests:

- https://github.com/zed-industries/zed/discussions/56161
- https://github.com/zed-industries/zed/discussions/41148
- https://github.com/htahaozlu/context-bar/issues/1

## Proposal

Add a built-in status bar item (right side) with:

- Horizontal progress bar from 0% to 100% usage
- Color bands: green (0–25%), yellow (25–50%), orange (50–75%), red (75–100%)
- Tooltip with provider name, used/limit, reset info
- Click opens billing/account page when available
- Setting: `ai_credit_status.enabled`, `refresh_seconds`, optional `monthly_budget_usd`

## Zed Pro API request

`PlanInfo.usage` currently exposes edit prediction usage only. Please expose hosted LLM token spend in `/client/users/me` (e.g. `usage.token_spend_cents`) so the editor can show the same data previously visible on the account dashboard.

## Implementation

- Pull request: https://github.com/zed-industries/zed/pull/59655
- Feature discussion: https://github.com/zed-industries/zed/discussions/59656
- Branch: `ai-credit-status-bar` in [henrikor/zed](https://github.com/henrikor/zed)
