# How to transfer vault positions

When you enter the strategy (_so the week after your deposit_), you do not gain the vault position tokens by default. However, we expose the functionality of redeeming vault tokens for power users that need to transfer across different accounts.&#x20;

Remember: if you stake your vault shares, [you'll automatically get the rTokens](how-to-stake-unstake-vault-shares-and-claim-rewards.md#h.stqn8ca118g).

Please notice that these steps aren't available for Solana.

First, navigate to the [Vault page](https://app.ribbon.finance/). On the right hand side, you can see the Contract Address. Click on it and go to Etherscan.

![](<../../.gitbook/assets/Screenshot 2021-12-29 at 4.25.54 PM.png>)

Now that you are on the contract's Etherscan/Snowscan page, you need to go to Contract > Write as Proxy.

![](<../../.gitbook/assets/Screenshot 2021-12-29 at 4.27.06 PM.png>)

Connect your Metamask or web wallet you want to redeem for your account.

Ctrl-F for the `maxRedeem` function. This function redeems your vault tokens from the vault itself. Click "Write" and proceed with the transaction.

![](<../../.gitbook/assets/Screenshot 2021-12-29 at 4.27.20 PM.png>)

Once the redeem transaction confirms, you should be able to see the vault ERC20 tokens in your wallet. You can freely transfer this ERC20 token around using your wallet.
