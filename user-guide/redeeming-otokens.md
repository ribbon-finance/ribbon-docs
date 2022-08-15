# Redeeming oTokens

**This is only relevant to oToken holders, which are buyers on the option auctions. Please take a look at the** [**Gnosis auction**](https://docs.ribbon.finance/products/participating-in-open-auctions) **and** [**Paradigm auction**](https://docs.ribbon.finance/products/participating-in-paradigm-auctions) **guides on how to participate.**

## oToken Redemption FAQ

**Q: Is there a deadline for exercising oTokens?**

A: The profits from exercising the options are locked in on expiry. There is no deadline for exercising oTokens.



**Q: Are oTokens cash-settled?**

A: The oTokens are cash-settled, which means you do not need physically deliver an asset on expiry. Call options are cash-settled with the collateral asset, whereas put options are cash-settled with USDC.



**Q: The options expired in-the-money. Why can't I claim the collateral?**

A: After the options expire at 8am UTC, there is a 1 hour dispute period for settlement. You can only claim the collateral with oTokens after 9am UTC.

## How to redeem oTokens

The process of redeeming collateral with oToken is not automatic and requires the holder to spend gas to claim the profits.

We can use the webapp developed by the Opyn team to access oTokens - [Gamma Portal](https://gammaportal.xyz/#/account).

First, connect your wallet to the website. This portal site allows oToken holders to see a list of options a Metamask wallet holds:

![Gamma Portal shows an account's oToken balance.](<../.gitbook/assets/image (6).png>)

To make sure you are viewing the correct account page, check that the URL matches what the account connected to the page on the top left. E.g. `https://gammaportal.xyz/#/account/ADDRESS`

![](<../.gitbook/assets/Screenshot 2022-07-19 at 7.14.40 PM.png>)

If the oTokens you hold are out-the-money, you are not able to redeem collateral from Opyn. The portal will show the "Payout" as 0.0 WETH and the Redeem button will be grayed out. The Redeem button could also be grayed out if the dispute period has not passed.

![](<../.gitbook/assets/image (7).png>)

If the oTokens are in-the-money and the dispute period has passed, the Portal will display a positive payout, and the Redeem button will be enabled.

![Redeem button is enabled and payout displayed in the Gamma Portal.](<../.gitbook/assets/image (4).png>)

Upon clicking the "Redeem" button, your wallet will be prompted to perform a transaction. Confirm the transaction.

![Example of a Metamask transaction](<../.gitbook/assets/image (3).png>)

![The redemption transaction burns oTokens and returns collateral from the vault.](../.gitbook/assets/Screenshot\_2021-03-07\_at\_7.16.11\_PM.png)
