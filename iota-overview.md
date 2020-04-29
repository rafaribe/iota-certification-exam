# Overview

## Why should I use IOTA

- Authenticity: Prove that you sent data and/or own IOTA tokens
- Integrity: Prove that your data is unchanged
- Confidentiality: Control who has access to your data through encryption
- Micropayments: Send small amounts of IOTA tokens without paying any fees.

### Trust in Data
Each note in an IOTA Network validates transactions, then sends them to other nodes that do the same. As a result all valid transactions are agreed on by all nodes, removing the need to trust a single one in the network.

### Integrity

All transactions in the Tangle are immutable and transparent
Each transaction references the transaction hashes of two previous ones. So if the contents of any transaction were to change, the hashes would be invalid, making the transactions invalid.

### Security and privacy

IOTA uses quantum robust (secure even to quantum attacks) one-time signatures to stop attackers from stealing IOTA tokens.

IOTA networks are p2p networks where no central authority controls the Tangle. Instead all nodes hold a copy of it, and reach an consensus on its contents.

### Cost Saving

Iota is free to use.
Transactions are feeless
You can store data in Tangle with no restrictions. All you need is a node to which you can send transactions.

### Scalability

Fro each transaction, two previous ones are validated. This process makes it scalable because more transactions lead to faster validations.


## How does IOTA work?

**Nodes:**
- The only devices with read and write access to be the immutable record of transactions called the Tangle

- Interconnected nodes form an IOTA network by running the same node software allowing them to validate transactions and attach them to the Tangle.

**Clients:**

- Clients are the devices that connect to nodes to transact and store data on the Tangle
- All clients in an IOTA network have a secret password called `seed` which acts as their identity. **Seeds** give clients access to addresses.

