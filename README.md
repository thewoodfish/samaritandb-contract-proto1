# DbContract

This Rust smart contract, `DbContract`, is designed to facilitate the management of a decentralized database, `SamaritanDB`. SamaritanDB is a blockchain-based data sovereignty solution that empowers users to have full control over their data input into applications running on SamaritanDB. This repository contains the core contract that underpins SamaritanDB. The contract uses the ink! smart contract language to handle various operations related to network nodes, accounts, access control, and subscriptions.

## Table of Contents

- [About](#about)
- [Usage](#usage)
- [Contract Overview](#contract-overview)
- [Data Structures](#data-structures)
- [Contract Functions](#contract-functions)
- [Testing](#testing)
- [License](#license)

## About

This repository hosts the core smart contract of SamaritanDB, a revolutionary data sovereignty solution. Users can interact with the contract to create accounts, manage data access, and more. The contract is built using Ink! and deployed on the blockchain to ensure data control and ownership.

## Contract Overview

The `DbContract` serves as the central hub and primary source of authority for governing various aspects of the database. Below is an overview of its pivotal functionalities:

- **Database Account Management**: Users have the ability to establish accounts using their Decentralized Identifiers (DID) and link data to these accounts.

- **Node Address Administration**: This contract maintains a record of network node addresses, particularly bootnodes. The node list is currently capped for performance and reliability considerations. Note that this restriction will be removed in the future.

- **Subscription Management**: Databases can individually subscribe to nodes that support specific applications, thereby integrating themselves as data providers for those applications. This subscription mechanism is utilized in `gossipsub` operations and will eventually be deprecated from the contract.

- **Access Control**: Access control is a fundamental feature of the contract. It empowers the contract to oversee and regulate access permissions, granting or denying specific applications access to distinct user data distributed across the network, all based on the unique DID identifiers.

## Data Structures

The contract defines several custom data structures:

- `AccountInfo`: Stores information about user accounts, including DID, CID, and authentication materials.

- `Multiaddr`: Represents a network address.

- `DID`: Represents a Decentralized Identifier.

- `CID`: Represents an IPFS content identifier.

## Contract Functions

The contract offers several functions to interact with its features:

- `new_account`: Create a new user account with DID, CID, and authentication materials.

- `add_address`: Add a network address to the list of nodes (bootnodes).

- `remove_address`: Remove a network address from the list of nodes.

- `get_node_addresses`: Retrieve the list of available node addresses.

- `get_account_ht_cid`: Get the hashtable CID associated with an account.

- `update_account_ht_cid`: Update the hashtable CID of an account.

- `subscribe_node`: Subscribe to join nodes supporting a specific application.

- `unsubscribe_node`: Stop supporting an application and unsubscribe from the associated nodes.

- `get_subscribers`: Get a list of nodes supporting a specific application.

- `restrict`: Add an application to the restricted list, limiting its data access to a specific user data.

- `unrestrict`: Remove an application from the restricted list, allowing its data access.

## Testing

The contract includes a set of unit tests to ensure that its functions work as expected. The tests cover account creation, subscription flow, adding/removing node addresses and managing user data access control.

## Database

For an in-depth analysis of when and how the contract functions are invoked during database operations, please refer to the complete database code available [here](https://github.com/algorealmInc/SamaritanDB).

## Interact

You can interact with the contract publicly here at the [Contracts-UI](https://contracts-ui.substrate.io/contract/5HkCfhUNU1c4UXzxC4WiiyojDbzbH1KMgkHrEw11ez9HAg5y).

## License

This contract is released under the [Apache License 2.0](LICENSE). Feel free to use and modify it in your projects.

For detailed usage instructions and more information about the contract, please refer to the inline comments within the code.

For any questions or issues, please contact [Algorealm, Inc](mailto:hello@algorealm.org) or open a PR.

Merci.
