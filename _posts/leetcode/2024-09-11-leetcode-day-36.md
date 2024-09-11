---
title: "Leetcode Day 36 - DP: Buy and Sell Stock Advanced"
description: 188 Best Time to Buy and Sell Stock IV ｜ 309 Best Time to Buy and Sell Stock with Cooldown
author: yoyo
date: 2024-09-11 20:47:00 +0800
categories: [Data Structure and Algorithm, Leetcode, Dynamic Programming, Buy and Sell Stock]
tags: [dynamic programming (DP)]
math: true
---

![Easy](https://img.shields.io/badge/Easy-brightgreen) 
![Medium](https://img.shields.io/badge/Medium-yellow)
![Hard](https://img.shields.io/badge/Hard-red)

## Dynamic Programming

| Diff                                                                                                | Problem                                                                                 | Python | Java |
|-----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|--------|------|
| ![Hard](https://img.shields.io/badge/Hard-red)                                               | [188 Best Time to Buy and Sell Stock IV](#best-time-to-buy-and-sell-stock-iv)                                 |✅      |       |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [309 Best Time to Buy and Sell Stock with Cooldown](#best-time-to-buy-and-sell-stock-with-cooldown)      |✅      |       |
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                              | [160 Intersection of Two Linked Lists](#the-link)               |        |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [142 Linked List Cycle II](#the-link)                                       |        |      |

## Best Time to Buy and Sell Stock IV

> [Link to Leetcode question](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv/description/)[^bttbassiv]
{: .prompt-info }

You are given an integer array `prices` where `prices[i]` is the price of a given stock on the `i<sup>th</sup>` day, and an integer `k`.

Find the maximum profit you can achieve. You may complete at most `k` transactions: i.e. you may buy at most k times and sell at most `k` times.

Note: You may not engage in multiple transactions simultaneously (i.e., you must sell the stock before you buy again).

**Example 1**

```yml
Input: k = 2, prices = [2,4,1]
Output: 2
Explanation: Buy on day 1 (price = 2) and sell on day 2 (price = 4), profit = 4-2 = 2.
```

**Example 2**

```
Input: k = 2, prices = [3,2,6,5,0,3]
Output: 7
Explanation: Buy on day 2 (price = 2) and sell on day 3 (price = 6), profit = 6-2 = 4. Then buy on day 5 (price = 0) and sell on day 6 (price = 3), profit = 3-0 = 3.
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0151.翻转字符串里的单词.html)[^bttbassivSolution].

- **`buy[j]`**: Represents the maximum profit after the `j`-th transaction on the day we bought the stock.
  - Update rule: `buy[j] = max(buy[j], sell[j - 1] - price)`, meaning we either keep the previous buy profit or decide to buy on the current day.
  
- **`sell[j]`**: Represents the maximum profit after the `j`-th transaction on the day we sold the stock.
  - Update rule: `sell[j] = max(sell[j], buy[j] + price)`, meaning we either keep the previous sell profit or decide to sell on the current day.
  
- **Special case**:  
  If `k >= n // 2` (i.e., the number of transactions is greater than or equal to half of the total days), the problem reduces to the unlimited transaction version of the problem (similar to Stock II).

#### Time Complexity

- **Time Complexity**:  
  \( O(n \cdot k) \), where `n` is the length of `prices` and `k` is the maximum number of transactions allowed.

- **Space Complexity**:  
  \( O(k) \), since we only use two arrays of size `k`.

#### Python

```python
class Solution(object):
    def maxProfit(self, k, prices):
        if not prices or k == 0:
            return 0
        
        n = len(prices)
        
        # 当交易次数 k 大于总天数的一半时，相当于无限次交易
        if k >= n // 2:
            return sum(max(prices[i + 1] - prices[i], 0) for i in range(n - 1))
        
        # dp arrays: profit[i][j] means max profit up to day i with at most j transactions
        buy = [-float('inf')] * (k + 1)  # Maximum profit on the day we bought
        sell = [0] * (k + 1)  # Maximum profit on the day we sold
        
        # Iterate over the prices
        for price in prices:
            for j in range(1, k + 1):
                # Update the buy array: max of keeping old buy or buying on this day
                buy[j] = max(buy[j], sell[j - 1] - price)
                # Update the sell array: max of keeping old sell or selling on this day
                sell[j] = max(sell[j], buy[j] + price)
        
        return sell[k]
```


## Best Time to Buy and Sell Stock with Cooldown

> [Link to Leetcode question](https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/)[^bttbasswc]
{: .prompt-info }

You are given an array `prices` where `prices[i]` is the price of a given stock on the `i<sup>th/sup>` day.

Find the maximum profit you can achieve. You may complete as many transactions as you like (i.e., buy one and sell one share of the stock multiple times) with the following restrictions:

- After you sell your stock, you cannot buy stock on the next day (i.e., cooldown one day).

**Note**: You may not engage in multiple transactions simultaneously (i.e., you must sell the stock before you buy again).

 

**Example 1**

```yml
Input: prices = [1,2,3,0,2]
Output: 3
Explanation: transactions = [buy, sell, cooldown, buy, sell]
```

**Example 2**

```yml
Input: prices = [1]
Output: 0
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0309.最佳买卖股票时机含冷冻期.html)[^bttbasswcSolution].

#### Python

```python
class Solution(object):
    def maxProfit(self, prices):
        # dp[i][0]: 持有股票状态
        # dp[i][1]: 保持卖出股票的状态
        # dp[i][2]: 今天卖出股票的状态
        # dp[i][3]: 冷冻期

        dp = [[0, 0, 0, 0] for _ in range(len(prices))]
        dp[0][0] -= prices[0]

        for day in range(1,len(prices)):
            dp[day][0] = max(dp[day - 1][0], max(dp[day - 1][1], dp[day - 1][3]) - prices[day])
            dp[day][1] = max(dp[day - 1][1], dp[day - 1][3])
            dp[day][2] = dp[day - 1][0] + prices[day]
            dp[day][3] = dp[day - 1][2]
        
        return max(dp[-1])
```

### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [2095 Delete the Middle Node of a Linked List](https://leetcode.com/problems/delete-the-middle-node-of-a-linked-list/)[^dtmnoall] |        |      |

## <2nd problem>

> [Link to Leetcode question](https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/)[^rnnfeol]
{: .prompt-info }

[^]:Leetcode-

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0151.翻转字符串里的单词.html)[^rhsSolution].

[^Solution]:代码随想录-

### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [2095 Delete the Middle Node of a Linked List](https://leetcode.com/problems/delete-the-middle-node-of-a-linked-list/)[^dtmnoall] |        |      |



## Reference

[^bttbassiv]:Leetcode-188 Best Time to Buy and Sell Stock IV: [https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv/description/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv/description/).
[^bttbassivSolution]:代码随想录-买卖股票的最佳时机IV: [https://programmercarl.com/0188.买卖股票的最佳时机IV.html](https://programmercarl.com/0188.买卖股票的最佳时机IV.html).
[^bttbasswc]:Leetcode-309 Best Time to Buy and Sell Stock with Cooldown: [https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/description/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/description/).
[^bttbasswcSolution]:代码随想录-最佳买卖股票时机含冷冻期: [https://programmercarl.com/0309.最佳买卖股票时机含冷冻期.html
](https://programmercarl.com/0309.最佳买卖股票时机含冷冻期.html).

