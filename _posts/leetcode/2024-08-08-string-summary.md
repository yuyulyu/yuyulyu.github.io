---
title: LeetCode Summary Days 7-8 - String
description: Reversing strings | KMP algorithm 
author: yoyo
date: 2024-08-08 15:34:00 +0800
categories: [Algorithm, Leetcode]
tags: [string,kmp]
---

## Reversing Strings
Reversing strings is a fundamental technique in string manipulation, forming the basis for solving more complex string problems.

### Basics and Variations
- **[`344 Reverse String`](https://yuyulyu.github.io/posts/leetcode-day-7/#reverse-string)**: Basic string reversal using two-pointer technique.
  - Utilize tuple unpacking for an elegant swap.
- **[`541 Reverse String II`](https://yuyulyu.github.io/posts/leetcode-day-7/#reverse-string-ii)**: Reversal in chunks, reversing the first `k` characters for every `2k` characters.
  - Iterative block processing with condition checks for remaining string length.
- **[`Kama-54 Replace Numbers`](https://yuyulyu.github.io/posts/leetcode-day-7/#replace-numbers)**
  - Explores replacing segments of strings, showcasing additional manipulation techniques beyond simple reversals and pattern matching.

### Advanced Reversals
- **[`151 Reverse Words in a String`](https://leetcode.com/problems/reverse-words-in-a-string)**: Full sentence reversal with space normalization.
  - Trimming spaces and reversing individual words post full string reversal.
- **[`Kama-55 Right-Handed String`](https://yuyulyu.github.io/posts/leetcode-day-8/#right-handed-string)**: Right rotation of the string by `k` places.
  - Concatenate the substring from `length-k` to `end` with the start to `length-k`.

## KMP Algorithm
The Knuth-Morris-Pratt (KMP) algorithm is crucial for pattern searching in strings, offering an efficient solution to the string search problem.

### Introduction to KMP
- **Efficiency**: Improves the worst-case time complexity to O(n + m) from O(n*m) by avoiding redundant checks.
- **LPS Array**: Preprocess pattern to create the longest prefix which is also suffix (LPS) array which helps in skipping non-matching characters.

> [Link to Note about KMP](https://yuyulyu.github.io/posts/kmp/).
{: .prompt-info }

### Practical Applications
- **[`28 Find the Index of the First Occurrence in a String`](https://yuyulyu.github.io/posts/leetcode-day-8/#find-the-index-of-the-first-occurrence-in-a-string)**: Utilize KMP to find the first occurrence of a `needle` in `haystack`.
  - Skips unnecessary comparisons after a mismatch.
- **[`459 Repeated Substring Pattern`](https://yuyulyu.github.io/posts/leetcode-day-8/#repeated-substring-pattern)**: Uses KMP to check if the string can be formed by repeating a substring.
  - Check if the complete string is a repetition of a substring using the LPS array.

### Additional Notes
- Python libraries offer high-level functions like `find()` and `index()` which can simplify solutions but do not provide the algorithmic understanding and efficiency of KMP in large text data.

For detailed explanations and code, refer to the daily notes linked in each section above.
