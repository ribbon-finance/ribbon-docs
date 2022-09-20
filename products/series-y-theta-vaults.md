# Introduction to Theta Vaults

## What are Theta Vaults?

Theta Vaults run an automated European options selling strategy, which earns yield on a weekly basis through writing out of the money options and collecting the premiums. We use the Vault terminology because it stems from the idea of depositing your assets into a vault and earning a yield on them.

Users can simply deposit and the vaults will automatically start running a specific option strategy. This alleviates a majority of the gas problems by socializing the gas costs across all the vault depositors: instead of doing 3–4 transactions per week per user, the vault will do 3–4 transactions per week for thousands of users at once. This makes the user experience of using these Theta Vaults extremely straightforward and relatively cheap.

Theta Vaults also allow you to choose when to participate or not to participate in the weekly strategy through a [pause and resume](../theta-vault/how-to-pause-and-resume.md) function, so that you do not limit your usage options in relation to your market expectations.

There are two vault types currently active:

1. [Covered call selling](https://www.investopedia.com/terms/c/coveredcall.asp): each week the vault issues [OTM (out of the money)](https://www.investopedia.com/terms/o/outofthemoney.asp) call options on all deposits.
2. [Put selling](https://www.investopedia.com/terms/p/putoption.asp): each week the vault issues OTM put options on all deposits.

## Strike Selection and Expiry <a href="#377c" id="377c"></a>

Strikes are selected by an [algorithm](https://github.com/ribbon-finance/rvol) at the last minute before the corresponding option auction. The pricing parameter is fixed and is 10 [delta](https://www.investopedia.com/terms/d/delta.asp), so there is no direct relationship between the spot price of collateral and the strike; the key element is volatility.

The strike calculation algorithm is based on the [Black\&Scholes model](https://www.investopedia.com/terms/b/blackscholes.asp), with appropriate adjustments. [Historical volatility](https://www.investopedia.com/terms/h/historicalvolatility.asp) is derived from Uniswap while [implied volatility](https://www.investopedia.com/terms/i/iv.asp) is determined by a proprietary closed source algorithm; it uses the 10 delta IV from Deribit for ETH/BTC while for alts there's a custom algorithm to set it. The whole model, although developed for onchain use, is executed offchain both because it is gas intensive and because it is of impractical use due to potential rounding errors and the auctions timeframe.

To further reduce the risk of the options getting exercised, Theta vaults sell _weekly_ call options, meaning we can adjust our expectation of ETH’s price on a weekly basis. This also has the positive side effect of letting us compound our premiums more frequently.

## Options Architecture

Theta Vaults in its present design relies on [Opyn](https://opyn.co/) oTokens. oTokens are ERC20 token representations of an options contract, where each of them have a strike price and expiry. Owning oTokens is functionally equivalent to owning an options contract. This gives the oToken holder the right to redeem some amount of the underlying asset if the strike price is hit.

In order to run an options-writing strategy, the Vault needs to be able to mint and short oTokens. The Vault uses the users’ deposited funds to lock collateral into Opyn + mint oTokens, then sells them for a premium. The Vault’s collateral will be locked until the expiry of the oToken. This collateral is used to pay off oToken holders in the case that the options expire in the money.

Opyn options are [cash settled](https://www.investopedia.com/terms/c/cash-settled-options.asp), so if the options expire ITM, there is no transfer of the underlying: the difference between the strike and the market price at expiry will be compensated by liquidating part of the deposits.

Also, Opyn options self exercise at expiry if ITM. In these docs you'll find more details about [settlement](../theta-vault/options-settlement.md) and [redeeming](../theta-vault/redeeming-otokens.md).

## Auctions

After an initial period of public auctions on Gnosis, we have partnered with [Paradigm](https://www.paradigm.co/) to bring the auctions to their platform and achieve more favorable execution for vault depositors. If you want to participate, take a look at [this section](../theta-vault/how-to-participate-in-paradigm-auctions.md).

Among the main reasons for the change is a structural limitation of Gnosis: it clears at the _lowest_ possible price where demand meets supply. This means that if A is willing to buy half the supply for $10, and B is willing to buy the other half at $9, the entire auction will clear at $9.

Using the Paradigm system, we are able to run [blind auctions](https://en.wikipedia.org/wiki/First-price\_sealed-bid\_auction), in all-or-nothing format. This helps to create more price competition between bidders and reduce gaming of the on-chain auction system, ultimately leading to better pricing.

For an in-depth analysis of the auctions, you can check this [Ribbon Research post](https://www.research.ribbon.finance/blog/ribbon-auction-performance-analysis).

As a fee structure, 4bps of the notional volume done by Ribbon go to Paradigm.

## Risk profile

The primary risk for running the covered call strategy and put selling is that the vault may incur a weekly loss in the case where the call options sold by the vault expire in-the-money (meaning the price of collateral is above -calls- or below -puts- the strike price of the call options minted by the vault).

## Fees

The vault fee structure consists of a 2% annualised management fee and a 10% performance fee.

If the weekly strategy is profitable, the weekly performance fee is charged on the premiums earned and the weekly management fee is charged on the assets managed by the vault. Please notice that the profitability is evaluated regardless of the expiry of the weekly options. In the unlikely event that the options expire ITM but the vault still makes a profit (i.e., if the weekly premium is able to absorb the loss), commissions will still be charged.

If the weekly strategy is unprofitable, there are no fees charged.
