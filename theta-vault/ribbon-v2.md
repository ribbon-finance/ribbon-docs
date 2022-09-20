# Theta vaults architecture

## Vault flow example

<figure><img src="../.gitbook/assets/1663452578-picsay.jpg" alt=""><figcaption></figcaption></figure>

1. User deposits 100 ETH into T-ETH-C (ETH call).
2. On Friday 8 am UTC, the vault closes the previous week roound and subsequently uses 100% of its funds to mint 100 [otokens](https://opyn.gitbook.io/opyn/contracts/otoken), which are ERC20 representations of options contracts. The 100 ETH is locked for a week in Opyn.
3. After receiving the 100 otokens, the vault puts it up for auction on [Paradigm](how-to-participate-in-paradigm-auctions.md).
   * Registered users can participate and bid on the otokens. They pay the premiums for the otoken in ETH. Paradigm can use different kinds of auctions to maximise depositors' returns (e.g. [blind auctions](https://en.wikipedia.org/wiki/First-price\_sealed-bid\_auction))
   * At the end of the auction, the vault collects 1 ETH in premiums in the form of ETH.
   * Any remaining otokens that are not bought are burned, redeeming 1 otoken for 1 unit of collateral from Opyn.
4. On the next Friday 8 am UTC,
   * If the options expire in the money, the vault withdraws less than 100 ETH from Opyn.
   * If the options expire out the money, the vault withdraws exactly 100 ETH.
5. Let's say it expires out the money. The vault repeats step 2 with 101 ETH (original 100 ETH + 1 ETH premium).

### Codebase

| Name                                                                                                                                               | Description                                                                                                        |
| -------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| [libraries/Vault.sol](https://github.com/ribbon-finance/ribbon-v2/blob/master/contracts/libraries/Vault.sol)                                       | Contains all data structures shared across all vault types                                                         |
| [libraries/VaultLifecycle.sol](https://github.com/ribbon-finance/ribbon-v2/blob/master/contracts/libraries/VaultLifecycle.sol)                     | Contains all logic related to how the Vault functions on a weekly basis                                            |
| [vaults/BaseVaults/base/RibbonVault.sol](https://github.com/ribbon-finance/ribbon-v2/blob/master/contracts/vaults/BaseVaults/base/RibbonVault.sol) | Contains all common logic like accounting and options rolling shared across RibbonThetaVault and RibbonDeltaVault. |
| [vaults/BaseVaults/RibbonThetaVault.sol](https://github.com/ribbon-finance/ribbon-v2/blob/master/contracts/vaults/BaseVaults/RibbonThetaVault.sol) | Theta Vault contract that creates short options position with Opyn on a weekly basis                               |

## Deposit Flow

IMPORTANT: this is a _technical_ explanation, if you need assistance on making a deposit please refer to [this page](how-to-deposit.md)!

<figure><img src="../.gitbook/assets/1663452248-picsay.jpg" alt=""><figcaption></figcaption></figure>

1. The user deposits 1 ETH into TV.
2. We first check if they have an existing `DepositReceipt` from the past `round`. Using the `round` and `amount`, we update the `unredeemedShares` field. This essentially tracks how many shares the user owns, but has not yet redeemed.

```
struct DepositReceipt {
	round
	amount
	unredeemedShares
}
```

1. We create the DepositReceipt with the new details.
2. At `rollToNextOption`, the vault will mint all the shares that are owed to users to `address(this)`. This increments the `vaultState.round`.
3. Since the round is concluded, the user's vault shares should show up by calling `RibbonVault.shares(account)`

The end result:

* Their shares show up automatically once the round concludes.
* `DepositReceipt`s are used to track all the user's unredeemed shares. This is used for withdrawals and redemptions in the future.

## Withdrawal Flow

IMPORTANT: this is a _technical_ explanation, if you need assistance on making a withdrawal please refer to [this page](how-to-withdraw.md)!

<figure><img src="../.gitbook/assets/Ribbon_v2_(5).png" alt=""><figcaption></figcaption></figure>

The withdrawal flow is slightly more involved. We have two types of withdrawals - Standard and Instant withdrawals.

### **Standard withdrawals**

* Withdrawals are created with the `initiateWithdraw` function, which queues the shares to be burned.
* Withdrawals are completed with `completeWithdraw` function, which burns the shares, and returns the assets.
* Users can only call `completeWithdraw` only AFTER the week's Friday 10am UTC. For example, the user calls `initiateWithdraw` on Wednesday. They can only complete the withdrawal after the same week's Friday 10am UTC.
* Withdrawals stack on top of each other. This means that if I do `initiateWithdraw(10)`, and I do `initiateWithdraw(20)` again, I will have a total withdrawal of 30 shares by Friday.

### **Instant withdrawals**

* Instant withdrawals are only accessible to funds that are deposited mid-week.
* For example, user deposits 10 ETH into TV on Wednesday. They can call `withdrawInstantly` to return up to 10 ETH, from Wednesday till Friday.

## Share Redemption Flow

IMPORTANT: this is a _technical_ explanation, if you need assistance on redeeming your vault shares please refer to [this page](how-to-transfer-vault-positions.md)!

<figure><img src="../.gitbook/assets/Ribbon_v2_(7).png" alt=""><figcaption></figcaption></figure>

As mentioned before, when the user deposits into the vault, the vault mints and holds custody of the user's shares on `address(this)`. This is not ideal for protocols or Meta-Vaults that want to hold custody of their shares. By calling the `redeem` or `maxRedeem` function, contracts are able to take custody of their vault shares.

The share redemption flow is also triggered implicitly when users call `initiateWithdraw`.

## Access Control

| Name  | Privileges                                                                                                                                                                                                                                          |
| ----- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Owner | <p>The owner can set key parameters of the vault such as feeRecipient, performanceFee, managementFee, deposit cap etc.</p><p>Some functions in the vault's lifecycle is only limited to the owner, such as commitAndClose and rollToNextOption.</p> |
| Admin | The admin can upgrade the proxy's implementation address.                                                                                                                                                                                           |

Both of these privileged roles use a Gnosis Safe multisig wallet.
