# Ribbon Factory

The RibbonFactory contract is a factory contract used to deploy new instances of instrument contracts. It is a ProxyFactory which deploys proxies of Instruments and keeps the records of all deployed instruments.

The RibbonFactory is also the Swiss Army knife of Ribbon. It also has a few key functionalities such as:

* Storing deployed instrument addresses
* Storing Adapter addresses

## API

#### `initialize(address _owner, address _instrumentAdmin)` \(public\)

Constructor that takes the owner address and the admin for the AdminUpgradeabilityProxy instances.

#### `getInstrument(string _name) → address instrumentAddress` \(public\)

Getter for getting contract address by instrument name.

#### `newInstrument(address _logic, bytes _initData) → address instrumentAddress` \(public\)

Deploys a new instrument. This is currently only limited to the owner.

**Parameters:**

* `_logic`: address of the logic contract of the instrument
* `_initData`: encoded call data for the `initialize` function for the instrument contract

#### `setAdapter(string protocolName, address adapter)` \(public\)

**Parameters:**

* `_logic`: address of the logic contract of the instrument
* `_initData`: encoded call data for the `initialize` function for the instrument contract

#### `getAdapters() → address[] _adapters` \(external\)

Returns an array of deployed instruments.

