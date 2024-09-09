---
title: "Leetcode Day 32 - DP: Complete Knapsack Problem"
description: Kama 52 Complete Knapsack | 518 Coin Change II | 377 Combination Sum IV | Kama 57 Climbing Stairs
author: yoyo
date: 2024-09-09 00:25:00 +0800
categories: [Data Structure and Algorithm, Leetcode, Dynamic Programming]
tags: [dynamic programming (DP)]
---

## Dynamic Programming

> [Link to note about Dynamic Programming](https://yuyulyu.github.io/posts/dynamic-programming/) 
{: .prompt-tip }

| Diff                                                                                                | Problem                                                                                 | Python | Java |
|-----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|--------|------|
| ![Kama](https://img.shields.io/badge/Kama-gray)                                                | [Kama 52 Complete Knapsack](#complete-knapsack)                                          |✅      |        |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [518 Coin Change II](#coin-change-ii)                                                    |✅      |        |
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                              | [377 Combination Sum IV](#combination-sum-iv)                                         |✅      |        |
|  ![Kama](https://img.shields.io/badge/Kama-gray)                                           | [Kama 57 Climbing Stairs](#climbing-stairs)                                                       |✅      |        |

## Complete Knapsack

> [Link to the question](https://kamacoder.com/problempage.php?pid=1052)[^ck]
{: .prompt-info }

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

#### Python

```python
class Solution(object):
    def change(self, amount, coins):
        dp = [0 for _ in range (amount + 1)]
        dp[0] = 1
        
        for coin in coins:   
            for m in range(coin, amount + 1):
                if m >= coin: dp[m] += dp[m - coin]
        return dp[amount]
```

### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Hard](https://img.shields.io/badge/Hard-red)                                                | [2218 Maximum Value of K Coins From Piles](https://leetcode.com/problems/maximum-value-of-k-coins-from-piles/description/)[^mvokcfp] |        |      |
| ![Hard](https://img.shields.io/badge/Hard-red)                                                | [2585 Number of Ways to Earn Points](https://leetcode.com/problems/number-of-ways-to-earn-points/description/)[^nwtep] |        |      |




## Combination Sum IV

> [Link to Leetcode question](https://leetcode.com/problems/combination-sum-iv/description/)[^csiv]
{: .prompt-info }

Given an array of distinct integers `nums` and a target integer `target`, return the number of possible combinations that add up to `target`.

The test cases are generated so that the answer can fit in a `32-bit` integer.

**Example 1**

```
Input: nums = [1,2,3], target = 4
Output: 7
Explanation:
The possible combination ways are:
(1, 1, 1, 1)
(1, 1, 2)
(1, 2, 1)
(1, 3)
(2, 1, 1)
(2, 2)
(3, 1)
Note that different sequences are counted as different combinations.
```

**Example 2**

```
Input: nums = [9], target = 3
Output: 0
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0377.组合总和Ⅳ.html)[^csivSolution].

#### Python

```python
class Solution(object):
    def combinationSum4(self, nums, target):
        dp = [0 for _ in range(target + 1)]
        dp[0] = 1

        for t in range(target + 1):
            for num in nums:
                if t >= num: dp[t] += dp[t - num]
        
        return dp[target]
```

## Climbing Stairs

> [Link to the question](https://kamacoder.com/problempage.php?pid=1067)[^cs]
{: .prompt-info }

**题目描述**

> 假设你正在爬楼梯。需要 `n` 阶你才能到达楼顶。<br>
> 每次你可以爬至多`m` (`1 <= m < n`)个台阶。你有多少种不同的方法可以爬到楼顶呢？<br>
> **注意**：给定 `n` 是一个正整数。

**输入描述**

> 输入共一行，包含两个正整数，分别表示`n`, `m`

**输出描述**

> 输出一个整数，表示爬到楼顶的方法数。

**输入示例**

> `3 2`

**输出示例**

> `3`

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0070.爬楼梯完全背包版本.html)[^csSolution].

#### Python

```python
stairs, steps = map(int, input().split())

dp = [0 for _ in range(1 + stairs)]
dp[0] = 1 

for stair in range(stairs + 1):
    for step in range(1, steps + 1):
        dp[stair] += dp[stair - step]

print(dp[stairs])
```


## Reference

[^ck]:KamaCoder-53 Complete Knapsack: [https://kamacoder.com/problempage.php?pid=1052](https://kamacoder.com/problempage.php?pid=1052).
[^ckSolution]:代码随想录-背包问题理论基础完全背包: [https://programmercarl.com/背包问题理论基础完全背包.html](https://programmercarl.com/背包问题理论基础完全背包.html).
[^ccii]:Leetcode-518 Coin Change II: [https://leetcode.com/problems/coin-change-ii/description/](https://leetcode.com/problems/coin-change-ii/description/).
[^cciiSolution]:代码随想录-零钱兑换II: [https://programmercarl.com/0518.零钱兑换II.html](https://programmercarl.com/0518.零钱兑换II.html).
[^mvokcfp]: Leetcode-2218 Maximum Value of K Coins From Piles: [https://leetcode.com/problems/maximum-value-of-k-coins-from-piles/description/](https://leetcode.com/problems/maximum-value-of-k-coins-from-piles/description/).
[^nwtep]: Leetcode-2585 Number of Ways to Earn Points: [https://leetcode.com/problems/number-of-ways-to-earn-points/description/](https://leetcode.com/problems/number-of-ways-to-earn-points/description/).
[^csiv]:Leetcode-377 Combination Sum IV: [https://leetcode.com/problems/combination-sum-iv/description/](https://leetcode.com/problems/combination-sum-iv/description/).
[^csivSolution]:代码随想录-组合总和Ⅳ: [https://programmercarl.com/0377.组合总和Ⅳ.html](https://programmercarl.com/0377.组合总和Ⅳ.html).
[^cs]:KamaCoder - Kama 57 Climbing Stairs: [https://kamacoder.com/problempage.php?pid=1067](https://kamacoder.com/problempage.php?pid=1067).
[^csSolution]:代码随想录-爬楼梯完全背包版本: [https://programmercarl.com/0070.爬楼梯完全背包版本.html](https://programmercarl.com/0070.爬楼梯完全背包版本.html).



