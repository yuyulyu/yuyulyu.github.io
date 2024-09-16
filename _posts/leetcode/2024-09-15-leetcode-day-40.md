---
title: "Leetcode Day 40 - DP: Palindromic Subsequence"
description: 647 Palindromic Substrings | 516 Longest Palindromic Subsequence
author: yoyo
date: 2024-09-15 22:29:00 +0800
categories: [Data Structure and Algorithm, Leetcode, Dynamic Programming]
tags: [dynamic programming (DP)]
image:
  path: /assets/covers/leetcode/leetcode-day-40.jpg
  alt: Leetcode Day 40 Cover
---

## Dynamic Programming

| Diff                                                                                                | Problem                                                                                 | Python | Java  |
|-----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|--------|-------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [647 Palindromic Substrings](#palindromic-substrings)                                   |✅      |       |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [516 Longest Palindromic Subsequence](#longest-palindromic-subsequence)              |✅      |       |

## Palindromic Substrings

> [Link to Leetcode question](https://leetcode.com/problems/palindromic-substrings/description/)[^ps]
{: .prompt-info }


Given a string `s`, return the number of palindromic substrings in it.

A string is a palindrome when it reads the same backward as forward.

A substring is a contiguous sequence of characters within the string.

**Example 1**

```yml
Input: s = "abc"
Output: 3
Explanation: Three palindromic strings: "a", "b", "c".
```

**Example 2**

```yml
Input: s = "aaa"
Output: 6
Explanation: Six palindromic strings: "a", "a", "a", "aa", "aa", "aaa".
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0647.回文子串.html)[^psSolution].

#### Solution 1: Greedy

```python
class Solution(object):
    def countSubstrings(self, s):
        
        result = 0

        for i in range(len(s)):
            j = 0
            while j <= i and j + i < len(s) and s[i + j] == s[i - j]:
                result += 1
                j += 1
            if i > 0 and s[i - 1] == s[i]:
                j = 0
                while j <= i - 1 and j + i < len(s) and s[i - 1 - j] == s[i + j]:
                    result += 1
                    j += 1
        
        return result
```

#### Solution 2: Dynamic Programming

Use `dp[i][j]` to record if `s[i:j]` is palindromic, which depends on if `s[i + 1:j - 1]` ( `dp[i - 1][j - 1]`) is palindromic.

When `s[i] == s[j]`:
- Case 1: `i == j`, a charater is palindromic.
- Case 2: `j - i == 1`, a string e.g. `"aa"` is palindromic.
- Case 3: `j - i > 1`,` s[i:j]` is palindromic if substring between `s[i]` and `s[j]` is palindromic -> `dp[i][j] = dp[i + 1][j - 1]`

In addtion: `s[i]`, `s[j]` are also palindromic.

```yml
class Solution:
    def countSubstrings(self, s: str) -> int:
        dp = [[False] * len(s) for _ in range(len(s))]
        result = 0
        for i in range(len(s)-1, -1, -1): #注意遍历顺序
            for j in range(i, len(s)):
                if s[i] == s[j] and (j - i <= 1 or dp[i+1][j-1]): 
                    result += 1
                    dp[i][j] = True
        return result
```


## Longest Palindromic Subsequence

> [Link to Leetcode question](https://leetcode.com/problems/longest-palindromic-subsequence/description/)[^lps]
{: .prompt-info }

Given a string `s`, find the longest palindromic subsequence's length in `s`.

A subsequence is a sequence that can be derived from another sequence by deleting some or no elements without changing the order of the remaining elements.

**Example 1**

```yml
Input: s = "bbbab"
Output: 4
Explanation: One possible longest palindromic subsequence is "bbbb".
```

**Example 2**

```yml
Input: s = "cbbd"
Output: 2
Explanation: One possible longest palindromic subsequence is "bb".
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0516.最长回文子序列.html)[^lpsSolution].





## Reference

[^ps]:Leetcode-647 Palindromic Substrings: [https://leetcode.com/problems/palindromic-substrings/description/](https://leetcode.com/problems/palindromic-substrings/description/).
[^psSolution]:代码随想录-回文子串: [https://programmercarl.com/0647.回文子串.html](https://programmercarl.com/0647.回文子串.html).
[^lps]:Leetcode-516 Longest Palindromic Subsequence: [https://leetcode.com/problems/longest-palindromic-subsequence/description/](https://leetcode.com/problems/longest-palindromic-subsequence/description/).
[^lpsSolution]:代码随想录-最长回文子序列: [https://programmercarl.com/0516.最长回文子序列.html](https://programmercarl.com/0516.最长回文子序列.html).
