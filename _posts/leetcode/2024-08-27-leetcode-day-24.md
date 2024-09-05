---
title: Leetcode Day 24 - Greedy Algorithm
description: 122 Best Time to Buy and Sell Stock II | 55 Jump Game | 45 Jump Game II | 1005 Maximize Sum Of Array After K Negations
author: yoyo
date: 2024-08-27 12:29:00 +0800
categories: [Data Structure and Algorithm, Leetcode]
tags: [greedy algorithm]
---

## Greedy Algorithm 

| Diff                                                                                                | Problem                                                                                 | Python | Java |
|-----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [122 Best Time to Buy and Sell Stock II](#best-time-to-buy-and-sell-stock-ii)                    |✅      |        |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [55 Jump Game](#jump-game)                                                                         |✅      |        |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [45 Jump Game II](#jump-game-ii)                                                               |✅      |        |
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                                | [1005 Maximize Sum Of Array After K Negations](#maximize-sum-of-array-after-k-negations)                                                               |✅      |        |

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

> A detailed explaination of solution can be found [here](https://programmercarl.com/0122.买卖股票的最佳时机II.html)[^bttbassiiSolution].

#### Python

```python
class Solution(object):
    def maxProfit(self, prices):
        stack = []
        buy = prices[0]
        sell = prices[0]

        def add(buy, sell):
            if len(stack) != 0:
                prv = stack[-1]
                if buy > prv[1]:
                    stack.pop()
                    stack.append([prv[0],sell])
                else:
                    stack.append([buy,sell])
                
            elif buy != sell:
                stack.append([buy,sell])

        for i in range(1, len(prices)):
            
            p = prices[i]
            if p < buy:
                if buy != sell:
                    add(buy, sell)
                    buy, sell = prices[i], prices[i]
                buy = p
                sell = p
                continue
            elif p > sell:
                sell = p
                continue
            elif buy != sell:
                add(buy, sell)
                buy, sell = prices[i], prices[i]
        
        if buy != sell:
            stack.append([buy,sell])
        
        profit = 0
        for deal in stack:
            profit += deal[1] - deal[0]
        
        return profit
```

```python
class Solution(object):
    def maxProfit(self, prices):
        result = 0
        for i in range(1, len(prices)):
            result += max(prices[i] - prices[i - 1], 0)
        return result
```

### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [309 Best Time to Buy and Sell Stock with Cooldown](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/description/)[^bttbasswc] |        |      |
| ![Hard](https://img.shields.io/badge/Hard-red)                                                       | [123 Best Time to Buy and Sell Stock III](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii/description/)[^stockiii]          |        |      |
| ![Hard](https://img.shields.io/badge/Hard-red)                                                       | [188 Best Time to Buy and Sell Stock IV](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv/description/)[^stockiv]          |        |      |


## Jump Game

> [Link to Leetcode question](https://leetcode.com/problems/jump-game/description/)[^jg]
{: .prompt-info }

You are given an integer array `nums`. You are initially positioned at the array's first index, and each element in the array represents your maximum jump length at that position.

Return `true` if you can reach the last index, or `false` otherwise.

**Example 1**

```
Input: nums = [2,3,1,1,4]
Output: true
Explanation: Jump 1 step from index 0 to 1, then 3 steps to the last index.
```

**Example 2**

```
Input: nums = [3,2,1,0,4]
Output: false
Explanation: You will always arrive at index 3 no matter what. Its maximum jump length is 0, which makes it impossible to reach the last index.
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0055.跳跃游戏.html)[^jgSolution].

#### Python

```python
class Solution(object):
    def canJump(self, nums):
        last_pos = len(nums) - 1
        
        for i in range(len(nums) - 2, -1, -1):
            if i + nums[i] >= last_pos:
                last_pos = i
        
        return last_pos == 0
```



## Jump Game II

> [Link to Leetcode question](https://leetcode.com/problems/jump-game-ii/)[^jgiii]
{: .prompt-info }

You are given a 0-indexed array of integers `nums` of length `n`. You are initially positioned at `nums[0]`.

Each element `nums[i]` represents the maximum length of a forward jump from index `i`. In other words, if you are at `nums[i]`, you can jump to any `nums[i + j]` where:

- `0 <= j <= nums[i]` and
- `i + j < n`

Return the minimum number of jumps to reach `nums[n - 1]`. The test cases are generated such that you can reach `nums[n - 1]`.

**Example 1**

```
Input: nums = [2,3,1,1,4]
Output: 2
Explanation: The minimum number of jumps to reach the last index is 2. Jump 1 step from index 0 to 1, then 3 steps to the last index.
```

**Example 2**

```
Input: nums = [2,3,0,1,4]
Output: 2
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0045.跳跃游戏II.html)[^jgiiiSolution].

#### Python

```python
class Solution(object):
    def jump(self, nums):
        if len(nums) == 1:
            return 0

        last_pos = len(nums) - 1
        stack = []
        
        for i in range(len(nums) - 2, -1, -1):
            if i + nums[i] >= last_pos:
                stack.append(i)
        while len(stack) != 0:
            i = stack[-1]
            stack.pop()
            result = self.jump(nums[:i + 1])
            if result != -1:
                return result + 1
        
        return - 1
```

```python
class Solution(object):
    def jump(self, nums):
        if len(nums) == 1:
            return 0
        
        cur_distance = 0  # 当前覆盖最远距离下标
        ans = 0  # 记录走的最大步数
        next_distance = 0  # 下一步覆盖最远距离下标
        
        for i in range(len(nums)):
            next_distance = max(nums[i] + i, next_distance)  # 更新下一步覆盖最远距离下标
            if i == cur_distance:  # 遇到当前覆盖最远距离下标
                ans += 1  # 需要走下一步
                cur_distance = next_distance  # 更新当前覆盖最远距离下标（相当于加油了）
                if next_distance >= len(nums) - 1:  # 当前覆盖最远距离达到数组末尾，不用再做ans++操作，直接结束
                    break
        
        return ans
```

### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [1306 Jump Game III](https://leetcode.com/problems/jump-game-iii/description/)[^jgiii] |        |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [1871 Jump Game VII](https://leetcode.com/problems/jump-game-vii/description/)[^jgvii] |        |      |


## Maximize Sum Of Array After K Negations

> [Link to Leetcode question](https://leetcode.com/problems/maximize-sum-of-array-after-k-negations/description/)[^msoaakn]
{: .prompt-info }

Given an integer array `nums` and an integer `k`, modify the array in the following way:

- choose an index `i` and replace `nums[i]` with `-nums[i]`.
- You should apply this process exactly `k` times. You may choose the same index `i` multiple times.

Return the largest possible sum of the array after modifying it in this way.

**Example 1**

```
Input: nums = [4,2,3], k = 1
Output: 5
Explanation: Choose index 1 and nums becomes [4,-2,3].
```

**Example 2**

```
Input: nums = [3,-1,0,2], k = 3
Output: 6
Explanation: Choose indices (1, 2, 2) and nums becomes [3,1,0,2].
```

**Example 3**

```
Input: nums = [2,-3,-1,5,-4], k = 2
Output: 13
Explanation: Choose indices (1, 4) and nums becomes [2,3,-1,5,4].
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/1005.K次取反后最大化的数组和.html)[^msoaaknSolution].

#### Python

```python
class Solution(object):
    def largestSumAfterKNegations(self, nums, k):
        nums.sort(key=lambda x: abs(x), reverse=True)

        for i in range(len(nums)):
            if nums[i] < 0:
                if k > 0:
                    nums[i] = - nums[i]
                    k -= 1
        
        if k % 2 == 1:
            nums[-1] = -nums[-1]
        
        return sum(nums)
```

### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [2099 Find Subsequence of Length K With the Largest Sum](https://leetcode.com/problems/find-subsequence-of-length-k-with-the-largest-sum/description/)[^abc] |        |      |




## Reference
[^bttbassii]:Leetcode-122 Best Time to Buy and Sell Stock II: [https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/description/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/description/).
[^bttbassiiSolution]:代码随想录-买卖股票的最佳时机II: [https://programmercarl.com/0122.买卖股票的最佳时机II.html](https://programmercarl.com/0122.买卖股票的最佳时机II.html).
[^bttbasswc]: Leetcode-309 Best Time to Buy and Sell Stock with Cooldown: [https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/description/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/description/).
[^stockiii]: Leetcode-123 Best Time to Buy and Sell Stock III: [https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii/description/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii/description/).
[^stockiv]: Leetcode-188 Best Time to Buy and Sell Stock IV: [https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv/description/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv/description/).
[^jg]:Leetcode-55 Jump Game: [https://leetcode.com/problems/jump-game/description/](https://leetcode.com/problems/jump-game/description/).
[^jgSolution]:代码随想录-跳跃游戏: [https://programmercarl.com/0055.跳跃游戏.html](https://programmercarl.com/0055.跳跃游戏.html).
[^jgiii]:Leetcode-45 Jump Game II: [https://leetcode.com/problems/jump-game-ii/](https://leetcode.com/problems/jump-game-ii/).
[^jgiiiSolution]:代码随想录-跳跃游戏II: [https://programmercarl.com/0045.跳跃游戏II.html](https://programmercarl.com/0045.跳跃游戏II.html).
[^jgiii]: Leetcode-1306 Jump Game III: [https://leetcode.com/problems/jump-game-iii/description/](https://leetcode.com/problems/jump-game-iii/description/).
[^jgvii]: Leetcode-1871 Jump Game VII: [https://leetcode.com/problems/jump-game-vii/description/](https://leetcode.com/problems/jump-game-vii/description/).
[^msoaakn]:Leetcode-1005 Maximize Sum Of Array After K Negations: [https://leetcode.com/problems/maximize-sum-of-array-after-k-negations/description/](https://leetcode.com/problems/maximize-sum-of-array-after-k-negations/description/).
[^msoaaknSolution]:代码随想录-K次取反后最大化的数组和: [https://programmercarl.com/1005.K次取反后最大化的数组和.html](https://programmercarl.com/1005.K次取反后最大化的数组和.html).
[^abc]:leetcode-2099 Find Subsequence of Length K With the Largest Sum: [https://leetcode.com/problems/find-subsequence-of-length-k-with-the-largest-sum/description/](https://leetcode.com/problems/find-subsequence-of-length-k-with-the-largest-sum/description/).

