# Instrument Contracts

Instrument contracts are financial contracts that have an expiry date. Using the example of a Strangle, the Instrument contract constructs a strangle position by buying a put and call position on behalf of the user.

![Flow chart for an Instrument contract](../../.gitbook/assets/instrument-flowchart%20%281%29.png)

When a user makes a function call to an Instrument contract, it 



The ProtocolAdapter contracts are called with [delegatecalls](https://medium.com/coinmonks/delegatecall-calling-another-contract-function-in-solidity-b579f804178c). This means that each Instrument contract is calling the function of the Protocol Adapter, but using its own storage. When an Instrument calls `HegicAdapter.purchase`, the `msg.sender` in the Hegic function call would be the Instrument, not the HegicAdapter itself.

This solves a few key problems:

* State is stored on Instrument contracts, not the Adapter contracts. For example, this means that we do not hold ALL of Ribbon's Hegic positions on the HegicAdapter contract.
* Adapter contracts are designed as pass-throughs, and do not hold any state. This is better from a security perspective.



