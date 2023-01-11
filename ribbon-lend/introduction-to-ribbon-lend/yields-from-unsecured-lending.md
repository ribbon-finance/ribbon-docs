# Yields from unsecured lending

The demand for leverage is at all-time-lows in DeFi. Lending USDC on Aave’s money market yields \~1% APY; lending USDC on Ribbon Lend to institutional market makers currently yields 7%-10% APY organically, plus additional RBN liquidity mining incentives. These are pre-3AC rates — major CeFi lending desks have already come back online to lend to the same market makers.

Ribbon Lend pools are permissionless, so anyone can participate. You can deposit into any available pool, based on your preferences and expectations. Therefore, you can individually choose to whom you lend your capital. Following each deposit, you will receive receipt tokens (rToken); they represent your position in a given pool and accrue that pool's interest rate on each block.

Pools interest rates are dynamic: they change according to the [utilization rate](no-lockups/pool-status.md), or percentage of the pool's liquidity that is being used by the borrower at any particular moment, following a [specific curve](no-lockups/pool-status.md#utilization-curve). Interest is accumulated for each block and it immediately raises the borrower's utilization rate. In other words, interest is immediately paid to the lenders, but from the liquidity of the pool itself. The borrower may choose the frequency and amount of each repayment, provided that the utilization rate does not exceed a specified level established by governance.