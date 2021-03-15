# Overview

## Introduction

Ribbon Finance is a protocol for designing structured products on-chain. Our smart contract architecture is designed to enable developers to create the financial tools of the future. The architecture has the following goals:

* Rapid and secure development of new financial instruments
* Simple integration of new third-party protocols
* Easy onboarding of new contributors who can work on independent modules

## Glossary

* **RibbonFactory** - RibbonFactory is the factory contract that is used by Ribbon to deploy new instances of an Instrument contract. The factory is used to simplify the deployment of a new Instrument contract, and to track instruments on-chain.
* **Instruments** - Instruments are contracts with an expiry date which represent a financial instrument.
* **ProtocolAdapters** - ProtocolAdapters are contracts that Instruments use to talk to third-party protocols such as Hegic and Opyn. More details can be found in the [Protocol Adapters page](protocol-adapters.md).
* **Vaults** - Vaults are contracts that hold user funds and construct financial positions on-chain on behalf of the user. These financial positions are automatically rolled over by managers and keepers of the protocol.

## Ribbon Factory



## Instrument Contracts

Instrument contracts are financial contracts that have an expiry date. Using the example of a Strangle, the Instrument contract constructs a strangle position by buying a put and call position on behalf of the user.

![Flow chart for an Instrument contract](../../.gitbook/assets/instrument-flowchart%20%281%29.png)

The ProtocolAdapter contracts are called with [delegatecalls](https://medium.com/coinmonks/delegatecall-calling-another-contract-function-in-solidity-b579f804178c). This means that each Instrument contract is calling the function of the Protocol Adapter, but using its own storage. This means that when an Instrument calls `HegicAdapter.purchase`, the `msg.sender` would be the Instrument, not the HegicAdapter itself.

This solves a few key problems:

* State is stored on Instrument contracts, not the Adapter contracts. For example, this means that we do not hold ALL of Ribbon's Hegic positions on the HegicAdapter contract.
* Adapter contracts are designed as pass-throughs, and do not hold any state. This is better from a security perspective.

## Vaults

