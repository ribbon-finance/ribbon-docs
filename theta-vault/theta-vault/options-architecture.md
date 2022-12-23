# Options Architecture

Theta Vaults in its present design relies on [Opyn](https://opyn.co/) oTokens. oTokens are ERC20 token representations of an options contract, where each of them have a strike price and expiry. Owning oTokens is functionally equivalent to owning an options contract. This gives the oToken holder the right to redeem some amount of the underlying asset if the strike price is hit.

In order to run an options-writing strategy, the Vault needs to be able to mint and short oTokens. The Vault uses the users’ deposited funds to lock collateral into Opyn + mint oTokens, then sells them for a premium. The Vault’s collateral will be locked until the expiry of the oToken. This collateral is used to pay off oToken holders in the case that the options expire in the money.

Opyn options are [cash settled](https://www.investopedia.com/terms/c/cash-settled-options.asp), so if the options expire ITM, there is no transfer of the underlying: the difference between the strike and the market price at expiry will be compensated by liquidating part of the deposits.

Also, Opyn options self exercise at expiry if ITM. In these docs you'll find more details about [settlement](options-settlement.md) and [redeeming](../user-guides/how-to-redeem-otokens.md).
