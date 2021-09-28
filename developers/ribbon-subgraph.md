# Ribbon Subgraph

Ribbon's subgraph is hosted on [The Graph](https://thegraph.com/explorer/subgraph?id=0x97230febf3e6595462d93600404a77223d5dc723-2&version=0x97230febf3e6595462d93600404a77223d5dc723-2-0). If you need any additional data, feel free to raise an issue at the [ribbon-subgraph repo](https://github.com/ribbon-finance/ribbon-subgraph), or contribute a change.

We have two subgraphs hosted on the legacy Graph explorer:

1. [Ribbon v2 Subgraph](https://thegraph.com/legacy-explorer/subgraph/ribbon-finance/ribbon-v2)
2. [Ribbon v1 Subgraph](https://thegraph.com/explorer/subgraph/kenchangh/ribbon-finance)

## Querying  Vaults

This query returns the first 5 vaults and vital statistics about the vault.

```text
{
  vaults(first: 5) {
    id
    totalPremiumEarned
    underlyingAsset
    underlyingSymbol
  }
}
```

## Querying  Vault APY

This query returns a chronological list of `pricePerShare` values for the vault. `pricePerShare` represents how much a vault share is worth in the collateral asset. For example, for the ETH Theta Vault, if the value of `pricePerShare` is more than 1\*10\*\*18, the vault is profitable.

```text
{
  vaultPerformanceUpdates(
    where:{vault:"0x25751853eab4d0eb3652b5eb6ecb102a2789644b"},
    orderBy:timestamp, orderDirection:asc) {
    id
    pricePerShare
    timestamp
  }
}
```

## Querying  Vault Fees

This query returns fee information for the vaults.

```text
{
  vaults(first: 5) {
    id
    totalFeeCollected
    managementFeeCollected
    performanceFeeCollected
    underlyingAsset
    underlyingSymbol
  }
}
```

