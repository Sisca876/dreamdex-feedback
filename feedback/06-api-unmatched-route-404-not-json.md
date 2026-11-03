# Unmatched API routes return a plain-text "404 page not found" instead of the documented JSON error format

Severity: normal
Area: API

## Steps to reproduce

1. Send a GET request to a route the API does not define, e.g. `curl https://api.dreamdex.io/v0/definitelynotathing`
2. Send GET requests to the two per-market order book paths the Market Data docs mention, e.g. `curl https://api.dreamdex.io/v0/markets/SOMI:USDso/orderbook` and `curl https://api.dreamdex.io/v0/orderbooks/SOMI:USDso`
3. Send a GET request to the API root: `curl https://api.dreamdex.io/v0`
4. Compare all three responses with the Error Handling documentation at https://app.dreamdex.io/docs/developers/http-api/error-handling

## Expected

Per the Error Handling page, "All error responses use a consistent JSON format" — `{"status": ..., "name": ..., "description": ...}` — with the error name also present in the `Error-Name` response header. An unmatched route should therefore return a JSON 404 body in that format.

## Actual

All three requests return HTTP 404 with a **plain-text** body consisting of the single line `404 page not found` (the Go HTTP server's default response), no JSON body, and **no `Error-Name` header**. API errors raised inside defined routes do follow the documented format (e.g. an unknown market returns `{"description":"market not found: NOPE:USDso","name":"market_not_found","status":404}` with an `error-name: market_not_found` header), so a client that parses every error as the documented JSON shape — as the docs instruct — crashes or mis-handles exactly the 404s produced by typos in the URL path, the most common integration mistake.

## Evidence

All requests made read-only (GET, no auth) on 2026-11-03 against production `https://api.dreamdex.io/v0`:

- `GET /v0/definitelynotathing` → 404, body `404 page not found`, no `Error-Name` header
- `GET /v0/markets/SOMI:USDso/orderbook` → 404, body `404 page not found`, no `Error-Name` header
- `GET /v0/orderbooks/SOMI:USDso` → 404, body `404 page not found`, no `Error-Name` header
- `GET /v0` → 404, body `404 page not found`, no `Error-Name` header
- Control case (documented format working): `GET /v0/markets/NOPE:USDso/trades` → 404, header `error-name: market_not_found`, body `{"description":"market not found: NOPE:USDso","name":"market_not_found","status":404}`
- Documented contract: https://app.dreamdex.io/docs/developers/http-api/error-handling ("All error responses use a consistent JSON format")

## Environment

SDK version if relevant: n/a (raw HTTP API)
Network: Somnia Tokyo testnet
Wallet address: TBD
