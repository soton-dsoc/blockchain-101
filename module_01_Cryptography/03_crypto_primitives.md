# Lecture 3: Cryptography Primitives & Data Structures

The main of a lecture is to introduce students to merkalised storage solutions and how they are used in the context of data verification.

## Binary tree

To understand merkalised storage solutions we need to understand the very basics underneath it.

> Binary Tree is defined as a Tree data structure with at most 2 children.

- Max 2 children
- No cycles
- No duplicates
- Greater number goes to the left, smaller number goes to the left


### Complexity for perfectly balances binary tree
- Search complexity: `O(log n)`
- Insert complexity: `O(log n)`
- Delete complexity: `O(log n)`

(i.e.) For a balances binary tree with 64 elements, it would on average take 8 steps to search, insert or delete an element.


## Binary Merkle tree

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

### Uses
- IPFS for data storage verification and Distributed Hash Tables
- Databases for data integrity
- Blockchain, blocks data is encoded using merkle tree, the header usually stores the root

## Workshop

TODO!