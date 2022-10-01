# No lockups

Most unsecured loans in DeFi are still fixed term — this means that lenders must wait until the loan maturity to exit their position. This leaves a significant void for on-chain USDC holders who are willing to lend unsecured but are unwilling to lock their capital. As DeFi users ourselves, we recognize the immense opportunity cost with being locked in a position.

Ribbon Lend operates like Aave — a peer-to-pool mechanism that sets rates based on [utilization of funds in the pool](pool-status.md). As long as there is liquidity in the pool, users can exit their loans instantly, and accrue interest only for as long as they have been in the pool. Ribbon Lend’s pools use a utilization curve that incentivizes borrowers to leave some liquidity in the pool to facilitate withdrawals.

Withdrawing is equivalent to making a token redemption for your rTokens: you return them in exchange for your capital.
