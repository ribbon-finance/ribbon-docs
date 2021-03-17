# Ribbon Architecture

## Introduction

Ribbon Finance is a protocol for designing structured products on-chain. Our smart contract architecture is designed to enable developers to create the financial tools of the future. The architecture has the following goals in mind:

* Rapid and secure development of new structured products
* Simple integration of new third-party protocols
* Easy onboarding of new contributors who can work on independent modules

## Components

| Component | Description |
| :--- | :--- |
| [RibbonFactory](ribbon-factory.md) | Factory contract that is used by Ribbon to deploy new instances of an Instrument contract. The factory is used to simplify the deployment of a new Instrument contract, and to track instruments on-chain. |
| [Instruments](instrument-contracts.md) | Contracts with an expiry date which represent a financial instrument. |
| [Protocol Adapters](protocol-adapters.md) | ProtocolAdapters are contracts that Instruments use to talk to third-party protocols such as Hegic and Opyn. More details can be found in the [Protocol Adapters page](protocol-adapters.md). |
| Vaults | Vaults are contracts that hold user funds and construct financial positions on-chain on behalf of the user. These financial positions are automatically rolled over by managers and keepers of the protocol. |



