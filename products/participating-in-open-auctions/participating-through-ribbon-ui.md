# Participating Through Ribbon UI

## Requirements:

1. `Wallet`. We support Metamask, Wallet Connect and Coinbase Wallet.
2. `Collateral`. When placing a bid, you need to have sufficient ERC20 tokens in your wallet.

## Step 1: Bidding

#### 1. Live auction will be featured at the top in the Ribbon Auction UI

![Live Auction](<../../.gitbook/assets/image (4).png>)

#### 2. If you are already at a specific auction’s page, you can also see its live status

![Auction Page Live](<../../.gitbook/assets/Screenshot 2022-02-17 at 2.53.17 PM.png>)

#### 3. To start placing a bid, ensure your wallet is connected. Ensure your wallet is connected to either of these 3 networks: Ethereum Mainnet, Avalanche C-Chain Mainnet or Aurora Mainnet.

#### 4. In case there is a mismatch in the network, the UI will help you redirect to the correct chain (This redirect only works if you are connected to either of the 3 networks mentioned above)

![Wrong Network Redirect](<../../.gitbook/assets/image (11).png>)

#### 5. Before placing a bid, you need to approve the Gnosis Auction contract to spend your ERC20 tokens. You only need to do this once for each chain\*

![Approval](<../../.gitbook/assets/image (6).png>)

#### 6. Afterwards, you can start placing your bids

* the total oToken quantity available is shown under Size (oTokens). You can click on the MAX button if you decide to bid for full size. You cannot bid more than the full size.

![oToken Quantity](<../../.gitbook/assets/Screenshot 2022-02-17 at 2.57.13 PM.png>)

* The minimum bid is shown under Min. Bid (per oToken). The price per oToken must be above or equal the minimum bid.&#x20;

![Minimum Bid](<../../.gitbook/assets/Screenshot 2022-02-17 at 2.57.47 PM (1).png>)

* Total payable is the product of oToken Quantity and Price Per oToken. You need to have sufficient balance to cover the collateral. Your balance is shown under the Total Payable field.

![Total Payable](<../../.gitbook/assets/Screenshot 2022-02-17 at 2.58.11 PM (2).png>)

* For auction which accepts wrapped native token as a bidding token, you can choose whether to bid in the native token or the wrapped native token. We currently support ETH and AVAX for bids in native token. Do note that if you decide to bid in wrapped native token, you might be prompted by the UI to approve the token if you have not done so previously.

![Select Bid Token](<../../.gitbook/assets/Screenshot 2022-02-17 at 2.59.36 PM.png>)

![Select Bid Token](<../../.gitbook/assets/Screenshot 2022-02-17 at 3.00.34 PM.png>)

#### 7. If there are no errors, you click PLACE BID and accept this transaction in your wallet

#### 8. Once your bid is confirmed, you will be able to see it in the box at the right side. The bids you owned are highlighted. You can also check the transaction details of the bid by clicking on the link at the end of the row

![Bid List](<../../.gitbook/assets/image (8).png>)



\*We set the approval to max. amount to avoid having to approve the contract each time you place a bid.

## Step 2: Claiming

#### 1. When the auction ends, it will take some time before the auction is fully settled. Do not worry if you see the auction stays in the below screen for some time.

![Auction Settlement Page](<../../.gitbook/assets/image (5).png>)

#### 2. Once the auction is fully settled, you should be able to see the below. This shows the amount of oToken you’ve won and the amount of collateral you can claim back. If the box is green color, this means that you have not claimed the amount you’ve won/able to claim.

![Unclaimed oToken](<../../.gitbook/assets/image (9).png>)

#### 3. To claim, simply click CLAIM and accept the transaction in your wallet. This will automatically claim all your winnings and collateral from all the bids you’ve made previously.

#### 4. Once the claim is completed, you should see the box becomes grey colored and the claim button is no longer enabled.

![Claimed oToken](<../../.gitbook/assets/image (10).png>)

