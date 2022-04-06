# Participating in Open Auctions

## Overview

* Open Auctions are a batch auction conducted on the Gnosis Auction platform to sell off options that are minted by Theta Vault.
* A batch auction means that there is **only one clearing price,** which eliminates front-running.&#x20;
* Using an auction allows for price discovery on-chain, to ensure the options sale process is decentralized.
* Currently it is possible to participate through two different UIs:
  * Ribbon Auction UI (Recommended) - [Guide](participating-through-ribbon-ui.md)
  * Gnosis Auction UI - [Guide](participating-through-gnosis-ui.md)

## Auction Process Flow

To run through how Theta Vaults would function, we use ETH Call Theta Vault as an example.

1. ETH Call Theta Vault holds 100 ETH from depositors. It rolls the 100 ETH into Opyn and mints 100 call options with $4000 strike, expiring next Friday.
2. The vault starts the option auction. The vault deposits 100 call options onto the auction, and specifies the minimum price of an option. (Premiums are denominated in underlying for calls, USDC for puts)
3. Auction participants participate in the auction by placing bids on-chain. They can place multiple bids and also cancel bids. Each bid consumes gas.
4. Auction is concluded in one hour. The vault withdraws the premiums and earns yield for the week.
5. If there are unsold options from the auctions, the vault withdraws the options and burns them.
6. Auction participants get to claim their options from the auction. If the bid is not filled, the auction participant will then get a refund of their bid amount.

## Auction Schedule\*

Friday 8.00am UTC - Previous week's options expire. Settlement price is set.

Friday \~9.00-10.00am UTC - Strike price selection.

Friday 10.20-10.30am UTC - WBTC Call Auction

Friday 10.30-10.40am UTC - AAVE Call Auction

Friday 10.40-10.50am UTC - stETH Call Auction

Friday 10.50-11.00am UTC - ETH Call Auction

Friday 11.00-11.10am UTC - ETH Put Auction (yvUSDC Vault)

Friday 11.10-11.20am UTC - AVAX Call Auction

Friday 11.20-11.30am UTCC - SOL Call Auction



\*Subject to changes, valid as of 24 February 2022

## Batch Auction Summary

To read the detailed doc about how Batch Auctions work, [please read this documentation by Gnosis](https://gnosis-auction.eth.link/#/docs/batch-auctions). This is only a summary of how the pricing mechanism works.

![](<../../.gitbook/assets/untitled-1- (1).png>)

1. Auction participants place their bids for the option.
2. The auction is concluded, no new bids are accepted and no orders can be cancelled.
3. The bids are sorted from the highest to the lowest bid.
4. Going through the bids from the highest price, the amount of options sold will be counted.
5. When the target sell volume is hit, the final price will settle at the last volume.

**Summary:** Everyone gets a single clearing price. However, bidding a high price increases our chance of being filled. Bidding low could result in not have their orders filled.

## Strategies for Executing a Buy

* Since each auction runs for 10 minutes, participants are not recommended to instantly hedge the other side by buying options. Each participants' allocation is only determined when the auction is closed.
* One way around this is to place a bid nearing the end of the auction. This way, the time difference between placing a bid and finding out your allocation will be much shorter.
* By bidding nearing the end, it also puts you in a better position to win the auction since you can simply outbid the current settlement price. This gives you a higher certainty of getting the desired allocation.

## Optimizing for Gas

There are 2 Ethereum transactions that have to land on-chain to participate in the auction:

#### 1. Placing an order

When placing an order, we recommend setting your gas price to high. This is to prevent failed submission, especially if you decide to bid nearing the end of the auction.

#### 2. Claiming an Order

For claiming an order, when the order is not filled, you will get a refund of the collateral you locked into the order. On the other hand, if it is filled, you will get the otokens auctioned.

When the auction is closed, there is no time limit for participants to claim their allocation and collateral. Hence, you can choose to set for regular gas price.

Additionally, we would suggest the following strategy when claiming:

* For claims in which you can get collateral refunds, you can claim them immediately after auction closure
* For claims in which you have an oToken allocation, you can avoid claiming the oTokens until expiry. Since the oTokens will be worthless if they expire out-the money, you can wait until after the expiry to decide if you want to claim them or not.
* If the oTokens are out-the-money, you can avoid claiming the oTokens entirely as it will incur gas costs.

