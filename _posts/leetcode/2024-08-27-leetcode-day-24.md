---
title: Leetcode Day 24 - Greedy Algorithm
description: 122 Best Time to Buy and Sell Stock II |
author: yoyo
date: 2024-08-27 12:29:00 +0800
categories: [Data Structure and Algorithm, Leetcode]
tags: [greedy algorithm]
---

![Easy](https://img.shields.io/badge/Easy-brightgreen) 
![Medium](https://img.shields.io/badge/Medium-yellow)
![Hard](https://img.shields.io/badge/Hard-red)

## Greedy Algorithm 

| Diff                                                                                                | Problem                                                                                 | Python | Java |
|-----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [122 Best Time to Buy and Sell Stock II](#best-time-to-buy-and-sell-stock-ii)                                          |        |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [19 Remove Nth Node From End of List](#the-link)                |        |      |
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                              | [160 Intersection of Two Linked Lists](#the-link)               |        |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [142 Linked List Cycle II](#the-link)                                       |        |      |

# the link

## Best Time to Buy and Sell Stock II

> [Link to Leetcode question](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/description/)[^bttbassii]
{: .prompt-info }

You are given an integer array `prices` where `prices[i]` is the price of a given stock on the i<sup>th</sup> day.

On each day, you may decide to buy and/or sell the stock. You can only hold at most one share of the stock at any time. However, you can buy it then immediately sell it on the same day.

Find and return the maximum profit you can achieve.

**Example 1**

> **Input**: prices = [7,1,5,3,6,4]
> **Output**: 7
> **Explanation**: Buy on day 2 (price = 1) and sell on day 3 (price = 5), profit = 5-1 = 4.
Then buy on day 4 (price = 3) and sell on day 5 (price = 6), profit = 6-3 = 3.
Total profit is 4 + 3 = 7.

**Example 2**

> **Input**: prices = [1,2,3,4,5]
> **Output**: 4
> **Explanation**: Buy on day 1 (price = 1) and sell on day 5 (price = 5), profit = 5-1 = 4.
Total profit is 4.

**Example 3**

> **Input**: prices = [7,6,4,3,1]
> **Output**: 0
> **Explanation**: There is no way to make a positive profit, so we never buy the stock to achieve the maximum profit of 0.

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0122.买卖股票的最佳时机II.html)[^bttbassiiSolution].



### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [309 Best Time to Buy and Sell Stock with Cooldown](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/description/)[^bttbasswc] |        |      |
| ![Hard](https://img.shields.io/badge/Hard-red)                                                       | [123 Best Time to Buy and Sell Stock III](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii/description/)[^stockiii]          |        |      |
| ![Hard](https://img.shields.io/badge/Hard-red)                                                       | [188 Best Time to Buy and Sell Stock IV](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv/description/)[^stockiv]          |        |      |


## <2nd problem>

> [Link to Leetcode question](https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/)[^rnnfeol]
{: .prompt-info }


### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0151.翻转字符串里的单词.html)[^rhsSolution].

### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [2095 Delete the Middle Node of a Linked List](https://leetcode.com/problems/delete-the-middle-node-of-a-linked-list/)[^dtmnoall] |        |      |

## <2nd problem>

> [Link to Leetcode question](https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/)[^rnnfeol]
{: .prompt-info }


### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0151.翻转字符串里的单词.html)[^rhsSolution].

### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [2095 Delete the Middle Node of a Linked List](https://leetcode.com/problems/delete-the-middle-node-of-a-linked-list/)[^dtmnoall] |        |      |



## Reference
[^bttbassii]:Leetcode-122 Best Time to Buy and Sell Stock II: [https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/description/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/description/).
[^bttbassiiSolution]:代码随想录-买卖股票的最佳时机II: [https://programmercarl.com/0122.买卖股票的最佳时机II.html](https://programmercarl.com/0122.买卖股票的最佳时机II.html).
[^bttbasswc]: Leetcode-309 Best Time to Buy and Sell Stock with Cooldown: [https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/description/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/description/).
[^stockiii]: Leetcode-123 Best Time to Buy and Sell Stock III: [https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii/description/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii/description/).
[^stockiv]: Leetcode-188 Best Time to Buy and Sell Stock IV: [https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv/description/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv/description/).
