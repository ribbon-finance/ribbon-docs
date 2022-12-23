# Vote-Escrowed RBN

Participating in Ribbon DAO governance requires that an account have a balance of vote-escrowed RBN (veRBN) or regular RBN. veRBN is a non-standard ERC20 implementation, used within Governor Bravo voting system to determine each account’s voting power.

veRBN is represented by the `VotingEscrow` contract, deployed to the Ethereum mainnet at:

> [0x19854C9A5fFa8116f48f984bDF946fB9CEa9B5f7](https://etherscan.io/address/0x19854C9A5fFa8116f48f984bDF946fB9CEa9B5f7)

veRBN cannot be transferred. The only way to obtain veRBN is by locking RBN. The maximum lock time is two years. One RBN locked for two years provides an initial balance of one veRBN.

A user’s veRBN balance decays linearly as the remaining time until the RBN unlock decreases. For example, a balance of 4000 RBN locked for 6 months provides the same amount of veRBN as 2000 RBN locked for one year, or 1000 RBN locked for two years.

### Unlock

There are two options for unlocking locked veRBN:

1. waiting until your vote lock expires and unlocking penalty-free
2. unlock RBN whenever you want at the cost of paying a penalty. The penalty is calculated by taking the minimum between .75 and (time left until unlock) / 2 years. For example if you have 1 year left on your lock, the penalty is min(.75, 1/2) = 0.5. So the penalty is 50%. **All penalties will be redistributed to the remaining lockers pro-rata.**

### Implementation Details

User voting power $$𝑤𝑖$$ is linearly decreasing since the moment of lock. So does the total voting power 𝑊. In order to avoid periodic check-ins, every time the user deposits, or withdraws, or changes the locktime, we record user’s slope and bias for the linear function $$𝑤𝑖(𝑡)$$ in the public mapping `user_point_history`. We also change slope and bias for the total voting power $$𝑊(𝑡)$$ and record it in `point_history`. In addition, when a user’s lock is scheduled to end, we schedule change of slopes of $$𝑊(𝑡)$$ in the future in `slope_changes`. Every change involves increasing the `epoch` by 1.

This way we don’t have to iterate over all users to figure out, how much should $$𝑊(𝑡)$$ change by, neither we require users to check in periodically. However, we limit the end of user locks to times rounded off by whole weeks.

Slopes and biases change both when a user deposits and locks governance tokens, and when the locktime expires. All the possible expiration times are rounded to whole weeks to make number of reads from blockchain proportional to number of missed weeks at most, not number of users (which is potentially large).

For more details, please visit [curve docs](https://curve.readthedocs.io/dao-vecrv.html#querying-balances-locks-and-supply).
