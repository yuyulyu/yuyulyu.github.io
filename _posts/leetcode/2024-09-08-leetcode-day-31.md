---
title: Leetcode Day 31 - Dynamic Programming
description: 416 Partition Equal Subset Sum | 1049 Last Stone Weight II | 494 Target Sum ｜ 474 Ones and Zeroes
author: yoyo
date: 2024-09-08 10:43:00 +0800
categories: [Data Structure and Algorithm, Leetcode, Dynamic Programming]
tags: [dynamic programming (DP)]
---


## Dynamic Programming 

> [Link to note about Dynamic Programming](https://yuyulyu.github.io/posts/dynamic-programming/) 
{: .prompt-tip }

| Diff                                                                                         | Problem                                                                                             | Python | C<sup>++</sup> |
|----------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------|--------|--------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                        | [416 Partition Equal Subset Sum](#partition-equal-subset-sum)                                    |✅      |        |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                        | [1049 Last Stone Weight II](#last-stone-weight-ii)                                                 |✅      |        |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                        | [494 Target Sum](#target-sum)                                                                       |✅      |✅      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                        | [474 Ones and Zeroes](#ones-and-zeroes)                                                          |✅      |        |

## Partition Equal Subset Sum

> [Link to Leetcode question](https://leetcode.com/problems/partition-equal-subset-sum/description/)[^pess]
{: .prompt-info }

Given an integer array `nums`, return `true` if you can partition the array into two subsets such that the sum of the elements in both subsets is equal or `false` otherwise.

**Example 1**

```
Input: nums = [1,5,11,5]
Output: true
Explanation: The array can be partitioned as [1, 5, 5] and [11].
```

**Example 2**

```
Input: nums = [1,2,3,5]
Output: false
Explanation: The array cannot be partitioned into equal sum subsets.
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0416.分割等和子集.html)[^pessSolution].

#### Python

```python
class Solution(object):
    def canPartition(self, nums):
        N = sum(nums)
        if N % 2 == 1: return False
        target = N // 2

        dp = [0] * (target + 1)

        for num in nums:
            for i in range(target, num - 1, -1):
                dp[i] = max(dp[i], dp[i - num] + num)
        
        return dp[target] == target
```


### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [698 Partition to K Equal Sum Subsets](https://leetcode.com/problems/partition-to-k-equal-sum-subsets/description/)[^pkess] |        |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                       | [1981 Minimize the Difference Between Target and Chosen Elements](https://leetcode.com/problems/minimize-the-difference-between-target-and-chosen-elements/description/)[^mtdbta]          |        |      |
| ![Hard](https://img.shields.io/badge/Hard-red)                                                       | [2025 Maximum Number of Ways to Partition an Array](https://leetcode.com/problems/maximum-number-of-ways-to-partition-an-array/description/)[^mnwpa]          |        |      |
| ![Hard](https://img.shields.io/badge/Hard-red)                                                       | [2035 Partition Array Into Two Arrays to Minimize Sum Difference](https://leetcode.com/problems/partition-array-into-two-arrays-to-minimize-sum-difference/description/)[^pamitmsd]          |        |      |


## Last Stone Weight II

> [Link to Leetcode question](https://leetcode.com/problems/last-stone-weight-ii/description/)[^lswii]
{: .prompt-info }

You are given an array of integers stones where `stones[i]` is the weight of the `i<sup>th</sup>` stone.

We are playing a game with the stones. On each turn, we choose any two stones and smash them together. Suppose the stones have weights `x` and `y` with `x <= y`. The result of this smash is:

- If `x == y`, both stones are destroyed, and
- If `x != y`, the stone of weight `x` is destroyed, and the stone of weight `y` has new weight `y - x`.
- At the end of the game, there is at most one stone left.

Return the smallest possible weight of the left stone. If there are no stones left, return `0`.

**Example 1**

```
Input: stones = [2,7,4,1,8,1]
Output: 1
Explanation:
We can combine 2 and 4 to get 2, so the array converts to [2,7,1,8,1] then,
we can combine 7 and 8 to get 1, so the array converts to [2,1,1,1] then,
we can combine 2 and 1 to get 1, so the array converts to [1,1,1] then,
we can combine 1 and 1 to get 0, so the array converts to [1], then that's the optimal value.
```

**Example 2**

```
Input: stones = [31,26,33,21,40]
Output: 5
```


### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/1049.最后一块石头的重量II.html)[^lswiiSolution].

#### Python

```python
class Solution(object):
    def lastStoneWeightII(self, stones):
        s = sum(stones)
        target = s // 2

        dp = [0] * (target + 1)

        for stone in stones:
            for j in range(target, stone - 1, -1):
                dp[j] = max(dp[j], dp[j - stone] + stone)
        
        return s - 2 * dp[target]
```


## Target Sum

> [Link to Leetcode question](https://leetcode.com/problems/target-sum/description/)[^]:]
{: .prompt-info }

You are given an integer array `nums` and an integer `target`.

You want to build an expression out of `nums` by adding one of the symbols `'+'` and `'-'` before each integer in `nums` and then concatenate all the integers.

For example, if nums = `[2, 1]`, you can add a `'+'` before 2 and a `'-'` before 1 and concatenate them to build the expression "+2-1".
Return the number of different expressions that you can build, which evaluates to `target`. 

**Example 1**

```
Input: nums = [1,1,1,1,1], target = 3
Output: 5
Explanation: There are 5 ways to assign symbols to make the sum of nums be target 3.
-1 + 1 + 1 + 1 + 1 = 3
+1 - 1 + 1 + 1 + 1 = 3
+1 + 1 - 1 + 1 + 1 = 3
+1 + 1 + 1 - 1 + 1 = 3
+1 + 1 + 1 + 1 - 1 = 3
```

**Example 2**

```
Input: nums = [1], target = 1
Output: 1
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0494.目标和.html)[^]:Solution].
#### Python

```python
from collections import Counter
class Solution(object):
    def findTargetSumWays(self, nums, target):

        # Pruning
        target = abs(target)
        if len(nums) == 1: return 1 if nums[0] == target else 0
        
        s = sum(nums)
        if s < target or s % 2 != target % 2: return 0

        # Initialize backpacking problem
        target = (s - target) // 2
        dp = [0] * (target + max(nums) + 1)
        dp[0] = 1

        # Backpacking
        for num in nums:
            if num == 0: continue
            for i in range(target, num - 1, -1):
                dp[i] += dp[i - num]
        
        # Return result
        counter = Counter(nums)
        return dp[target] * (2 ** counter[0])
```

#### C++

```c++
class Solution {
public:
    int findTargetSumWays(vector<int>& nums, int target) {
        // Pruning
        target = abs(target);
        if (nums.size() == 1) return nums[0] == target ? 1 : 0;

        int s = accumulate(nums.begin(), nums.end(), 0);
        if (s < target || (s - target) % 2 != 0) return 0;

        // Initializaiton
        target = (s - target) / 2;
        vector<int> dp(target + 1, 0);
        dp[0] = 1;
        int zeros = count(nums.begin(), nums.end(), 0);

        // Backpacking
        for (int num : nums) {
            if (num == 0) continue;
            for (int j = target; j >= num; j--) {
                dp[j] += dp[j - num];
            }
        }

        // Return result
        return dp[target] * pow(2, zeros);
    }
};

```

### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [2787 Ways to Express an Integer as Sum of Powers](https://leetcode.com/problems/ways-to-express-an-integer-as-sum-of-powers/description/)[^weisop] |        |      |
| ![Hard](https://img.shields.io/badge/Hard-red)                                                | [282 Expression Add Operators](https://leetcode.com/problems/expression-add-operators/)[^eao] |        |      |



## Ones and Zeroes

> [Link to Leetcode question](https://leetcode.com/problems/ones-and-zeroes/description/)[^oaz]
{: .prompt-info }

You are given an array of binary strings `strs` and two integers `m` and `n`.

Return the size of the largest subset of `strs` such that there are at most `m` `0`s and `n` `1`'s in the subset.

A set `x` is a subset of a set `y` if all elements of `x` are also elements of `y`.

**Example 1**

```
Input: strs = ["10","0001","111001","1","0"], m = 5, n = 3
Output: 4
Explanation: The largest subset with at most 5 0's and 3 1's is {"10", "0001", "1", "0"}, so the answer is 4.
Other valid but smaller subsets include {"0001", "1"} and {"10", "1", "0"}.
{"111001"} is an invalid subset because it contains 4 1's, greater than the maximum of 3.
```

**Example 2**

```
Input: strs = ["10","0","1"], m = 1, n = 1
Output: 2
Explanation: The largest subset is {"0", "1"}, so the answer is 2.
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0474.一和零.html)[^oazSolution].



#### Python

```python
class Solution(object):
    def findMaxForm(self, strs, m, n):
        dp = [[0] * (n + 1) for _ in range(m + 1)]

        for s in strs:
            zeros, ones = s.count('0'), s.count('1')

            for M in range(m, zeros - 1, -1):
                for N in range(n, ones - 1, -1):
                    dp[M][N] = max(dp[M][N], dp[M - zeros][N - ones] + 1)

        return dp[m][n]
```

### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Hard](https://img.shields.io/badge/Hard-red)                                                | [600 Non-negative Integers without Consecutive Ones](https://leetcode.com/problems/non-negative-integers-without-consecutive-ones/description/)[^nniwco] |        |      |





## Reference

[^pess]:Leetcode-416 Partition Equal Subset Sum: [https://leetcode.com/problems/partition-equal-subset-sum/description/](https://leetcode.com/problems/partition-equal-subset-sum/description/).
[^pessSolution]:代码随想录-分割等和子集: [https://programmercarl.com/0416.分割等和子集.html](https://programmercarl.com/0416.分割等和子集.html).
[^pkess]: Leetcode-698 Partition to K Equal Sum Subsets: [https://leetcode.com/problems/partition-to-k-equal-sum-subsets/description/](https://leetcode.com/problems/partition-to-k-equal-sum-subsets/description/).
[^mtdbta]: Leetcode-1981 Minimize the Difference Between Target and Chosen Elements: [https://leetcode.com/problems/minimize-the-difference-between-target-and-chosen-elements/description/](https://leetcode.com/problems/minimize-the-difference-between-target-and-chosen-elements/description/).
[^mnwpa]: Leetcode-2025 Maximum Number of Ways to Partition an Array: [https://leetcode.com/problems/maximum-number-of-ways-to-partition-an-array/description/](https://leetcode.com/problems/maximum-number-of-ways-to-partition-an-array/description/).
[^pamitmsd]: Leetcode-2035 Partition Array Into Two Arrays to Minimize Sum Difference: [https://leetcode.com/problems/partition-array-into-two-arrays-to-minimize-sum-difference/description/](https://leetcode.com/problems/partition-array-into-two-arrays-to-minimize-sum-difference/description/).
[^lswii]:Leetcode-1049 Last Stone Weight II: [https://leetcode.com/problems/last-stone-weight-ii/description/](https://leetcode.com/problems/last-stone-weight-ii/description/).
[^lswiiSolution]:代码随想录-最后一块石头的重量II: [https://programmercarl.com/1049.最后一块石头的重量II.html](https://programmercarl.com/1049.最后一块石头的重量II.html).
[^ts]:Leetcode-494 Target Sum: [https://leetcode.com/problems/target-sum/description/](https://leetcode.com/problems/target-sum/description/).
[^tsSolution]:代码随想录-目标和: [https://programmercarl.com/0494.目标和.html](https://programmercarl.com/0494.目标和.html).
[^weisop]: Leetcode-2787 Ways to Express an Integer as Sum of Powers: [https://leetcode.com/problems/ways-to-express-an-integer-as-sum-of-powers/description/](https://leetcode.com/problems/ways-to-express-an-integer-as-sum-of-powers/description/).
[^eao]: Leetcode-282 Expression Add Operators: [https://leetcode.com/problems/expression-add-operators/](https://leetcode.com/problems/expression-add-operators/).
[^oaz]:Leetcode-474 Ones and Zeroes: [https://leetcode.com/problems/ones-and-zeroes/description/](https://leetcode.com/problems/ones-and-zeroes/description/).
[^oazSolution]:代码随想录-一和零: [https://programmercarl.com/0474.一和零.html](https://programmercarl.com/0474.一和零.html).
[^nniwco]:Leetcode-600 Non-negative Integers without Consecutive Ones : [https://leetcode.com/problems/non-negative-integers-without-consecutive-ones/description/](https://leetcode.com/problems/non-negative-integers-without-consecutive-ones/description/).
