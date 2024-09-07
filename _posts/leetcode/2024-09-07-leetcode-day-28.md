---
title: Leetcode 28 - Dynamic Programming
description: 509 Fibonacci Number | 70 Climbing Stairs | 746 Min Cost Climbing Stairs
author: yoyo
date: 2024-09-07 14:46:00 +0800
categories: [Data Structure and Algorithm, Leetcode]
tags: [dynamic programming (DP)]
---


## Dynamic Programming

[Link to note about Dynamic Programming](https://yuyulyu.github.io/posts/dynamic-programming/) {: .prompt-tip }

| Diff                                                                                                | Problem                                                                                 | Python | Java |
|-----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|--------|------|
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                               | [509 Fibonacci Number](#fibonacci-number)                                              |✅      |        |
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                                | [70 Climbing Stairs](#climbing-stairs)                                               |✅      |        |
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                              | [746 Min Cost Climbing Stairs](#min-cost-climbing-stairs)                               |✅      |        |


## Fibonacci Number

> [Link to Leetcode question](https://leetcode.com/problems/fibonacci-number/description/)[^fn]
{: .prompt-info }

The Fibonacci numbers, commonly denoted `F(n)` form a sequence, called the Fibonacci sequence, such that each number is the sum of the two preceding ones, starting from `0` and `1`. That is,

> F(0) = 0, F(1) = 1<br>
> F(n) = F(n - 1) + F(n - 2), for n > 1.

Given `n`, calculate `F(n)`.

**Example 1**

```
Input: n = 2
Output: 1
Explanation: F(2) = F(1) + F(0) = 1 + 0 = 1.
```

**Example 2**

```
Input: n = 3
Output: 2
Explanation: F(3) = F(2) + F(1) = 1 + 1 = 2.
```

**Example 3**

```
Input: n = 4
Output: 3
Explanation: F(4) = F(3) + F(2) = 2 + 1 = 3.
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0509.斐波那契数.html)[^fnSolution].

#### Python

```python
class Solution(object):
    def fib(self, n):
        return n if n < 2 else self.fib(n - 1) + self.fib(n - 2)
```

```python
class Solution(object):
    def fib(self, n):
        if n < 2:
            return n
        
        record = [0, 1]

        for i in range(2, n + 1):
            record.append(record[i - 1] + record[i - 2])
        
        return record[-1]
```

### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [842 Split Array into Fibonacci Sequence](https://leetcode.com/problems/split-array-into-fibonacci-sequence/description/)[^saf] |        |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [873 Length of Longest Fibonacci Subsequence](https://leetcode.com/problems/length-of-longest-fibonacci-subsequence/)[^llfs] |        |      |



## Climbing Stairs

> [Link to Leetcode question](https://leetcode.com/problems/climbing-stairs/description/)[^cs]
{: .prompt-info }

You are climbing a staircase. It takes `n` steps to reach the top.

Each time you can either climb `1` or `2` steps. In how many distinct ways can you climb to the top?

**Example 1**

```
Input: n = 2
Output: 2
Explanation: There are two ways to climb to the top.
1. 1 step + 1 step
2. 2 steps
```

**Example 2**

```
Input: n = 3
Output: 3
Explanation: There are three ways to climb to the top.
1. 1 step + 1 step + 1 step
2. 1 step + 2 steps
3. 2 steps + 1 step
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0070.爬楼梯.html)[^csSolution].



#### Python

```python
class Solution(object):
    def climbStairs(self, n):
        if n < 3: return n

        record = [1, 2]

        for i in range(2, n):
            record.append(record[i - 1] + record[i - 2])
        
        return record[-1]
```


## Min Cost Climbing Stairs

> [Link to Leetcode question](https://leetcode.com/problems/min-cost-climbing-stairs/)[^mccs]
{: .prompt-info }

You are given an integer array cost where cost[i] is the cost of ith step on a staircase. Once you pay the cost, you can either climb one or two steps.

You can either start from the step with index `0`, or the step with index `1`.

Return the minimum cost to reach the top of the floor.

**Example 1**

```
Input: cost = [10,15,20]
Output: 15
Explanation: You will start at index 1.
- Pay 15 and climb two steps to reach the top.
The total cost is 15.
```

**Example 2**

```
Input: cost = [1,100,1,1,1,100,1,1,100,1]
Output: 6
Explanation: You will start at index 0.
- Pay 1 and climb two steps to reach index 2.
- Pay 1 and climb two steps to reach index 4.
- Pay 1 and climb two steps to reach index 6.
- Pay 1 and climb one step to reach index 7.
- Pay 1 and climb two steps to reach index 9.
- Pay 1 and climb one step to reach the top.
The total cost is 6.
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0746.使用最小花费爬楼梯.html)[^mccsSolution].

#### Python

```python
class Solution(object):
    def minCostClimbingStairs(self, cost):
        if len(cost) < 3:
            return min(cost[0], cost[1])
        
        dp = [0,0]

        for i in range(2, len(cost) + 1):
            dp.append(min(dp[i - 2] + cost[i - 2], dp[i - 1] + cost[i - 1]))
        
        return dp[-1]
```



| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Hard](https://img.shields.io/badge/Hard-red)                                                | [3154 Find Number of Ways to Reach the K-th Stair](https://leetcode.com/problems/find-number-of-ways-to-reach-the-k-th-stair/)[^fnowtrtks] |        |      |




## Reference
[^fn]:Leetcode-509 Fibonacci Number: [https://leetcode.com/problems/fibonacci-number/description/
](https://leetcode.com/problems/fibonacci-number/description/).
[^fnSolution]:代码随想录-斐波那契数: [https://programmercarl.com/0509.斐波那契数.html](https://programmercarl.com/0509.斐波那契数.html).
[^cs]: Leetcode-70 Climbing Stairs: [https://leetcode.com/problems/climbing-stairs/description/](https://leetcode.com/problems/climbing-stairs/description/).
[^saf]: Leetcode-842 Split Array into Fibonacci Sequence: [https://leetcode.com/problems/split-array-into-fibonacci-sequence/description/](https://leetcode.com/problems/split-array-into-fibonacci-sequence/description/).
[^llfs]: Leetcode-873 Length of Longest Fibonacci Subsequence: [https://leetcode.com/problems/length-of-longest-fibonacci-subsequence/](https://leetcode.com/problems/length-of-longest-fibonacci-subsequence/).
[^csSolution]:代码随想录-爬楼梯: [https://programmercarl.com/0070.爬楼梯.html](https://programmercarl.com/0070.爬楼梯.html).
[^mccs]:Leetcode-746 Min Cost Climbing Stairs: [https://leetcode.com/problems/min-cost-climbing-stairs/](https://leetcode.com/problems/min-cost-climbing-stairs/).
[^mccsSolution]:代码随想录-使用最小花费爬楼梯: [https://programmercarl.com/0746.使用最小花费爬楼梯.html](https://programmercarl.com/0746.使用最小花费爬楼梯.html).
[^fnowtrtks]:Leetcode-3154 Find Number of Ways to Reach the K-th Stair: [https://leetcode.com/problems/find-number-of-ways-to-reach-the-k-th-stair/](https://leetcode.com/problems/find-number-of-ways-to-reach-the-k-th-stair/).


