---
layout: post
title: Digital Signatures and Public Keys as Identities
---
# Digital Signatures and Public Keys as Identities

## Digital Signatures

- **签名**，那肯定是不希望有人冒充我发消息，只有我才能发布这个签名，所以可得出私钥负责签名，公钥负责验证
- **加密**，那肯定是不希望别人知道我的消息，所以只有我才能解密，所以可得出公钥负责加密，私钥负责解密

[RSA的公钥和私钥到底哪个才是用来加密和哪个用来解密？ - 知乎](https://www.zhihu.com/question/25912483/answer/46649199)

![My helpful screenshot]({{ "/assets/2018-02-03-Bitcoin-and-Cryptocurrency-Technologies-week01-3rd-img01.png" | absolute_url }})

## Pratical stuff

- **algorithms are randomized**
  生成私钥和公钥的算法需随机, good randomness is essential. foul this up in generateKeys() or sign() probably leaked your private key.

- limit on message size
  use Hash(msg) rather than msg. 对哈希值签名

- sign a hash pointer
  signature "covers" the whole structure. 对哈希指针签名

- Bitcoin uses ECDSA 椭圆曲线签名算法

## Public Keys as Identities

- Useful trick: public key == an identity (用公钥作为身份)

  if you see sig such that verify(pk, msg, sig) == true, think of it as pk says, "[msg]"
  如果一个带有前面的消息可以被pk来验证，那么可以认为消息来自pk, 或者pk说: msg

- How to make a new identity? (如何创建一个身份)

  create a new, random key-pair (sk, pk)
  - pk is the public "name" you can use [usually better to use Hash(pk)] pk就是在系统中向外公布的"姓名"，一般选择pk的哈希值(固定长度)
  - sk lets you "speak for" the identity. sk则允许你用这个身份发言

- Decentralized identity management (去中心化的身份管理)

  anybody can make a new identity at any time (make as many as you want) 按照上面的方法，任何人都可以创建无限多的身体

  no central point of coordination (去中心)