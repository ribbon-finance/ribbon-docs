# Liquidity Gauges and RBN Emissions

Ribbon incentivizes vault depositors with RBN, the protocol governance token. Allocation, distribution and emission of RBN are managed via several related DAO contracts:

* `LiquidityGauge`: Measures vault tokens (i.e. rETH-THETA) provided by users over time, in order to distribute RBN and other rewards
* `GaugeController`: Central controller that maintains a list of gauges, weights and type weights, and coordinates the rate of RBN production for each gauge
* `Minter`: RBN emission contract, sends non-circulating RBN into circulation via liquidity gauges

### Implementation Details

#### RBN Emissions

RBN follows a constant inflation schedule of 250,000 RBN per week rewarded to vault depositors over the course of 6 months. This is \~6.5 M RBN overall, or 0.65% of total supply. This is subject to changes before the 6 months have elapsed. We will officially revisit this inflation schedule after the 6 months.&#x20;

![Imgur](https://aws1.discourse-cdn.com/standard21/uploads/ribbon/optimized/1X/5495db8819f2efd51484e025dc450a0ea187a899\_2\_690x427.png)

#### Liquidity Gauges

Emissions are directed to users who deposit into the protocol option selling vaults. This usage is measured via “Liquidity Gauge” contracts. Each pool has an individual liquidity gauge. The [Gauge Controller ](liquidity-gauges-and-rbn-emissions.md#the-gauge-controller)maintains a list of gauges and their types, with the weights of each gauge and type.

To measure liquidity over time, the user deposits their vault tokens into the liquidity gauge. Coin rates which the gauge is getting depends on current emission rate, gauge weight, and gauge type weights. Each user receives a share of newly emitted RBN proportional to the amount of vault tokens locked. Additionally, rewards may be boosted by up to factor of 2.5 if the user vote-locks tokens for Ribbon governance in the [Voting Escrow](vote-escrowed-rbn.md) contract.

Suppose we have the constant emission rate $$𝑟$$, gauge weight $$𝑤g$$ and gauge type weight $$𝑤𝑡$$. Then, all the gauge handles the stream of inflation with the rate $$𝑟′=𝑤𝑔*𝑤𝑡*𝑟$$ which it can update every time $$𝑤𝑔,𝑤𝑡$$, or mining epoch changes.

To calculate a user’s share of $$𝑟′$$, we must calculate the integral: $$ $𝐼𝑢=∫(𝑟′(𝑡)𝑏𝑢(𝑡)/𝑆(𝑡))𝑑𝑡 $$ where $$𝑏𝑢(𝑡)$$ is the balance supplied by the user (measured in vault tokens) and $$𝑆(𝑡)$$ is total deposits supplied by users, depending on the time $$𝑡$$; the value $$𝐼𝑢$$ gives the amount of tokens which the user has to have emitted to them. The user’s balance $$𝑏𝑢$$ changes every time the user $$ $𝑢 $$ makes a deposit or withdrawal, and $$𝑆$$ changes every time \_any\_ user makes a deposit or withdrawal (so $$ $𝑆 $$ can change many times in between two events for the user $$𝑢"$$. In the liquidity gauge contract, the value of $$𝐼𝑢$$ is recorded per-user in the public `integrate_fraction` mapping.

To avoid requiring that all users to checkpoint periodically, we keep recording values of the following integral (integrated over 0 -> t) (named `integrate_inv_supply` in the contract):

> $$ $𝐼𝑖𝑠(𝑡)=∫(𝑟′(𝑡)/𝑆(𝑡))𝑑t $$

The value of $$𝐼𝑖𝑠$$ is recorded at any point any user deposits or withdraws, as well as every time the rate $$𝑟′$$ changes (either due to weight change or change of mining epoch).

#### Boosting

In order to incentivize users to participate in governance, and additionally create stickiness for liquidity, we implement the following mechanism. A user’s balance, counted in the liquidity gauge, gets boosted by users locking RBN tokens in [Voting Escrow](vote-escrowed-rbn.md) contract, depending on their vote weight $$𝑤𝑖wi$$: $$𝑏𝑢*=min(0.4𝑏𝑢+0.6𝑆*𝑤𝑖/𝑊,𝑏𝑢)$$ The value of $$𝑤𝑖$$ is taken at the time the user performs any action (deposit, withdrawal, withdrawal of emitted RBN tokens) and is applied until the next action this user performs.

If no users vote-lock any RBN (or simply don’t have any), the inflation will simply be distributed proportionally to the liquidity $$𝑏𝑢$$ each one of them provided. However, if a user stakes enough RBN, they are able to boost their stream of RBN by up to factor of 2.5 (reducing it slightly for all users who are not doing that).

Implementation details are such that a user gets the boost at the time of the last action or checkpoint. Since the voting power decreases with time, it is favorable for users to apply a boost and do no further actions until they vote-lock more tokens. However, once the vote-lock expires, everyone can “kick” the user by creating a checkpoint for that user and, essentially, resetting the user to no boost if they have no voting power at that point already.

RBN lockers can delegate their boost to other addresses and in return earn yield through [bribes](bribes/).

#### Gauge Weight Voting

Users can allocate their veRBN towards one or more liquidity gauges. Gauges receive a fraction of newly minted RBN tokens proportional to how much veRBN the gauge is allocated. Each user with a veRBN balance can change their preference at any time.

When a user applies a new weight vote, it gets applied at the start of the next epoch week. The weight vote for any one gauge cannot be changed more often than once in 10 days.

RBN lockers can vote for particular gauges and in return earn yield through [bribes](bribes/).

#### The Gauge Controller

The “Gauge Controller” maintains a list of gauges and their types, with the weights of each gauge and type. In order to implement weight voting, `GaugeController` has to include parameters handling linear character of voting power each user has.

`GaugeController` records points (bias + slope) per gauge in `vote_points`, and \_scheduled\_ changes in biases and slopes for those points in `vote_bias_changes` and `vote_slope_changes`. New changes are applied at the start of each epoch week.

Per-user, per-gauge slopes are stored in `vote_user_slopes`, along with the power the user has used and the time their vote-lock ends.

The totals for slopes and biases for vote weight per gauge, and sums of those per type, are scheduled / recorded for the next week, as well as the points when voting power gets to 0 at lock expiration for some of users.

When a user changes their gauge weight vote, the change is scheduled for the next epoch week, not immediately. This reduces the number of reads from storage which must to be performed by each user: it is proportional to the number of weeks since the last change rather than the number of interactions from other users.

### Gauge Types

Each liquidity gauge is assigned a type within the gauge controller. Grouping gauges by type allows the DAO to adjust the emissions according to type, making it possible to e.g. end all emissions for a single type.

Currently active gauge types are as follows:

> * Vault (all Ethereum vaults): `0`

### LiquidityGauge

Each pool has a unique liquidity gauge. Deployment addresses can be found in the [addresses reference](../../developers/contract-addresses.md) section of the documentation.

There are several versions of liquidity gauge contracts in use. Source code for these contracts is available on [Github](https://github.com/ribbon-finance/governance/tree/main/contracts/tvl-staking).



For more details, please visit [curve docs](https://curve.readthedocs.io/dao-gauges.html#querying-gauge-information).
