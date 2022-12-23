# How to deposit

In this guide you will find instructions for making a vault deposit. If while following these instructions you encounter any difficulties or errors, we are at your disposal in our [Discord](https://www.google.com/url?q=https://discord.gg/rm7h9ce3ep\&sa=D\&source=editors\&ust=1662912471945831\&usg=AOvVaw00JXnO\_q07bRaXfgkQLl2m) server Support channel.

Before proceeding, make sure you have read and understand the risks involved in investing in the vaults. You can find the relevant information in each vault card on the webapp. If you need more information, the community is ready to help you.

In order for your deposit to be used by the vault starting the following week, be sure to invest before 8 am UTC on Friday. If you deposit after that time, your funds will remain unused until the following Friday.

## Connect your wallet <a href="#connect-your-wallet" id="connect-your-wallet"></a>

After entering the webapp from desktop or mobile, you will need to connect your wallet. Select the appropriate button at the top right (desktop) or bottom (mobile) to proceed.

<figure><img src="../../.gitbook/assets/image1 (8)" alt=""><figcaption></figcaption></figure>

![](<../../.gitbook/assets/image15 (8)>)

A selection menu will open: the first step is to choose the network; the second is to select one of the compatible wallets.

![](<../../.gitbook/assets/image12 (7)>)![](<../../.gitbook/assets/image8 (9)>)

Once your wallet is connected, the app will show in the top right (desktop) or bottom (mobile) corner your address in use. It will also automatically filter only those vaults that are compatible with the network you selected. Under each vault card it will show the total of your previous investments.

<figure><img src="../../.gitbook/assets/image14 (8)" alt=""><figcaption></figcaption></figure>

![](<../../.gitbook/assets/image3 (6)>)

## Invest <a href="#h.ig30e2hrjp4j" id="h.ig30e2hrjp4j"></a>

Select the vault into which you intend to deposit by clicking on its card. In the desktop version, you will immediately have the form to make the deposit, on the right side. In the mobile version you will have to select "INVEST" at the bottom of the screen.

<figure><img src="../../.gitbook/assets/image21 (5)" alt=""><figcaption></figcaption></figure>

![](<../../.gitbook/assets/image11 (6)>)

If this is the first time you are depositing a particular asset on Ribbon, the deposit form will contain a request for permission to use your tokens. You need to make this transaction only at the first deposit for each asset. In case you later revoke the authorization, you will have to approve the use of tokens again at the next deposit.

![](<../../.gitbook/assets/image17 (6)>)

Some vaults accept two assets equally:

* STETH-THETA: you can deposit both ETH and stETH; if you deposit ETH, the vault will convert them to stETH at market values on Curve;
* RETH-THETA: you can deposit both ETH and rETH;
* SAVAX-THETA: you can deposit both Avax and sAvax.

A very important note about these three vaults: the moment you deposit ETH and AVAX, they will be immediately converted to stETH, rETH or sAVAX. Therefore, it will no longer be possible to withdraw ETH and AVAX again but only staked tokens.

<img src="../../.gitbook/assets/image5 (8)" alt="" data-size="original"><img src="../../.gitbook/assets/image18 (6)" alt="" data-size="original"><img src="../../.gitbook/assets/image9 (9)" alt="" data-size="original">

Once you have entered your deposit amount, the interface will show you a preview of the transaction. If the data is correct, all you have to do is confirm by selecting "DEPOSIT NOW" to activate the authorization prompt in your wallet.

![](<../../.gitbook/assets/image13 (7)>)![](https://lh3.googleusercontent.com/cySraakXp7B\_PUYTIVc8zEfSvHog23QEfCNPgoME1iJKXG8NlUtTt-0GhtSpbXdCVb1XNAKbUCgMo52DW8jqSO4Rmncw-2o8g8WAISI7fwhR6etEklW9vjqINtHaqiSWS-zXaIxkD6kfwjDZYEhYLuB2pbwxfG\_ZBLr0Pa1XzfNWwCYkPnvo78gdEQ)![](<../../.gitbook/assets/image7 (9)>)

Once the onchain transaction is confirmed, the app will show you a notification in the top right (desktop) or top center (mobile). A reminder of your total investment will also appear in the bottom left (desktop) or bottom center (mobile).

<figure><img src="../../.gitbook/assets/image19 (8)" alt=""><figcaption></figcaption></figure>

![](<../../.gitbook/assets/image10 (8)>)

Selecting the reminder will open a summary of your vault position, with the option of seeing your deposited or staked funds.

Please remember that staking what you have just deposited is not possible: you will have to wait until the following Friday, when your funds will be actively used by the vault.

![](<../../.gitbook/assets/image2 (9)>)![](<../../.gitbook/assets/image6 (8)>)

Finally, it should be noted that the vault does not automatically issue any receipt tokens. Therefore, if you need to transfer your position to another wallet, you will need to follow the instructions [here](https://app.gitbook.com/o/-MVFqZpOAlPK2YlaTpjh/s/-MVFqgfeL1BL15YGTBdD/\~/changes/2RuXzRZnXGk0Ws6LkUB4/user-guides/transferring-v2-vault-positions).

Your receipt tokens will be automatically claimed in case you are staking your vault shares (only for vaults on ETH mainnet); you can find the instructions [here](how-to-stake-unstake-vault-shares-and-claim-rewards.md).

Your funds are now deposited in the vault: welcome to Ribbon!

## (optional) Check your deposit on Etherscan <a href="#h.ejzcwg4bex7m" id="h.ejzcwg4bex7m"></a>

If you want to check the status of your deposit in a vault, you can proceed via Etherscan/Snowtrace. These steps are not possible for vaults on Solana.

Go to the Etherscan/Snowtrace page of the vault in which you deposited (you will find the links in the vault cards) and select the "contract" tab; then select "read as proxy."

![](<../../.gitbook/assets/image20 (6)>)

Select the function "depositReceipts" and paste your address. The amount the smart contract will show you corresponds to your deposit. Please pay attention to the decimals.

![](https://lh6.googleusercontent.com/TQ8fGkFQ3obzf6WSARSnYdXNWiGMJxBmWiTY1RSDxgKFbiUoV83GzyXEkjWlOvpFqcEYJ9URdql-jbF7MSRZKE1gXZqfvh2hUjpd9zr0iv8SJSl3bHAjjJB36bHFxZz-FdmEe8x4\_QU2uvrrQjhCjBJLbUN4KaHU8IJEZsWz2Tg0eKdlovzfXLmnFA)

Keep in mind that vaults for USDC have a different number of decimal places: in the example below you can see a deposit of 150 USDC.

![](<../../.gitbook/assets/image16 (7)>)
