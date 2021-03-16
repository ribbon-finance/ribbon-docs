# Protocol Adapters

To construct our products, we source liquidity from on-chain options protocols like Opyn and Hegic. This means that when users `purchase` a product on our contracts, our contracts actually use those funds to purchase options on other protocols.

The problem is that all the options protocols are _slightly_ different, and options on protocol A are not fungible with options on protocol B. Hence, we create "adapters" that standardize these protocols. These adapters are Solidity contracts that transform the data to normalize. Integrating a new option protocol is as simple as creating a new adapter for it.

## Available Adapters

* HegicAdapter \([https://github.com/ribbon-finance/structured-products/blob/master/contracts/adapters/HegicAdapter.sol](https://github.com/ribbon-finance/structured-products/blob/master/contracts/adapters/HegicAdapter.sol)\)
* GammaAdapter \([https://github.com/ribbon-finance/structured-products/blob/master/contracts/adapters/GammaAdapter.sol](https://github.com/ribbon-finance/structured-products/blob/master/contracts/adapters/GammaAdapter.sol)\)
* CharmAdapter \(under development\)

In order to have a unified interface across different Protocol Adapters, we have `IProtocolAdapter` . Below is the API reference for IProtocolAdapter.

If you are a protocol developer for an options/derivatives protocol, and want an Adapter developed, reach out to us on Discord!

## IProtocolAdapter

#### `protocolName() → string` \(external\)

Name of the adapter. E.g. "HEGIC", "GAMMA". Used as index key for adapter addresses.

#### `nonFungible() → bool` \(external\)

Boolean flag to indicate whether to use option IDs or not. Fungible protocols normally use tokens to represent option contracts.

#### `purchaseMethod() → enum ProtocolAdapterTypes.PurchaseMethod` \(external\)

Returns the purchase method used to purchase options.

#### `optionsExist(struct ProtocolAdapterTypes.OptionTerms optionTerms) → bool` \(external\)

Check if an options contract exist based on the passed parameters.

#### `getOptionsAddress(struct ProtocolAdapterTypes.OptionTerms optionTerms) → address` \(external\)

Get the options contract's address based on the passed parameters

#### `premium(struct ProtocolAdapterTypes.OptionTerms optionTerms, uint256 purchaseAmount) → uint256 cost` \(external\)

Gets the premium to buy `purchaseAmount` of the option contract in ETH terms.

#### `exerciseProfit(address options, uint256 optionID, uint256 amount) → uint256 profit` \(external\)

Amount of profit made from exercising an option contract \(current price - strike price\). 0 if exercising out-the-money.

#### `canExercise(address options, uint256 optionID, uint256 amount) → bool` \(external\)

#### `purchase(struct ProtocolAdapterTypes.OptionTerms optionTerms, uint256 amount, uint256 maxCost) → uint256 optionID` \(external\)

Purchases the options contract.

#### `exercise(address options, uint256 optionID, uint256 amount, address recipient)` \(external\)

Exercises the options contract.

#### `createShort(struct ProtocolAdapterTypes.OptionTerms optionTerms, uint256 amount) → uint256` \(external\)

Opens a short position for a given `optionTerms`.

#### `closeShort() → uint256` \(external\)

Closes an existing short position. In the future, we may want to open this up to specifying a particular short position to close.

