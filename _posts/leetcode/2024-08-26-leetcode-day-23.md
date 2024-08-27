---
title: Leetcode Day 23 - Greedy Algorithm
description: 455 Assign Cookies | 376 Wiggle Subsequence | 53 Maximum Subarray
author: yoyo
date: 2024-08-26 14:00:00 +0800
categories: [Data Structure and Algorithm, Leetcode]
tags: [greedy]
---

## Greedy Algorithm 

| Diff                                                                                                | Problem                                                                                 | Python | Java |
|-----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|--------|------|
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                                | [455 Assign Cookies](#assign-cookies)                                     |✅      |        |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [376 Wiggle Subsequence](#wiggle-subsequence)                             |✅      |        |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [53 Maximum Subarray](#maximum-subarray)                                 |✅      |        |

## Assign Cookies

> [Link to Leetcode question](https://leetcode.com/problems/assign-cookies/description/)[^ac]
{: .prompt-info }

Assume you are an awesome parent and want to give your children some cookies. But, you should give each child at most one cookie.

Each child `i` has a greed factor `g[i]`, which is the minimum size of a cookie that the child will be content with; and each cookie `j` has a size `s[j]`. If `s[j] >= g[i]`, we can assign the cookie `j` to the child `i`, and the child `i` will be content. Your goal is to maximize the number of your content children and output the maximum number.

**Example 1**

```
Input: g = [1,2,3], s = [1,1]
Output: 1
Explanation: You have 3 children and 2 cookies. The greed factors of 3 children are 1, 2, 3. 
And even though you have 2 cookies, since their size is both 1, you could only make the child whose greed factor is 1 content.
You need to output 1.
```

**Example 2**

```
Input: g = [1,2], s = [1,2,3]
Output: 2
Explanation: You have 2 children and 3 cookies. The greed factors of 2 children are 1, 2. 
You have 3 cookies and their sizes are big enough to gratify all of the children, 
You need to output 2.
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0455.分发饼干.html)[^acSolution].

#### Python

```python
class Solution(object):
    def findContentChildren(self, g, s):
        g.sort()
        s.sort()
        i = 0
        count = 0
        ls = len(s)

        for child in g:
            while i < ls:
                i += 1
                if s[i - 1] >= child:
                    count += 1
                    break
        
        return count
```

## Wiggle Subsequence

> [Link to Leetcode question](https://leetcode.com/problems/wiggle-subsequence/description/)[^ws]
{: .prompt-info }

A **wiggle sequenc**e is a sequence where the differences between successive numbers strictly alternate between positive and negative. The first difference (if one exists) may be either positive or negative. A sequence with one element and a sequence with two non-equal elements are trivially wiggle sequences.

- For example, `[1, 7, 4, 9, 2, 5]` is a wiggle sequence because the differences `(6, -3, 5, -7, 3)` alternate between positive and negative.
- In contrast, `[1, 4, 7, 2, 5]` and `[1, 7, 4, 5, 5]` are not wiggle sequences. The first is not because its first two differences are positive, and the second is not because its last difference is zero.

A subsequence is obtained by deleting some elements (possibly zero) from the original sequence, leaving the remaining elements in their original order.

Given an integer array `nums`, return the length of the longest wiggle subsequence of `nums`.

**Example 1**

> **Input**: nums = [1,7,4,9,2,5]<br>
> **Output**: 6<br>
> **Explanation**: The entire sequence is a wiggle sequence with differences (6, -3, 5, -7, 3).

**Example 2**

```
Input: nums = [1,17,5,10,13,15,10,5,16,8]
Output: 7
Explanation: There are several subsequences that achieve this length.
One is [1, 17, 10, 13, 10, 16, 8] with differences (16, -7, 3, -3, 6, -8).
```

**Example 3**

```
Input: nums = [1,2,3,4,5,6,7,8,9]
Output: 2
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0376.摆动序列.html)[^wsSolution].

#### Python

```python
class Solution(object):
    def wiggleMaxLength(self, nums):
        if len(nums) == 1:
            return 1
        if len(nums) == 2:
            return 2 if nums[1] - nums[0] != 0 else 1

        prv_diff = nums[1] - nums[0]
        count = 2 if prv_diff != 0 else 1

        for i in range(2,len(nums)):
            cur_diff = nums[i] - nums[i - 1]
            if cur_diff * prv_diff < 0 or (count == 1 and cur_diff != 0):
                count += 1
                prv_diff = cur_diff
            if count == 1:
                prv_diff = cur_diff
            
        
        return count
```

### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [2149 Rearrange Array Elements by Sign](https://leetcode.com/problems/rearrange-array-elements-by-sign/)[^raebs] |        |      |


## Maximum Subarray

> [Link to Leetcode question](https://leetcode.com/problems/maximum-subarray/description/)[^ms]
{: .prompt-info }

Given an integer array nums, find the subarray with the largest sum, and return its sum.

**Example 1**

```
Input: nums = [-2,1,-3,4,-1,2,1,-5,4]
Output: 6
Explanation: The subarray [4,-1,2,1] has the largest sum 6.
```

**Example 2**

```
Input: nums = [1]
Output: 1
Explanation: The subarray [1] has the largest sum 1.
```

**Example 3**

```
Input: nums = [5,4,-1,7,8]
Output: 23
Explanation: The subarray [5,4,-1,7,8] has the largest sum 23.
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0053.最大子序和.html)[^msSolution].

#### Python

```python
class Solution(object):
    def maxSubArray(self, nums):
        if len(nums) == 1:
            return nums[0]

        cur_sum = min(nums[0],0)
        max_sum = cur_sum
        flag = False

        for fast in range(len(nums)):
            if cur_sum <= 0 and not flag and max_sum <= 0:
                max_sum = max(nums[fast], max_sum)
                cur_sum = max_sum
                continue
            if nums[fast] < 0:
                if not flag:
                    max_sum = max(max_sum, cur_sum)
                    flag = True
                cur_sum += nums[fast]
                continue
            
            if flag:
                flag = False
                if cur_sum <= 0:
                    cur_sum = 0

            cur_sum += nums[fast]
        
        max_sum = max(max_sum, cur_sum) 
        return max_sum
```


### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [152 Maximum Product Subarray](https://leetcode.com/problems/maximum-product-subarray/description/)[^mps] |        |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [978 Longest Turbulent Subarray](https://leetcode.com/problems/longest-turbulent-subarray/description/)[^lts] |        |      |
| ![Hard](https://img.shields.io/badge/Hard-red)                                                | [2321 Maximum Score Of Spliced Array](https://leetcode.com/problems/maximum-score-of-spliced-array/)[^msosa] |        |      |



## Reference

[^ac]:Leetcode-455 Assign Cookies: [https://leetcode.com/problems/assign-cookies/description/](https://leetcode.com/problems/assign-cookies/description/).
[^acSolution]:代码随想录-分发饼干: [https://programmercarl.com/0455.分发饼干.html](https://programmercarl.com/0455.分发饼干.html).
[^ws]:Leetcode-376 Wiggle Subsequence: [https://leetcode.com/problems/wiggle-subsequence/description/](https://leetcode.com/problems/wiggle-subsequence/description/).
[^wsSolution]:代码随想录-摆动序列: [https://programmercarl.com/0376.摆动序列.html](https://programmercarl.com/0376.摆动序列.html).
[^raebs]:Leetcode-2149 Rearrange Array Elements by Sign: [https://leetcode.com/problems/rearrange-array-elements-by-sign/](https://leetcode.com/problems/rearrange-array-elements-by-sign/).
[^ms]:Leetcode-53 Maximum Subarray: [https://leetcode.com/problems/maximum-subarray/description/](https://leetcode.com/problems/maximum-subarray/description/).
[^msSolution]:代码随想录-最大子序和: [https://programmercarl.com/0053.最大子序和.html](https://programmercarl.com/0053.最大子序和.html).
[^mps]: Leetcode-152 Maximum Product Subarray: [https://leetcode.com/problems/maximum-product-subarray/description/](https://leetcode.com/problems/maximum-product-subarray/description/).
[^lts]: Leetcode-978 Longest Turbulent Subarray: [https://leetcode.com/problems/longest-turbulent-subarray/description/](https://leetcode.com/problems/longest-turbulent-subarray/description/).
[^msosa]: Leetcode-2321 Maximum Score Of Spliced Array: [https://leetcode.com/problems/maximum-score-of-spliced-array/](https://leetcode.com/problems/maximum-score-of-spliced-array/).


