# Testnet app root redirects to the spot market; no direct perps entry point is linked for a perps bounty

Severity: normal
Area: app

## Steps to reproduce

1. Open the dreamDEX testnet app root: https://app.testnet.dreamdex.io/
2. Observe where the redirect lands.
3. Open the DoraHacks bounty page https://dorahacks.io/hackathon/dreamdex-perps-bounty/detail and scan the Resources section for a direct link to the perps interface.

## Expected

For a bounty that is specifically about perpetuals, the testnet app root — or at minimum the bounty Resources — provides a direct entry point to the perps trading interface, so participants can start testing perps without hunting through the app.

## Actual

https://app.testnet.dreamdex.io/ redirects to the SPOT market (https://app.testnet.dreamdex.io/trade/spot/tokyo/STT:USDso), not to perps. The bounty Resources list no direct perps URL either, even though the entire bounty concerns perps on testnet. A new participant following the official links lands on spot trading and has to discover the perps section on their own.

## Evidence

- Testnet app root: https://app.testnet.dreamdex.io/ → redirects to https://app.testnet.dreamdex.io/trade/spot/tokyo/STT:USDso (observed 2026-11-03)
- Bounty page and its Resources (no direct perps URL listed): https://dorahacks.io/hackathon/dreamdex-perps-bounty/detail

## Environment

SDK version if relevant: n/a (app navigation only)
Network: Somnia Tokyo testnet
Wallet address: TBD
