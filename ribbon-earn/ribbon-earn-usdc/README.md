# Ribbon Earn USDC

Ribbon Earn USDC is an all-weather product that generates yield by purchasing [Backed IB01 $ Treasury Bond 0–1yr](https://uploads-ssl.webflow.com/622f4d1701727dc75198439a/640f24743a879f53d86468fe\_bIB01%20Factsheet.pdf) tokens with an average YTM of 4.64% (as of April 10), then enhancing that by purchasing weekly at-the-money [knock-out barrier options](https://bookdown.org/maxime\_debellefroid/MyBook/barrier-options.html#knock-out-options) on ETH, to get exposure to short-term volatility in the market in either direction. Depositors can get upside exposure to the crypto market and remain principal protected. Read more about the strategy [here](https://www.research.ribbon.finance/blog/introducing-ribbon-earn).

#### **V2 Upgrade**

We are making two key changes in the V2 upgrade:

1. **Risk-Free Rate**: Instead of sourcing funding by lending USDC open-term to market makers like Wintermute and Folkvang in V1, V2 sources funding by purchasing Backed IB01 tokens which represent ownership of the tracker certificate for the underlying [iShares $ Treasury Bond 0–1yr UCITS ETF](https://www.blackrock.com/americas-offshore/en/products/307243/ishares-treasury-bond-0-1yr-ucits-etf).
2. **ETH 10-delta Knock-Out Barrier:** Instead of maintaining fixed % knock-out barriers for the exotic option in V1, in V2 the barriers will be fixed at the 10-delta levels and thus move dynamically with volatility.
