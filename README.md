
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

## Mitigations to be reviewed
- [H-01 Fix](https://github.com/coinbase/smart-wallet/pull/42): The issue is remediated by updating the parameterization of `removeOwnerAtIndex` to also take an `owner` argument. We then check that the `owner` passed matches the owner found at the index. In this way, we prevent a replayable transaction removing a different owner at the same index. 
- [M-01 Fix](https://github.com/coinbase/magic-spend/pull/17): This issue is complex to address. The warden suggested adding a variable to track in flight withdraws, and we [pursued this](https://github.com/coinbase/magic-spend/pull/16). However, we realized that bundlers penalize paymasters when the UserOp behaves differently when simulated in isolation vs. in the bundle, and this would not fix this. Instead, we give the owner a tool to address this probabilistically: the owner can set a `maxWithdrawDenominator` and we enforce that native asset withdraws must be `<= address(this).balance / maxWithdrawDenominator`. For example, if `maxWithdrawDenominator` is set to 20, it would take 20 native asset withdraws (each withdrawing max allowed) + 1 native asset withdraw in the same transaction to cause a revert. It is of course known that this doesn't entirely solve the issue, and the efficacy depends the value chosen and usage. 
- [QA-01 Fix](https://github.com/coinbase/smart-wallet/pull/43): We decided to take action here, changing `removeOwnerAtIndex` to revert if the owner is the last owner and adding `removeLastOwner`.

###
Gas & QA Fixes
- ...

## Out of Scope

We are not taking action https://github.com/code-423n4/2024-03-coinbase-findings/issues/39. 


