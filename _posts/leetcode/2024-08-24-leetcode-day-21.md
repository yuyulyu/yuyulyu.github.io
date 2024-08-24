---
title: Leetcode Day 21 - Backtracking Algorithm
description: 93 Restore IP Addresses | 78 Subsets | 90 Subsets II
author: yoyo
date: 2024-08-24 17:28:00 +0800
categories: [Data Structure and Algorithm, Leetcode]
tags: [backtracking]
---
## Backtracking Algorithm 

| Diff                                                                                                | Problem                                                                                 | Python | Java |
|-----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [93 Restore IP Addresses](#restore-ip-addresses)                                          |        |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [78 Subsets](#subsets)                |        |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [90 Subsets II](#subsets-ii)                                       |        |      |

## Restore IP Addresses

> [Link to Leetcode question](https://leetcode.com/problems/restore-ip-addresses/description/)[^ria]
{: .prompt-info }

A valid IP address consists of exactly four integers separated by single dots. Each integer is between `0` and `255` (**inclusive**) and cannot have leading zeros.

- For example, `"0.1.2.201"` and `"192.168.1.1"` are valid IP addresses, but `"0.011.255.245"`, `"192.168.1.312"` and `"192.168@1.1"` are invalid IP addresses.

Given a string `s` containing only digits, return all possible valid IP addresses that can be formed by inserting dots into `s`. You are not allowed to reorder or remove any digits in `s`. You may return the valid IP addresses in any order.

**Example 1**

```
Input: s = "25525511135"
Output: ["255.255.11.135","255.255.111.35"]
```

**Example 2**

```
Input: s = "0000"
Output: ["0.0.0.0"]
```

**Example 3**

```
Input: s = "101023"
Output: ["1.0.10.23","1.0.102.3","10.1.0.23","10.10.2.3","101.0.2.3"]
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0093.复原IP地址.html)[^riaSolution].



## Subsets

> [Link to Leetcode question](https://leetcode.com/problems/subsets/description/)[^subsets]
{: .prompt-info }

Given an integer array `nums` of unique elements, return all possible subsets (the power set).

The solution set must not contain duplicate subsets. Return the solution in any order.

**Example 1**

```
Input: nums = [1,2,3]
Output: [[],[1],[2],[1,2],[3],[1,3],[2,3],[1,2,3]]
```

**Example 2**

```
Input: nums = [0]
Output: [[],[0]]
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0078.子集.html)[^subsetsSolution].



## Subsets II

> [Link to Leetcode question](https://leetcode.com/problems/subsets-ii/description/)[^sii]
{: .prompt-info }

Given an integer array `nums` that may contain duplicates, return all possible subsets (the power set).

The solution set must not contain duplicate subsets. Return the solution in any order. 

**Example 1**

```
Input: nums = [1,2,2]
Output: [[],[1],[1,2],[1,2,2],[2],[2,2]]
```

**Example 2**

```
Input: nums = [0]
Output: [[],[0]]
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0090.子集II.html)[^siiSolution].



### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [784 Letter Case Permutation](https://leetcode.com/problems/letter-case-permutation/description/)[^lcp] |        |      |
| ![Hard](https://img.shields.io/badge/Hard-red)                                                | [1982 Find Array Given Subset Sums](https://leetcode.com/problems/find-array-given-subset-sums/)[^fagss] |        |      |



## Reference
[^ria]:Leetcode-93 Restore IP Addresses: [https://leetcode.com/problems/restore-ip-addresses/description/](https://leetcode.com/problems/restore-ip-addresses/description/).
[^riaSolution]:代码随想录-复原IP地址: [https://programmercarl.com/0093.复原IP地址.html](https://programmercarl.com/0093.复原IP地址.html).
[^subsets]:Leetcode-78 Subsets: [https://leetcode.com/problems/subsets/description/](https://leetcode.com/problems/subsets/description/).
[^subsetsSolution]:代码随想录-子集: [https://programmercarl.com/0078.子集.html](https://programmercarl.com/0078.子集.html).
[^sii]:Leetcode-90 Subsets II: [https://leetcode.com/problems/subsets-ii/description/](https://leetcode.com/problems/subsets-ii/description/).
[^siiSolution]:代码随想录-子集II: [https://programmercarl.com/0090.子集II.html](https://programmercarl.com/0090.子集II.html).
[^lcp]: Leetcode-784 Letter Case Permutation: [https://leetcode.com/problems/letter-case-permutation/description/](https://leetcode.com/problems/letter-case-permutation/description/).
[^fagss]: Leetcode-1982 Find Array Given Subset Sums: [https://leetcode.com/problems/find-array-given-subset-sums/](https://leetcode.com/problems/find-array-given-subset-sums/).
