# Pool status

Each pool is characterized by a utilization status, based on the utilization rate:

| Utilization rate | Pool Status      | Time Limit                      |
| ---------------- | ---------------- | ------------------------------- |
| <95%             | Active           | ꝏ                               |
| >95%             | High Utilization | Until utilization = 99% or <95% |
| 99%              | Warning          | 120 Hours                       |

Each status corresponds to possible actions by lenders and borrowers:

* ACTIVE: Lenders: can deposit and withdraw; Borrower: can draw liquidity and repay.
* HIGH UTILIZATION: Lenders: can deposit and withdraw; Borrower: can only repay. Interest will continue to accrue.
* WARNING: Lenders: deposit and withdrawals are blocked; Borrower: has 120 hours to deposit and get the utilization rate under 95%

If past 120 hours the borrower has not brought the utilization rate below 95 percent, the pool will go into [Default](default.md).
