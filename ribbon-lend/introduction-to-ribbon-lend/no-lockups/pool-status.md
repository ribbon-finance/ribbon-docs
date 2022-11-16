# Pool status

Each pool is characterized by a utilization status, based on the utilization rate:

| Utilization rate | Pool Status         | Time Limit                      |
| ---------------- | ------------------- | ------------------------------- |
| <95%             | Active              | ꝏ                               |
| >95%             | Warning             | Until utilization = 99% or <95% |
| 99%              | Provisional Default | 120 Hours                       |

Each status corresponds to possible actions by lenders and borrowers:

* ACTIVE: Lenders: can deposit and withdraw; Borrower: can draw liquidity and repay.
* WARNING: Lenders: can deposit and withdraw; Borrower: can only repay. Interest will continue to accrue.
* PROVISIONAL DEFAULT: Lenders: deposit and withdrawals are blocked; Borrower: has 120 hours to deposit and get the utilization rate under 95%

If past 120 hours the borrower has not brought the utilization rate below 95 percent, the pool will go into [Default](default.md).

### Utilization curve

<figure><img src="../../../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

The relationship between interest rates and pool utilization rates follow curves set by the Team, based on prevailing CeFi lending rates to market makers.

* The curve has its lowest interest rate (Ym) at utilization (Xm) in order to achieve optimal utilization and capital efficiency;
* The curve discourages utilization in lower and extreme high ranges;
* The borrow APR steadily decreases with utilization from X0 to Xm. This compensates lenders who maintain funds within the pool with a more favorable interest rate when the borrower utilization rate is below optimal;
* Concurrently the curve increases sharply from Xm to X1, discouraging high utilization. This design reinforces the exit liquidity available for lenders even when utilization is optimal;
* During periods of volatility where liquidity withdrawal rates are higher, utilization/interest rates will peak, incentivising borrowers to reduce utilization in order to avoid higher interest rates. Higher interest rates may also attract new lenders to the pool.
