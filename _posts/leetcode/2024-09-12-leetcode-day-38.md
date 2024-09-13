---
title: "Leetcode Day 38 - DP: Subsequence"
description: 1143 Longest Common Subsequence | 1035 Uncrossed Lines
author: yoyo
date: 2042-09-12 15:26:00 +0800
categories: [Data Structure and Algorithm, Leetcode, Dynamic Programming]
tags: [dynamic programming (DP)]
---

![Easy](https://img.shields.io/badge/Easy-brightgreen) 
![Medium](https://img.shields.io/badge/Medium-yellow)
![Hard](https://img.shields.io/badge/Hard-red)

## Dynamic Programming

| Diff                                                                                                | Problem                                                                                 | Python | Java |
|-----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [1143 Longest Common Subsequence](#longest-common-subsequence)              |✅      |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [1035 Uncrossed Lines](#uncrossed-lines)                                     |✅      |      |
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                              | [160 Intersection of Two Linked Lists](#the-link)               |        |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [142 Linked List Cycle II](#the-link)                                       |        |      |

# the link

## 1143 Longest Common Subsequence

> [Link to Leetcode question](https://leetcode.com/problems/swap-nodes-in-pairs/description/)[^lcs]
{: .prompt-info }

Given two strings `text1` and `text2`, return the length of their longest common subsequence. If there is no common subsequence, return `0`.

A subsequence of a string is a new string generated from the original string with some characters (can be none) deleted without changing the relative order of the remaining characters.

For example, `"ace"` is a subsequence of `"abcde"`.
A common subsequence of two strings is a subsequence that is common to both strings.

**Example 1**

```
Input: text1 = "abcde", text2 = "ace" 
Output: 3  
Explanation: The longest common subsequence is "ace" and its length is 3.
```

**Example 2**

```
Input: text1 = "abc", text2 = "abc"
Output: 3
Explanation: The longest common subsequence is "abc" and its length is 3.
```

**Example 3**

```
Input: text1 = "abc", text2 = "def"
Output: 0
Explanation: There is no such common subsequence, so the result is 0.
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/1143.最长公共子序列.html)[^lcsSolution].

#### Python

```python
class Solution(object):
    def longestCommonSubsequence(self, text1, text2):
        text1, text2 = list(text1), list(text2)
        n1 = len(text1)
        n2 = len(text2)

        dp = [[0] * (n2 + 1) for _ in range(n1 + 1)]
        result = 0

        for t1 in range(1,n1 + 1):
            for t2 in range(1,n2 + 1):
                temp = max(dp[t1][t2 - 1], dp[t1 - 1][t2])
                if dp[t1 - 1][t2 - 1] < temp: 
                    dp[t1][t2] = temp
                else:
                    dp[t1][t2] = dp[t1 - 1][t2 - 1]
                    if text1[t1 - 1] == text2[t2 - 1]:
                        dp[t1][t2] += 1
                        if dp[t1][t2] > result: result = dp[t1][t2]

        return result
```

Use scrolling arrays to increase efficiency

```python
class Solution(object):
    def longestCommonSubsequence(self, text1, text2):
        n1, n2 = len(text1), len(text2)
        
        # 确保使用较短的字符串进行列计算，以节省空间
        if n1 < n2:
            text1, text2 = text2, text1
            n1, n2 = n2, n1
        
        # 滚动数组优化空间，只保留前一行和当前行
        prev = [0] * (n2 + 1)
        curr = [0] * (n2 + 1)
        
        for i in range(1, n1 + 1):
            for j in range(1, n2 + 1):
                if text1[i - 1] == text2[j - 1]:
                    curr[j] = prev[j - 1] + 1
                else:
                    curr[j] = max(prev[j], curr[j - 1])
            # 交换 prev 和 curr
            prev, curr = curr, prev
        
        # 结果在最后一行
        return prev[n2]
```


## Uncrossed Lines

> [Link to Leetcode question](https://leetcode.com/problems/uncrossed-lines/description/)[^ul]
{: .prompt-info }

You are given two integer arrays `nums1` and `nums2`. We write the integers of `nums1` and `nums2` (in the order they are given) on two separate horizontal lines.

We may draw connecting lines: a straight line connecting two numbers `nums1[i]` and `nums2[j]` such that:

- `nums1[i] == nums2[j]`, and
- the line we draw does not intersect any other connecting (non-horizontal) line.

Note that a connecting line cannot intersect even at the endpoints (i.e., each number can only belong to one connecting line).

Return the maximum number of connecting lines we can draw in this way.

**Example 1**

[image]: uncrossed-lines-example-1

```yml
Input: nums1 = [1,4,2], nums2 = [1,2,4]
Output: 2
Explanation: We can draw 2 uncrossed lines as in the diagram.
We cannot draw 3 uncrossed lines, because the line from nums1[1] = 4 to nums2[2] = 4 will intersect the line from nums1[2]=2 to nums2[1]=2.
```

**Example 2**

```yml
Input: nums1 = [2,5,1,2,5], nums2 = [10,5,2,1,5,2]
Output: 3
```

**Example 3**

```yml
Input: nums1 = [1,3,7,1,7,5], nums2 = [1,9,2,5,1]
Output: 2
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/1035.不相交的线.html)[^ulSolution].

#### Python

```python
class Solution(object):
    def maxUncrossedLines(self, nums1, nums2):
        n1, n2 = len(nums1), len(nums2)
        
        if n1 < n2:
            nums1, nums2 = nums2, nums1
            n1, n2 = n2, n1
        
        prev = [0] * (n2 + 1)
        curr = [0] * (n2 + 1)
        
        for i in range(1, n1 + 1):
            for j in range(1, n2 + 1):
                if nums1[i - 1] == nums2[j - 1]:
                    curr[j] = prev[j - 1] + 1
                else:
                    curr[j] = max(prev[j], curr[j - 1])
            prev, curr = curr, prev
        
        return prev[n2]
```


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

[^lcs]:Leetcode-1143 Longest Common Subsequence: [https://leetcode.com/problems/longest-common-subsequence/description/
](https://leetcode.com/problems/longest-common-subsequence/description/).
[^lcsSolution]:代码随想录-最长公共子序列: [https://programmercarl.com/1143.最长公共子序列.html](https://programmercarl.com/1143.最长公共子序列.html).
[^ul]:Leetcode-1035 Uncrossed Lines: [https://leetcode.com/problems/uncrossed-lines/description/](https://leetcode.com/problems/uncrossed-lines/description/).
[^ulSolution]:代码随想录-不相交的线: [https://programmercarl.com/1035.不相交的线.html](https://programmercarl.com/1035.不相交的线.html).


