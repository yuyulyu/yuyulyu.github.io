---
title: "Leetcode Day 37 - DP: Subsequence"
description: 300 Longest Increasing Subsequence | 
author: yoyo
date: 2024-09-12 09:53:00 +0800
categories: [Data Structure and Algorithm, Leetcode, Dynamic Programming, Subsequence]
tags: [dynamic programming (DP)]
---

![Easy](https://img.shields.io/badge/Easy-brightgreen) 
![Medium](https://img.shields.io/badge/Medium-yellow)
![Hard](https://img.shields.io/badge/Hard-red)

## Dynamic Programming

| Diff                                                                                                | Problem                                                                                 | Python | Java |
|-----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [300 Longest Increasing Subsequence](#longest-increasing-subsequence)                   |✅      |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [19 Remove Nth Node From End of List](#the-link)                |        |      |
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                              | [160 Intersection of Two Linked Lists](#the-link)               |        |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [142 Linked List Cycle II](#the-link)                                       |        |      |

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
        dp = [[1,0] for _ in range(len(nums))] 
        
        for i in range(1, len(nums)):
            dp[i][1] = max(dp[i - 1])
            for j in range(i - 1, -1, -1):
                if nums[j] < nums[i]:
                    dp[i][0] = max(dp[j][0] + 1, dp[i][0])

        return max(dp[-1])
```

### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [1721 Swapping Nodes in a Linked List](https://leetcode.com/problems/swapping-nodes-in-a-linked-list/description/)[^sniall] |        |      |
| ![Hard](https://img.shields.io/badge/Hard-red)                                                       | [25 Reverse Nodes in k-Group](https://leetcode.com/problems/reverse-nodes-in-k-group/)[^rnikg]          |        |      |


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

[^lis]:Leetcode-300 Longest Increasing Subsequence: [https://leetcode.com/problems/longest-increasing-subsequence/description/](https://leetcode.com/problems/longest-increasing-subsequence/description/).
[^lisSolution]:代码随想录-最长上升子序列: [https://programmercarl.com/0300.最长上升子序列.html](https://programmercarl.com/0300.最长上升子序列.html).

