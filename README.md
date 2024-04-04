
# Coinbase Smart Wallet Mitigation Review details
- Total Prize Pool: $12,500 in USDC
  - HM awards: $10,000 in USDC
  - Judge awards: $2,000 in USDC
- Join [C4 Discord](https://discord.gg/code4rena) to register
- Submit findings [using the C4 form](https://code4rena.com/audits/2024-04-coinbase-smart-wallet-mitigation-review/submit)
- [Read our guidelines for more details](https://docs.code4rena.com/roles/wardens)
- Starts April 5, 2024 20:00 UTC
- Ends April 8, 2024 20:00 UTC

## Important note 

Each warden must submit a mitigation review for *every finding* from the parent audit that is listed as in-scope for the mitigation review as well as noted additional items. **Incomplete mitigation reviews will not be eligible for awards.**

## Findings being mitigated

Mitigations of all issues listed here will be considered in-scope.

- [H-01: Users making specific chain account ownership upgrades will likely cause issues when later using cross-chain replay-able ownership upgrades](https://github.com/code-423n4/2024-03-coinbase-findings/issues/114)

- [M-01: Balance check during MagicSpend validation cannot ensure that MagicSpend has enough balance to cover the requested fund.](https://github.com/code-423n4/2024-03-coinbase-findings/issues/110)

- [QA-01: All Smart Wallet funds will be lost if users remove all owners](https://github.com/code-423n4/2024-03-coinbase-findings/issues/181)

Additional Items
[ ⭐️ SPONSORS ADD INFO HERE ]

## Overview of changes

Please provide context about the mitigations that were applied if applicable and identify any areas of specific concern.

## Mitigations to be reviewed

### Branch
[ ⭐️ SPONSORS ADD A LINK TO THE BRANCH IN YOUR REPO CONTAINING ALL PRS ]

### Individual PRs
[ ⭐️ SPONSORS ADD ALL RELEVANT PRs TO THE TABLE BELOW:]

Wherever possible, mitigations should be provided in separate pull requests, one per issue. If that is not possible (e.g. because several audit findings stem from the same core problem), then please link the PR to all relevant issues in your findings repo. 

| URL | Mitigation of | Purpose | 
| ----------- | ------------- | ----------- |
| https://github.com/your-repo/sample-contracts/pull/XXX | H-01 | This mitigation does XYZ | 

## Out of Scope

Please list any High and Medium issues that were judged as valid but you have chosen not to fix.


