# Decentralization

The two major pieces for decentralization is \(a\) strike price selection, and \(b\) options sale. These pieces require new modules to be written.

**Strike Selection**

1. Instead of having the manager manually picking and setting the strike price, the strike price will be programmatically computed by the contract.
2. We are going to start with the simple logic of selecting a % from spot price.
3. For example, ETH is trading at $4000 now. We have a parameter `percentFromSpot = 25%` . The `selectStrikePrice` function is called and sets the strike price to be `4000 * 1.25 = 5000`

[Strike selection module](https://github.com/ribbon-finance/ribbon-v2/blob/master/contracts/utils/StrikeSelection.sol)

The Strike Selection contract is a periphery contract. Roughly speaking a 0.1 delta means that an option is 10% likely to expire in-the-money, which is the parameter we are going for.

```text
function getStrikePrice(uint256 expiryTimestamp, bool isPut)
```

The StrikeSelection contract exposes the `getStrikePrice` function which iterates through a set of strike prices, evaluating its delta value, and settling on a strike price that has the closest match.

**Options Sale**

1. After the strike price is selected and the otokens are minted, we create a [Gnosis auction](https://gnosis-auction.eth.link/#/start) and put the options up for sale.  This allows anyone to bid on the otokens.
2. The vault will list all the tokens onto the auction, which will last for 1 hour \(as of now\).
3. The vault sets the minimum price it will receive for the options. This establishes a price floor.
4. Bidding commences - option buyers get to set limit orders on the amount and price they want to buy.
5. Bidding ends - Vault withdraws all the premiums paid by the auction participants.

[Gnosis Auction module](https://github.com/ribbon-finance/ribbon-v2/blob/master/contracts/libraries/GnosisAuction.sol)

The key data structure here is `AuctionDetails`.

```text
struct AuctionDetails {
    address oTokenAddress;
    address gnosisEasyAuction;
    address asset;
    uint256 assetDecimals;
    uint256 oTokenPremium;
    uint256 duration;
}
```

The `oTokenPremium` is the price per otoken that the theta vault has calculated using the [OptionPremiumPricer](https://github.com/ribbon-finance/rvol/blob/master/contracts/core/OptionsPremiumPricer.sol) from [RVOL](https://github.com/ribbon-finance/rvol).

The `duration` is set by the vault. But it is likely going to be 1 hour.

