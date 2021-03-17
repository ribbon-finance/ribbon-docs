# System Roles

Currently, the protocol has a few privileged roles that help bootstrap the protocol at its initial development.

| Role | Description |
| :--- | :--- |
| Admin | Multisig address that is able upgrade proxies of the RibbonFactory and instrument contracts. |
| Owner | Multisig address that is able to set adapters to be used in the protocol and select managers for a vault. |
| Manager | Multisig address that performs the day-to-day operations of an Options Vault. This includes selecting parameters of options to sell for a vault. |

## Progressive Decentralization <a id="83a6"></a>

As you can probably tell, there are a few pieces of this process that are more centralized:

* Managers have sole discretion over strike selection
* Managers and selected market makers decide on option prices off-chain \(OTC\).
* We have whitelisted specific market makers who we are partnering with

Although we are starting with this, we plan to decentralize these functions over time once the vaults are more battle tested on mainnet. For example:

* We plan to decentralize the function of the manager to a group of strategists that are voted on by the community, including better incentive mechanisms for encouraging good management of the vault
* We plan to open up the option buying function to anyone in the community through an auction-like mechanism, and remove whitelists



