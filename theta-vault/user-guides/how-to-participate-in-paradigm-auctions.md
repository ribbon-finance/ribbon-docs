# How to participate in Paradigm Auctions

## Requirements

* `Wallet`. We support Metamask, Wallet Connect and Coinbase Wallet.

### **Please note that you will also need to be registered in Paradigm's platform and there are setups required on Paradigm's platform before you can start bidding on the auctions.**

## Token Approval

To participate in Paradigm auctions, bidders need to approve their tokens beforehand. Follow the instructions below to approve your tokens. The instruction below is an example if you use Metamask wallet.

1\. Head over to [https://auction.ribbon.finance/approval](https://auction.ribbon.finance/approval). You will see the following page. Click on `CONNECT WALLET`.&#x20;

![Token Approval Page](<../../.gitbook/assets/Screenshot 2022-05-10 at 2.33.40 PM.png>)

2\. The following window will pop up. In this instruction, we will use Metamask.

![](<../../.gitbook/assets/Screenshot 2022-05-10 at 2.37.48 PM.png>)

3\. When you click Metamask, the following window will open. Click `Next` and then `Connect`. Note that the steps might be different if you are using another wallet.

![Metamask Step 1](<../../.gitbook/assets/Screenshot 2022-05-10 at 2.39.03 PM.png>)

![Metamask Step 2](<../../.gitbook/assets/Screenshot 2022-05-10 at 2.40.47 PM (1).png>)

4\. Ensure that you are in the correct network, either Ethereum or Avalanche C-Chain Mainnet. Note that the steps might be different if you are using another wallet.

![Ensure Correct Network](<../../.gitbook/assets/Screenshot 2022-05-10 at 2.43.54 PM.png>)

5\. Once you are connected, you will be able to see the auction options. Choose `PARADIGM`.

![Auction Selection](<../../.gitbook/assets/Screenshot 2022-05-10 at 2.46.22 PM (2).png>)

6\. Once you select the auction, you will be able to see the list of tokens you can approve. We'll choose WBTC this time round.

![Token Selection](<../../.gitbook/assets/Screenshot 2022-05-10 at 2.48.58 PM.png>)

7\. Afterwards, click on the button `APPROVE`. This will trigger a pop-up in Metamask. You need to approve the transaction. Similarly, if you are not using Metamask, you will need to approve the transaction in your respective wallet. **Ensure you are approving the right contract.**&#x20;

Our swap contract (the contract used for bid settlement) addresses:

* **Ethereum Mainnet: 0xEb8CAB2F4663247db8eAfb556F498c861bB4e161**
* **Avalanche Mainnet: 0x15988ceA1F11D62e63bAa02B0e8B3046942983c0**

![Approve Pop-Up](<../../.gitbook/assets/Screenshot 2022-07-11 at 1.29.57 PM.png>)

8\. After the transaction is confirmed, you can see that the token has been labelled as approved. You can now head over to Paradigm's platform to register your wallet.

![Approved Label](<../../.gitbook/assets/Screenshot 2022-05-10 at 2.59.29 PM.png>)

## Multi-Sig Wallet

For multi-sig wallets, you need to assign a delegate to sign on your behalf to participate in Paradigm auctions. This is because Gnosis multi-sig does not support message signing.

Follow the steps below to sign assign a delegate:

1\. Head over to [https://auction.ribbon.finance/approval](https://auction.ribbon.finance/approval). You will see the following page. Click on `CONNECT WALLET`. **Connect with your multi-sig wallet, NOT your delegate wallet.**

![Token Approval Page](<../../.gitbook/assets/Screenshot 2022-05-10 at 2.33.40 PM.png>)

2\. Ensure that you are in the correct network, either Ethereum or Avalanche C-Chain Mainnet. Note that the steps might be different if you are using another wallet.

![Ensure Correct Network](<../../.gitbook/assets/Screenshot 2022-05-10 at 2.43.54 PM.png>)

3\. Once you are connected, you will be able to see the auction options. Choose `PARADIGM`.

![Auction Selection](<../../.gitbook/assets/Screenshot 2022-05-10 at 2.46.22 PM (2).png>)

4\. Enter the delegate address. This is the address that will sign bids on behalf of your multi-sig.

![Enter Delegate's Address](<../../.gitbook/assets/Screenshot 2022-07-11 at 1.38.21 PM.png>)

5\. Click `AUTHORIZE` and approve the transaction in your wallet. Now you will be able to use the delegate's wallet to bid on behalf of your multi-sig.&#x20;

**Note that your delegate's wallet does not need to approve the tokens for bidding, only the multi-sig needs to approve the tokens.**
