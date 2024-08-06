---
title: Leetcode Day 6 - Hash Table 
description: # <problem> | # <Problem> 
author: yoyo
date: 2024-08-06 14:07:00 +0800
categories: [Algorithm, Leetcode]
tags: []
---  

![Easy](https://img.shields.io/badge/Easy-brightgreen) 
![Medium](https://img.shields.io/badge/Medium-yellow)
![Hard](https://img.shields.io/badge/Hard-red)

## <Topic> [^dmsxl] 

| Diff                                                                                                | Problem                                                                                 | Python | Java |
|-----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [454 4Sum II](#4sum-ii)                                          |✅      |      |
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                              | [383 Ransom Note](#ransom-note)                |✅      |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                              | [15 3Sum](#3sum)               |        |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [142 Linked List Cycle II](#the-link)                                       |        |      |

## 4Sum II

> [Link to Leetcode question](https://leetcode.com/problems/4sum-ii/description/)[^4sum]

Given four integer arrays `nums1`, `nums2`, `nums3`, and `nums4` all of length `n`, return the number of tuples `(i, j, k, l)` such that:

  - `0 <= i, j, k, l < n`
  - `nums1[i] + nums2[j] + nums3[k] + nums4[l] == 0`

**Example 1**

```
Input: nums1 = [1,2], nums2 = [-2,-1], nums3 = [-1,2], nums4 = [0,2]
Output: 2
Explanation:
The two tuples are:
1. (0, 0, 0, 1) -> nums1[0] + nums2[0] + nums3[0] + nums4[1] = 1 + (-2) + (-1) + 2 = 0
2. (1, 1, 0, 0) -> nums1[1] + nums2[1] + nums3[0] + nums4[0] = 2 + (-1) + (-1) + 0 = 0
```

**Example 2**

```
Input: nums1 = [0], nums2 = [0], nums3 = [0], nums4 = [0]
Output: 1
```

### Solution[^4sumSolution]

#### Python

```python
class Solution(object):
    def fourSumCount(self, nums1, nums2, nums3, nums4):
        record = dict()
        n = len(nums1)

        for i in range(n):
            for j in range(n):
                ab = nums1[i] + nums2[j]
                if ab in record:
                    record[ab] += 1
                else:
                    record[ab] = 1
        
        count = 0

        for k in range(n):
            for l in range(n):
                cd = - nums3[k] - nums4[l]
                if cd in record:
                    count += record[cd]
        
        return count
```

### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [18 4Sum](https://leetcode.com/problems/4sum/)[^4s] |        |      |


## Ransom Note

> [Link to Leetcode question](https://leetcode.com/problems/ransom-note/description/)[^rn]

Given two strings `ransomNote` and `magazine`, return `true` if `ransomNote` can be constructed by using the letters from `magazine` and `false` otherwise.

Each letter in `magazine` can only be used once in `ransomNote`.

**Example 1**

```
Input: ransomNote = "a", magazine = "b"
Output: false
```

**Example 2**

```
Input: ransomNote = "aa", magazine = "ab"
Output: false
```

**Example 3**

```
Input: ransomNote = "aa", magazine = "aab"
Output: true
```

### Solution[^rnSolution]

#### Python

```python
class Solution(object):
    def canConstruct(self, ransomNote, magazine):
        from collections import Counter

        counter_ransom = Counter(ransomNote)
        counter_maga = Counter(magazine)

        for k in counter_ransom.keys():
            try:
                if counter_maga[k] < counter_ransom[k]:
                    return False
            except:
                return False
        
        return True
```

### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Hard](https://img.shields.io/badge/Hard-red)                                                | [691 Stickers to Spell Word](https://leetcode.com/problems/stickers-to-spell-word/)[^stsw] |        |      |

## 3Sum

> [Link to Leetcode question](https://leetcode.com/problems/3sum/description/)[^3sum]

Given an integer array `nums`, return all the triplets `[nums[i], nums[j], nums[k]]` such that `i != j, i != k, and j != k`, and `nums[i] + nums[j] + nums[k] == 0`.

Notice that the solution set must not contain duplicate triplets.

**Example 1**

```
Input: nums = [-1,0,1,2,-1,-4]
Output: [[-1,-1,2],[-1,0,1]]
Explanation: 
nums[0] + nums[1] + nums[2] = (-1) + 0 + 1 = 0.
nums[1] + nums[2] + nums[4] = 0 + 1 + (-1) = 0.
nums[0] + nums[3] + nums[4] = (-1) + 2 + (-1) = 0.
The distinct triplets are [-1,0,1] and [-1,-1,2].
Notice that the order of the output and the order of the triplets does not matter.
```

**Example 2**

```
Input: nums = [0,1,1]
Output: []
Explanation: The only possible triplet does not sum up to 0.
```

**Example 3**

```
Input: nums = [0,0,0]
Output: [[0,0,0]]
Explanation: The only possible triplet sums up to 0.
```

### Solution[^rnnfeolSolution]

### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [2095 Delete the Middle Node of a Linked List](https://leetcode.com/problems/delete-the-middle-node-of-a-linked-list/)[^dtmnoall] |        |      |

## Ransom Note

> [Link to Leetcode question](https://leetcode.com/problems/ransom-note/description/)[^rn]


### Solution[^rnnfeolSolution]

### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [2095 Delete the Middle Node of a Linked List](https://leetcode.com/problems/delete-the-middle-node-of-a-linked-list/)[^dtmnoall] |        |      |



## Reference
[^dmsxl]:
[^4sum]:Leetcode-454 4Sum II: [https://leetcode.com/problems/4sum-ii/description/](https://leetcode.com/problems/4sum-ii/description/).
[^4sumSolution]: 代码随想录-四数相加II: [https://programmercarl.com/0454.四数相加II.html#其他语言版本](https://programmercarl.com/0454.四数相加II.html#其他语言版本).
[^rn]:Leetcode-383 Ransom Note: [https://leetcode.com/problems/ransom-note/description/](https://leetcode.com/problems/ransom-note/description/).
[^rnSolution]: 代码随想录-赎金信:[https://programmercarl.com/0383.赎金信.html](https://programmercarl.com/0383.赎金信.html).
[^stsw]: Leetcode-691 Stickers to Spell Word: [https://leetcode.com/problems/stickers-to-spell-word/](https://leetcode.com/problems/stickers-to-spell-word/).
[^4s]: Leetcode-18 4Sum: [https://leetcode.com/problems/4sum/](https://leetcode.com/problems/4sum/).
[^3sum]: Leetcode-15 3Sum: [https://leetcode.com/problems/3sum/description/](https://leetcode.com/problems/3sum/description/).
