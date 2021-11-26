---
id: unjail
sidebar_position: 4
sidebar_label: Unjail
slug: /validator-zone/troubleshoot/unjail
---
# How to unjail your validator

"Jail" is a Tendermint/Cosmos concept---it is not specific to Axelar.  If your validator misses 50 or more of the last 100 blocks then your tendermint status becomes `jailed`.  You can see your 'jailed' status via the Cosmos command `axelard q staking validators`.

:::tip
Axelar-core currently uses the word "jail" to describe a different Axelar-specific status in the context of eligibility to participate in keygen/sign protocols.  This terminology can be confusing and we intend to change it in future versions of axelar-core.  To see whether your validator's has this Axelar-specific jail status use `axelard q snapshot validators`.
:::

The minimum duration for `jail` status is 10 minutes.  After this period you can restore your validator to healthy status by posting a transaction to the Axelar blockchain as follows.

## Docker

In the `axelar-core` container:
```
axelard tx slashing unjail --from validator
```

## Binaries

```
~/.axelar_testnet/bin/axelard tx slashing unjail --from validator --home ~/.axelar_testnet/.core --chain-id axelar-testnet-barcelona
```