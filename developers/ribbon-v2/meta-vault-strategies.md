# Meta-Vault Strategies

We have made the v2 vaults more robust to make building on top of the base put selling and covered call vaults relatively easy.

Example Vaults:

1. [Short strangle](https://www.chittorgarh.com/options-trading-strategy/short-strangle-or-sellstrangle/18/#:\~:text=The%20Short%20Strangle%20\(or%20Sell,volatility%20in%20the%20near%20term.\)) strategy, which simultaneously deposits your funds into the eth covered call vault and put selling vault
2. Eth put vault which borrows USDC with your ETH and deposits it into the put selling vaults

More info can be found in this [medium article](https://chuddster.medium.com/ribbon-meta-vaults-ce094dab65a) and the [metavault repo](https://github.com/ribbon-finance/metavault).
