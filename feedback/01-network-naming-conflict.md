# Conflicting Somnia testnet names and chain IDs across official dreamDEX sources

Severity: normal
Area: docs

## Steps to reproduce

1. Open the DoraHacks bounty page for the dreamDEX Perps Builder Bounty (https://dorahacks.io/hackathon/dreamdex-perps-bounty/detail) and note that the bounty text and the feedback template refer to the "Somnia Tokyo testnet".
2. Open the developer documentation page https://app.dreamdex.io/docs/developers/perps-testnet and note that it calls the perps chain the "Hideki testnet" (Chain ID 50383, RPC api.hideki2.infra.testnet.somnia.network, as of 2026-11-03 13:34 UTC+7). Earlier the same day (2026-11-03 13:21 UTC+7) the same page was observed showing Chain ID 5115 with RPC dream-rpc.somnia.network, so the published network parameters themselves changed during the bounty.
3. Open the public bot kit README at https://github.com/somnia-chain/dreamdex-bot-kit and note that it tells users to start spot trading on the "Shannon testnet" (Chain ID 50312).
4. Open the testnet app at https://app.testnet.dreamdex.io/trade/spot/tokyo/STT:USDso and note that the URL path uses yet another name, `/tokyo/`.

## Expected

All official sources use one consistent testnet name (and state the matching chain ID) for the network that perps feedback should target, so a tester knows exactly which chain to connect to and reproduce issues against.

## Actual

Four different labels are in use across official Somnia/dreamDEX sources — "Somnia Tokyo testnet" (bounty + template), "Hideki testnet", Chain ID 50383 (developer docs, current), "Shannon testnet", Chain ID 50312 (bot kit README, for spot), and `/tokyo/` (testnet app URL). The developer docs' own chain ID also changed during the bounty (5115 observed at 13:21 UTC+7, 50383 at 13:34 UTC+7 on 2026-11-03). A tester cannot tell which name/chain the perps feedback is supposed to target, and risks filing reports against the wrong network or being unable to reproduce issues reported by others.

## Evidence

- Bounty page / feedback template wording: "Somnia Tokyo testnet" — https://dorahacks.io/hackathon/dreamdex-perps-bounty/detail
- Developer docs naming the perps chain "Hideki testnet", Chain ID 50383 (RPC api.hideki2.infra.testnet.somnia.network) when fetched 2026-11-03 13:34 UTC+7; the same page showed Chain ID 5115 (RPC dream-rpc.somnia.network) at 13:21 UTC+7 the same day: https://app.dreamdex.io/docs/developers/perps-testnet
- Bot kit README instructing users to start spot on "Shannon testnet", Chain ID 50312: https://github.com/somnia-chain/dreamdex-bot-kit
- Testnet app URL containing `/tokyo/`: https://app.testnet.dreamdex.io/trade/spot/tokyo/STT:USDso
- Observed read-only on 2026-11-03.

## Environment

SDK version if relevant: n/a (documentation naming only)
Network: Somnia Tokyo testnet
Wallet address: TBD
