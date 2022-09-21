# Lecture 3: Cryptography Primitives & Data Structures

The main goal of this lecture is to introduce students to merkalised storage solutions and how they are used in the context of data verification.

## Problem to address

Consider a modern NoSQL database, such as a key-value storage distributed over several nodes, where the size of the values is arbitrarily large.
- For fault tolerance and load balancing reasons, each key-value pair is replicated over more nodes. 
- Over time, nodes fail and may recover or not, and new nodes can be added -> data inconsistencies may arise.
- A re-synch mechanism is therefore required to restore data consistency.
> Given the extremely large size of stored data (in the order of TBs, at the very least), how can we efficiently identify out-of-synch key-value entries?

_This problem is also highly relevant to blockchain, since the ledger of transactions is replicated over many nodes and is very large (more than 400GB in Bitcoin) and the existence and integrity of a given transaction in the ledger is a common operation to perform_

## Outline

Merkle tree is a data structure that allows to store in a compact way information about the content of a set of data items. This data structure can be efficiently used to perform integrity checks on those data items. This lecture covers the following topics.
- __Tree data structure__. Brief introduction to the basics of trees as data structures.
- __Merkle tree__. What it looks like and how to build one.
- __Using Merkle tree__. How to verify a data item using a Merkle tree.
- __Merkle trees in blockchain__. What is the role of Merkel trees in a blockchain?

## Tree data structure

To understand merkalised storage solutions we need to understand the very basics underneath it.

Topics to cover
- why data structures?
- Tree as a data structure - figure with n-ary tree to introduce basic jargon
- Binary tree - properties
- Example of binary search tree

<!--
> Binary tree is defined as a tree data structure with at most 2 children.

- Max 2 children
- No cycles
- No duplicates
- Greater number goes to the left, smaller number goes to the left


### Complexity for perfectly balances binary tree
- Search complexity: `O(log n)`
- Insert complexity: `O(log n)`
- Delete complexity: `O(log n)`
-->

E.g., for a balanced binary tree with 64 elements, it would take at most 8 steps to search an element.


## Merkle tree

Binary Merkle tree is a combination of hash function and binary tree.

![](https://upload.wikimedia.org/wikipedia/commons/thumb/9/95/Hash_Tree.svg/620px-Hash_Tree.svg.png)

Instead of inserting a value instead, the hash of data is inserted.
Binary Merkle tree is very useful when we need to verify an integrity of data.

To create a merkle tree:
1. Split data into equal chunks
2. Hash each chunk of data
3. Combine hashes into pairs and hash those pairs into another hashes
4. Repeat previous step until you are left with just 2 hashes
5. Calculate the root of a tree

Essentially, merkle tree allows us to verify the very big chunk of data and even find the point where the data might corrupted.

If we want to verify that some chunk of data is part of the whole data (e.g. we want to verify that "Hello" is indeed in "Hello World" sentence),
we can only need half of hashes to be known.

If we want to change any piece of data, the root must be recalculated.

## Using Merkle tree

Topics to cover
- example to show how to use a Merkle tree to verify a data item
- generalise operation
- discussion on time and space complexity

## Merkle trees in blockchain

Topics to cover (very briefly)
- blocks and transactions
- verify a transaction using Merkle tree

<!--
### Uses
- IPFS for data storage verification and Distributed Hash Tables
- Databases for data integrity
- Blockchain, blocks data is encoded using merkle tree, the header usually stores the root
-->

## Workshop

TODO!
