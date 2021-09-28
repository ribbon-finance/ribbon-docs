# No withdrawal fees

Mid-week withdrawals are no longer possible so it is only fair that we allow free withdrawals. We are replacing this with a management fee / performance fee \(only on profitable weeks\) to maintain ribbon finance and to potentially allow for $RBN value capture in the future.

You can find the current performance / management fees either in the UI or via etherscan.

For example the [v2 WBTC call vault](https://etherscan.io/address/0x65a833afdc250d9d38f8cd9bc2b1e3132db13b2f/advanced#readProxyContract) has the `managementFee` and `performanceFee` variables both with 6 decimals. So if the `performanceFee` is 20000000, the fee is 20% of profitable weeks.

