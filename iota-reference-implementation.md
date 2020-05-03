# Iota Reference Implementation
The IRI is a OSS for the IOTA protocol that runs on nodes of the public IOTA network, 
where clients can transfer IOTA tokens among each other.

IRI Nodes are the core of an IOTA network, and are responsible for the following functions:
- Validate transactions
- Store valid transactions in a ledger
 Allow clients to interact with their transactions appended to the ledger
 
Other techinical notes:
 - Written in Java
 - Requires a coordinator
 
 **Limitations:**
IRI receives transactions and records them in a ledger. it doesn't create or sign them. 
To create and sign them you must use client software such as Trintiy or a client library
 and send the transactions to the IRI node.
 
 ## Local Snapshots
 
 - Allows for faster node bootstrap 
 - Disk requirements massively reduced  (some nodes with < 1GB Disk )
 - Handle thousands of transactions per second without db size becoming a problem.
 
 ### How does it work?
 - Choose a confirmed transaction that is sufficiently old and use as anchor to the local snapshot.
 - Persist the balances affected by the cleanup in a local snapshot file which will be used by IRI as a new starting point.
 - Prune all transactions that are directly or indirectly referenced by this transaction and clean up
 the db accordingly.


## Transaction Validation

 When the IRI node receives a new transaction it checks it for:
 - Proof of Work was done
 - Value of any transaction in the bundle doesn't exceed the total global supply
 - Transaction is not older than the last snapshot and not newer than 2h ahead of the node's current time.
 - The last trit of an address is 0 for value transactions
 
 
## Bundle Validator

The bundle validator makes sure that all transactions in a bundle are valid.
During a weighted random walk, the bundle validator checks the bundle of transactions for the following:
- The value of any transaction in the bundle doesn’t exceed the total global supply
- The total value of all transactions in the bundle is 0 (all IOTA tokens that are withdrawn are also deposited into other addresses)
- Any signatures in value transactions are valid

## Ledger validator

The ledger validator makes sure that double spends are never confirmed.
During a weighted random walk, the ledger validator checks that each bundle does not 
lead to a double-spend by checking the values of all addresses in a bundle. 
If a double spend is found, the weighted random walk steps back one transaction 
and finds another route to a tip transaction.


## Validator conditions

A transaction is considered invalid if any of the following occur:
- It is not solid and we cannot reconstruct its state, since a portion of the Tangle that this transaction references is unknown.
- It references a transaction that's too far in the past, namely beyond latestSolidMilestone - maxDepth.
- The ledger state is not consistent, such as trying to withdraw or deposit missing funds or double-spending.
- The validator maintains a list of transactions that have been checked for validity. Every time a new transaction is validated, it is also checked against these.