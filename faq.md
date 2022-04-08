# FAQ

## General&#x20;

### What are structured products?

Structured products are packaged financial instruments that use a combination of derivatives to achieve some specific risk-return objective, such as betting on volatility, enhancing yields or principal protection.

### What kind of structured products does Ribbon have?

We currently offer structured products on ETH, AVAX, USDC, and SOL which generates high yield through automated covered-call or put-selling option strategies. For more information on the strategies used, please consult the product cards for a breakdown.

### What is the risk of the covered-call vault?

The primary risk for running a covered-call strategy is that depositors could potentially give up upside in exchange for guaranteed yield. By selling a call option users are essentially promising to sell the asset at the strike price even if the price rises. This may result in a negative yield on the underlying asset. Please note that although a negative yield is uncommon, depositors will still be up in USD terms as the underlying asset would have appreciated significantly in a short period of time.

### What is the risk of the put-selling vault?

The primary risk for running a put-selling strategy is that the vault may incur a weekly loss in the case where the put options sold by the vault expire in-the-money (meaning the price of the underlying asset is below the strike price of the put options minted by the vault).

### What is the options infrastructure used by the vaults?

Ribbon options are built on the Opyn V2 protocol.

### Is Ribbon multichain?

We're currently on Ethereum mainnet, Avalanche, and Solana.

### Does Ribbon have a token?

Yes, Ribbon has a governance token, RBN. Please read the RBN announcement blog [post](https://ribbonfinance.medium.com/decentralizing-ribbon-governance-395950da7a6) for more details. The RBN token is [0x6123B0049F904d730dB3C36a31167D9d4121fA6B](https://etherscan.io/address/0x6123b0049f904d730db3c36a31167d9d4121fa6b).&#x20;

### Are the vaults audited?

We're audited by [OpenZeppelin](https://blog.openzeppelin.com/ribbon-finance-audit/), [ChainSafe](https://github.com/ribbon-finance/audit/blob/master/reports/RibbonThetaVault%20V2%20Smart%20Contract%20Review%20And%20Verification.pdf) and [Peckshield](https://github.com/ribbon-finance/audit/blob/master/reports/PeckShield-Audit-Report-Ribbon-v1.0.pdf). Despite that, users are advised to exercise caution and only risk funds they can afford to lose.

### Do you have a bounty program?

Yes, we offer a bounty for up to $250,000. Learn more [here](https://immunefi.com/bounty/ribbon/).

## Deposits&#x20;

### Where are the deposits?

Deposits go into each vault smart contract, depending on which product you are using. On each product page, there is a link to the smart contract address for that vault.

### What is the minimum deposit for vaults?

There are no minimum deposit to participate in our vaults.

### Will I receive vault tokens when I deposit?

You will not receive vault tokens by default as you have to manually claim them by calling maxRedeem on Etherscan, and then transfer the tokens to your wallet. Please refer to our guide [here](https://docs.ribbon.finance/user-guide/transferring-v2-vault-positions).&#x20;

### Do I have to confirm and redo my deposits every week?

No, the vaults re-invest your deposits on a rolling basis.

### Are deposits subjected to profit or loss from the previous week

No, if you deposit mid-week, you are not exposed to the vault's performance from the previous week.

### Do you recover deposits accidentally made to an incorrect receiving address?

Although we do not generally offer token recovery services, we review these instances on a case by case basis depending on their significance. We do not guarantee token recovery and advise depositors to double check their transactions.

## Withdrawals&#x20;

### How do I process a withdrawal?

We offer two types of withdrawals:

1. Instant: only applicable to funds that are deposited mid-week and have yet to be actively used in the vault. You can withdraw until Friday 10am UTC
2. Queued: a two-step withdrawal process. At any point in time you can submit a withdrawal (or many) to the queue and then finalise your it after Friday 10am UTC

### Are queued withdrawals subjected to profit or loss of the week?

Yes, since you are initiating a withdrawal for vault shares, those shares are subject to either the profits or losses of that week which will adjust the final withdrawable amount.

### Can I cancel a queued withdrawal?

Unfortunately, you can't cancel a withdrawal as you'll have to complete it and reinvest the funds at a later time.

### Do planned/queued withdrawals count as two gas transactions?

Yes, this process with count as two gas transactions.

### Can I withdraw stETH from the T-STETH-C vault?

Yes.

### Can I withdraw yvUSDC from the T-YVUSDC-P-ETH vault?

No, you will get back USDC.

## Trading

### What is the fee structure?

The vault fee structure consists of a 2% annualised management fee and a 10% performance fee. If the weekly strategy is profitable, the weekly performance fee is charged on the premiums earned and the weekly management fee is charged on the assets managed by the vault. If the weekly strategy is unprofitable, there are no fees charged.

### How is APY calculated?

We calculate APY by annulizing (52 weeks) this weeks performance. Please refer [here](https://www.notion.so/ribbonfinance/How-is-APY-calculated-fb514d774da64ba09b4847e88bfcae81) for a breakdown.&#x20;

### Are the management and performance fees included in the expected APY?

Yes.&#x20;

### Where can I see the historical performance?

Every product has a card with the vault's graphical representation of historical performance. You may refer [here](https://www.tokenterminal.com/terminal/projects/ribbon-finance) for further insights.

### Are the management and performance fees included in the previous week's performance?

Yes.

### What asset are the vault yields paid in?

Yields are paid in the same underlying deposit asset. The only exception is stETH vault - you can deposit either ETH or stETH and withdraw stETH.

### Are the vaults cash or physically settled?

Our vaults are cash settled.

### Do vaults use a delta neutral strategy?

No.

### How is the strike calculated?

Our V2 vaults use an algorithmic strike selection with a delta of 0.1 for writing options, see our blog post [here](https://ribbonfinance.medium.com/algorithmic-strike-selection-e07ae917c146) and the underlying model is Black-Scholes [here](https://github.com/ribbon-finance/rvol/blob/master/contracts/core/OptionsPremiumPricerInStables.sol#L163).&#x20;

### How can I find out the next strike in advance?

There is no way to know the strike in advance as it's calculated using last minute data feeds.

### How is the IV calculated/sourced?

The model for IV isn't open but based on IV at 10d and adjusted with historical volatility. We use the 10d IV from Deribit for ETH/BTC and roll our own algo for alts.

### Where can I learn more about the strategies?

Please refer to the vault cards on our website as they have a step-by-step guide to the strategy currently used.

### Can I buy the options written by the vaults?

Yes, if you'd like to participate in our auctions, please join our Telegram [channel](https://t.me/+vzLH75fnssMxMGI1) - and access our new auctions [website](https://auction.ribbon.finance). For more information please refer to the guide [here](https://docs.ribbon.finance/products/participating-in-open-auctions).&#x20;

### I've bought some options and they are expiring ITM, do I need to do something to exercise?

There is no further action needed on your end as we are using Opyn V2, options self exercise when needed. You just need to claim them at any time.

### How can I redeem my assets if the options expire in the money?

Please refer to the Opyn V2 interface [here](http://gammaportal.xyz).&#x20;

### I've called the max redeem but I didn't get any token. Why?

If you called max redeem the same week you deposited, you wouldn't receive any tokens as your funds weren't used by the vaults.

### Are vault tokens are 1:1 with the underlying?

No, rETH-THETA is constantly changing as premiums are collected each week. So rETH-THETA is not 1:1 to ETH.

### I just deposited in a vault, why can't I stake any rTokens?

You'll have to wait until the next Friday to stake your rTokens because your funds aren't actively used right now.

### I have an old V1 position, what can I do?

The old V1 vaults are inactive. You can either migrate to V2 or withdraw your funds paying only the gas required. Please see the pinned walkthrough in our Discord support [channel](https://discord.com/channels/808777716396195851/808784857261146142).&#x20;

## Ribbonomics&#x20;

### Where can I learn more about the Ribbonomics?

Please refer to our documents [here](https://docs.ribbon.finance/ribbon-dao/overview).&#x20;

### I've staked the vault tokens, when can I claim my RBN rewards?

Although you can claim whenever you like, please note that you'll accumulate at every block but rewards are restocked weekly.

### Do I need to stake the vault tokens every week?

No, you just need to stake them once.

### When staking vault tokens, do I still receive the APY from the vaults or the pool rewards only?

You receive both APY from the vaults and pool rewards.

### Do I have to lock my RBN for 2 years?

No, 2 years is the maximum lock up duration.

### Can I lock some of my RBN for different durations?

In order to lock  your RBN for various durations you'll have to split them between wallets. Be mindful of your vault position(s), as you will likely lose the boost.

### If I boost locking RBN but I have more than one vault position, which one takes the boost?

All of your vault positions will get boosted.

### If I lock RBN for X time and then decide to extend the lock up, will I be able to do so?

Yes, you can extend the lock up period - by clicking on "Lock RBN" you'll be prompted a modal that allows you to extend the duration / lock up more RBN.

## Help! I am having trouble using the app.

Reach out to us on [Discord](https://discord.gg/85gcVafPyN), we'll help you out.\
