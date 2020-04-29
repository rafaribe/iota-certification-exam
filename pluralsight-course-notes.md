
# Basics  
  
What a ledger is?  
  
Starting balances and transactions - like a bank!  
  
Characteristics:  
- Accessible  
- Non-stoppable  
- Verifiable  
  
Usage Scenario:  
- Transportations  
- Sensor Data  
- IOT  
  
# Different between IOTA and Blockchain:  
  
Blockchain keeps the initial balance + transactions since the beginning of time.   
And every new participant (node) needs to have a copy of this.  
Currently about 165GB o data.  
IOTA uses snapshots which allows the same outcome in a leaner way.  
  
Blockchain needs miners. IOTA users verify 2 past transactions when they issue a new one. This eliminates transaction fees.  
  
  
# Directed Acyclic Graph (DAG)  
  
1 new transaction validates 2 past transactions.  
  
  
## Proof of work  
  
Avoids spamming. Not like blockchain, even simple devices can use it. You need to do some computational work.  
The workload is big enough to prevent spam.  
  
## Tips:  
  
Unconfirmed Transactions  
They can be traced to the root  
  
## Addresses and Keys (Seed)  
  
Addresses and Seeds: Long strings that consist of letters from A-Z and number 9  
  
## Making a transaction  
  
Sign using PK  
Tip Selection and Confirm 2 prev. transactions  
Do the proof of work and then it is ready to be confirmed  
  
## The coordinator  
  
Centralized Node to protect the tangle from attacks such as parasite chains.  Nodes use the coordinator to reach a consensus on which transactions are confirmed.  
It's just another node that will be switched off once the network grows.  
  
The Coordinator is a program that regularly sends bundles that reference and approve two new random transactions in the ledger. The signed tail transaction in the bundle is called a milestone.  
  
### Milestones  
Every node in the same IOTA Network is hard-coded with the address of a coordinator. So wherever nodes see a milestone, they make sure it's valid by doing several checks like:  
- The milestone came from the coordinator address  
- The milestone doesn't reference any invalid transactions  
  
When a transaction in a valid milestone references an existing transaction in the tangle, nodes mark the state of that existing transaction and its entire history as confirmed.  
  
### Buying IOTA  
  
- Exchanges: You can buy iota in exchanges by trading iota  
- Coinbase.com  
  
# Deep dive:  
  
## Denominations:  
  
i  - iota  
ki - 1000 i  
Mi - 1000 ki (Used on exchnage)  
Gi - 1000 Mi  
Ti - 1000 Gi  
Pi - 1000 Ti  
  
All amount of iota that will ever exist is already created and amounts to about 2.8Ti  
  
## Hashing:  
Create a mathematical algorithm that outputs result a result with a given length regardless of input   
One-way function. Only return the same result on the same input, cannot get input based on output.  
  
The algorithms are publicly available and are usually fast to compute values.  
  
IOTA uses **KECCAK-384**:  
- Based on an approach called on Sponge construction  
- Quantum resistance  
  
  
## Trinary System:  
  
-1 , 0 , 1  
  
In binary we have bits, in trinary we have trits.  
  
In binary, we have bytes in trinary we have trytes.  
  
Efficient for new processors.  
  
When converting a tryte to a character, you end up getting A-Z and number 9: Total combinations: 27  
(Used for seeds an addresses)  
  
Trytes are calculated left to right, not right to left as with binary.  
  
### Tryte alphabet  
  
- Human Readable   
- 26 letters and the number 9  
- 27 different combinations = 1 tryte  
  
Example:  
  
0,0,0 = 9  
  
1,0,0 = A  
  
-1,0,0= B  
  
# Seed:  
  
Combined username and password  
Each seed has 81 Trytes  
String A-Z and 9 with 81 characters.  
  
Combinations: 8,7X10^1115 Combinations 😅  
Main purposes: Generating addresses for sending and receiving transactions.  
  
## Generating seeds:  
 - Script-based generation  
 - Online generators (CAREFUL with this)  
  ## Randomizers:  
How does proper randomizer work?  
  
- Takes in some entropy: Random network traffic, mouse movement, temperature, etc.  
- Entropy to a Cryptographic Secure Sudo Graphic random number generator  
- This produces a random number  
  
# IOTA Addresses:  
- Receive many, Send once  
- Acts as a Public Key  
- Quantum Resistant  
  
## Generating Addresses:  
  
- Index (starts at 0)  
- Seed  
- Security Setting  
  
## Reuse of Addresses   
- Shares 50% of PK  
- Each time the address is less and less save  
  
  
## Transaction Bundles  
  
If we cannot re-use address we use transaction bundles  
  
- Transaction info  
- Bundle Reference  
- Index  
  
## Attaching to tangle  
  
  
### Snapshots  
  
- Announced  
-  
  
#Transactions  
## Validated:  
  
- Random Walk Monte Carlo (RWMC) to select random transactions.  
- Calculate how many of the new transactions are tips  
- If less than 50% not validated  
- If more than 50% high probability to be validated  
- If 99% or transactions are validated directly or indirectly the transaction is considered validated.  
  
## Tag and Message  
Add meta info: Tag and Message.  
Everyone can view the tag and message, so probably a good idea to encrypt the messages.  
  
  
# IOTA API  
  
Reached in two ways:  
  
- REST API = HTTP REQ WITH JSON OBJECTS  
- Client Libraries: Makes it easier to work with IOTA  
  
  
## IOTA NODES HTTPS API  
  
Production Network: Mainnet => Connect to a node  
  
Testnet => Testnet for testing  
  
PoWbox => Service that does the proof of work remotely for you  
  
  
## Iota Client Libraries:  
  
- Javascript (more mature)  
- Java  
- C# (Community Based)  
- Go  
- Python