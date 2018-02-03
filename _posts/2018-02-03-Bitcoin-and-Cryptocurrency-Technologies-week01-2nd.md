---
layout: post
title: Hash Pointers and Data Structures
---
# hash-pointers-and-data-structures

## hash pointer

- pointer to where some info is stored and (cryptographic) hash of the info
  哈希指针是一段数据的哈希值，并可以指向这段存储数据的地址

- having a hash pointer, we can ask to get the info back and verify that it hasn't changed
  由哈希指针，我们可以获得存储的数据，并且验证数据未改变

![My helpful screenshot]({{ "/assets/2018-02-03-Bitcoin-and-Cryptocurrency-Technologies-week01-2nd-img01.png" | absolute_url }})

通过 H(x) = y 的关系，其实可以理解为 哈希值y指向了存储的数值x.

## data structures

- 基于哈希指针的链表 (BlockChain)

![My helpful screenshot]({{ "/assets/2018-02-03-Bitcoin-and-Cryptocurrency-Technologies-week01-2nd-img02.png" | absolute_url }})

与普通指针链表相似, 链表由很多区块组成。不同的是，每个数据块除了包含了本块存储的数据，还包含了指向上一个区块(同样包含指针和数据两部分)的哈希指针。 这样可以用来检测对区块的恶意修改，确保了链中任意一个区块的数据被更改，其后的所有数据块都会mismatch(hash值改变)，除非重新计算和写入其后所有的区块直到链尾。

- 基于哈希指针的二叉树 (Merkle tree)

![My helpful screenshot]({{ "/assets/2018-02-03-Bitcoin-and-Cryptocurrency-Technologies-week01-2nd-img03.png" | absolute_url }})

- 改变底层节点data的值，同样需要改变其上所有节点的值直到root。
- 检索(verification)节点快速，复杂度 show O(log n) items

![My helpful screenshot]({{ "/assets/2018-02-03-Bitcoin-and-Cryptocurrency-Technologies-week01-2nd-img04.png" | absolute_url }})

- 优点： Tree  holds many items, but just need to remember the root hash. Can verify membership in O(log n) time/space
- sorted Merkle tree can verify non-membership

Hash pointer can be used in any pointer-based data structure that has no cycles.

推荐阅读： [Merkle Tree 概念](http://www.cnblogs.com/fengzhiwu/p/5524324.html)

Blockchain Demo: <https://anders.com/blockchain/blockchain.html>