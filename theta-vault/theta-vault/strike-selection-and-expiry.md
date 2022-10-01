# Strike Selection and Expiry

Strikes are selected by an [algorithm](https://github.com/ribbon-finance/rvol) at the last minute before the corresponding option auction. The pricing parameter is fixed and is 10 [delta](https://www.investopedia.com/terms/d/delta.asp), so there is no direct relationship between the spot price of collateral and the strike; the key element is volatility.

The strike calculation algorithm is based on the [Black\&Scholes model](https://www.investopedia.com/terms/b/blackscholes.asp), with appropriate adjustments. [Historical volatility](https://www.investopedia.com/terms/h/historicalvolatility.asp) is derived from Uniswap while [implied volatility](https://www.investopedia.com/terms/i/iv.asp) is determined by a proprietary closed source algorithm; it uses the 10 delta IV from Deribit for ETH/BTC while for alts there's a custom algorithm to set it. The whole model, although developed for onchain use, is executed offchain both because it is gas intensive and because it is of impractical use due to potential rounding errors and the auctions timeframe.

To further reduce the risk of the options getting exercised, Theta vaults sell _weekly_ call options, meaning we can adjust our expectation of ETH’s price on a weekly basis. This also has the positive side effect of letting us compound our premiums more frequently.

##
