# Ribbon v2

Ribbon v2 is the next version for Ribbon’s Theta Vault product. It brings several major improvements to the vault and makes the vault operations decentralized. 

### V2 changes include: <a id="V2-changes-include"></a>

1. Decentralization of Theta Vault operations
2. Improved capital efficiency
3. No more withdrawal fees
4. Meta-Vault strategies

[Paired video](https://www.loom.com/share/be2a76a724ab45769737bd8ffeddadb3)

#### Decentralization

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

#### Capital Efficiency <a id="Capital-Efficiency"></a>

Before, 90% of funds were utilized to allow for early withdrawals. Since we disallowed mid-week withdrawals, we can utilize 100% of vault funds as collateral. This boosts APY.

#### Withdrawal Fees <a id="Withdrawal-Fees"></a>

Mid-week withdrawals are no longer possible so it is only fair that we allow free withdrawals. We are replacing this with a management fee / performance fee to maintain ribbon finance and to potentially allow for $RBN value capture in the future.

You can find the current performance / management fees either in the UI or via etherscan.

For example the [v2 wbtc call vault](https://etherscan.io/address/0x65a833afdc250d9d38f8cd9bc2b1e3132db13b2f/advanced#readProxyContract) has the `managementFee` and `performanceFee` variables both with 6 decimals. So if the `performanceFee` is 20000000, the fee is 20% of profitable weeks.

#### Meta Vaults <a id="Meta-Vaults"></a>

We have made the v2 vaults more robust to make building on top of the base put selling and covered call vaults relatively easy.

Example Vaults:

1. [Short strangle](https://www.chittorgarh.com/options-trading-strategy/short-strangle-or-sellstrangle/18/#:~:text=The%20Short%20Strangle%20%28or%20Sell,volatility%20in%20the%20near%20term.%29) strategy, which simultaneously deposits your funds into the eth covered call vault and put selling vault
2. Eth put vault which borrows USDC with your ETH and deposits it into the put selling vaults

More info can be found in this [medium article](https://chuddster.medium.com/ribbon-meta-vaults-ce094dab65a) and the [metavault repo](https://github.com/ribbon-finance/metavault).

