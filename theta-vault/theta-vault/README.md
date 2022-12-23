# Introduction to Theta Vaults

## What are Theta Vaults?

Theta Vaults run an automated European options selling strategy, which earns yield on a weekly basis through writing out of the money options and collecting the premiums. We use the Vault terminology because it stems from the idea of depositing your assets into a vault and earning a yield on them.

Users can simply deposit and the vaults will automatically start running a specific option strategy. This alleviates a majority of the gas problems by socializing the gas costs across all the vault depositors: instead of doing 3–4 transactions per week per user, the vault will do 3–4 transactions per week for thousands of users at once. This makes the user experience of using these Theta Vaults extremely straightforward and relatively cheap.

Theta Vaults also allow you to choose when to participate or not to participate in the weekly strategy through a [pause and resume](../user-guides/how-to-pause-and-resume.md) function, so that you do not limit your usage options in relation to your market expectations.

There are two vault types currently active:

1. [Covered call selling](https://www.investopedia.com/terms/c/coveredcall.asp): each week the vault issues [OTM (out of the money)](https://www.investopedia.com/terms/o/outofthemoney.asp) call options on all deposits.
2. [Put selling](https://www.investopedia.com/terms/p/putoption.asp): each week the vault issues OTM put options on all deposits.
