# Merkle trees

Merkle trees are trees in which every non-leaf node is labelled with a hash of the labels or values of its child nodes.

Hashed trees allow fast abd safe verification of the contents of large structures.

## Uses

Merkle trees can be used anywhere, but are popular in:

* P2P networks where one needs to make sure the data blocks received are safe and undamaged
* File systems (IPFS, ZSF)
* Git

## Overview

A hash tree is a tree of hashes in which the leaves are hashes of data blocks. Nodes up the tree are hashes of their children. One branch of the tree can be downloaded at a time and the integrity of each can be checked immediately regardless of the status of hte rest of the tree.

## More info

https://en.wikipedia.org/wiki/Merkle_tree
