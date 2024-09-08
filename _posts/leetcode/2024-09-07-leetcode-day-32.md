---
title: "Leetcode Day 32 - DP: Complete Knapsack Problem"
description: Kama 52 Complete Knapsack | 518 Coin Change II | 
author: yoyo
date: 2024-09-09 00:25:00 +0800
categories: [Data Structure and Algorithm, Leetcode]
tags: [dynamic programming (DP)]
---

## Dynamic Programming

| Diff                                                                                                | Problem                                                                                 | Python | Java |
|-----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|--------|------|
|                                                                                                      | [Kama 52 Complete Knapsack](#complete-knapsack)                                          |✅      |        |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [518 Coin Change II](#coin-change-ii)                |        |      |
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                              | [160 Intersection of Two Linked Lists](#the-link)               |        |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [142 Linked List Cycle II](#the-link)                                       |        |      |

## Complete Knapsack

> [Link to the question](https://kamacoder.com/problempage.php?pid=1052)[^ck]
{: .prompt-info }

[^ck]:Kamacoder-53 Complete Knapsack: [https://kamacoder.com/problempage.php?pid=1052](https://kamacoder.com/problempage.php?pid=1052).

**题目描述**

> 小明是一位科学家，他需要参加一场重要的国际科学大会，以展示自己的最新研究成果。他需要带一些研究材料，但是他的行李箱空间有限。这些研究材料包括实验设备、文献资料和实验样本等等，它们各自占据不同的重量，并且具有不同的价值。<br>
> 小明的行李箱所能承担的总重量为 `N`，问小明应该如何抉择，才能携带最大价值的研究材料，每种研究材料可以选择无数次，并且可以重复选择。

**输入描述**

> 第一行包含两个整数，`N`，`V`，分别表示研究材料的种类和行李空间<br>
> 接下来包含 `N` 行，每行两个整数 `wi` 和 `vi`，代表第 `i` 种研究材料的重量和价值

**输出描述**

> 输出一个整数，表示最大价值。

**输入示例**

> 4 5<br>
> 1 2<br>
> 2 4<br>
> 3 4<br>
> 4 5

**输出示例**

> 10

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/背包问题理论基础完全背包.html)[^ckSolution].

#### Python

```python
N, V = map(int, input().split())

weights = []
values = []

for _ in range(N):
    wi, vi = map(int, input().split())
    weights.append(wi)
    values.append(vi)


dp = [0] * weights[0] + [values[0]] * (V - weights[0] + 1)

for i in range(N):
    for n in range(weights[i], V + 1):
        dp[n] = max(dp[n], dp[n - weights[i]] + values[i])

print(dp[-1])
```


## Coin Change II

> [Link to Leetcode question](https://leetcode.com/problems/coin-change-ii/description/)[^ccii]
{: .prompt-info }

You are given an integer array `coins` representing coins of different denominations and an integer `amount` representing a total amount of money.

Return the number of combinations that make up that amount. If that amount of money cannot be made up by any combination of the coins, return 0.

You may assume that you have an infinite number of each kind of coin.

The answer is guaranteed to fit into a signed 32-bit integer. 

**Example 1**

```
Input: amount = 5, coins = [1,2,5]
Output: 4
Explanation: there are four ways to make up the amount:
5=5
5=2+2+1
5=2+1+1+1
5=1+1+1+1+1
```

**Example 2**

```
Input: amount = 3, coins = [2]
Output: 0
Explanation: the amount of 3 cannot be made up just with coins of 2.
```

**Example 3**

```
Input: amount = 10, coins = [10]
Output: 1
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0518.零钱兑换II.html)[^cciiSolution].


### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [2218. Maximum Value of K Coins From Piles](https://leetcode.com/problems/maximum-value-of-k-coins-from-piles/description/)[^dtmnoall] |        |      |

## <2nd problem>

> [Link to Leetcode question](https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/)[^rnnfeol]
{: .prompt-info }


### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0151.翻转字符串里的单词.html)[^rhsSolution].

### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [2218. Maximum Value of K Coins From Piles](https://leetcode.com/problems/maximum-value-of-k-coins-from-piles/description/)[^dtmnoall] |        |      |



## Reference
[^ckSolution]:代码随想录-背包问题理论基础完全背包: [https://programmercarl.com/背包问题理论基础完全背包.html](https://programmercarl.com/背包问题理论基础完全背包.html).
[^ccii]:Leetcode-518 Coin Change II: [https://leetcode.com/problems/coin-change-ii/description/](https://leetcode.com/problems/coin-change-ii/description/).
[^cciiSolution]:代码随想录-零钱兑换II: [https://programmercarl.com/0518.零钱兑换II.html](https://programmercarl.com/0518.零钱兑换II.html).



