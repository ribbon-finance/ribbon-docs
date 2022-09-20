# Introduction to Ribbon Treasury

## **What is Ribbon Treasury?**

Ribbon Treasury are private Ribbon [Theta vaults](../products/series-y-theta-vaults.md) built specifically for DAOs to run covered calls on their native tokens. These private vaults are segregated from the main Ribbon vaults, and run a custom strategy for each DAO. Each vault has a few unique parameters:

* **Strike Selection Methodology**\
  DAOs can choose how aggressive they want to be with regards to the strike selection methodology.&#x20;
* **Tenor**\
  DAOs can choose how often they want to run the strategy. The current Ribbon Vaults run a weekly strategy that automatically re-rolls, but DAOs can choose longer tenors.
* **Premium Currency**\
  DAOs can also choose what currency they want to receive the premiums in. For example, a DAO could elect to receive premiums in USDC or ETH, depending on their treasury diversification goals.

## Why Ribbon Treasury?

As noted in Hasu’s [“A New Mental Model for Defi Treasuries”](https://uncommoncore.co/a-new-mental-model-for-defi-treasuries/), many DAO treasuries consist primarily of their own native token, which should not/cannot be considered as a real treasury. Ribbon Treasury allows DAOs to generate income on their native tokens and build a healthy diversified portfolio of assets.

We think this makes it a perfect product for DAO treasuries for multiple reasons:

1. DAOs who are sitting on hundreds of millions of dollars of their own native token often have **no way to generate yield on them**. Covered calls unlocks significantly higher income generation on those assets;
2. Instead of selling tokens on the open market to **diversify the treasury**, DAOs could sell covered calls on their native asset and collect the premiums in stables;
3. DAOs are **well suited to sell upside volatility in their own native token** in exchange for cash today. In the case that the token is flat or down, the DAO would have collected premiums for free. In the case that the token goes up significantly, the DAO would have given up some of that upside — which is totally reasonable risk-reward for a DAO that already owns significant amounts of the native token.

## **Partners**

#### [Perpetual Protocol](https://mobile.twitter.com/perpprotocol/status/1492105547490988051) (launch partner, take a look here for a [case study](https://www.research.ribbon.finance/blog/perp-vault-case-study-on-treasury-management))

#### [Balancer Labs](https://twitter.com/ribbonfinance/status/1547077500215341056)

#### [Abracadabra](https://mobile.twitter.com/MIM\_Spell/status/1557774128891011073)

#### [Badger DAO](https://twitter.com/ribbonfinance/status/1562363921087967233)

## How to get involved

If your DAO is interested, please fill this [very short form](https://forms.gle/SkfCJaBbXi5R4zs96) use our [comms channels](../#communication-channels) to get in touch.\
There are no special requirements to start the conversation; however, these two conditions should be met:

* There should be perps for the token on a CEX, so that market makers can hedge easily;
* DAO should be willing to deploy between $1-$5 million of their native token into Ribbon Treasury.
