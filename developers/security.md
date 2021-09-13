# Security

## Bug Bounty

We have an ongoing [bug bounty on ImmuneFi](https://immunefi.com/bounty/ribbon/), with up to $50,000 of bounty. The contracts that are included in the bounty are ETH and WBTC Theta Vaults.

## Audits

Ribbon's v1 and v2 Theta Vault contracts are audited. Despite the audits and security measures we have taken, we advice users to exercise caution and to not risk funds they are not willing to lose.

Theta Vault v2 Audits:

* [OpenZeppelin](https://blog.openzeppelin.com/ribbon-finance-audit/)
* [ChainSafe](https://github.com/ribbon-finance/audit/blob/master/reports/RibbonThetaVault%20V2%20Smart%20Contract%20Review%20And%20Verification.pdf)

Theta Vault v1 Audits:

* [Peckshield](https://github.com/ribbon-finance/audit/blob/master/reports/PeckShield-Audit-Report-Ribbon-v1.0.pdf)
* [ChainSafe](https://github.com/ChainSafe/audits/blob/main/Ribbon%20Finance/Ribbon-Audit_April-2021.pdf)
* [Quantstamp](https://github.com/ribbon-finance/audit/blob/master/reports/Quantstamp%20Theta%20Vault.pdf)

## System Roles

Currently, the protocol has a few privileged roles that help bootstrap the protocol at its initial development.

| Role | Description |
| :--- | :--- |
| Admin | Multisig address that is able upgrade proxies for the Theta Vault contracts. |
| Owner | Multisig address that is able to set new keepers, set performance or management fees and override strike prices. |
| Keeper | EOA used to perform day-to-day operations of a Theta Vault. |



