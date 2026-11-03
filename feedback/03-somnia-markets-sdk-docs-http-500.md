# Somnia Markets SDK documentation page returns HTTP 500

Severity: major
Area: SDK

## Steps to reproduce

1. Open the Somnia Markets SDK documentation page linked from the bounty Resources: https://docs.somnia.network/developers/products/markets/overview
2. Wait for the page to load.
3. Reload the page and try to open it again.

## Expected

The Markets overview page loads successfully and documents the `@somnia-chain/markets-sdk` package (installation, client setup, and links to the API surface), since it is the primary SDK documentation referenced by the bounty.

## Actual

The page returns "500 Internal Server Error" instead of documentation. The failure reproduced on two separate attempts on 2026-11-03, including after a reload, so it is not a transient client-side glitch. Participants following the bounty Resources to learn the SDK land on a server error and cannot read the SDK overview.

## Evidence

- Failing URL: https://docs.somnia.network/developers/products/markets/overview
- Response on both attempts (2026-11-03): HTTP 500, "500 Internal Server Error"
- The same URL is the Markets SDK documentation linked from the dreamDEX Perps Builder Bounty Resources on DoraHacks: https://dorahacks.io/hackathon/dreamdex-perps-bounty/detail

## Environment

SDK version if relevant: `@somnia-chain/markets-sdk` (version as documented on the linked overview page; page itself unreachable)
Network: Somnia Tokyo testnet
Wallet address: TBD
