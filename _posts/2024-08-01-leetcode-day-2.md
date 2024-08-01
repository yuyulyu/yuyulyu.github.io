---
title: Leetcode Day2
description: 209 Minimum Size Subarray Sum | 59 Spiral Matrix II
author: yoyo
date: 2024-08-01 13:26:00 +0800
categories: [Algorithm, Leetcode]
tags: [array, sliding window]
---

**Topic**: Array[^dmsxl]
  * [209 Minimum Size Subarray Sum](https://leetcode.cn/problems/minimum-size-subarray-sum/)
  * [59 Spiral Matrix II](https://leetcode.cn/problems/spiral-matrix-ii/)

[^dmsxl]:代码随想录-数组:https://programmercarl.com/数组理论基础.html.

## Minimum Size Subarray Sum[^msss]

[^msss]:Leetcode-209 Minimum Size Subarray Sum: https://leetcode.cn/problems/minimum-size-subarray-sum/.

Given an array of positive integers ```nums``` and a positive integer ```target```, return the minimal length of a 
subarray whose sum is greater than or equal to target. If there is no such subarray, return``` 0``` instead.

**Example 1***
```
Input: target = 7, nums = [2,3,1,2,4,3]
Output: 2
Explanation: The subarray [4,3] has the minimal length under the problem constraint.
```

**Example 2**
```
Input: target = 4, nums = [1,4,4]
Output: 1
```

**Example 3**
```
Input: target = 11, nums = [1,1,1,1,1,1,1,1]
Output: 0
```

### Note 
**Sliding Window**



### Solution [^bsssSolution]

[^bsssSolution]:代码随想录-289长度最小的子数组:https://programmercarl.com/0209.%E9%95%BF%E5%BA%A6%E6%9C%80%E5%B0%8F%E7%9A%84%E5%AD%90%E6%95%B0%E7%BB%84.html.

**Python**
```python
class Solution(object):
    def minSubArrayLen(self, target, nums):
        left = 0
        right = 0
        cur_sum = 0
        min_len = float('inf')

        while right < len(nums):
            cur_sum += nums[right]
            while cur_sum >= target:
                min_len = min(min_len, right - left + 1)
                cur_sum -= nums[left]
                left += 1
            right += 1

        if min_len == float('inf'):
            return 0
        else:
            return min_len
```
        
        

## Reference
[^slideWindowVideo]:Sliding Window Video (Bilibili, CN): https://www.bilibili.com/video/BV1tZ4y1q7XE/.
