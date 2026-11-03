# Bounty page resource links to perps docs redirect to the docs homepage

Severity: normal
Area: docs

## Steps to reproduce

1. Open the official DoraHacks bounty page: https://dorahacks.io/hackathon/dreamdex-perps-bounty/detail
2. In the Resources section, follow the perps developer link: https://docs.dreamdex.io/perps-on-testnet-for-developers
3. Follow the perps trader link: https://docs.dreamdex.io/perps-on-testnet-for-traders
4. Compare the destination of both links with the working documentation pages https://app.dreamdex.io/docs/developers/perps-testnet and https://app.dreamdex.io/docs/trading/perps-testnet

## Expected

Each resource link from the bounty page lands on the specific perps documentation page it names (developer guide and trader guide respectively), so bounty participants can read the exact instructions the bounty refers to.

## Actual

Both links redirect to the generic documentation homepage https://app.dreamdex.io/docs instead of the intended perps pages. The correct content exists, but under different URLs (https://app.dreamdex.io/docs/developers/perps-testnet and https://app.dreamdex.io/docs/trading/perps-testnet), so participants following the official bounty resources never reach it and have to guess or search for the right pages.

## Evidence

- Link listed in the bounty Resources: https://docs.dreamdex.io/perps-on-testnet-for-developers → redirects to https://app.dreamdex.io/docs
- Link listed in the bounty Resources: https://docs.dreamdex.io/perps-on-testnet-for-traders → redirects to https://app.dreamdex.io/docs
- Working developer page: https://app.dreamdex.io/docs/developers/perps-testnet
- Working trader page: https://app.dreamdex.io/docs/trading/perps-testnet
- Observed read-only on 2026-11-03.

## Environment

SDK version if relevant: n/a (documentation links only)
Network: Somnia Tokyo testnet
Wallet address: TBD
