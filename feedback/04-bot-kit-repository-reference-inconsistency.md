# Conflicting bot kit repository references: bounty Resources link 404s while the official guide points to a different repo

Severity: normal
Area: docs

## Steps to reproduce

1. Open the DoraHacks bounty page https://dorahacks.io/hackathon/dreamdex-perps-bounty/detail and follow the bot kit link in the Resources section: https://github.com/dreamdexio/bot-kit — while logged out of GitHub, this returns a GitHub 404 page.
2. Open the official "Link a Bot" guide in the testnet app docs: https://app.testnet.dreamdex.io/docs/trading/common/link-a-bot and note which repository it points to.
3. Open the dreamBot Builder page in the testnet app and note how it describes the bot kit's availability on GitHub.

## Expected

Every official source references the same, publicly reachable bot kit repository, so a participant can always clone the kit the bounty and guides describe.

## Actual

The references are inconsistent:

- The bounty Resources link (https://github.com/dreamdexio/bot-kit) returns a GitHub 404 when visited logged out. From the outside it is not verifiable whether that repository is private or does not exist — either way, a logged-out participant cannot reach it.
- The official "Link a Bot" guide points to a different, publicly accessible repository: https://github.com/somnia-chain/dreamdex-bot-kit
- The dreamBot Builder page states the kit "is public on GitHub" but gives no URL at all.

A participant following the bounty page hits a dead end, while a participant following the app guide reaches a working repo — the two official paths disagree about where the bot kit lives.

## Evidence

- Bounty Resources link returning GitHub 404 (logged out), observed 2026-11-03: https://github.com/dreamdexio/bot-kit
- Official guide pointing to the public repository: https://app.testnet.dreamdex.io/docs/trading/common/link-a-bot → https://github.com/somnia-chain/dreamdex-bot-kit
- dreamBot Builder page in the testnet app (https://app.testnet.dreamdex.io) describing the kit as "public on GitHub" with no URL given.
- Bounty page listing the Resources: https://dorahacks.io/hackathon/dreamdex-perps-bounty/detail

## Environment

SDK version if relevant: n/a (repository references only)
Network: Somnia Tokyo testnet
Wallet address: TBD
