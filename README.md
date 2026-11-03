# dreamDEX Perps Builder Bounty — Feedback Reports

Feedback reports for the dreamDEX perpetuals testnet, prepared for the
[dreamDEX Perps Builder Bounty](https://dorahacks.io/hackathon/dreamdex-perps-bounty/detail)
on DoraHacks (Feedback track, Somnia Network).

Each report lives in its own Markdown file under [`feedback/`](feedback/),
following the bounty template exactly: title, severity, area, steps to
reproduce, expected vs. actual behaviour, evidence, and environment.

## Reports

| # | File | Area | Severity | Summary |
|---|------|------|----------|---------|
| 1 | [01-network-naming-conflict.md](feedback/01-network-naming-conflict.md) | docs | normal | Official sources use four different testnet names/chain IDs (Tokyo, Hideki, Shannon, `/tokyo/`), so testers cannot tell which network perps feedback targets. |
| 2 | [02-broken-perps-docs-links-from-bounty-page.md](feedback/02-broken-perps-docs-links-from-bounty-page.md) | docs | normal | Both perps documentation links in the bounty Resources redirect to the docs homepage instead of the perps pages. |
| 3 | [03-somnia-markets-sdk-docs-http-500.md](feedback/03-somnia-markets-sdk-docs-http-500.md) | SDK | major | The Somnia Markets SDK overview page linked from the bounty Resources returns HTTP 500. |
| 4 | [04-bot-kit-repository-reference-inconsistency.md](feedback/04-bot-kit-repository-reference-inconsistency.md) | docs | normal | The bounty Resources link to a bot kit repo that 404s when logged out, while the official Link-a-Bot guide points to a different, public repo. |
| 5 | [05-no-direct-perps-entry-point.md](feedback/05-no-direct-perps-entry-point.md) | app | normal | The testnet app root redirects to the spot market and the bounty Resources list no direct perps URL, although the bounty is about perps. |
| 6 | [06-api-unmatched-route-404-not-json.md](feedback/06-api-unmatched-route-404-not-json.md) | API | normal | Unmatched API routes return a plain-text `404 page not found` with no `Error-Name` header, contradicting the documented "all error responses use a consistent JSON format". |
| 7 | [07-candles-invalid-interval-error-name.md](feedback/07-candles-invalid-interval-error-name.md) | API | normal | An unsupported candle interval returns the generic `invalid_param` error instead of the documented `invalid_interval` error. |

## How these reports were produced

All findings were gathered **read-only** on 2026-11-03 — no account actions,
no order placement, no trading:

- **Documentation and app review.** The bounty page and its Resources, the
  developer and trading documentation at `app.dreamdex.io/docs`, the testnet
  app at `app.testnet.dreamdex.io`, the Somnia developer docs, and the public
  bot kit repository were opened and cross-checked against each other. Every
  claim in the reports quotes the exact URL where the behaviour was observed.
- **Public REST API probing.** The documented public endpoints of the HTTP API
  (`/v0/markets`, `/v0/currencies`, `/v0/tickers`, `/v0/orderbooks`,
  `/v0/markets/{symbol}/trades`, `/v0/markets/{symbol}/volume`,
  `/v0/markets/{symbol}/candles`, `/v0/auth/nonce`, plus error cases) were
  called with unauthenticated GET requests against both production
  (`https://api.dreamdex.io/v0`) and staging
  (`https://stg.api.dreamdex.io/v0`), and the responses were compared with the
  behaviour promised on the docs' Error Handling, Authentication, and Market
  Data pages. 27 requests in total, sent sequentially. Responses that matched
  the documentation (market discovery, `market_not_found`, `missing_field`,
  `unauthorized`, staging/production error parity) are not reported as issues;
  only reproducible contradictions were written up.

## Evaluation note

Per the bounty rules, each feedback item is filed as its own Markdown file in
the `feedback/` folder of this repository so items can be evaluated
individually (first valid report of an issue is rewarded; critical/major items
at the higher rate). Environment details that depend on the submitter's own
setup (wallet address) are marked `TBD` in the drafts and will be filled in at
submission time.
