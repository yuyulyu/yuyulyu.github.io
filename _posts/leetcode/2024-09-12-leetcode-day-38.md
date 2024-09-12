---
title: "Leetcode Day 38 - DP: Subsequence"
description: 1143 Longest Common Subsequence | 
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
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [1143 Longest Common Subsequence](#best-time-to-buy-and-sell-stock)                                          |        |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [19 Remove Nth Node From End of List](#the-link)                |        |      |
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

> A detailed explaination of solution can be found [here](https://programmercarl.com/0151.翻转字符串里的单词.html)[^lcsSolution].

[^lcsSolution]:代码随想录-

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

[^lcs]:Leetcode-1143 Longest Common Subsequence: [https://leetcode.com/problems/longest-common-subsequence/description/
](https://leetcode.com/problems/longest-common-subsequence/description/).



