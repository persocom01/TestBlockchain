This document attempt to clarify some of the background and reasons why to use blockchain technology.

1. Why blockchain.
The need for blockchain arises due to the need to authenticate that a transaction is unique. In the case of digital currencies, this problem is known as the **double spending** problem, since digital money, which is just binary data, can be replicated and used endlessly if there is no way to verify that each transaction in which it is used is unique.

One way to do this is to use a trusted 3rd party to verify the transaction. This normally means a bank. However, this also means the bank can take a cut of every transaction.

2. What is blockchain.
It is a distributed ledger that records all the transactions that take place on the network. Once a transaction request is made, it is broadcasted to all nodes in the entire network. Note that it is not necessary for it to reach all nodes. Blockchain technology is sometimes called Distributed Ledger Technologies (DLT) instead.

To maintain anonymity, only the public key of the receiver of the transaction is recorded. To identify the receiver, the key has to be tied to the identity of the receiver, but it is not recorded in the ledger. Keys can be regenerated for every transaction to make it seem like the receivers are different for each transaction.

Multiple transactions are combined with the hash of the previous block, a timestamp and a nonce, before being used to produce a new hash. The introduction of the hash from the previous block is what makes this block part of a chain, and the timestamp helps ensure the block cannot be tampered with without invalidating the hash.

Essential to any blockchain is a nonce. A nonce is an arbitrary, unique number that is used to prevent replay attacks. The entire transaction, including the nonce, is cryptographically signed with the sender's private key, thus proving to a miner that the transaction's sender was in possession of the private key. What constitutes a nonce is dependent on the blockchain. In Bitcoin, the nonce is a 32-bit field whose value is adjusted by miners so that the hash of the block will be less than or equal to the current target of the network, the target difficulty being automatically adjusted so that moving average of block discovery intervals will equal a certain pace (10min for bitcoin). Finding the correct nonce is considered proof of work, and the miner who finds it is awarded the block and bitcoin. In Ethereum, the nonce is simply the transaction number.

Proof of work is the evidence required by public blockchains to allow a node to add a block to the ledger. This purposely raises the bar for participation in ledger writing so that certain service attacks such as spam are difficult to execute. It is necessary in untrusted, public networks as a kind of security measure to ensure nodes have some skin in the game. In bitcoin, proof of work constitutes finding the correct nonce, which requires significant computing power.

When a valid block is assembled by a node, the block is broadcasted to the network. Other miners that receive the new block will accept it only after verifying that all transactions in the block are valid and not already spent.

Once the new block is accepted, the node which is working on its own new block will have to re-assemble the transactions in its block ensuring that the transactions are not duplicated.

It is possible that two nodes add a block to the chain at the same time. In this case, whichever chain ends up longer is accepted and the other chain is purged, and its transactions returned to the pool.

3. Challenges of blockchain.
a. Ledger must be tamper proof.
b. how to maintain anonymity.
c. size of ledger.

4. Public Key Cryptography (PKI)
Also known as asymmetric cryptography. It uses two pairs of keys - public and private. A key is a some long binary number. The public key is distributed worldwide and is truly public as its name suggests. The private key is to be strictly held private and one should never lose it. The most popular PKI algorithms are RSA and ECDSA, Bitcoin uses the latter one.

One of the most important function in PKI is the hashing function. A hash function maps the data of any arbitrary size to data of fixed size. Bitcoin uses SHA-256 hash function that produces a hash (output) of size 256 bits (32 bytes). The beauty of this hash is that it is unique for the contents of the transaction. Thus if the transaction is modified, the hash would change and become invalid.

5. Types of attacks.
a. race attack.
Occurs when two transactions are attempted at the same time and the transaction is not verified with the nodes before being executed due to the time it takes to build a block.
b. finney attack.
A node can include a transaction to an account it controls as a block, and use it to override a transaction that it wants to make, by not releasing the former as a block until the latter is executed, and then releasing the former to invalidate the latter as a duplicate.
c. reorganizations attack.
A node can mine a series of blocks as an alternate version of history that it does not release until the transaction is made. It then attempts to make this alternative history the true history by making it longest legitimate blockchain at the time. Technically, if this is done with the attacker controlling at least 51% of the computing power among the nodes, he can always make a false history true, given enough time.

6. Blockchain technologies.
a. Ethereum.
Runs Smart Contracts on the Ethereum Virtual Machine (EVM) for applications that are attributed to being decentralized and are for mass consumption.
b. Hyperledger.
Blockchain technology for business. It is designed to support pluggable implementations of components delivering high degrees of confidentiality, resilience and scalability. Hyperledger has a modular architecture and provides a lot of flexibility in how you want to use it.
