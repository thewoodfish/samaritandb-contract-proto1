# DbContract

This Rust smart contract, `DbContract`, is designed to facilitate the management of a decentralized database, `SamaritanDB`. SamaritanDB is a blockchain-based data sovereignty solution that empowers users to have full control over their data input into applications across the internet running on the database. This repository contains the core contract that underpins SamaritanDB. The contract uses the ink! smart contract language to handle various operations related to network nodes, accounts, access control, and subscriptions.

## Table of Contents

- [About](#about)
- [Usage](#usage)
- [Contract Overview](#contract-overview)
- [Data Structures](#data-structures)
- [Contract Events](#contract-events)
- [Contract Functions](#contract-functions)
- [Testing](#testing)
- [License](#license)

## About

This repository hosts the core smart contract of SamaritanDB, a revolutionary data sovereignty solution. Users can interact with the contract to create accounts, manage data access, and more. The contract is built using ink! and deployed on the Rococo Contract Testnet to ensure data control and ownership.

## Contract Overview

The `DbContract` serves as the central hub and primary source of authority for governing various aspects of the database. Below is an overview of its pivotal functionalities:

- **Database Account Management**: Users have the ability to establish accounts using their Decentralized Identifiers (DID) and link data to these accounts.

- **Node Address Management:** This contract is responsible for maintaining a record of network node addresses, especially bootnodes. Currently, the node list is capped to ensure optimal performance and reliability. It's worth noting that this capability will be phased out from the contract in the future.

- **Subscription Management:** Databases have the ability to individually subscribe to nodes that support specific applications, effectively becoming data providers for those applications. This subscription mechanism is utilized in `gossipsub` and is facilitated by the contract. However, please be aware that it will eventually be deprecated from the contract.

- **Access Control**: Access control is a fundamental feature of the contract. It empowers the contract to oversee and regulate access permissions, granting or denying specific applications access to distinct user data distributed across the network, all based on the unique DID identifiers.

## Data Structures

The contract defines several custom data structures:

- `AccountInfo`: Stores information about user accounts, including DID, CID, and authentication materials.

- `Multiaddr`: Represents a network address.

- `DID`: Represents a Decentralized Identifier.

- `CID`: Represents an IPFS content identifier.

## Contract Events

- **AccountCreated:**

  - Emits when a new account is created on the network.
  - Parameters:
    - `did`: Decentralized Identifier (DID) of the created account.

- **BootNodeAdded:**

  - Emits when a bootnode is added to the network.
  - Parameters:
    - `address`: The address of the added bootnode.

- **BootNodeRemoved:**

  - Emits when a bootnode is removed from the network.
  - Parameters:
    - `address`: The address of the removed bootnode.

- **HashTableAddressUpdated:**

  - Emits when the IPFS address for an account's hash table is updated.
  - Parameters:
    - `did`: The Decentralized Identifier (DID) associated with the account.
    - `ipfs_address`: The updated IPFS content identifier (CID).

- **EntryNotFound:**

  - Emits when a requested entry is not found.
  - Parameters:
    - `entry_value`: The value of the entry that was not found.

- **TopicSubscriptionComplete:**

  - Emits when the subscription to a topic is successfully completed.
  - Parameters:
    - `did`: The Decentralized Identifier (DID) of the subscribing user or application.
    - `node`: The address of the node where the topic was subscribed.

- **TopicUnsubscriptionComplete:**

  - Emits when the unsubscription from a topic is successfully completed.
  - Parameters:
    - `did`: The Decentralized Identifier (DID) of the unsubscribing user or application.
    - `node`: The address of the node from which the unsubscription occurred.

- **RestrictApplicationAccess:**

  - Emits when a user restricts access to an application.
  - Parameters:
    - `user_did`: The Decentralized Identifier (DID) of the user.
    - `application_did`: The Decentralized Identifier (DID) of the restricted application.

- **UnrestrictApplicationAccess:**
  - Emits when a user lifts access restrictions from an application.
  - Parameters:
    - `user_did`: The Decentralized Identifier (DID) of the user.
    - `application_did`: The Decentralized Identifier (DID) of the unrestricted application.

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

- **`get_restriction_list`**: Retrieves a list of users who have restricted access to a specific application. The `DbContract` smart contract utilizes this function to provide transparency about access restrictions.

    - **Parameters**

    - `app_did` (Decentralized Identifier): The Decentralized Identifier (DID) of the application for which you want to retrieve the list of restricted users.

    - **Return Value**

    - `Vec<u8>`: A byte vector containing the list of restricted users' Decentralized Identifiers (DIDs) separated by a delimiter. Each user's DID is followed by `$$$` as a separator.

    - **Usage**

    - When calling this function, provide the `app_did` as a parameter, which represents the application you're interested in.
    - If the application has restricted access from users, the function will return a `Vec<u8>` containing the DIDs of those restricted users. The DIDs are separated by `$$$`.
    - If no users have restricted access to the application or the application is not found, an empty `Vec<u8>` is returned.

    This function is a valuable tool for querying the list of users who have restricted access to an application on the SamaritanDB network.

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
