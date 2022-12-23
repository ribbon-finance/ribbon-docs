# DOV Trading and options

### What is the fee structure?

The vault fee structure consists of a 2% annualized management fee and a 10% performance fee. If the weekly strategy is profitable, the weekly performance fee is charged on the premiums earned and the weekly management fee is charged on the assets managed by the vault. If the weekly strategy is unprofitable, there are no fees charged.

### How is APY calculated?

We calculate APY by getting the average of the past 4 week's annualized performance:

Weekly Yield = ((1+(Curr. Week’s Performance)^52)-1)\*100&#x20;

Projected Yield (APY) = Average of Past 4 Week's Weekly Yield (in the money weeks are excluded)

### Are the management and performance fees included in the expected APY?

Yes.&#x20;

### Where can I see the historical performance?

Every product has a card with the vault's graphical representation of historical performance. You may refer [here](https://www.tokenterminal.com/terminal/projects/ribbon-finance) for further insights.

### Are the management and performance fees included in the previous week's performance?

Yes.

### What asset are the vault yields paid in?

Yields are paid in the same underlying deposit asset. The only exception are the staked tokens vaults: stETH, rETH and sAvax. You can deposit either vanilla ETH/Avax or the staked versions but you'll be able to withdraw stETH, rETH and sAvax only.

### Are the vaults cash or physically settled?

Our vaults are [cash settled](https://www.investopedia.com/terms/c/cash-settled-options.asp), which means you do not need physically deliver an asset on expiry. Call options are cash-settled with the collateral asset, whereas put options are cash-settled with USDC.

### Do vaults use a delta neutral strategy?

No.

### How is the strike calculated?

Our V2 vaults use an algorithmic strike selection with a delta of 0.1 for writing options, see our blog post [here](https://ribbonfinance.medium.com/algorithmic-strike-selection-e07ae917c146) and the underlying Black-Scholes model [here](https://github.com/ribbon-finance/rvol/blob/master/contracts/core/OptionsPremiumPricerInStables.sol#L163). The process is currently managed offchain, because it would be very gas intensive and impractical.

### How can I find out the next strike in advance?

There is no way to know the strike in advance as it's calculated using last minute data feeds. For now, you can make an educated guess looking at 10d on Deribit.

### How is the IV calculated/sourced?

The model for IV isn't open but based on IV at 10d and adjusted with historical volatility. We use the 10d IV from Deribit for ETH/BTC and roll our own algo for alts.

### Where can I learn more about the strategies?

Please refer to the vault cards on our website as they have a step-by-step guide to the strategy currently used.

### Can I buy the options written by the vaults?

Yes, if you'd like to participate in our auctions, please join our Telegram [channel](https://t.me/+vzLH75fnssMxMGI1) - and access our new auctions [website](https://auction.ribbon.finance). For more information please refer to the guide [here](../theta-vault/user-guides/how-to-participate-in-paradigm-auctions.md).&#x20;

### I've bought some options and they are expiring ITM, do I need to do something to exercise?

There is no further action needed on your end as we are using Opyn V2, options self exercise when needed. You just need to claim them at any time.

### How can I redeem my assets if the options expire in the money?

Please refer to the Opyn V2 interface [here](https://gammaportal.xyz/#/account/). Also, here's a [practical guide](../theta-vault/user-guides/how-to-redeem-otokens.md).

### **Is there a deadline for exercising oTokens?**

The profits from exercising the options are locked in on expiry. There is no deadline for exercising oTokens.

### **The options expired in-the-money. Why can't I claim the collateral?**

After the options expire at 8am UTC, there is about 1 hour dispute period for settlement. You can only claim the collateral with oTokens after 9/10 am UTC.

### I've called the max redeem but I didn't get any token. Why?

If you called max redeem the same week you deposited, you wouldn't receive any tokens as your funds weren't used by the vaults.

### Are vault tokens are 1:1 with the underlying?

No, rETH-THETA is constantly changing as premiums are collected each week. So rETH-THETA is not 1:1 to ETH.

### I just deposited in a vault, why can't I stake any rTokens?

You'll have to wait until the next Friday to stake your rTokens because your funds aren't actively used right now.
