# Introduction to Ribbon Finance

[Ribbon Finance](https://app.ribbon.finance/) is a suite of DeFi protocols that help users access crypto structured products. By combining derivatives, lending and a proprietary [on-chain options exchange (Aevo)](aevo.md), Ribbon aims to be the one-stop solution for users who want to improve a portfolio's risk-return profile.

Here you can find the products descriptions and [outgoing links](broken-reference) to the different communication channels, where you can reach out to the Team and Community.

## Theta Vaults (DOVs)

Theta Vaults, also known as DOVs (DeFi Options Vaults), were invented by Ribbon in 2021. At its core, a Theta vault is a yield-oriented strategy that proposes that depositors trade volatility on their underlying by selling [European options](https://www.investopedia.com/terms/e/europeanoption.asp) with weekly expiration. The sale value of these options, or "premium," is set through [auctions](theta-vault/theta-vault/#auctions) and determines the vault return. The vault reinvests the premiums earned back into the strategy, effectively compounding them for depositors over time.

There are two types currently active:

1. [Covered call selling](https://www.investopedia.com/terms/c/coveredcall.asp): each week the vault issues [OTM (out of the money)](https://www.investopedia.com/terms/o/outofthemoney.asp) call options on all deposits.
2. [Put selling](https://www.investopedia.com/terms/p/putoption.asp): each week the vault issues OTM put options on all deposits.

For more information you can check [this section](theta-vault/theta-vault/).

## Ribbon Earn

The [R-Earn vaults](ribbon-earn/introduction-to-ribbon-earn.md) employ fully funded strategies to capitalize on the intra-week ETH movements, while also ensuring their capital is protected. The vaults earns a base APY and uses the remaining funding to purchase weekly options.

There are currently two vaults available:

1. Earn USDC: it employs a twin win strategy through which depositors can capitalise on the intra-week ETH movements in either direction;
2. Earn stETH: employs dolphin strategy through which depositors can capitalise on the upside ETH movements.

For more information you can check [this section](ribbon-earn/introduction-to-ribbon-earn.md).

## Ribbon Treasury

Ribbon Treasury are private Ribbon Theta vaults built specifically for DAOs to run covered calls on their native tokens. These private vaults are segregated from the main Ribbon vaults, and run a custom strategy for each DAO. Each vault has a few unique parameters:

* **Strike Selection Methodology**\
  DAOs can choose how aggressive they want to be with regards to the strike selection methodology.&#x20;
* **Tenor**\
  DAOs can choose how often they want to run the strategy. The current Ribbon Vaults run a weekly strategy that automatically re-rolls, but DAOs can choose longer tenors.
* **Premium Currency**\
  DAOs can also choose what currency they want to receive the premiums in. For example, a DAO could elect to receive premiums in USDC or ETH, depending on their treasury diversification goals.

For more information you can check [this section](broken-reference).

## Ribbon Lend

#### \*\*\*Ribbon Lend is currently paused until further notice\*\*\*

Ribbon Lend can be described as an uncollateralized Aave, allowing depositors to lend unsecured to KYC/AML’d institutional market makers of their choosing with high liquidity. Ribbon Lend offers the best of both worlds between TradFi and DeFi:

* High yields from unsecured lending
* No lockups from Aave’s money market model
* Off-chain enforcement / credit underwriting
* Built-in insurance

For more information you can check [this section](ribbon-lend/introduction-to-ribbon-lend/).
