# RVOL \(Ribbon Volatility\)

## Overview

RVOL \(Ribbon Volatility\) is a set of Solidity contracts that utilizes Uniswap v3 to make on-chain volatility data accessible.

Its goals are to help builders for:

* Building on-chain volatility indices
* Querying realized volatility information
* Pricing derivatives and options with on-chain data

The RVOL library intends to have the below features:

* Realized volatility oracles for any Uniswap v3 pool
* Options pricing with Black Scholes for Uniswap v3 pool

## Usage in Ribbon v2

RVOL is used heavily by Theta Vaults in Ribbon v2. Of note, v2 uses RVOL for:

* Selecting weekly strike price for Theta Vault.
* Calculating the starting price of options in v2 auctions.

## VolOracle

[VolOracle](https://etherscan.io/address/0x4df938e57fD4Ad1dFDdDEEb1B4cFAbAB19E33A0E) is an oracle contract that serves historical volatility information for any Uniswap v3 pool.

Every 12 hours, the VolOracle's `commit` function is called, which uses the Uniswap v3 TWAP feature to get the TWAP for the time period. This TWAP is added to the contract, which is then used to calculate the period's return and the pool's price volatility.

### API

#### `function vol(address pool) public returns (uint256 stdev)`

The `vol` function returns the [volatility](https://goodcalculators.com/historical-volatility-calculator/) of a Uniswap pool for a 12-hour time period. Volatility is defined as the standard deviation of logarithmic returns.

#### `function annualizedVol(address pool) public returns (uint256 stdev)`

The `annualizedVol` function annualizes the output from `vol` and returns what is typically used as a Historical Volatility number in options exchanges.

## OptionsPremiumPricer

[OptionsPremiumPricer](https://github.com/ribbon-finance/rvol/blob/master/contracts/core/OptionsPremiumPricer.sol) is a read-only contract that allows developers to calculate the premium for a given option. The Pricer uses the VolOracle contract to fetch historical volatility information to inform its pricing.

### API

#### `function getPremium(uint strike, uint expiryTimestamp, bool isPut) public returns (uint256 premium)`

The `getPremium` function takes in the option's terms such as strike price, expiry and option type to determine the pricing of the option using the Black-Scholes model. Internally, it retrieves the spot price of the underlying asset from ChainLink and the annualized volatility from the VolOracle as additional inputs for Black-Scholes.

The `strike` parameter is in the unit of `10**8`, so the strike price of $3000 is `3000 * 10**8`. The premium is in the unit of `10**18`.

#### `function getOptionDelta(uint strike, uint expiryTimestamp) public returns (uint256 delta)`

The `getOptionDelta` function takes in the option's terms such as strike price and expiry to calculate the option's [Greek delta value](https://www.investopedia.com/terms/g/greeks.asp). The `delta` value is in the unit of `10**5`.

## Contract Addresses

| Contract | Address |
| :--- | :--- |
| VolOracle | [0x4df938e57fD4Ad1dFDdDEEb1B4cFAbAB19E33A0E](https://etherscan.io/address/0x4df938e57fD4Ad1dFDdDEEb1B4cFAbAB19E33A0E) |
| OptionsPremiumPricer ETH/USDC | [0x16Bc6DECA21B28D45233393553A9bf31792aE23C](https://etherscan.io/address/0x16Bc6DECA21B28D45233393553A9bf31792aE23C) |
| OptionsPremiumPricer WBTC/USDC | [0x2843bD3BF280Aa37Cc3a7d6a85B6d8f2F23a7b83](https://etherscan.io/address/0x2843bD3BF280Aa37Cc3a7d6a85B6d8f2F23a7b83) |

## Security

RVOL contracts deployed on the Ethereum mainnet is beta software and should be used with caution. These contracts still require time and usage on mainnet until it can prove its maturity. The smart contracts behind RVOL have been [audited by Peckshield](https://github.com/ribbon-finance/audit/blob/master/reports/PeckShield-Audit-Report-RVOL-v1.0rc.pdf).

## FAQ

**Is there a fee for using RVOL?**

No, RVOL

## Resources

GitHub: [https://github.com/ribbon-finance/rvol](https://github.com/ribbon-finance/rvol)

RVOL Feed & Calculator: [https://rvol.ribbon.finance/](https://rvol.ribbon.finance/)

