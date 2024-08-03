---
title: Leetcode Day 2
description: 209 Minimum Size Subarray Sum | 59 Spiral Matrix II
author: yoyo
date: 2024-08-01 13:26:00 +0800
categories: [Algorithm, Leetcode]
tags: [array, sliding window]
---
| **Topic**: Array[^dmsxl]                                    |   Python   |   Java     |
|-------------------------------------------------------------|------------|------------|
| [209 Minimum Size Subarray Sum](#minimum-size-subarray-sum) |✅          |✅         |
| [59 Spiral Matrix II](#spiral-matrix-ii)                    |✅          |            |
| [ACM 59 Range Sum](#range-sum)                              |            |            |

## Minimum Size Subarray Sum

> [Link to Leetcode question](https://leetcode.com/problems/minimum-size-subarray-sum/)[^msss]

Given an array of positive integers `nums` and a positive integer `target`, return the minimal length of a 
subarray whose sum is greater than or equal to target. If there is no such subarray, return` 0` instead.

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

**Python**
```python
class Solution(object):
    def minSubArrayLen(self, target, nums):
        left = 0
        right = 0
        cur_sum = 0
        min_len = len(nums) + 1

        while(right < len(nums)):
            cur_sum += nums[right]
            while(cur_sum >= target):
                min_len = min(min_len,right - left + 1)
                cur_sum -= nums[left]
                left += 1
            right += 1
        
        if(min_len == len(nums) + 1):
            return 0
        
        return min_len
```

**Java**

```java
class Solution {
    public int minSubArrayLen(int target, int[] nums) {
        int left = 0;
        int cur_sum = 0;
        int min_len = nums.length + 1;

        for(int right = 0;right < nums.length;right++){
            cur_sum += nums[right];
            while(cur_sum >= target){
                min_len = Math.min(min_len,right - left + 1);
                cur_sum -=nums[left++];
            }
        }

        return min_len == nums.length + 1 ? 0 : min_len;
    }
}
```

## Spiral Matrix II

> [Link to Leetcode question](https://leetcode.com/problems/spiral-matrix-ii/)[^smii]

Given a positive integer n, generate an n x n matrix filled with elements from 1 to n2 in spiral order.

**Example 1**

![Desktop View](/assets/image//leetcode-day2-1.jpg){: .normal }

```
Input: n = 3
Output: [[1,2,3],[8,9,4],[7,6,5]]
```

**Example 2**
```
Input: n = 1
Output: [[1]]
```

### Note [^smiiSolution]
![Desktop View](/assets/image/leetcode-day2-2.jpg){: width="210" height="210" }


### Solution

**Python**

```python
class Solution(object):
    def generateMatrix(self, n):
        """
        :type n: int
        :rtype: List[List[int]]
        """
        if n == 0:
            return []

        nums = [[0] * n for _ in range(n)]
        loops,mid = n//2, n//2
        row_start = 0
        col_start = 0
        num = 1

        for loop in range(loops):
            print(loop)
            for i in range(col_start,n - loop - 1):
                nums[row_start][i] = num
                num += 1
            for i in range(row_start,n - loop - 1):
                nums[i][n - loop - 1] = num
                num += 1
            for i in range(n - loop - 1,col_start,-1):
                nums[n - loop - 1][i] = num
                num += 1
            for i in range(n - loop - 1,row_start,-1):
                nums[i][col_start] = num
                num += 1
            
            col_start += 1
            row_start += 1
            
        if(len(nums) % 2 == 1):
            nums[mid][mid] = num
        
        return nums
```

## Range Sum

> [Link to Leetcode question](https://kamacoder.com/problempage.php?pid=1070)[^rs]

**Problem Description**

Given an integer array `Array`, calculate the sum of the elements within each specified range.

**Input Description**

The first line contains the length `n` of the integer array `Array`. The next `n` lines each contain an integer, representing the elements of the array. The subsequent inputs are the indices of the ranges to calculate the sum: `a` and `b` (`b >= a`), until the end of the file.

**Output Description**

Output the sum of the elements within each specified range.

**Input Example**

```
5
1
2
3
4
5
0 1
1 3
```

**Output Example**

```
3
9
```       

## Reference
[^dmsxl]:代码随想录-数组:[https://programmercarl.com/数组理论基础.html](https://programmercarl.com/数组理论基础.html).
[^msss]:Leetcode-209 Minimum Size Subarray Sum: [https://leetcode.cn/problems/minimum-size-subarray-sum/](https://leetcode.cn/problems/minimum-size-subarray-sum/).
[^bsssSolution]:代码随想录-289长度最小的子数组: [https://programmercarl.com/0209.%E9%95%BF%E5%BA%A6%E6%9C%80%E5%B0%8F%E7%9A%84%E5%AD%90%E6%95%B0%E7%BB%84.html](https://programmercarl.com/0209.%E9%95%BF%E5%BA%A6%E6%9C%80%E5%B0%8F%E7%9A%84%E5%AD%90%E6%95%B0%E7%BB%84.html).
[^smii]:Leetcode-59: Spiral Matrix: [https://leetcode.com/problems/spiral-matrix-ii/](https://leetcode.com/problems/spiral-matrix-ii/).
[^smiiSolution]:代码随想录-螺旋矩阵: [https://programmercarl.com/0059.螺旋矩阵II.html](https://programmercarl.com/0059.螺旋矩阵II.html).
[^slideWindowVideo]:Sliding Window Video (Bilibili, CN): https://www.bilibili.com/video/BV1tZ4y1q7XE/.
[^rs]:Kamacoder-59 Range Sum: [https://kamacoder.com/problempage.php?pid=1070](https://kamacoder.com/problempage.php?pid=1070).
