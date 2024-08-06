---
title: Leetcode Day 6 - Hash Table 
description: 454 4Sum II |  383 Ransom Note | 15 3Sum | 18 4Sum
author: yoyo
date: 2024-08-06 14:07:00 +0800
categories: [Algorithm, Leetcode]
tags: [hash table, array, double pointers,]
---  


## Hash Table [^dmsxl] 

> [Link to note about hash table](https://yuyulyu.github.io/posts/hash-table/)
{: .prompt-info }

| Diff                                                                                                | Problem                                                                                 | Python | Java |
|-----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [454 4Sum II](#4sum-ii)                                          |✅      |      |
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                              | [383 Ransom Note](#ransom-note)                |✅      |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                              | [15 3Sum](#3sum)               |✅      |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [18 4Sum](#4sum)                                       |✅      |      |

## 4Sum II

> [Link to Leetcode question](https://leetcode.com/problems/4sum-ii/description/)[^4sum]
{: .prompt-info }

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
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [18 4Sum](#4sum)[^4s]                                                                                   |✅      |      |


## Ransom Note

> [Link to Leetcode question](https://leetcode.com/problems/ransom-note/description/)[^rn]
{: .prompt-info }

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
{: .prompt-info }

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

### Solution[^3sumSolution]

## Python

```python
class Solution(object):
    def threeSum(self, nums):
        nums.sort()
        if nums[0] > 0:
            return []
        result = []

        for i in range(len(nums)):
            if(i > 0 and nums[i-1] == nums[i]):
                continue  
            left = i + 1
            right = len(nums) - 1
           
            while left < right:
                s = nums[i] + nums[left] + nums[right] 
                
                if s == 0:
                    result.append([nums[i],nums[left],nums[right]])
                    left += 1
                    while(nums[left] == nums[left - 1] and left < right):
                        left += 1
                elif s < 0:
                    left += 1
                    while(nums[left] == nums[left - 1] and left < right):
                        left += 1
                else:
                    right -= 1
            
        return result
```

### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [16 3Sum Closest](https://leetcode.com/problems/3sum-closest/description/)[^3sc] |        |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [2909 Minimum Sum of Mountain Triplets II](https://leetcode.com/problems/minimum-sum-of-mountain-triplets-ii/)[^msomt] |        |      |

## 4Sum

> [Link to Leetcode question](https://leetcode.com/problems/4sum/description/)[^4s]
{: .prompt-info }

Given an array `nums` of `n` integers, return an array of all the unique quadruplets `[nums[a], nums[b], nums[c], nums[d]]` such that:

  - `0 <= a, b, c, d < n`
  - `a, b, c, and d are distinct.`
  - `nums[a] + nums[b] + nums[c] + nums[d] == target`

You may return the answer in any order. 

**Example 1**

```
Input: nums = [1,0,-1,0,-2,2], target = 0
Output: [[-2,-1,1,2],[-2,0,0,2],[-1,0,0,1]]
```

**Example 2**

```
Input: nums = [2,2,2,2,2], target = 8
Output: [[2,2,2,2]]
```

### Solution[^4sSolution]

#### Python

```python
class Solution(object):
    def fourSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[List[int]]
        """
        nums.sort()

        if((nums[0] > 0 and target < 0) or (nums[-1] < 0 and target > 0)):
            return []

        record = []

        for i in range(len(nums) - 3):
            for j in range(i + 1, len(nums) - 2):
                left = j + 1
                right = len(nums) - 1

                while(left < right and right > j + 1):
                    s = nums[i] + nums[j] + nums[left] + nums[right]
                    if(s == target):
                        if ([nums[i],nums[j],nums[left],nums[right]] not in record):
                            record.append([nums[i],nums[j],nums[left],nums[right]])
                        right -= 1
                    elif(s < target):
                        left += 1
                    else:
                        right -= 1
            
        return record
```

## Reference
[^dmsxl]:代码随想录-哈希表理论基础: [https://programmercarl.com/哈希表理论基础.html#哈希表](https://programmercarl.com/哈希表理论基础.html#哈希表).
[^4sum]:Leetcode-454 4Sum II: [https://leetcode.com/problems/4sum-ii/description/](https://leetcode.com/problems/4sum-ii/description/).
[^4sumSolution]: 代码随想录-四数相加II: [https://programmercarl.com/0454.四数相加II.html#其他语言版本](https://programmercarl.com/0454.四数相加II.html#其他语言版本).
[^rn]:Leetcode-383 Ransom Note: [https://leetcode.com/problems/ransom-note/description/](https://leetcode.com/problems/ransom-note/description/).
[^rnSolution]: 代码随想录-赎金信:[https://programmercarl.com/0383.赎金信.html](https://programmercarl.com/0383.赎金信.html).
[^stsw]: Leetcode-691 Stickers to Spell Word: [https://leetcode.com/problems/stickers-to-spell-word/](https://leetcode.com/problems/stickers-to-spell-word/).
[^4s]: Leetcode-18 4Sum: [https://leetcode.com/problems/4sum/](https://leetcode.com/problems/4sum/).
[^3sum]: Leetcode-15 3Sum: [https://leetcode.com/problems/3sum/description/](https://leetcode.com/problems/3sum/description/).
[^3sc]: Leetcode-16 3Sum Closest: [https://leetcode.com/problems/3sum-closest/description/](https://leetcode.com/problems/3sum-closest/description/).
[^msomt]: Leetcode-2909 Minimum Sum of Mountain Triplets II: [https://leetcode.com/problems/minimum-sum-of-mountain-triplets-ii/](https://leetcode.com/problems/minimum-sum-of-mountain-triplets-ii/).
[^3sumSolution]:代码随想录-三数之和: [https://programmercarl.com/0015.三数之和.html](https://programmercarl.com/0015.三数之和.html).
[^4sSolution]:代码随想录-四数之和:[https://programmercarl.com/0018.四数之和.html#算法公开课](https://programmercarl.com/0018.四数之和.html#算法公开课)

