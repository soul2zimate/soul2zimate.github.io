---
layout: post
title: Introduction to Crypto and Cryptocurrencies
---
# cryptographic-hash-functions

## Hash funciton

- takes any string as input
- fixed-size output (e.g. 256 bits)
- efficiently computable

### Security properties

- collision-free 近乎无冲突

    Nobody can find x and y such that
      x != y and H(x)=H(y) 对于不同的两个input x and y, 近乎不能够找到经过哈希函数计算后相同的两个哈希值

      Therefore, if we know H(x) = H(y), it's safe to assume that x = y. 如果两个输入具有相同的哈希值，则我们可以假设两个输入也相同。所以与其比较庞大的输入，我们可以比较他们的哈希值(hash as message digest 消息的摘要)，因为哈希值相对而言要小很多(256 bits)。

- hiding 隐秘性（不可逆）

    Given H(x), it's infeasibale to find x. 如果r取自高阶最小熵的概率广泛分布(a probability distribution that has high min-entropy)，没有可行的方案允许从哈希值 H(r|x) 反向求出值 x.

- puzzle-friendly 谜题友好

    For every possible output value y, if k is chosen from a distrubution with hight min-entropy, then it's infeasible to find x such that H(k|x) = y. 对于具有广泛概率分布的值k, 则没有比随机找x更优的方法，使H(k|x)= y.

    Puzzle-friendly property implies that no solving strategy is much better than trying random values of x. 

- 比特币使用的SHA-256 哈希函数
- 使用512bits作为分组长度
- 加上多余的一段数据，padding还包括了整条信息的bit长度 (占64bit)，在这之前有1位1和指定的若干位0，使总长为512位。函数计算流程如图

![My helpful screenshot]({{ "/assets/2018-02-03-Bitcoin-and-Cryptocurrency-Technologies-week01-img01.png" | absolute_url }})

To be continued...
