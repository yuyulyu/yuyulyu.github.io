---
title: "Leetcode Day 35 - DP: Buy and Sell Stock"
description: 121 Best Time to Buy and Sell Stock ｜ 122 Best Time to Buy and Sell Stock II | 123 Best Time to Buy and Sell Stock III
author: yoyo
date: 2024-09-11 11:38:00 +0800
categories: [Data Structure and Algorithm, Leetcode, Dynamic Programming]
tags: [dynamic programming (DP)]
---

## Dynamic Programming

| Diff                                                                                                | Problem                                                                                 | Python | Java |
|-----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|--------|------|
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                               | [121 Best Time to Buy and Sell Stock](#best-time-to-buy-and-sell-stock)               |✅      |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [122 Best Time to Buy and Sell Stock II](#best-time-to-buy-and-sell-stock-ii)         |✅      |      |
| ![Hard](https://img.shields.io/badge/Hard-red)                                              | [123 Best Time to Buy and Sell Stock III](#best-time-to-buy-and-sell-stock-iii)       |✅      |      |


## Best Time to Buy and Sell Stock

> [Link to Leetcode question](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description/)[^bttbass]
{: .prompt-info }

You are given an array prices where `prices[i]` is the price of a given stock on the `i<sup>th</sup>` day.

You want to maximize your profit by choosing a single day to buy one stock and choosing a different day in the future to sell that stock.

Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return 0.

**Example 1**

```
Input: prices = [7,1,5,3,6,4]
Output: 5
Explanation: Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.
Note that buying on day 2 and selling on day 1 is not allowed because you must buy before you sell.
```

**Example 2:**

```
Input: prices = [7,6,4,3,1]
Output: 0
Explanation: In this case, no transactions are done and the max profit = 0.
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0121.买卖股票的最佳时机.html)[^bttbassSolution].

#### Python

```python
class Solution(object):
    def maxProfit(self, prices):
        min_price = 10001
        max_profit = 0

        for price in prices:
            max_profit = max(max_profit, price - min_price)
            min_price = min(min_price, price)
        
        return max_profit
```

## Best Time to Buy and Sell Stock II

> [Link to Leetcode question](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/description/)[^bttbassii]
{: .prompt-info }

You are given an integer array `prices` where `prices[i]` is the price of a given stock on the i<sup>th</sup> day.

On each day, you may decide to buy and/or sell the stock. You can only hold at most one share of the stock at any time. However, you can buy it then immediately sell it on the same day.

Find and return the maximum profit you can achieve.

**Example 1**

```yml
Input: prices = [7,1,5,3,6,4]
Output: 7
Explanation: Buy on day 2 (price = 1) and sell on day 3 (price = 5), profit = 5-1 = 4.
Then buy on day 4 (price = 3) and sell on day 5 (price = 6), profit = 6-3 = 3.
Total profit is 4 + 3 = 7.
```

**Example 2**

```yml
Input: prices = [1,2,3,4,5]
Output: 4
Explanation**: Buy on day 1 (price = 1) and sell on day 5 (price = 5), profit = 5-1 = 4.
Total profit is 4.
```
**Example 3**

```yml
Input: prices = [7,6,4,3,1]
Output: 0
Explanation: There is no way to make a positive profit, so we never buy the stock to achieve the maximum profit of 0.
```

### Solution

> A detaild explanation of greedy solution can be found [here](https://yuyulyu.github.io/posts/leetcode-day-24/#best-time-to-buy-and-sell-stock-ii).

```python
class Solution(object):
    def maxProfit(self, prices):
        result = 0
        for i in range(1, len(prices)):
            result += max(prices[i] - prices[i - 1], 0)
        return result
```


## Best Time to Buy and Sell Stock III

> [Link to Leetcode question](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii/description/)[^bttbassiii]
{: .prompt-info }

You are given an array prices where `prices[i]` is the price of a given stock on the `i<sup>th</sup>` day.

Find the maximum profit you can achieve. You may complete at most two transactions.

Note: You may not engage in multiple transactions simultaneously (i.e., you must sell the stock before you buy again).

**Example 1**

```yml
Input: prices = [3,3,5,0,0,3,1,4]
Output: 6
Explanation: Buy on day 4 (price = 0) and sell on day 6 (price = 3), profit = 3-0 = 3.
Then buy on day 7 (price = 1) and sell on day 8 (price = 4), profit = 4-1 = 3.
```

**Example 2**

```yml
Input: prices = [1,2,3,4,5]
Output: 4
Explanation: Buy on day 1 (price = 1) and sell on day 5 (price = 5), profit = 5-1 = 4.
Note that you cannot buy on day 1, buy on day 2 and sell them later, as you are engaging multiple transactions at the same time. You must sell before buying again.
```

**Example 3**

```yml
Input: prices = [7,6,4,3,1]
Output: 0
Explanation: In this case, no transaction is done, i.e. max profit = 0.
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0123.买卖股票的最佳时机III.html)[^rhsSolution].


#### Python

```python
class Solution(object):
    def maxProfit(self, prices):
        if not prices:
            return 0

        n = len(prices)
        
        # Left profits array: max profit until day i (first transaction)
        left_profits = [0] * n
        min_price = prices[0]
        
        for i in range(1, n):
            min_price = min(min_price, prices[i])
            left_profits[i] = max(left_profits[i - 1], prices[i] - min_price)

        # Right profits array: max profit from day i to the end (second transaction)
        right_profits = [0] * n
        max_price = prices[n - 1]
        
        for i in range(n - 2, -1, -1):
            max_price = max(max_price, prices[i])
            right_profits[i] = max(right_profits[i + 1], max_price - prices[i])

        # Combine the two profits
        max_total_profit = 0
        for i in range(n):
            max_total_profit = max(max_total_profit, left_profits[i] + right_profits[i])
        
        return max_total_profit
```



## Reference

[^bttbass]:Leetcode-121 Best Time to Buy and Sell Stock: [https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description/).
[^bttbassSolution]:代码随想录-买卖股票的最佳时机: [https://programmercarl.com/0121.买卖股票的最佳时机.html](https://programmercarl.com/0121.买卖股票的最佳时机.html).
[^bttbassii]:Leetcode-122 Best Time to Buy and Sell Stock II: [https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/description/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/description/).
[^bttbassiiSolution]:代码随想录-买卖股票的最佳时机II: [https://programmercarl.com/0122.买卖股票的最佳时机II（动态规划）.html](https://programmercarl.com/0122.买卖股票的最佳时机II（动态规划）.html).
[^bttbassiii]:Leetcode-123 Best Time to Buy and Sell Stock III: [https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii/description/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii/description/).
[^bttbassiiiSolution]:代码随想录-买卖股票的最佳时机III: [https://programmercarl.com/0123.买卖股票的最佳时机III.html](https://programmercarl.com/0123.买卖股票的最佳时机III.html).

