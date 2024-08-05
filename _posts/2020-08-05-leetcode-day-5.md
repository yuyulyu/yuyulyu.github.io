---
title: Leetcode Day 5 - Hash Table
description: 242 Valid Anagram | 349 Intersection of Two Arrays | 202 Happy Number | 1 Two Sum
author: yoyo
date: 2024-08-05 23:07:00 +0800
categories: [Algorithm, Leetcode,Hash Table]
tags: [hash table,string,sorting,two pointers,binary search]
---

## Hash Table [^dmsxl] 

> [Link to note about hash table](https://yuyulyu.github.io/posts/hash-table/)

| Diff                                                                                                | Problem                                                                                 | Python | Java |
|-----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|--------|------|
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                               | [242 Valid Anagram](#valid-anagram)                                          |✅      |      |
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                              | [349 Intersection of Two Arrays](#intersection-of-two-arrays)                |        |      |
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                              | [202 Happy Number](#happy-number)               |        |      |
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                              | [1 Two Sum](#two-sum)                                       |        |      |

## Valid Anagram

> [Link to Leetcode question](https://leetcode.com/problems/valid-anagram/description/)[^va]

Given two strings `s` and `t`, return `true` if `t` is an anagram of `s`, and `false` otherwise.

An Anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

**Example 1**

```
Input: s = "anagram", t = "nagaram"
Output: true
```

**Example 2**

```
Input: s = "rat", t = "car"
Output: false
```

### Solution[^vaSolution]

#### Python

**Solution 1**: Implement a hash table to record the number of each letter.

  ```python
  class Solution(object):
    def isAnagram(self, s, t):        
        record = [0] * 26

        for c in s:
            record[ord(c) - ord('a')] += 1
        
        for c in t:
            record[ord(c) - ord('a')] -= 1
        
        for i in range(len(record)):
            if (record[i] != 0):
                return False
        
        return True
  ```

**Solution 2**: Use `Counter` to count number of each letter exist in each string.

  ```python
  class Solution(object):
      def isAnagram(self, s, t):        
          from collections import Counter
          a = Counter(s)
          b = Counter(t)
          return a == b
  ```

### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                                | [2273 Find Resultant Array After Removing Anagrams](https://leetcode.com/problems/find-resultant-array-after-removing-anagrams/description/)[^fraara] |        |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                       | [49 Group Anagrams](https://leetcode.com/problems/group-anagrams/description/)[^ga]          |        |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                       | [438. Find All Anagrams in a String](https://leetcode.com/problems/find-all-anagrams-in-a-string/)[^faaias]          |        |      |


## Intersection of Two Arrays

> [Link to Leetcode question](https://leetcode.com/problems/intersection-of-two-arrays/description/)[^iota]

Given two integer arrays `nums1` and `nums2`, return an array of their intersection. Each element in the result must be unique and you may return the result in any order.

**Example 1**

```
Input: nums1 = [1,2,2,1], nums2 = [2,2]
Output: [2]
```

**Example 2**

```
Input: nums1 = [4,9,5], nums2 = [9,4,9,8,4]
Output: [9,4]
Explanation: [4,9] is also accepted.
```

### Solution[^iotaSolution]



### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                               | [350 Intersection of Two Arrays II](https://leetcode.com/problems/intersection-of-two-arrays-ii/description/)[^iotaii] |        |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [3002 Maximum Size of a Set After Removals](https://leetcode.com/problems/maximum-size-of-a-set-after-removals/)[^msoasar] |        |      |

## Happy Number

> [Link to Leetcode question](https://leetcode.com/problems/happy-number/description/)[^hn]

Write an algorithm to determine if a number `n` is happy.

A happy number is a number defined by the following process:

  - Starting with any positive integer, replace the number by the sum of the squares of its digits.
  - Repeat the process until the number equals `1` (where it will stay), or it loops endlessly in a cycle which does not include `1`.
  - Those numbers for which this process ends in `1` are happy.

Return `true` if `n` is a happy number, and `false` if not.

**Example 1**

```
Input: n = 19
Output: true
Explanation:
12 + 92 = 82
82 + 22 = 68
62 + 82 = 100
12 + 02 + 02 = 1
```

**Example 2**

```
Input: n = 2
Output: false
```


### Solution[^hnSolution]

### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                                | [263 Ugly Number](https://leetcode.com/problems/ugly-number/description/)[^un] |        |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [2457 Minimum Addition to Make Integer Beautiful](https://leetcode.com/problems/minimum-addition-to-make-integer-beautiful/)[^matmib] |        |      |

## Two Sum

> [Link to Leetcode question](https://leetcode.com/problems/two-sum/description/)[^ts]

Given an array of integers `nums` and an integer `target`, return indices of the two numbers such that they add up to `target`.

You may assume that each input would have **exactly one solution**, and you may not use the same element twice.

You can return the answer in any order.

**Example 1**

```
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].
```

**Example 2**

```
Input: nums = [3,2,4], target = 6
Output: [1,2]
```

**Example 3**

```
Input: nums = [3,3], target = 6
Output: [0,1]
```

### Solution[^tsSolution]

### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [15 3Sum](https://leetcode.com/problems/3sum/description/)[^3sum] |        |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [167. Two Sum II - Input Array Is Sorted](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/description/)[^tsiiiais] |        |      |



## Reference
[^dmsxl]:代码随想录-哈希表理论基础: [https://programmercarl.com/哈希表理论基础.html#哈希表](https://programmercarl.com/哈希表理论基础.html#哈希表).
[^va]:Leetcode-242 Valid Anagram: [https://leetcode.com/problems/valid-anagram/description/](https://leetcode.com/problems/valid-anagram/description/).
[^fraara]:Leetcode-2273 Find Resultant Array After Removing Anagrams: [https://leetcode.com/problems/find-resultant-array-after-removing-anagrams/description/](https://leetcode.com/problems/find-resultant-array-after-removing-anagrams/description/).
[^ga]:Leetcode-49 Group Anagrams: [https://leetcode.com/problems/group-anagrams/description/](https://leetcode.com/problems/group-anagrams/description/).
[^faaias]:Leetcode-438 Find All Anagrams in a String: [https://leetcode.com/problems/find-all-anagrams-in-a-string/](https://leetcode.com/problems/find-all-anagrams-in-a-string/).
[^vaSolution]:代码随想录-有效的字母异位词: [https://programmercarl.com/0242.有效的字母异位词.html](https://programmercarl.com/0242.有效的字母异位词.html).
[^iota]:Leetcode-349 Intersection of Two Arrays: [https://leetcode.com/problems/intersection-of-two-arrays/description/](https://leetcode.com/problems/intersection-of-two-arrays/description/).
[^iotaSolution]:代码随想录-两个数组的交集: [https://programmercarl.com/0349.两个数组的交集.html](https://programmercarl.com/0349.两个数组的交集.html).
[^iotaii]:Leetcode-350 Intersection of Two Arrays II: [https://leetcode.com/problems/intersection-of-two-arrays-ii/description/](https://leetcode.com/problems/intersection-of-two-arrays-ii/description/).
[^msoasar]:Leetcode-3002 Maximum Size of a Set After Removals: [https://leetcode.com/problems/maximum-size-of-a-set-after-removals/](https://leetcode.com/problems/maximum-size-of-a-set-after-removals/).
[^hn]:Leetcode-202 Happy Number: [https://leetcode.com/problems/happy-number/description/](https://leetcode.com/problems/happy-number/description/).
[^tsSolution]:代码随想录-两数之和: [https://programmercarl.com/0001.两数之和.html](https://programmercarl.com/0001.两数之和.html).
[^hnSolution]:代码随想录-快乐数: [https://programmercarl.com/0202.快乐数.html](https://programmercarl.com/0202.快乐数.html).
[^un]:Leetcode-263 Ugly Number: [https://leetcode.com/problems/ugly-number/description/](https://leetcode.com/problems/ugly-number/description/).
[^matmib]:Leetcode-2457 Minimum Addition to Make Integer Beautiful: [https://leetcode.com/problems/minimum-addition-to-make-integer-beautiful/](https://leetcode.com/problems/minimum-addition-to-make-integer-beautiful/).
[^un]:Leetcode-263 Ugly Number: [https://leetcode.com/problems/ugly-number/description/](https://leetcode.com/problems/ugly-number/description/).
[^matmib]:Leetcode-2457 Minimum Addition to Make Integer Beautiful: [https://leetcode.com/problems/minimum-addition-to-make-integer-beautiful/](https://leetcode.com/problems/minimum-addition-to-make-integer-beautiful/).
[^ts]:Leetcode-1 Two Sum: [https://leetcode.com/problems/two-sum/description/](https://leetcode.com/problems/two-sum/description/).


