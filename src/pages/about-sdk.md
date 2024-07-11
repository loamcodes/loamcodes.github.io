&nbsp;

## composable, upgradeable & secure

### Composable

With [Loam SDK](https://crates.io/crates/loam-sdk), you compose your smart contract from many sub contracts. Subcontracts are like lego blocks that you can either use off-the-shelf from the open source ecosystem or that you can build yourself. A single Loam smart contract is composed of one or more subcontracts.

### Upgradeable

The one subcontract that all Loam smart contracts must include (loam-subcontract-core) adds an important method to the smart contract: redeploy. You can call this method to switch the wasm hash—the behavior/brains of the contract—to a new one, while keeping the same contract ID. The storage accessed by each particular subcontract is loaded lazily, so upgrading one subcontract does not require migrating the data of another; each subcontract within your smart contract can be considered and upgraded independently.

### Secure

The core subcontract also adds admin_set and admin_get to your contract, to make sure that only your trusted admin account can call redeploy. Our full loam architecture, beyond Loam SDK, also includes a universal factory contract, which makes it possible to deploy your contract and call admin_set in a single transaction, helping avoid front-running.
