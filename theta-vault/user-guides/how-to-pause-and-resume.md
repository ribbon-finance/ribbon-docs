# How to pause and resume

In this guide you will find instructions for pausing and resuming your vault positions. If while following these instructions you encounter any difficulties or errors, we are at your disposal in our [Discord](https://www.google.com/url?q=https://discord.gg/rm7h9ce3ep\&sa=D\&source=editors\&ust=1662913972973504\&usg=AOvVaw1wksdZ9YIQLZTjXYbta2UF) server Support channel.

Putting positions on pause will signal the vault not to use your funds actively starting the following week. This is something you must keep in mind: during the week you pause you will still be subject to the week's profits or losses. So it is important to determine whether or not to pause a week in advance.

Once you pause your funds, you will not be able to resume them until the following week; so the resume button won’t appear until then.

The pause will never be stopped automatically; you will necessarily have to take action to get your funds active again.

It is not possible to pause staked vault shares, you'll have to unstake first. If you need help, you can refer to [this guide](how-to-stake-unstake-vault-shares-and-claim-rewards.md#h.stqn8ca118g).

If after pausing your funds you wish to withdraw them, you'll have to resume first. Then you will need to make an instant withdrawal; if you need assistance with this last step, take a look [here](how-to-withdraw.md#h.ig30e2hrjp4j).

## Connect your wallet <a href="#h.hf5hlm9dkqrg" id="h.hf5hlm9dkqrg"></a>

Please refer to the first section of [this guide](how-to-deposit.md#connect-your-wallet) if you need help connecting your wallet.

## Pause <a href="#h.ig30e2hrjp4j" id="h.ig30e2hrjp4j"></a>

Select the vault in which you deposited, and if your vault shares are not staked, you will notice the presence of the "PAUSE" button right near your position bar at the bottom (desktop and mobile).

<figure><img src="../../.gitbook/assets/image6 (4)" alt=""><figcaption></figcaption></figure>

![](<../../.gitbook/assets/image1 (6)>)

By selecting it, a card will appear for confirmation. Just confirm the transaction in your wallet.

![](<../../.gitbook/assets/image3 (5)>)

After the transaction has been confirmed onchain, a notification will appear in the upper section. Your funds are now paused, so the vault will put them on hold starting from the following Friday.

![](<../../.gitbook/assets/image9 (6)>)![](<../../.gitbook/assets/image8 (3)>)

## Resume <a href="#h.stqn8ca118g" id="h.stqn8ca118g"></a>

Select the vault in which you deposited and in which you paused funds. You will notice the presence of the "RESUME" button right near your position bar at the bottom (desktop and mobile).

<figure><img src="../../.gitbook/assets/image10 (1)" alt=""><figcaption></figcaption></figure>

![](<../../.gitbook/assets/image2 (4)>)

Select it and confirm the transaction in your wallet.

![](<../../.gitbook/assets/image7 (3)>)![](<../../.gitbook/assets/image12 (5)>)

After the transaction has been confirmed onchain, a notification will appear in the upper section as usual. Your funds are now resumed, so the vault will use them again starting from the following Friday.

In case you want to withdraw, you will have until Friday 8 am UTC to make an instant withdrawal. After that time, you will have to proceed with a standard withdrawal.  Again, if you need assistance with these last steps, have a look [here](how-to-withdraw.md#h.ig30e2hrjp4j).

<figure><img src="../../.gitbook/assets/image5 (6)" alt=""><figcaption></figcaption></figure>

## (optional) Pause on Etherscan <a href="#h.ejzcwg4bex7m" id="h.ejzcwg4bex7m"></a>

You can also pause via Etherscan/Snowtrace. These steps are not possible for vaults on Solana.

Go to the Etherscan/Snowtrace page of the vault in which you deposited (you will find the links in the vault cards) and select the "contract" tab, then "write as proxy" and finally connect your wallet.

![](<../../.gitbook/assets/image11 (5)>)![](<../../.gitbook/assets/image14 (3)>)

Select the function "pausePosition" and select write.

![](<../../.gitbook/assets/image13 (4)>)

## (optional) Resume on Etherscan <a href="#h.98p7u0fs35v0" id="h.98p7u0fs35v0"></a>

You can resume your position via Etherscan/Snowtrace. These steps are not possible for vaults on Solana.

Go to these addresses:

* Etherscan: [https://etherscan.io/address/0xe04e8ae290965ad4f7e40c68041c493d2e89cdc3#writeContract](https://www.google.com/url?q=https://etherscan.io/address/0xe04e8ae290965ad4f7e40c68041c493d2e89cdc3%23writeContract\&sa=D\&source=editors\&ust=1662913972979079\&usg=AOvVaw15ysZuzJchavgejtb\_dmwd)
* Snowtrace: [https://snowtrace.io/address/0xf08d6a9c2c5a2dc9b8645c5ac0b529d4046d19aa#writeContract](https://www.google.com/url?q=https://snowtrace.io/address/0xf08d6a9c2c5a2dc9b8645c5ac0b529d4046d19aa%23writeContract\&sa=D\&source=editors\&ust=1662913972979528\&usg=AOvVaw0QE6H0zVAxu8BFYMykL0GX)

From the contract tab select “Write as proxy”, connect your wallet and select the function n. 5, “resumePosition”. Paste the vault address and select “Write”.

![](<../../.gitbook/assets/image4 (3)>)
