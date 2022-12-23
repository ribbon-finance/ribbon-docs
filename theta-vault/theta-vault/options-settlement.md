# Options Settlement

## Settlement price

Currently, we are relying on Opyn's infrastructure for option settlement. Opyn uses Chainlink's spot prices as a data source to settle options.

After a few improvements and learnings, we have decided to use [Pyth's](https://pyth.network/) oracle for settlement price when options expire in-the-money. The reasons as follows:

* Chainlink's data source is not designed to be used for expiries because it uses data sources such as aggregators (CoinGecko or CoinMarketCap) which are often delayed.
* Pyth provides a more accurate view of the price data due to how it fetches real-time price data from exchanges.

## wstETH and rETH options

Ribbon's vaults writes options that are collateralized with liquid staking derivative tokens such as wstETH (Wrapped Staked ETH) and rETH (Rocket Pool ETH).

There are some core differences for how settlement price is calculated for these options. How the settlement price is calculated is as below:

1. We figure out how much stETH each wstETH can be unwrapped for.
2. We treat 1 stETH as 1 ETH from a price perspective.
3. We set the expiry price to the price of ETH.

#### Example

We have an ETH $2000 call option. For this example, we will be collateralizing the call option with wstETH and we assume that 1 wstETH = 1 stETH. If ETH ends up in-the-money at $2500, an option holder would be able to claim $500 worth of ETH for a normal ETH call option, or 0.2 ETH.

In the case of wstETH, 0.2 wstETH can be claimed at expiry. However, 0.2 wstETH can only be traded for 0.19 ETH on liquidity pools like Curve, which means the option holder would have 5% less profits if they swapped back to ETH after claiming.

The implications for this are:

* wstETH options have the same payoff calculation as a regular ETH option, except the collateral received is wstETH, which is unwrapped for stETH.
* This means if stETH is trading 5% below the value of ETH, the amount returned from exercising the option is 5% less.

