# FAQ

## General&#x20;

### What are structured products?

[Structured products](https://www.investopedia.com/articles/optioninvestor/07/structured\_products.asp) are packaged financial instruments that use a combination of derivatives to achieve some specific risk-return objective, such as betting on volatility, enhancing yields or principal protection.

### What is the risk of the covered-call vault?

The primary risk for running a covered-call strategy is that depositors could potentially give up upside in exchange for guaranteed yield. By selling a call option users are essentially promising to sell the asset at the strike price even if the price rises. This may result in a negative yield on the underlying asset. However, in that case depositors will still be up in USD terms, as the underlying asset would have appreciated significantly in a short period of time.

### What is the risk of the put-selling vault?

The primary risk for running a put-selling strategy is that the vault may incur a weekly loss in the case where the put options sold by the vault expire in-the-money (meaning the price of the underlying asset is below the strike price of the put options minted by the vault).

### What is the options infrastructure used by the vaults?

Ribbon options are built on the Opyn V2 protocol, even on Avax.

### Is Ribbon multichain?

We're currently on Ethereum mainnet, Avalanche, and Solana. There are currently no plans to expand to further chains.

### Does Ribbon have a token?

Yes, Ribbon has a governance token, RBN. Please read the RBN announcement blog [post](https://ribbonfinance.medium.com/decentralizing-ribbon-governance-395950da7a6) for more details. The RBN token is [0x6123B0049F904d730dB3C36a31167D9d4121fA6B](https://etherscan.io/address/0x6123b0049f904d730db3c36a31167d9d4121fa6b).&#x20;

### Where's the Treasury?

[Here's the address](https://etherscan.io/address/0xDAEada3d210D2f45874724BeEa03C7d4BBD41674). The Treasury is managed by a multisig made by the Team with two members of the core community.

### Is Ribbon audited?

We're audited by [OpenZeppelin](https://blog.openzeppelin.com/ribbon-finance-audit/), [ChainSafe](https://github.com/ribbon-finance/audit/blob/master/reports/RibbonThetaVault%20V2%20Smart%20Contract%20Review%20And%20Verification.pdf) and [Peckshield](https://github.com/ribbon-finance/audit/blob/master/reports/PeckShield-Audit-Report-Ribbon-v1.0.pdf). Despite that, users are advised to exercise caution and only risk funds they can afford to lose.

### Do you have a bounty program?

Yes, we offer a bounty for up to $250,000. Learn more [here](https://immunefi.com/bounty/ribbon/).

## DOV Deposits&#x20;

### Where can I find assistance on deposits?

[Right here!](theta-vault/how-to-deposit.md)

### What is the minimum deposit for vaults?

There are no minimum deposits to participate in our vaults.

### Will I receive vault tokens when I deposit?

You will NOT receive vault tokens by default, as you have to manually claim them by calling maxRedeem on Etherscan, and then transfer the tokens to your wallet. Please refer to our guide [here](theta-vault/how-to-transfer-vault-positions.md).&#x20;

### Do I have to confirm and redo my deposits every week?

No, the vaults re-invest your deposits on a rolling basis.

### Are deposits subjected to profit or loss from the previous week

No, if you deposit mid-week, you are not exposed to the vault's performance from the previous week.

### Do you recover deposits accidentally made to an incorrect receiving address?

Although we do not generally offer token recovery services, we review these instances on a case by case basis depending on their significance. We do not guarantee token recovery and advise depositors to double check their transactions.

## DOV Withdrawals&#x20;

### Where can I find assistance on withdrawals?

[Right here!](theta-vault/how-to-withdraw.md)

### Are queued withdrawals subject to profit or loss of the week?

Yes, since you are initiating a withdrawal for vault shares, those shares are subject to either the profits or losses of that week, which will adjust the final withdrawable amount.

### Can I cancel a queued withdrawal?

Unfortunately, you can't cancel a queued withdrawal. You'll have to complete it and reinvest the funds at a later time. [Remember that you can also pause your position](theta-vault/how-to-pause-and-resume.md) instead of withdraw.

### Do planned/queued withdrawals count as two gas transactions?

Yes, this process will count as two gas transactions.

### Can I withdraw stETH from the T-STETH-C vault?

You can ONLY withdraw stETH from the T-STETH-C vault.

## DOV Trading and options

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

Yes, if you'd like to participate in our auctions, please join our Telegram [channel](https://t.me/+vzLH75fnssMxMGI1) - and access our new auctions [website](https://auction.ribbon.finance). For more information please refer to the guide [here](theta-vault/how-to-participate-in-paradigm-auctions.md).&#x20;

### I've bought some options and they are expiring ITM, do I need to do something to exercise?

There is no further action needed on your end as we are using Opyn V2, options self exercise when needed. You just need to claim them at any time.

### How can I redeem my assets if the options expire in the money?

Please refer to the Opyn V2 interface [here](https://gammaportal.xyz/#/account/). Also, here's a [practical guide](theta-vault/redeeming-otokens.md).

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

## Ribbonomics&#x20;

### Can I stake my RBN?

YES but NO, it's not staking, it's locking so be sure to understand the differences taking a look at [this guide](ribbon-dao/how-to-lock-rbn-boost-and-claim-protocol-revenues.md). You can proceed to lock your RBN on the Governance portal: [https://vote.ribbon.finance/](https://vote.ribbon.finance/)

### Where can I see any details on veRBN in circulation, holders, average lock duration?

Here's a Dune dashboard made by our fellow Ribbonato Lewi: [https://dune.com/lewi/VeRBN-Ribbon-Finance](https://dune.com/lewi/VeRBN-Ribbon-Finance)

### Where can I learn more about the Ribbonomics?

Please refer to our documents [here](ribbon-dao/overview-and-rbn-distribution.md).&#x20;

### I've staked the vault tokens, when can I claim my RBN rewards?

Although you can claim whenever you like, please note that you'll accumulate at every block but rewards are restocked weekly. For more information, take a look [here](theta-vault/how-to-stake-unstake-vault-shares-and-claim-rewards.md).

### Do I need to stake the vault tokens every week?

No, you just need to stake them once.

### When staking vault tokens, do I still receive the APY from the vaults or the pool rewards only?

You receive both APY from the vaults and pool rewards.

### Do I have to lock my RBN for 2 years?

No, 2 years is the maximum lock up duration. For more info, take a look [here](ribbon-dao/how-to-lock-rbn-boost-and-claim-protocol-revenues.md).

### Can I lock some of my RBN for different durations?

In order to lock your RBN for various durations you'll have to split them between wallets. Be mindful of your vault position(s), as you will likely lose the boost. Please, check our [guide](ribbon-dao/how-to-lock-rbn-boost-and-claim-protocol-revenues.md).

### How often does my boost records voting power changes?

Your voting weight decreases over time but your boost will take notice of your decreasing voting power at certain checkpoints like withdrawing or staking. For example if you start at 1000 veRBN and your voting power decreases to 800 veRBN, your boost will still use your original voting power of 1000 veRBN until a user checkpoint.

### How can I apply my boost?

After creating or adding to your lock, you need to click the "Apply Boost" button on each gauge you're providing liquidity in to apply the boost. Your boost can also be updated by depositing and withdrawing from a gauge as well as claiming RBN.&#x20;

### If I boost locking RBN but I have more than one vault position, which one takes the boost?

All of your vault positions will get boosted. Please, check our [guide](ribbon-dao/how-to-lock-rbn-boost-and-claim-protocol-revenues.md).

### If I lock RBN for X time and then decide to extend the lock up, will I be able to do so?

Yes, you can extend the lock up period. Please, check our [guide](ribbon-dao/how-to-lock-rbn-boost-and-claim-protocol-revenues.md).

## Help! I am having trouble using the app.

Reach out to us on [Discord](https://discord.gg/85gcVafPyN), we'll help you out.\
