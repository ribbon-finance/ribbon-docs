# Transferring V2 Vault Positions

In V2, due to how the vault functions, you do not gain the vault position tokens by default. However, we expose the functionality of redeeming vault tokens for power users that need to transfer across different accounts.



1\. First, navigate to the [Vault page](https://app.ribbon.finance/v2/theta-vault/T-ETH-C). On the right hand side, you can see the Contract Address. Click on it and go to Etherscan.

![](<../.gitbook/assets/Screenshot 2021-12-29 at 4.25.54 PM.png>)

2\. Now that you are on the contract's Etherscan page, you need to go to Contract > Write as Proxy.

![](<../.gitbook/assets/Screenshot 2021-12-29 at 4.27.06 PM.png>)

3\. Connect your Metamask or web wallet you want to redeem for your account.

4\. Ctrl-F for the `maxRedeem` function. This function redeems your vault tokens from the vault itself. Click "Write" and proceed with the transaction.

![](<../.gitbook/assets/Screenshot 2021-12-29 at 4.27.20 PM.png>)

5\. Once the redeem transaction confirms, you should be able to see the vault ERC20 tokens in your wallet. You can freely transfer this ERC20 token around using your wallet.
