# Risk profile

The main risks associated with the vault are market risk, stETH/ETH price risk and the slashing risk:&#x20;

* Market risk: as each trade is 99.5% protected, if the option payout is 0, depositors can lose a fraction of their capital invested every week.&#x20;
* stETH/ETH price risk: as the payoff is based on the ETH price but is paid in stETH, the actual quantity of stETH earned is dependent on the exchange rate between ETH and stETH.
* Slashing risk: ETH validators risk staking penalties, with up to 100% of staked funds at risk if validators fail. To minimise this risk, Lido stakes across multiple professional and reputable node operators with heterogeneous setups, with additional mitigation in the form of insurance that is paid from Lido fees.
