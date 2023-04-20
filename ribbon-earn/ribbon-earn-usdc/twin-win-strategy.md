# Twin win strategy

The vault earns a base APY and uses the remaining funding to purchase weekly [at-the-money](https://www.investopedia.com/terms/a/atthemoney.asp) [knock-out barrier options](https://www.investopedia.com/terms/k/knock-outoption.asp).

<figure><img src="https://images.squarespace-cdn.com/content/v1/627988321d6a280b407f270b/54a5feb6-dd20-436b-bde4-2d5cf96068e3/REARNV2.jpg?format=500w" alt=""><figcaption></figcaption></figure>

Adjusting to a 10-delta barrier strike for both the lower and upper barriers makes the barriers move with volatility. This means that:

1. If the market anticipates low volatility, we don’t have to pay extra for wider barriers that will not be useful (as the probability of hitting them is very low so price goes up)
2. Barriers level will move with how spot has been moving historically
3. Keeps participation rate more stable from week to week as option price doesn’t vary as much
