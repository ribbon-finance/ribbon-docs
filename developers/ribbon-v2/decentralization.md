# Decentralization

The two major pieces for decentralization is \(a\) strike price selection, and \(b\) options sale. These pieces require new modules to be written.

**Strike Selection**

1. Instead of having the manager manually picking and setting the strike price, the strike price will be programmatically computed by the contract.
2. We are going to start with the simple logic of selecting a % from spot price.
3. For example, ETH is trading at $4000 now. We have a parameter `percentFromSpot = 25%` . The `selectStrikePrice` function is called and sets the strike price to be `4000 * 1.25 = 5000`

[Strike selection module](https://github.com/ribbon-finance/ribbon-v2/blob/master/contracts/utils/StrikeSelection.sol)

**Options Sale**

1. After the strike price is selected and the otokens are minted, we create a [Gnosis auction](https://gnosis-auction.eth.link/#/start).
2. The vault will list all the tokens onto the auction, which will last for 6 hours.
3. The vault sets the minimum price it will receive for the options. This establishes a price floor.
4. Bidding commences - option buyers get to set limit orders on the amount and price they want to buy.
5. Bidding ends - Vault withdraws all the premiums paid by the auction participants.

[Gnosis Auction module](https://github.com/ribbon-finance/ribbon-v2/blob/master/contracts/libraries/GnosisAuction.sol)

