---
title: Leetcode Day 29 - Dynamic Programming
description: 62 Unique Paths | 63 Unique Paths II | 343 Integer Break | 96 Unique Binary Search Trees
author: yoyo
date: 2024-09-07 15:48:00 +0800
categories: [Data Structure and Algorithm, Leetcode, Dynamic Programming]
tags: [dynamic programming (DP)]
---

## Dynamic Programming

> [Link to note about Dynamic Programming](https://yuyulyu.github.io/posts/dynamic-programming/) 
{: .prompt-tip }

| Diff                                                                                                | Problem                                                                                 | Python | Java |
|-----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [62 Unique Paths](#unique-paths)                                                           |✅      |        |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [63 Unique Paths II](#unique-paths-ii)                                               |✅      |        |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                              | [343 Integer Break](#integer-break)                                                           |✅      |        |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [96 Unique Binary Search Trees](#unique-binary-search-trees)                              |✅      |        |

## Unique Paths

> [Link to Leetcode question](https://leetcode.com/problems/unique-paths/description/)[^up]
{: .prompt-info }

here is a robot on an `m x n` grid. The robot is initially located at the top-left corner (i.e., `grid[0][0]`). The robot tries to move to the bottom-right corner (i.e., `grid[m - 1][n - 1]`). The robot can only move either down or right at any point in time.

Given the two integers m and n, return the number of possible unique paths that the robot can take to reach the bottom-right corner.

The test cases are generated so that the answer will be less than or equal to `2 * 109`.

**Example 1**

![Unique Paths Example 1](/assets/image/leetcode/leetcode-day-29/unique-paths-example-1.png)

> **Input**: m = 3, n = 7<br>
> **Output**: 28

*Example 2**

> **Input**: m = 3, n = 2<br>
> **Output**: 3<br>
> **Explanation**: From the top-left corner, there are a total of 3 ways to reach the bottom-right corner:<br>
> 1. Right -> Down -> Down<br>
> 2. Down -> Down -> Right<br>
> 3. Down -> Right -> Down<br>

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0062.不同路径.html)[^upSolution].

#### Python

```python
class Solution(object):
    def uniquePaths(self, m, n):
        if m == 1 or n == 1:
            return 1
        
        grid = [[0] * n for _ in range(m)]
        grid[0][0] = 1

        for M in range(m):
            for N in range(n):
                if M != 0: grid[M][N] += grid[M - 1][N]
                if N != 0: grid[M][N] += grid[M][N - 1]

        return grid[-1][-1]
```

## Unique Paths II

> [Link to Leetcode question](https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/)[^upii]
{: .prompt-info }

You are given an `m x n` integer array grid. There is a robot initially located at the top-left corner (i.e., grid[0][0]). The robot tries to move to the bottom-right corner (i.e., `grid[m - 1][n - 1]`). The robot can only move either down or right at any point in time.

An obstacle and space are marked as `1` or `0` respectively in grid. A path that the robot takes cannot include any square that is an obstacle.

Return the number of possible unique paths that the robot can take to reach the bottom-right corner.

The testcases are generated so that the answer will be less than or equal to `2 * 109`.

**Example 1**

![Unique Paths II Example 1](/assets/image/leetcode/leetcode-day-29/unique-paths-ii-example-1.jpeg)

> **Input**: obstacleGrid = [[0,0,0],[0,1,0],[0,0,0]]<br>
> **Output**: 2<br>
> **Explanation**: There is one obstacle in the middle of the 3x3 grid above.<br>
> There are two ways to reach the bottom-right corner:<br>
> 1. Right -> Right -> Down -> Down<br>
> 2. Down -> Down -> Right -> Right

![Unique Paths II Example 2](/assets/image/leetcode/leetcode-day-29/unique-paths-ii-example-2.jpeg)

> **Input**: obstacleGrid = [[0,1],[0,0]]<br>
> **Output**: 1

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0063.不同路径II.html)[^upiiSolution].

#### Python

```python
class Solution(object):
    def uniquePathsWithObstacles(self, obstacleGrid):
        if obstacleGrid[0][0] == 1 or obstacleGrid[-1][-1] == 1: return 0
        m, n = len(obstacleGrid), len(obstacleGrid[0])
        
        grid = [[0] * n for _ in range(m)]
        grid[0][0] = 1

        for M in range(m):
            for N in range(n):
                if obstacleGrid[M][N] == 1: continue
                if M != 0: grid[M][N] += grid[M - 1][N]
                if N != 0: grid[M][N] += grid[M][N - 1]

        return grid[-1][-1]
```

### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [64 Minimum Path Sum](https://leetcode.com/problems/minimum-path-sum/description/)[^mps] |        |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [2304 Minimum Path Cost in a Grid](https://leetcode.com/problems/minimum-path-cost-in-a-grid/description/)[^mpciag] |        |      |
| ![Hard](https://img.shields.io/badge/Hard-red)                                                       | [980 Unique Paths III](https://leetcode.com/problems/unique-paths-iii/)[^upiii]          |        |      |


## Integer Break

> [Link to Leetcode question](https://leetcode.com/problems/integer-break/description/)[^ib]
{: .prompt-info }

Given an integer `n`, break it into the sum of `k` positive integers, where `k >= 2`, and maximize the product of those integers.

Return the maximum product you can get.

**Example 1**

> **Input**: n = 2<br>
> **Output**: 1<br>
> **Explanation**: 2 = 1 + 1, 1 × 1 = 1.

**Example 2**

> **Input**: n = 10<br>
> **Output**: 36<br>
> **Explanation**: 10 = 3 + 3 + 4, 3 × 3 × 4 = 36.

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0343.整数拆分.html)[^ibSolution].


#### <ins>Solution 1: Dynamic Programming</ins>

Time complexity: O(n<sup>2</sup>)

```python
class Solution(object):
    def integerBreak(self, n):
        if n == 2: return 1
        if n == 3: return 2

        dp = [0] * (n + 1)
        dp[2], dp[3] = 2, 3

        for i in range(4, n+1):
            for j in range(1, i // 2 + 1):
                dp[i] = max(dp[i], dp[j] * dp[i - j])
        
        return dp[n]
```

#### <ins>Solution 2: Greedy</ins>

Time complexity: O(1)

The second solution uses a **greedy algorithm**. It directly breaks down `n` into as many 3's as possible, aiming to maximize the product of the integer breakdown. This approach is based on a mathematical pattern, and it returns the maximum product directly by considering different cases.

By breaking down `n`, we can observe that the more we break `n` into 3's, the larger the product becomes. However, there are two special cases to consider:

- **When `n % 3 == 1`**: Splitting out a `4` is better than splitting out a `1` (i.e., `3 * 3 * 1 < 3 * 4`).
- **When `n % 3 == 2`**: Directly multiplying by `2` yields the optimal product.

1. **If `n` is a multiple of 3**: We can completely break `n` into `3`'s, and the maximum product is `3 ** (n // 3)`.
2. **If `n % 3 == 1`**: Since the remainder `1` would decrease the product, we adjust by removing one `3` and replacing it with `4` (because `3 + 1 = 4`). The maximum product in this case is `3 ** ((n // 3) - 1) * 4`.
3. **If `n % 3 == 2`**: The remainder `2` can be directly multiplied, so the maximum product is `3 ** (n // 3) * 2`.

```python
class Solution(object):
    def integerBreak(self, n):
        if n == 2: return 1
        if n == 3: return 2
        if n % 3 == 0: return 3 ** (n // 3)
        if n % 3 == 1: return 3 ** ((n // 3) - 1) * 4
        return 3 ** (n // 3) * 2


```python
class Solution(object):
    def integerBreak(self, n):
        if n == 2: return 1
        if n == 3: return 2
        if n % 3 == 0: return 3 ** (n // 3)
        if n % 3 == 1: return 3 ** ((n // 3) - 1) * 4
        return 3 ** (n // 3) * 2
```


### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Hard](https://img.shields.io/badge/Hard-red)                                                | [1808 Maximize Number of Nice Divisors](https://leetcode.com/problems/maximize-number-of-nice-divisors/)[^mnond] |        |      |


## Unique Binary Search Trees

> [Link to Leetcode question](https://leetcode.com/problems/unique-binary-search-trees/description/)[^ubst]
{: .prompt-info }

Given an integer `n`, return the number of structurally unique BST's (binary search trees) which has exactly `n` nodes of unique values from `1` to `n`.

**Example 1**

![Unique Binary Search Trees Example 1](/assets/image/leetcode/leetcode-day-29/unique-binary-search-trees-example-1.jpeg)

> **Input**: n = 3<br>
> **Output**: 5

**Example 2**

> **Input**: n = 1<br>
> **Output**: 1


### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0096.不同的二叉搜索树.html)[^ubstSolution].

#### Python

```python
class Solution(object):
    def numTrees(self, n):
        if n == 1: return 1
        if n == 2: return 2

        dp = [0] * (n + 1)
        dp[0],dp[1], dp[2] = 1, 1, 2
        

        for i in range(3,n + 1):
            for j in range((i - 1) // 2 + 1):
                dp[i] += dp[j] * dp[i - j - 1] * 2 if j != i - j - 1 else dp[j] * dp[i - j - 1]
        
        return dp[n]
```

### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [95 Unique Binary Search Trees II](https://leetcode.com/problems/unique-binary-search-trees-ii/description/)[^ubstii] |        |      |

## Reference

[^up]:Leetcode-62 Unique Paths: [https://leetcode.com/problems/unique-paths/description/](https://leetcode.com/problems/unique-paths/description/).
[^upSolution]:代码随想录-不同路径: [https://programmercarl.com/0062.不同路径.html](https://programmercarl.com/0062.不同路径.html).
[^upii]: Leetcode-63 Unique Paths II: [https://leetcode.com/problems/unique-paths-ii/description/](https://leetcode.com/problems/unique-paths-ii/description/).
[^mps]: Leetcode-64 Minimum Path Sum: [https://leetcode.com/problems/minimum-path-sum/description/](https://leetcode.com/problems/minimum-path-sum/description/).
[^upiiSolution]:代码随想录-不同路径II: [https://programmercarl.com/0063.不同路径II.html](https://programmercarl.com/0063.不同路径II.html).
[^mpciag]: Leetcode-2304 Minimum Path Cost in a Grid: [https://leetcode.com/problems/minimum-path-cost-in-a-grid/description/](https://leetcode.com/problems/minimum-path-cost-in-a-grid/description/).
[^upiii]: Leetcode-980 Unique Paths III: [https://leetcode.com/problems/unique-paths-iii/](https://leetcode.com/problems/unique-paths-iii/).
[^ib]:Leetcode-343 Integer Break: [https://leetcode.com/problems/integer-break/description/](https://leetcode.com/problems/integer-break/description/).
[^ibSolution]:代码随想录-整数拆分: [https://programmercarl.com/0343.整数拆分.html](https://programmercarl.com/0343.整数拆分.html).
[^mnond]:Leetcode-1808 Maximize Number of Nice Divisors: [https://leetcode.com/problems/maximize-number-of-nice-divisors/](https://leetcode.com/problems/maximize-number-of-nice-divisors/).
[^ubst]:Leetcode-96 Unique Binary Search Trees: [https://leetcode.com/problems/unique-binary-search-trees/description/](https://leetcode.com/problems/unique-binary-search-trees/description/).
[^ubstSolution]:代码随想录-不同的二叉搜索树: [https://programmercarl.com/0096.不同的二叉搜索树.html](https://programmercarl.com/0096.不同的二叉搜索树.html).
[^ubstii]: Leetcode-95 Unique Binary Search Trees II: [https://leetcode.com/problems/unique-binary-search-trees-ii/description/](https://leetcode.com/problems/unique-binary-search-trees-ii/description/).
