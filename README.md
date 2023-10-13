# DbContract

This Rust smart contract, `DbContract`, is designed to facilitate the management of a decentralized database, `SamaritanDB`. The contract uses the Ink! framework to handle various operations related to network nodes, accounts, access control, and subscriptions.

## Table of Contents

- [Contract Overview](#contract-overview)
- [Data Structures](#data-structures)
- [Contract Functions](#contract-functions)
- [Testing](#testing)
- [License](#license)

## Contract Overview

Samaritan OS relies on a decentralized database, and `DbContract` acts as the core contract responsible for managing various aspects of the database. Here's an overview of its key features:

- **Database Account Management**: Users can create accounts with their Decentralized Identifiers (DID) and associate data with these accounts.

- **Node Address Management**: This contract keeps track of network node addresses, specifically bootnodes. The list of nodes is limited to ensure efficiency and reliability.

- **Subscription Management**: Users can subscribe to nodes that support specific applications.

- **Access Control**: The contract provides restricted access control, allowing or denying specific applications access to data based on DID.

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

- `restrict`: Add an application to the restricted list, limiting its data access.

- `unrestrict`: Remove an application from the restricted list, allowing its data access.

## Testing

The contract includes a set of tests to ensure that its functions work as expected. The tests cover account creation, subscription flow, and adding/removing node addresses.

## License

This contract is released under the [Apache License 2.0](LICENSE). Feel free to use and modify it in your projects.

For detailed usage instructions and more information about the contract, please refer to the inline comments within the code.

For any questions or issues, please contact [Algorealm, Inc](https://www.algorealm.com/).

