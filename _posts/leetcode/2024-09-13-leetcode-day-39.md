---
title: "Leetcode Day 39 - DP: Subsequence"
description: 115 Distinct Subsequences | 583 Delete Operation for Two Strings | 72 Edit Distance
author: yoyo
date: 2024-09-13 23:07:00 +0800
categories: [Data Structure and Algorithm, Leetcode, Dynamic Programming, Subsequence]
tags: [dynamic programming (DP)]
image:
  path: /assets/covers/leetcode/leetcode-day-39.jpg
  alt: Leetcode Day 39 Cover
---

## Dynamic Programming

| Diff                                                                                                | Problem                                                                                 | Python | Java |
|-----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|--------|------|
| ![Hard](https://img.shields.io/badge/Hard-red)                                               | [115 Distinct Subsequences](#distinct-subsequences)                                          |✅      |       |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [583 Delete Operation for Two Strings](#delete-operation-for-two-strings)                   |✅      |       |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                              | [72 Edit Distance](#edit-distance)                                                         |✅      |        |


## Distinct Subsequences

> [Link to Leetcode question](https://leetcode.com/problems/distinct-subsequences/description/)[^ds]
{: .prompt-info }

Given two strings `s` and `t`, return the number of distinct subsequences of `s` which equals `t`.

The test cases are generated so that the answer fits on a `32-bit` signed integer.

**Example 1**

```yml
Input: s = "rabbbit", t = "rabbit"
Output: 3
Explanation:
As shown below, there are 3 ways you can generate "rabbit" from s.
rabbbit
rabbbit
rabbbit
```

**Example 2**

```yml
Input: s = "babgbag", t = "bag"
Output: 5
Explanation:
As shown below, there are 5 ways you can generate "bag" from s.
babgbag
babgbag
babgbag
babgbag
babgbag
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0115.不同的子序列.html)[^dsSolution].

#### Python

```python
class Solution(object):
    def numDistinct(self, s, t):
        m, n = len(t), len(s)
        
        # 创建 dp 数组，dp[i][j] 表示 t 的前 i 个字符在 s 的前 j 个字符中出现的次数
        dp = [[0] * (n + 1) for _ in range(m + 1)]
        
        # 初始化 dp[0][j] 为 1，因为空字符串 t 可以在 s 的任意前缀中匹配出 1 个子序列（不选任何字符）
        for j in range(n + 1):
            dp[0][j] = 1
        
        # 动态规划填表
        for i in range(1, m + 1):
            for j in range(1, n + 1):
                if t[i - 1] == s[j - 1]:
                    dp[i][j] = dp[i - 1][j - 1] + dp[i][j - 1]
                else:
                    dp[i][j] = dp[i][j - 1]

        # 返回 dp[m][n]，表示 t 的整个字符串在 s 中的出现次数
        return dp[m][n]
```


## Delete Operation for Two Strings

> [Link to Leetcode question](https://leetcode.com/problems/delete-operation-for-two-strings/description/)[^dofts]
{: .prompt-info }

Given two strings `word1` and `word2`, return the minimum number of steps required to make `word1` and `word2` the same.

In one step, you can delete exactly one character in either string. 

**Example 1**

```yml
Input: word1 = "sea", word2 = "eat"
Output: 2
Explanation: You need one step to make "sea" to "ea" and another step to make "eat" to "ea".
```

**Example 2**

```yml
Input: word1 = "leetcode", word2 = "etco"
Output: 4
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0583.两个字符串的删除操作.html)[^doftsSolution].


#### Python

**Solution 1**

`dp[w1][w2]` records the largest common subsequence between `word1[:w1]` and `word2[w2]`, and return `(n1 + n2 - 2 * dp[-1][-1])` at the end to find the minimum delete operations needed.

```python
class Solution(object):
    def minDistance(self, word1, word2):
        n1, n2 = len(word1), len(word2)
        dp = [[0] * (n2 + 1) for _ in range(n1 + 1)]
        
        for w1 in range(1, n1 + 1):
            for w2 in range(1, n2 + 1):
                dp[w1][w2] = max(dp[w1][w2 - 1], dp[w1 - 1][w2])
                if dp[w1 - 1][w2 - 1] >= dp[w1][w2] and word1[w1 - 1] == word2[w2 - 1]:
                    dp[w1][w2] = dp[w1 - 1][w2 - 1] + 1
        
        return(n1 + n2 - 2 * dp[-1][-1])
```

**Solution 2**

`dp[w1][w2]` records the minimum delete operations needed between `word1[:w1]` and `word2[w2]` directly, so `dp[-1][-1]` is the answer.

```python
class Solution(object):
    def minDistance(self, word1, word2):
        dp = [[0] * (len(word2)+1) for _ in range(len(word1)+1)]
        for i in range(len(word1)+1):
            dp[i][0] = i
        for j in range(len(word2)+1):
            dp[0][j] = j
        for i in range(1, len(word1)+1):
            for j in range(1, len(word2)+1):
                if word1[i-1] == word2[j-1]:
                    dp[i][j] = dp[i-1][j-1]
                else:
                    dp[i][j] = min(dp[i-1][j-1] + 2, dp[i-1][j] + 1, dp[i][j-1] + 1)
        return dp[-1][-1]
```


## Edit Distance

> [Link to Leetcode question](https://leetcode.com/problems/edit-distance/description/)[^ed]
{: .prompt-info }

Given two strings `word1` and `word2`, return the minimum number of operations required to convert `word1` to `word2`.

You have the following three operations permitted on a word:

- Insert a character
- Delete a character
- Replace a character
 

**Example 1**

```yml
Input: word1 = "horse", word2 = "ros"
Output: 3
Explanation: 
horse -> rorse (replace 'h' with 'r')
rorse -> rose (remove 'r')
rose -> ros (remove 'e')
```

**Example 2**

```yml
Input: word1 = "intention", word2 = "execution"
Output: 5
Explanation: 
intention -> inention (remove 't')
inention -> enention (replace 'i' with 'e')
enention -> exention (replace 'n' with 'x')
exention -> exection (replace 'n' with 'c')
exection -> execution (insert 'u')
```


### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0072.编辑距离.html)[^edSolution].

#### 1. `dp` table and its meaning

`dp[i][j]` represents the minimum edit distance between `word1[:i]` and `word2[:j]`. 

#### 2. Recursive formula
```
if (word1[i - 1] == word2[j - 1])
    不操作
if (word1[i - 1] != word2[j - 1])
    #Delete a character
    #Insert a character
    #Replace a character
```

** Delete a character from `word1`**

At state `dp[i][j]`, a character deleted from `word1` -> 1 more operation than state `dp[i - 1=[j]`

`dp[i][j] = dp[i - 1][j] + 1`

** Delete a character from `word2`**

At state `dp[i][j]`, a character deleted from `word2` -> 1 more operation than state `dp[i][j - 1]`

`dp[i][j] = dp[i][j - 1] + 1`

**Replace a chareacter in `word1`**

At state `dp[i][j]`, replace chareacter `word1[i - 1]` so that it equals to `word2[j - 1]`

`dp[i][j] = dp[i - 1][j - 1] + 1`

#### Python

```python
class Solution(object):
    def minDistance(self, word1, word2):
        dp = [[0] * (len(word2)+1) for _ in range(len(word1)+1)]
        for i in range(len(word1)+1):
            dp[i][0] = i
        for j in range(len(word2)+1):
            dp[0][j] = j
        for i in range(1, len(word1)+1):
            for j in range(1, len(word2)+1):
                if word1[i-1] == word2[j-1]:
                    dp[i][j] = dp[i-1][j-1]
                else:
                    dp[i][j] = min(dp[i-1][j-1], dp[i-1][j], dp[i][j-1]) + 1
        return dp[-1][-1]
```


## Reference

[^ds]:Leetcode-115 Distinct Subsequences: [https://leetcode.com/problems/distinct-subsequences/description/](https://leetcode.com/problems/distinct-subsequences/description/).
[^dsSolution]:代码随想录-不同的子序列: [https://programmercarl.com/0115.不同的子序列.html](https://programmercarl.com/0115.不同的子序列.html).
[^dofts]:Leetcode-583 Delete Operation for Two Strings: [https://leetcode.com/problems/delete-operation-for-two-strings/description/](https://leetcode.com/problems/delete-operation-for-two-strings/description/).
[^doftsSolution]:代码随想录-两个字符串的删除操作: [https://programmercarl.com/0583.两个字符串的删除操作.html](https://programmercarl.com/0583.两个字符串的删除操作.html).
[^ed]:Leetcode-72 Edit Distance: [https://leetcode.com/problems/edit-distance/description/](https://leetcode.com/problems/edit-distance/description/).
[^edSolution]:代码随想录-编辑距离: [https://programmercarl.com/0072.编辑距离.html](https://programmercarl.com/0072.编辑距离.html).


