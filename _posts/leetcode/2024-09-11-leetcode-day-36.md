---
title: "Leetcode Day 36 - DP: Buy and Sell Stock Advanced"
description: 188 Best Time to Buy and Sell Stock IV ｜ 309 Best Time to Buy and Sell Stock with Cooldown | 714 Best Time to Buy and Sell Stock with Transaction Fee
author: yoyo
date: 2024-09-11 20:47:00 +0800
categories: [Data Structure and Algorithm, Leetcode, Dynamic Programming, Buy and Sell Stock]
tags: [dynamic programming (DP)]
math: true
image:
  path: /assets/covers/leetcode/leetcode-day-36.png
  alt: Leetcode Day 36 Cover
---

## Dynamic Programming

| Diff                                                                                                | Problem                                                                                 | Python | Java |
|-----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|--------|------|
| ![Hard](https://img.shields.io/badge/Hard-red)                                               | [188 Best Time to Buy and Sell Stock IV](#best-time-to-buy-and-sell-stock-iv)                                 |✅      |       |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [309 Best Time to Buy and Sell Stock with Cooldown](#best-time-to-buy-and-sell-stock-with-cooldown)      |✅      |       |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [714 Best Time to Buy and Sell Stock with Transaction Fee](#best-time-to-buy-and-sell-stock-with-transaction-fee)       |✅      |      |

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


## Best Time to Buy and Sell Stock with Transaction Fee

> [Link to Leetcode question](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-transaction-fee/description/)[^bttbasswtf]
{: .prompt-info }

You are given an array prices where `prices[i]` is the price of a given stock on the ith day, and an integer fee representing a transaction fee.

Find the maximum profit you can achieve. You may complete as many transactions as you like, but you need to pay the transaction fee for each transaction.

**Note**:

You may not engage in multiple transactions simultaneously (i.e., you must sell the stock before you buy again).
The transaction fee is only charged once for each stock purchase and sale.
 

**Example 1**

```yml
Input: prices = [1,3,2,8,4,9], fee = 2
Output: 8
Explanation: The maximum profit can be achieved by:
- Buying at prices[0] = 1
- Selling at prices[3] = 8
- Buying at prices[4] = 4
- Selling at prices[5] = 9
The total profit is ((8 - 1) - 2) + ((9 - 4) - 2) = 8.
```

**Example 2**

```yml
Input: prices = [1,3,7,5,10,3], fee = 3
Output: 6
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0714.买卖股票的最佳时机含手续费（动态规划）.html)[^bttbasswtfSolution].

#### Python

```python
class Solution(object):
    def maxProfit(self, prices, fee):
        dp = [[0,0] for _ in range(len(prices))]
        dp[0][0] = -prices[0]

        for day in range(1,len(prices)):
            dp[day][0] = max(dp[day - 1][0], dp[day - 1][1] - prices[day]) #持有股票状态
            dp[day][1] = max(dp[day - 1][0] + prices[day] - fee, dp[day - 1][1]) #已卖出股票状态
        
        return max(dp[-1])
```

```python
class Solution(object):
    def maxProfit(self, prices, fee):
        hold_stock = -prices[0]
        not_hold_stock = 0

        for day in range(1,len(prices)):
            hold_stock, not_hold_stock = max(hold_stock, not_hold_stock - prices[day]), max(hold_stock + prices[day] - fee, not_hold_stock) 
        
        return max(hold_stock, not_hold_stock)
```



## Reference

[^bttbassiv]:Leetcode-188 Best Time to Buy and Sell Stock IV: [https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv/description/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv/description/).
[^bttbassivSolution]:代码随想录-买卖股票的最佳时机IV: [https://programmercarl.com/0188.买卖股票的最佳时机IV.html](https://programmercarl.com/0188.买卖股票的最佳时机IV.html).
[^bttbasswc]:Leetcode-309 Best Time to Buy and Sell Stock with Cooldown: [https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/description/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/description/).
[^bttbasswcSolution]:代码随想录-最佳买卖股票时机含冷冻期: [https://programmercarl.com/0309.最佳买卖股票时机含冷冻期.html
](https://programmercarl.com/0309.最佳买卖股票时机含冷冻期.html).
[^bttbasswtf]:Leetcode-714 Best Time to Buy and Sell Stock with Transaction Fee: [https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-transaction-fee/description/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-transaction-fee/description/).
[^bttbasswtfSolution]:代码随想录-买卖股票的最佳时机含手续费（动态规划）: [https://programmercarl.com/0714.买卖股票的最佳时机含手续费（动态规划）.html](https://programmercarl.com/0714.买卖股票的最佳时机含手续费（动态规划）.html).

