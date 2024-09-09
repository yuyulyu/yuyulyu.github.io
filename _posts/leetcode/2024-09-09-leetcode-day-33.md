---
title: “Leetcode Day 33 - DP: Multiple Knapsack Problem”
description: 322 Coin Change | 279 Perfect Squares | 139 Word Break
author: yoyo
date: 2024-09-09 11:32:00 +0800
categories: [Data Structure and Algorithm, Leetcode]
tags: [dynamic programming (DP)]
---

## Dynamic Programming

| Diff                                                                                                | Problem                                                                                 | Python | Java |
|-----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [322 Coin Change](#coin-change)                                                             |✅      |        |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [279 Perfect Squares](#perfect-squares)                                                  |✅      |        |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [139 Word Break](#word-break)                                                              |✅      |      |

如果求组合数就是外层for循环遍历物品，内层for遍历背包。

如果求排列数就是外层for遍历背包，内层for循环遍历物品。

## Coin Change

> [Link to Leetcode question](https://leetcode.com/problems/coin-change/description/)[^cc]
{: .prompt-info }

You are given an integer array `coins` representing coins of different denominations and an integer `amount` representing a total amount of money.

Return the fewest number of coins that you need to make up that amount. If that amount of money cannot be made up by any combination of the coins, return `-1`.

You may assume that you have an infinite number of each kind of coin.

**Example 1**

```
Input: coins = [1,2,5], amount = 11
Output: 3
Explanation: 11 = 5 + 5 + 1
```

**Example 2**

```
Input: coins = [2], amount = 3
Output: -1
```

**Example 3**

```
Input: coins = [1], amount = 0
Output: 0
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0322.零钱兑换.html)[^ccSolution].

#### Python

```python
class Solution(object):
    def coinChange(self, coins, amount):
        if amount == 0: return 0
        
        dp = [float('inf')] * (amount + 1)
        dp[0] = 0  

        for money in range(1, amount + 1):
            for coin in coins:
                if coin <= money:
                    dp[money] = min(dp[money], dp[money - coin] + 1)
        
        return dp[amount] if dp[amount] != float('inf') else -1
```


### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [983 Minimum Cost For Tickets](https://leetcode.com/problems/minimum-cost-for-tickets/description/)[^mcft] |        |      |
| ![Hard](https://img.shields.io/badge/Hard-red)                                                       | [2547 Minimum Cost to Split an Array](https://leetcode.com/problems/minimum-cost-to-split-an-array/description/)[^mctsaa]          |        |      |



## Perfect Squares

> [Link to Leetcode question](https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/)[^ps]
{: .prompt-info }

Given an integer `n`, return the least number of perfect square numbers that sum to `n`.

A perfect square is an integer that is the square of an integer; in other words, it is the product of some integer with itself. For example, `1`, `4`, `9`, and `16` are perfect squares while 3 and 11 are not.

**Example 1**

```
Input: n = 12
Output: 3
Explanation: 12 = 4 + 4 + 4.
```

**Example 2**

```
Input: n = 13
Output: 2
Explanation: 13 = 4 + 9.
```


### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0279.完全平方数.html)[^psSolution].

#### Python

**Dynamic Programming**

```python
import math
class Solution(object):
    def numSquares(self, n):
        if int(math.sqrt(n)) ** 2 == n: return 1

        while n % 4 == 0:
            n //= 4

        nums = [i for i in range(int(math.sqrt(n)), - 1, -1)]
        dp = [float('inf') for _ in range(n + 1)]
        dp[0] = 0

        for N in range(n + 1):
            for num in nums:
                if num ** 2 <= N:
                    dp[N] = min(dp[N], dp[N - num ** 2] + 1)
        
        return dp[n]
```

**Solution 2**

```python
import math

class Solution(object):
    def numSquares(self, n):
        """
        :type n: int
        :rtype: int
        """
        def check_two_squares(c):
            i, j = 0, int(math.sqrt(c))
            while i <= j:
                current_sum = i * i + j * j
                if current_sum == c:
                    return True
                elif current_sum < c:
                    i += 1
                else:
                    j -= 1
            return False
        
        def integer_sqrt(x):
            """Compute the integer square root of x."""
            return int(math.sqrt(x))
        
        # Check if n is a perfect square
        if n == integer_sqrt(n) ** 2:
            return 1
        
        # Check if n can be expressed as the sum of two squares
        if check_two_squares(n):
            return 2
        
        # Continuously divide n by 4
        original_n = n
        while n % 4 == 0:
            n //= 4
        
        # Check if n is not of the form 8k + 7
        if n % 8 != 7:
            return 3
        
        # If none of the above, return 4 (Lagrange's Four Square Theorem)
        return 4
```

### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [204 Count Primes](https://leetcode.com/problems/delete-the-middle-node-of-a-linked-list/)[^cp] |        |      |



## Word Break

> [Link to Leetcode question](https://leetcode.com/problems/word-break/description/)[^wb]
{: .prompt-info }

Given a string `s` and a dictionary of strings `wordDict`, return `true` if `s` can be segmented into a space-separated sequence of one or more dictionary words.

Note that the same word in the dictionary may be reused multiple times in the segmentation. 

**Example 1**

```
Input: s = "leetcode", wordDict = ["leet","code"]
Output: true
Explanation: Return true because "leetcode" can be segmented as "leet code".
```

**Example 2**

```
Input: s = "applepenapple", wordDict = ["apple","pen"]
Output: true
Explanation: Return true because "applepenapple" can be segmented as "apple pen apple".
Note that you are allowed to reuse a dictionary word.
```

**Example 3**

```
Input: s = "catsandog", wordDict = ["cats","dog","sand","and","cat"]
Output: false
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0139.单词拆分.html)[^wbSolution].

#### Python

```python
lass Solution(object):
    def wordBreak(self, s, wordDict):
        s_l = len(s)
        dp = [0] * (s_l + 1)
        dp[0] = 1  
        
        for i in range(1, s_l + 1):
            for word in wordDict:
                word_l = len(word)
                if i >= word_l and s[i - word_l:i] == word:  
                    dp[i] = dp[i] or dp[i - word_l]  
                
        return dp[-1] == 1
```

### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Hard](https://img.shields.io/badge/Hard-red)                                                | [140 Word Break II](https://leetcode.com/problems/word-break-ii/)[^wbii] |        |      |



## Reference

[^cc]:Leetcode-322 Coin Change: [https://leetcode.com/problems/coin-change/description/](https://leetcode.com/problems/coin-change/description/).
[^ccSolution]:代码随想录-零钱兑换 [https://programmercarl.com/0322.零钱兑换.html](https://programmercarl.com/0322.零钱兑换.html).
[^mcft]:Leetcode-983 Minimum Cost For Tickets: [https://leetcode.com/problems/minimum-cost-for-tickets/description/](https://leetcode.com/problems/minimum-cost-for-tickets/description/).
[^mctsaa]:Leetcode-2547 Minimum Cost to Split an Array: [https://leetcode.com/problems/minimum-cost-to-split-an-array/description/](https://leetcode.com/problems/minimum-cost-to-split-an-array/description/).
[^ps]:Leetcode-279 Perfect Squares: [https://leetcode.com/problems/perfect-squares/description/](https://leetcode.com/problems/perfect-squares/description/).
[^psSolution]:代码随想录-完全平方数: [https://programmercarl.com/0279.完全平方数.html](https://programmercarl.com/0279.完全平方数.html).
[^cp]:Leetcode-204. Count Primes: [https://leetcode.com/problems/count-primes/description/](https://leetcode.com/problems/count-primes/description/).
[^wb]:Leetcode-139 Word Break: [https://leetcode.com/problems/word-break/description/](https://leetcode.com/problems/word-break/description/).
[^wbSolution]:代码随想录-单词拆分: [https://programmercarl.com/0139.单词拆分.html](https://programmercarl.com/0139.单词拆分.html).
[^wbii]:Leetcode-140 Word Break II: [https://leetcode.com/problems/word-break-ii/](https://leetcode.com/problems/word-break-ii/).



