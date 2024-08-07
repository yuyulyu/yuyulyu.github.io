---
title: Leetcode Day 8 - String
description: 151 Reverse Words in a String | Kama-55 Right-Handed String |
author: yoyo
date: 2024-08-08 23:07:00 +0800
categories: [Algorithm, Leetcode]
tags: [string]
---

![Easy](https://img.shields.io/badge/Easy-brightgreen) 
![Medium](https://img.shields.io/badge/Medium-yellow)
![Hard](https://img.shields.io/badge/Hard-red)

## String 

| Diff                                                                                                | Problem                                                                                 | Python | Java |
|-----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [151 Reverse Words in a String](#reverse-words-in-a-string)                                          |        |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [Kama-55 Right-Handed String](#right-handed-string)                |        |      |
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                              | [160 Intersection of Two Linked Lists](#the-link)               |        |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [142 Linked List Cycle II](#the-link)                                       |        |      |

# the link

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

> A detailed explaination of solution can be found [here](https://programmercarl.com/0151.翻转字符串里的单词.html).

## Right-Handed String

> [Link to the question](https://kamacoder.com/problempage.php?pid=1065/)[^rhsl]
{: .prompt-info }

**题目描述**

字符串的右旋转操作是把字符串尾部的若干个字符转移到字符串的前面。给定一个字符串 s 和一个正整数 k，请编写一个函数，将字符串中的后面 k 个字符移到字符串的前面，实现字符串的右旋转操作。 
例如，对于输入字符串 "abcdefg" 和整数 2，函数应该将其转换为 "fgabcde"。
输入描述

输入共包含两行，第一行为一个正整数 k，代表右旋转的位数。第二行为字符串 s，代表需要旋转的字符串。
输出描述

输出共一行，为进行了右旋转操作后的字符串。
输入示例

2
abcdefg
输出示例

fgabcde
提示信息

数据范围：
1 <= k < 10000,
1 <= s.length < 10000;

### Solution[^rnnfeolSolution]

### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [2095 Delete the Middle Node of a Linked List](https://leetcode.com/problems/delete-the-middle-node-of-a-linked-list/)[^dtmnoall] |        |      |

## <2nd problem>

> [Link to Leetcode question](https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/)[^rnnfeol]


### Solution[^rnnfeolSolution]

### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [2095 Delete the Middle Node of a Linked List](https://leetcode.com/problems/delete-the-middle-node-of-a-linked-list/)[^dtmnoall] |        |      |



## Reference
[^rwias]:Leetcode-151 Reverse Words in a String: [https://leetcode.com/problems/reverse-words-in-a-string/description/](https://leetcode.com/problems/reverse-words-in-a-string/description/).
[^rwiasSolution]:代码随想录-翻转字符串里的单词: [https://programmercarl.com/0151.翻转字符串里的单词.html](https://programmercarl.com/0151.翻转字符串里的单词.html).
[^rhsl]: 卡码网-55 右旋字符串: [https://kamacoder.com/problempage.php?pid=1065/](https://kamacoder.com/problempage.php?pid=1065/).


