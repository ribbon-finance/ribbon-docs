# Decentralization

The two major pieces for decentralization is \(a\) strike price selection, and \(b\) options sale. These pieces require new modules to be written.

## Strike Selection

Instead of having the manager manually picking and setting the strike price, the strike price will be programmatically computed by the contract. The [Strike Selection contract](https://github.com/ribbon-finance/ribbon-v2/blob/master/contracts/utils/StrikeSelection.sol) is a periphery contract.

Currently the vaults use a 0.1 delta for writing options. This means that the vault will only be selling far out-the-money options.

```text
function getStrikePrice(uint256 expiryTimestamp, bool isPut)
```

The StrikeSelection contract exposes the `getStrikePrice` function which iterates through a set of strike prices, evaluating its delta value, and settling on a strike price that has the closest match.

## Open Auction

1. After the strike price is selected and the otokens are minted, we create a [Gnosis auction](https://gnosis-auction.eth.link/#/start) and put the options up for sale.  This allows anyone to bid on the otokens.
2. The vault will list all the tokens onto the auction, which will last for 1 hour \(as of now\).
3. The vault sets the minimum price it will receive for the options. This establishes a price floor.
4. Bidding commences - option buyers get to set limit orders on the amount and price they want to buy.
5. Bidding ends - Vault withdraws all the premiums paid by the auction participants.

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

The `duration` is set by the vault. But it is 1 hour.

