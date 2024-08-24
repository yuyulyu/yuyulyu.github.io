---
title: Leetcode Day 20 Backtracking Algorithm
description: 39 Combination Sum | 40 Combination Sum II | 131 Palindrome Partitioning
author: yoyo
date: 2024-08-24 15:03:00 +0800
categories: [Data Structure and Algorithm, Leetcode]
tags: [backtracking]
---

## Backtracking Algorithm 

| Diff                                                                                                | Problem                                                                                 | Python | Java |
|-----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [39 Combination Sum](#combination-sum)                                          |        |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [40 Combination Sum II](#combination-sum-ii)                |        |      |
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                              | [131 Palindrome Partitioning](#palindrome-partitioning)               |        |      |


## Combination Sum

> [Link to Leetcode question](https://leetcode.com/problems/combination-sum/description/)[^cs]
{: .prompt-info }

Given an array of distinct integers `candidates` and a target integer `target`, return a list of all unique combinations of `candidates` where the chosen numbers sum to `target`. You may return the combinations in any order.

The same number may be chosen from `candidates` an unlimited number of times. Two combinations are unique if the 
frequency of at least one of the chosen numbers is different.

The test cases are generated such that the number of unique combinations that sum up to `target` is less than `150` combinations for the given input.

**Example 1**

```
Input: candidates = [2,3,6,7], target = 7
Output: [[2,2,3],[7]]
Explanation:
2 and 3 are candidates, and 2 + 2 + 3 = 7. Note that 2 can be used multiple times.
7 is a candidate, and 7 = 7.
These are the only two combinations.
```

**Example 2**

```
Input: candidates = [2,3,5], target = 8
Output: [[2,2,2,2],[2,3,3],[3,5]]
```

**Example 3**

```
Input: candidates = [2], target = 1
Output: []
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0039.组合总和.html)[^csSolution].


## Combination Sum II

> [Link to Leetcode question](https://leetcode.com/problems/combination-sum-ii/)[^csii]
{: .prompt-info }

Given a collection of candidate numbers ( `candidates`) and a target number (`target`), find all unique combinations in `candidates` where the candidate numbers sum to `target`.

Each number in `candidates` may only be used once in the combination.

**Note**: The solution set must not contain duplicate `combinations`.

**Example 1**
```
Input: candidates = [10,1,2,7,6,1,5], target = 8
Output: 
[
[1,1,6],
[1,2,5],
[1,7],
[2,6]
]
```

**Example 2**

```
Input: candidates = [2,5,2,1,2], target = 5
Output: 
[
[1,2,2],
[5]
]
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0040.组合总和II.html)[^csiiSolution].


### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [216 Combination Sum III](https://leetcode.com/problems/combination-sum-iii/)[^csiii] |        |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [377 Combination Sum IV](https://leetcode.com/problems/combination-sum-iv/description/)[^csiv] |        |      |


## Palindrome Partitioning

> [Link to Leetcode question](https://leetcode.com/problems/palindrome-partitioning/description/)[^pp]
{: .prompt-info }

Given a string `s`, partition `s` such that every substring of the partition is a palindrome. Return all possible palindrome partitioning of `s`.

**Example 1**

```
Input: s = "aab"
Output: [["a","a","b"],["aa","b"]]
```

**Example 2**

```
Input: s = "a"
Output: [["a"]]
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0131.分割回文串.html)[^ppSolution].



### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Hard](https://img.shields.io/badge/Hard-red)                                                | [132 Palindrome Partitioning II](https://leetcode.com/problems/palindrome-partitioning-ii/)[^ppii] |        |      |
| ![Hard](https://img.shields.io/badge/Hard-red)                                                | [1745 Palindrome Partitioning IV](https://leetcode.com/problems/palindrome-partitioning-iv/description/)[^ppiv] |        |      |


## Reference
[^cs]:Leetcode-39 Combination Sum: [https://leetcode.com/problems/combination-sum/description/](https://leetcode.com/problems/combination-sum/description/).
[^csSolution]:代码随想录-组合总和: [https://programmercarl.com/0039.组合总和.html](https://programmercarl.com/0039.组合总和.html).
[^csii]:Leetcode-40 Combination Sum II: [https://leetcode.com/problems/combination-sum-ii/](https://leetcode.com/problems/combination-sum-ii/).
[^csiiSolution]:代码随想录-组合总和II: [https://programmercarl.com/0040.组合总和II.html](https://programmercarl.com/0040.组合总和II.html).
[^pp]:Leetcode-131 Palindrome Partitioning: [https://leetcode.com/problems/palindrome-partitioning/description/](https://leetcode.com/problems/palindrome-partitioning/description/).
[^csiii]: Leetcode-216 Combination Sum III: [https://leetcode.com/problems/combination-sum-iii/](https://leetcode.com/problems/combination-sum-iii/).
[^csiv]: Leetcode-377 Combination Sum IV: [https://leetcode.com/problems/combination-sum-iv/description/](https://leetcode.com/problems/combination-sum-iv/description/).
[^ppSolution]:代码随想录-分割回文串: [https://programmercarl.com/0131.分割回文串.html](https://programmercarl.com/0131.分割回文串.html).
[^ppii]: Leetcode-132 Palindrome Partitioning II: [https://leetcode.com/problems/palindrome-partitioning-ii/](https://leetcode.com/problems/palindrome-partitioning-ii/).
[^ppiv]: Leetcode-1745 Palindrome Partitioning IV: [https://leetcode.com/problems/palindrome-partitioning-iv/description/](https://leetcode.com/problems/palindrome-partitioning-iv/description/).
