# Ribbon Factory

Ribbon uses the Proxy Factory pattern to deploy new instruments in the protocol. The RibbonFactory has the function `newInstrument` which deploys a new instrument and keeps the record of newly deployed instrument's address.

The factory is also the swiss-army knife of Ribbon, and holds a few different information:

* Instrument addresses
* Adapter addresses
* Gas subsidies from the Ribbon team

