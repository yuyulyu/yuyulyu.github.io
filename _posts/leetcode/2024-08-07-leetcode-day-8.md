---
title: Leetcode Day 8 - String
description: 151 Reverse Words in a String | Kama-55 Right-Handed String | 28 Find the Index of the First Occurrence in a String |459 Repeated Substring Pattern 
author: yoyo
date: 2024-08-07 23:07:00 +0800
categories: [Algorithm, Leetcode]
tags: [string, double pointers]
---

## String 

| Diff                                                                                                | Problem                                                                                 | Python | Java |
|-----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [151 Reverse Words in a String](#reverse-words-in-a-string)                                          |        |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [Kama-55 Right-Handed String](#right-handed-string)                |        |      |

**Optional Queations**

| Diff                                                                                                | Problem                                                                                 | Python | Java |
|-----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|--------|------|
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                                | [28 Find the Index of the First Occurrence in a String](#find-the-index-of-the-first-occurrence-in-a-string)                                          |        |      |
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                                | [459 Repeated Substring Pattern](#repeated-substring-pattern)                |        |      |

## Reverse Words in a String

> [Link to Leetcode question](https://leetcode.com/problems/reverse-words-in-a-string/description/)[^rwias]
{: .prompt-info }

Given an input string `s`, reverse the order of the words.

A word is defined as a sequence of non-space characters. The words in `s` will be separated by at least one space.

Return a string of the words in reverse order concatenated by a single space.

Note that `s` may contain leading or trailing spaces or multiple spaces between two words. The returned string should only have a single space separating the words. Do not include any extra spaces.

**Example 1**

```
Input: s = "the sky is blue"
Output: "blue is sky the"
```

**Example 2**

```
Input: s = "  hello world  "
Output: "world hello"
Explanation: Your reversed string should not contain leading or trailing spaces.
```

**Example 3**

```
Input: s = "a good   example"
Output: "example good a"
Explanation: You need to reduce multiple spaces between two words to a single space in the reversed string.
```

### Solution[^rwiasSolution]

> A detailed explaination of solution can be found [here](https://programmercarl.com/0151.翻转字符串里的单词.html).[^rwiasSolution]

  - Remove extra spaces: `the sky is blue ` -> `the sky is blue`
  - reverse charaters: `the sky is blue` -> `eulb si yks eht`
  - reverse each word: `eulb si yks eht` -> `blue is sky the`

1. <ins> Remove extra spaces </ins>
  - **Solution 1: Traverse the String**:
    - Complexity: O(n<sup>2</sup>)

  - **Solution 2: Use double pointers to remove extra spaces**
    - Complexity: O(n) 

    ```python
    # Remove leading spaces
        # Remove leading spaces
        while(s[fast] == ' ' and fast < len(s)):
            fast += 1
        
        # Remove extra spaces between words
        while(fast < len(s)):
            if not(fast - 1 > 0 and s[fast -1] == res[fast] and s[fast] == ' '):
                s[slow] = s[fast]
                slow += 1
            fast += 1
        
        # Remove trailing spaces
        if(slow - 1 > 0 and s[slow - 1] == ' '):
            s = s[:slow - 1]
        else:
            s = s[:slow]
    ```
  - **Solution 3: Similar to idea in [27 Remove Element](https://yuyulyu.github.io/posts/leetcode-day-1/#remove-element)**:
    - Complexity: O(n)
      
    ```python
    i = 0
    slow = 0

        while i < len(s):
            if (s[i] != ' '):
                if(slow != 0):
                    s[slow] = ' '
                    slow += 1
                while(i < len(s) and s[i] != ' '):
                    s[slow] = s[i]
                    slow += 1
                    i += 1
            i += 1
        s = s[:slow]
    ```
    
  - **Other tricky solution in python**: 
    - `strip()` removes the leading and trailing spaces in a string.
    - `split()` splits string into a list of word.

2. <ins>Revers charaaters</ins>
  Similar to [344 Revers String](https://yuyulyu.github.io/posts/leetcode-day-7/#reverse-string), use double pointers.

  ```python
  def reverseWord(s):
              for i in range(len(s) // 2):
                  s[i], s[len(s) - i - 1] = s[len(s) - i - 1], s[i]
              return s
  ```
  
4. <ins>Reverse each word</ins>
    


## Right-Handed String

> [Link to the question](https://kamacoder.com/problempage.php?pid=1065/)[^rhs].
{: .prompt-info }

**题目描述**

> 字符串的右旋转操作是把字符串尾部的若干个字符转移到字符串的前面。给定一个字符串 `s` 和一个正整数 `k`，请编写一个函数，将字符串中的后面 `k` 个字符移到字符串的前面，实现字符串的右旋转操作。
> 例如，对于输入字符串 `abcdefg` 和整数 `2`，函数应该将其转换为 `fgabcde`。

**输入描述**

> 输入共包含两行，第一行为一个正整数`k`，代表右旋转的位数。第二行为字符串 `s`，代表需要旋转的字符串。

**输出描述**

> 输出共一行，为进行了右旋转操作后的字符串。

**输入示例**

> ```
> 2
> abcdefg
> ```

**输出示例**

> ```
> fgabcde
> ```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0151.翻转字符串里的单词.html)[^rhsSolution].

## Find the Index of the First Occurrence in a String

> [Link to Leetcode question](https://leetcode.com/problems/find-the-index-of-the-first-occurrence-in-a-string/description/)[^ftiotfoias].
{: .prompt-info }

Given two strings `needle` and `haystack`, return the index of the first occurrence of `needle` in `haystack`, or `-1` if `needle` is not part of `haystack`.

**Example 1**

```
Input: haystack = "sadbutsad", needle = "sad"
Output: 0
Explanation: "sad" occurs at index 0 and 6.
The first occurrence is at index 0, so we return 0.
```

**Example 2**

```
Input: haystack = "leetcode", needle = "leeto"
Output: -1
Explanation: "leeto" did not occur in "leetcode", so we return -1.
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0028.实现strStr.html)[^ftiotfoiasSolution].


### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                                | [459 Repeated Substring Pattern](https://leetcode.com/problems/repeated-substring-pattern/description/)[^rsp] |        |      |
| ![Hard](https://img.shields.io/badge/Hard-red)                                                | [214 Shortest Palindrome](https://leetcode.com/problems/shortest-palindrome/description/)[^sp] |        |      |

## Repeated Substring Pattern

> [Link to Leetcode question](https://leetcode.com/problems/repeated-substring-pattern/description/)[^rsp].
{: .prompt-info }

Given a string `s`, check if it can be constructed by taking a substring of it and appending multiple copies of the substring together.

**Example 1**

```
Input: s = "abab"
Output: true
Explanation: It is the substring "ab" twice.
```

***Example 2**

```
Input: s = "aba"
Output: false
```

**Example 3**

```
Input: s = "abcabcabcabc"
Output: true
Explanation: It is the substring "abc" four times or the substring "abcabc" twice.
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0459.重复的子字符串.html)[^rspSolution].


### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [686 Repeated String Match](https://leetcode.com/problems/repeated-string-match/description/)[^rsm] |        |      |



## Reference
[^rwias]:Leetcode-151 Reverse Words in a String: [https://leetcode.com/problems/reverse-words-in-a-string/description/](https://leetcode.com/problems/reverse-words-in-a-string/description/).
[^rwiasSolution]:代码随想录-翻转字符串里的单词: [https://programmercarl.com/0151.翻转字符串里的单词.html](https://programmercarl.com/0151.翻转字符串里的单词.html).
[^rhs]: 卡码网-55 右旋字符串: [https://kamacoder.com/problempage.php?pid=1065/](https://kamacoder.com/problempage.php?pid=1065/).
[^rhsSolution]: 代码随想录-右旋字符串: [https://programmercarl.com/kama55.右旋字符串.html](https://programmercarl.com/kama55.右旋字符串.html).
[^ftiotfoias]: Leetcode-28 Find the Index of the First Occurrence in a String: [https://leetcode.com/problems/find-the-index-of-the-first-occurrence-in-a-string/description/](https://leetcode.com/problems/find-the-index-of-the-first-occurrence-in-a-string/description/).
[^rsp]: Leetcode-459 Repeated Substring Pattern: [https://leetcode.com/problems/repeated-substring-pattern/description/](https://leetcode.com/problems/repeated-substring-pattern/description/).
[^sp]: Leetcode-214 Shortest Palindrome: [https://leetcode.com/problems/shortest-palindrome/description/](https://leetcode.com/problems/shortest-palindrome/description/).
[^ftiotfoiasSolution]: 代码随想录-实现 strStr(): [https://programmercarl.com/0028.实现strStr.html](https://programmercarl.com/0028.实现strStr.html).
[^rsp]: Leetcode - 459 Repeated Substring Pattern: [https://leetcode.com/problems/repeated-substring-pattern/description/](https://leetcode.com/problems/repeated-substring-pattern/description/).
[^rspSolution]: 代码随想录-重复的子字符串: [https://programmercarl.com/0459.重复的子字符串.html](https://programmercarl.com/0459.重复的子字符串.html).
[^rsm]: Leetcode-686 Repeated String Match: [https://leetcode.com/problems/repeated-string-match/description/](https://leetcode.com/problems/repeated-string-match/description/).




