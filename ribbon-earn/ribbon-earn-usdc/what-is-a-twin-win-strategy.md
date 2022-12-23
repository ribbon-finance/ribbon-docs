# What is a twin win strategy?

The vault earns a base APY and uses the remaining funding to purchase weekly [at-the-money](https://www.investopedia.com/terms/a/atthemoney.asp) [knock-out barrier options](https://www.investopedia.com/terms/k/knock-outoption.asp).

The weekly barrier options enable the vault to participate in any ETH upside up to 108% of the ETH's spot level at the start of the week (upside barrier) and any ETH downside down to 92% of ETH's spot level at the start of the week (downside barrier). However, if the price of ETH has increased or decreased by more than 8% at the end of the week, the barrier options expire worthless and the vault earns the base APY only.

So, instead of trading a difficult and choppy market, Ribbon Earn lets you get exposure to weekly moves in both directions, up to a certain level. If the price level does not move, or exceeds the range in either direction, users will get back a rebate of 4% APY, as well as their principal back.&#x20;

Let’s break it down with an example:

**Step 1**: You deposit USDC into the R-Earn vault.

**Step 2**: The vault invests in [Ribbon Lend](../../ribbon-lend/introduction-to-ribbon-lend/), lending its funds to credit worthy institutions and collects an interest rate (let’s say 9% p.a.)

**Step 3**: Ribbon used that 9% p.a. to buy weekly ATM Straddle KO options.

**Result 1**: ETH moves up or down but doesn’t break the barrier thus resulting in profit for the vault (profit capped at 16.33% projected APY).

**Result 2**: ETH breaks a barrier resulting in the options expiring worthless. However, since the options were bought with interest earned from lending the principal you lose no money.
