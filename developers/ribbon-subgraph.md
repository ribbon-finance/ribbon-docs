# Ribbon Subgraph

Ribbon's subgraph is hosted on [The Graph](https://thegraph.com/explorer/subgraph/kenchangh/ribbon-finance). If you need any additional data, feel free to raise an issue at the [ribbon-subgraph repo](https://github.com/ribbon-finance/ribbon-subgraph), or contribute a change.

## Querying Instrument Positions

This query returns the first 5 instrument positions and their details.

```text
{
  instrumentPositions(first: 5) {
    id
    instrumentAddress
    account
    cost
    amount
  }
}
```

## Querying  Vaults

This query returns the first 5 vaults and vital statistics about the vault.

```text
{
  vaults(first: 5) {
    id
    name
    symbol
    numDepositors
    totalPremiumEarned
    totalWithdrawalFee
  }
}
```

