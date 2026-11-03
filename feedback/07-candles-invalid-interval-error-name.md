# Unsupported candle interval returns `invalid_param`, not the documented `invalid_interval` error

Severity: normal
Area: API

## Steps to reproduce

1. Send a GET request with an unsupported candle interval: `curl "https://api.dreamdex.io/v0/markets/SOMI:USDso/candles?interval=3x"`
2. Read the `name` field of the error response (and the `Error-Name` header).
3. Compare with the error table on the Error Handling documentation page: https://app.dreamdex.io/docs/developers/http-api/error-handling

## Expected

The Error Handling page documents a dedicated 400 error for this case: `invalid_interval` — "Unsupported candle interval". A client built against the docs handles an unsupported interval by matching on `invalid_interval`.

## Actual

The API returns HTTP 400 with `name: "invalid_param"` — the generic parameter error — plus a description that embeds the endpoint's raw OpenAPI schema fragment. The documented `invalid_interval` name is not emitted for an unsupported interval value, so error handling written against the documentation never triggers for the exact case the docs describe. (The staging API at https://stg.api.dreamdex.io/v0 behaves identically.)

## Evidence

Request/response captured read-only on 2026-11-03:

- Request: `GET https://api.dreamdex.io/v0/markets/SOMI:USDso/candles?interval=3x`
- Response: HTTP 400, header `error-name: invalid_param`, body:
  `{"description":"parameter \"interval\" in query has an error: value is not one of the allowed values [\"1m\",\"5m\",\"15m\",\"1h\",\"4h\",\"1d\"]\nSchema:\n  {\n    \"enum\": [...],\n    \"type\": \"string\"\n  }\n\nValue:\n  \"3x\"\n","name":"invalid_param","status":400}`
- Same request against staging (`https://stg.api.dreamdex.io/v0/...`) returned the identical status, name, and description.
- Documented error table (Validation 400 section) lists `invalid_interval` = "Unsupported candle interval": https://app.dreamdex.io/docs/developers/http-api/error-handling
- Related check: omitting `interval` entirely returns 400 `missing_field` ("Query argument interval is required, but not found"), which does match the docs — only the unsupported-value case diverges.

## Environment

SDK version if relevant: n/a (raw HTTP API)
Network: Somnia Tokyo testnet
Wallet address: TBD
