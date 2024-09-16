---
title: "Leetcode Day 37 - DP: Subsequence"
description: 300 Longest Increasing Subsequence | 674 Longest Continuous Increasing Subsequence | 18 Maximum Length of Repeated Subarray
author: yoyo
date: 2024-09-12 09:53:00 +0800
categories: [Data Structure and Algorithm, Leetcode, Dynamic Programming, Subsequence]
tags: [dynamic programming (DP)]
---

## Dynamic Programming

| Diff                                                                                                | Problem                                                                                 | Python | Java |
|-----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [300 Longest Increasing Subsequence](#longest-increasing-subsequence)                           |✅      |       |
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                              | [674 Longest Continuous Increasing Subsequence](#longest-continuous-increasing-subsequence)     |✅      |       |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [18 Maximum Length of Repeated Subarray](#maximum-length-of-repeated-subarray)                |✅      |       |


## Longest Increasing Subsequence

> [Link to Leetcode question](https://leetcode.com/problems/longest-increasing-subsequence/description/)[^lis]
{: .prompt-info }

Given an integer array `nums`, return the length of the longest strictly increasing subsequence.

**Example 1**

```yml
Input: nums = [10,9,2,5,3,7,101,18]
Output: 4
Explanation: The longest increasing subsequence is [2,3,7,101], therefore the length is 4.
```

**Example 2**

```yml
Input: nums = [0,1,0,3,2,3]
Output: 4
```

**Example 3**

```yml
Input: nums = [7,7,7,7,7,7,7]
Output: 1
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0300.最长上升子序列.html)[^lisSolution].



#### Python

```python
class Solution(object):
    def lengthOfLIS(self, nums):
        dp = [1] * len(nums)
        
        for i in range(1, len(nums)):
            for j in range(i - 1, -1, -1):
                if nums[j] < nums[i]:
                    dp[i] = max(dp[j] + 1, dp[i])

        return max(dp)
```


## Longest Continuous Increasing Subsequence

> [Link to Leetcode question](https://leetcode.com/problems/longest-continuous-increasing-subsequence/description/)[^lcis]
{: .prompt-info }

Given an unsorted array of integers `nums`, return the length of the longest continuous increasing subsequence (i.e. subarray). The subsequence must be strictly increasing.

A continuous increasing subsequence is defined by two indices `l` and `r (l < r)` such that it is `[nums[l], nums[l + 1], ..., nums[r - 1], nums[r]]` and for each `l <= i < r`, `nums[i] < nums[i + 1]`. 

**Example 1**

```yml
Input: nums = [1,3,5,4,7]
Output: 3
Explanation: The longest continuous increasing subsequence is [1,3,5] with length 3.
Even though [1,3,5,7] is an increasing subsequence, it is not continuous as elements 5 and 7 are separated by element
4.
```

**Example 2**

```yml
Input: nums = [2,2,2,2,2]
Output: 1
Explanation: The longest continuous increasing subsequence is [2] with length 1. Note that it must be strictly
increasing.
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0300.最长上升子序列.html)[^rhsSolution].

#### Python

```python
class Solution(object):
    def findLengthOfLCIS(self, nums):
        max_len, cur_len = 1, 1

        for i in range(1, len(nums)):
            if nums[i - 1] < nums[i]:
                cur_len += 1
            else:
                max_len = max(cur_len, max_len)
                cur_len = 1
        
        return max(max_len, cur_len)
```

```python
class Solution(object):
    def findLengthOfLCIS(self, nums):
        result = 1

        dp = [1] * len(nums)

        for i in range(1,len(nums)):
            if nums[i] > nums[i - 1]:
                dp[i] = max(dp[i], dp[i - 1] + 1)
            
            if result < dp[i]: result = dp[i]
        
        return result
```


## Maximum Length of Repeated Subarray

> [Link to Leetcode question](https://leetcode.com/problems/maximum-length-of-repeated-subarray/description/)[^mlors]
{: .prompt-info }

Given two integer arrays `nums1` and `nums2`, return the maximum length of a subarray that appears in both arrays.

**Example 1**

```yml
Input: nums1 = [1,2,3,2,1], nums2 = [3,2,1,4,7]
Output: 3
Explanation: The repeated subarray with maximum length is [3,2,1].
```

**Example 2**

```yml
Input: nums1 = [0,0,0,0,0], nums2 = [0,0,0,0,0]
Output: 5
Explanation: The repeated subarray with maximum length is [0,0,0,0,0].
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0718.最长重复子数组.html)[^mlorsSolution].



#### Python

```python
class Solution(object):
    def findLength(self, nums1, nums2):
        n1, n2 = len(nums1), len(nums2)
        dp = [ [0] * (n1 + 1) for _ in range(n2 + 1) ]

        dp[1][1] = 0 if nums1[0] != nums2[0] else 1

        result = 0

        for b in range(1,n2 + 1):
            for a in range(1,n1 + 1):
                if nums2[b - 1] == nums1[a - 1]:
                    dp[b][a] = dp[b - 1][a - 1] + 1
                    if dp[b][a] > result: result = dp[b][a]

        return result
```




## Reference

[^lis]:Leetcode-300 Longest Increasing Subsequence: [https://leetcode.com/problems/longest-increasing-subsequence/description/](https://leetcode.com/problems/longest-increasing-subsequence/description/).
[^lisSolution]:代码随想录-最长上升子序列: [https://programmercarl.com/0300.最长上升子序列.html](https://programmercarl.com/0300.最长上升子序列.html).
[^lcis]:Leetcode-674 Longest Continuous Increasing Subsequence: [https://leetcode.com/problems/longest-continuous-increasing-subsequence/description/](https://leetcode.com/problems/longest-continuous-increasing-subsequence/description/).
[^lcisSolution]:代码随想录-最长上升子序列: [https://programmercarl.com/0300.最长上升子序列.html](https://programmercarl.com/0300.最长上升子序列.html).
[^mlors]:Leetcode-18 Maximum Length of Repeated Subarray: [https://leetcode.com/problems/maximum-length-of-repeated-subarray/description/](https://leetcode.com/problems/maximum-length-of-repeated-subarray/description/).
[^mlorsSolution]:代码随想录-最长重复子数组: [https://programmercarl.com/0718.最长重复子数组.html](https://programmercarl.com/0718.最长重复子数组.html).





