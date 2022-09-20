# Introduction to Ribbon Earn

## What is Ribbon Earn?

Ribbon Earn is a new line of yield vaults, designed to have a risk profile complementary to Theta vaults. It's an all-weather yield product that offers principal protection and uses a combination of lending and exotic options to enhance yields through exposure to short-term volatility in the market.

It employs a fully funded "twin win" strategy through which depositors can capitalize on the intra-week ETH movements in either direction, while also ensuring their capital is protected.&#x20;

## What is a twin win strategy?

The vault earns a base APY and uses the remaining funding to purchase weekly [at-the-money](https://www.investopedia.com/terms/a/atthemoney.asp) [knock-out barrier options](https://www.investopedia.com/terms/k/knock-outoption.asp). As the epoch of the vault is one month but the options purchased are weekly options, 4 options are purchased within one epoch.

The weekly barrier options enable the vault to participate in any ETH upside up to 108% of the ETH's spot level at the start of the week (upside barrier) and any ETH downside down to 92% of ETH's spot level at the start of the week (downside barrier). However, if the price of ETH has increased or decreased by more than 8% at the end of the week, the barrier options expire worthless and the vault earns the base APY only.

So, instead of trading a difficult and choppy market, Ribbon Earn lets you get exposure to weekly moves in both directions, up to a certain level. If the price level does not move, or exceeds the range in either direction, users will get back a rebate of 4% APY, as well as their principal back.&#x20;

Let’s break it down with an example:

**Step 1**: You deposit USDC into the R-Earn vault.

**Step 2**: Ribbon lends money to credit worthy institutions and collects an interest rate (let’s say 9% p.a.)

**Step 3**: Ribbon used that 9% p.a. to buy weekly ATM Straddle KO options.

**Result 1**: ETH moves up or down but doesn’t break the barrier thus resulting in profit for the vault (profit capped at 16.33% projected APY).

**Result 2**: ETH breaks a barrier resulting in the options expiring worthless. However, since the options were bought with interest earned from lending the principal you lose no money.

## Vault specifications

* Loan Tenor 28 DAYS&#x20;
* Option Tenor 7 DAYS&#x20;
* Upside Barrier 108%&#x20;
* Downside Barrier 92%
* Strike 100%&#x20;
* Capital Protection 100%&#x20;
* Base APY 4.00%&#x20;
* Barrier Type EUROPEAN (OBSERVED AT MATURITY)

## Risk profile

Ribbon Earn is designed to be an all-weather yield product, much more akin to a “set and forget” strategy that users do not need to actively pause-resume based on market conditions. People who are looking for a place to earn yield on USDC, and want some exposure to the market volatility, may find Ribbon Earn the right product for them.&#x20;

It is important, in any case, to understand the risks associated with the investment: Ribbon Earn generates yield through lending, which has credit risk; market makers taking the other side of Ribbon Earn trades carry credit risk and could potentially default in the case of extreme events. This means that both the principal and yield invested could be lost in the event of market makers defaulting. However, to minimize this risk Ribbon select a basket of leading accredited crypto market makers, whose credit assessment passed strict requirements set by [Credora](https://credora.io/), the leading real-time credit underwriter in crypto.&#x20;

For the first epoch, 50% of the capital assigned to this pool is lent to [Wintermute](https://www.wintermute.com/) (rating AA) and 50% is lent to [Folkvang](https://folkvang.io/) (rating AA).

In the situation that the knock-out options expire in-the-money, sellers of the knock-out options structure may be unable to fulfill part of their obligations to the vault.

## Fees

The vault fee structure consists of a 15% flat fee on the yield earned between epochs.

## Future development

Ribbon Earn is new line of vaults, so more variants will soon follow.
