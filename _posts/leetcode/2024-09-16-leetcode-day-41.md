---
title: "Leetcode Day 41 - Monotone stack "
description: 739 Daily Temperatures | 496 Next Greater Element I | 503 Next Greater Element II
author: yoyo
date: 2024-09-16 20:26:00 +0800
categories: [Data Structure and Algorithm, Leetcode, Monotone stack]
tags: [monotone stack]
---

## Monotone stack

| Diff                                                                                                | Problem                                                                                 | Python | Java |
|-----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [739 Daily Temperatures](#daily-temperatures)                                          |✅      |        |
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                                | [496 Next Greater Element I](#next-greater-element-i)                                    |✅      |        |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [503 Next Greater Element II](#next-greater-element-ii)                                  |✅      |        |

## Daily Temperatures

> [Link to Leetcode question](https://leetcode.com/problems/daily-temperatures/description/)[^dt]
{: .prompt-info }

Given an array of integers `temperatures` represents the daily temperatures, return an array answer such that `answer[i]` is the number of days you have to wait after the `i<sup>th</sup>` day to get a warmer temperature. If there is no future day for which this is possible, keep `answer[i] == 0` instead.

**Example 1**

```yml
Input: temperatures = [73,74,75,71,69,72,76,73]
Output: [1,1,4,2,1,1,0,0]
```

**Example 2**

```yml
Input: temperatures = [30,40,50,60]
Output: [1,1,1,0]
```

**Example 3**

```yml
Input: temperatures = [30,60,90]
Output: [1,1,0]
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0739.每日温度.html)[^dtSolution].

#### Python

```python
class Solution(object):
    def dailyTemperatures(self, temperatures):
        stack = [len(temperatures) - 1]
        answer = [0] * len(temperatures)

        for i in range(len(temperatures) - 2, -1, -1):
            l = len(stack)
            for j in range(1, l + 1):
                if temperatures[stack[l - j]] > temperatures[i]:
                    answer[i] = stack[l - j] - i
                    break
                else:
                    stack.pop()
            stack.append(i)
        
        return answer
```

```python
class Solution(object):
    def dailyTemperatures(self, temperatures):
        answer = [0]*len(temperatures)
        stack = []
        for i in range(len(temperatures)):
            while len(stack)>0 and temperatures[i] > temperatures[stack[-1]]:
                answer[stack[-1]] = i - stack[-1]
                stack.pop()
            stack.append(i)
        return answer
```



## Next Greater Element I

> [Link to Leetcode question](https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/)[^ngei]
{: .prompt-info }

The next greater element of some element `x` in an array is the first greater element that is to the right of `x` in the same array.

You are given two distinct 0-indexed integer arrays `nums1` and `nums2`, where `nums1` is a subset of `nums2`.

For each `0 <= i < nums1.length`, find the index `j` such that `nums1[i] == nums2[j]` and determine the next greater element of `nums2[j]` in `nums2`. If there is no next greater element, then the answer for this query is `-1`.

Return an array `ans` of length `nums1.length` such that `ans[i]` is the next greater element as described above.

**Example 1**

```yml
Input: nums1 = [4,1,2], nums2 = [1,3,4,2]
Output: [-1,3,-1]
Explanation: The next greater element for each value of nums1 is as follows:
- 4 is underlined in nums2 = [1,3,4,2]. There is no next greater element, so the answer is -1.
- 1 is underlined in nums2 = [1,3,4,2]. The next greater element is 3.
- 2 is underlined in nums2 = [1,3,4,2]. There is no next greater element, so the answer is -1.
```

**Example 2**

```yml
Input: nums1 = [2,4], nums2 = [1,2,3,4]
Output: [3,-1]
Explanation: The next greater element for each value of nums1 is as follows:
- 2 is underlined in nums2 = [1,2,3,4]. The next greater element is 3.
- 4 is underlined in nums2 = [1,2,3,4]. There is no next greater element, so the answer is -1.
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0496.下一个更大元素I.html)[^ngeiSolution].

#### Python

```python
class Solution(object):
    def nextGreaterElement(self, nums1, nums2):
        stack = [len(nums2) - 1]
        ans = [-1] * len(nums1)
        count = 0

        for i in range(len(nums2) - 2, -1, -1):
            while len(stack) > 0 and nums2[stack[-1]] < nums2[i]:
                stack.pop()
            temp = -1 if len(stack) == 0 else nums2[stack[-1]]
            if nums2[i] in nums1: 
                ans[nums1.index(nums2[i])] = temp
                count += 1
                if count == len(nums1): return ans
            stack.append(i)
        
        return ans
```

```python
class Solution(object):
    def nextGreaterElement(self, nums1, nums2):
        stack = []
        # 创建答案数组
        ans = [-1] * len(nums1)
        for i in range(len(nums2)):
            while len(stack) > 0 and nums2[i] > nums2[stack[-1]]:
                # 判断 num1 是否有 nums2[stack[-1]]。如果没有这个判断会出现指针异常
                if nums2[stack[-1]] in nums1:
                    # 锁定 num1 检索的 index
                    index = nums1.index(nums2[stack[-1]])
                    # 更新答案数组
                    ans[index] = nums2[i]
                # 弹出小元素
                # 这个代码一定要放在 if 外面。否则单调栈的逻辑就不成立了
                stack.pop()
            stack.append(i)
        return ans
```


## Next Greater Element II

> [Link to Leetcode question](https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/)[^ngeii]
{: .prompt-info }

Given a circular integer array `nums` (i.e., the next element of `nums[nums.length - 1]` is `nums[0]`), return the next greater number for every element in `nums`.

The next greater number of a number `x` is the first greater number to its traversing-order next in the array, which means you could search circularly to find its next greater number. If it doesn't exist, return -1 for this number.

**Example 1**

```yml
Input: nums = [1,2,1]
Output: [2,-1,2]
Explanation: The first 1's next greater number is 2; 
The number 2 can't find next greater number. 
The second 1's next greater number needs to search circularly, which is also 2.
```

**Example 2**

```yml
Input: nums = [1,2,3,4,3]
Output: [2,3,4,-1,4]
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0503.下一个更大元素II.html)[^ngeiiSolution].

#### Python

```python
class Solution(object):
    def nextGreaterElements(self, nums):
        ans = [-1] * len(nums)
        stack = nums[::-1]

        for i in range(len(nums) - 1, -1, -1):
            l = len(stack)
            for j in range(1, l + 1):
                if stack[l - j] > nums[i]:
                    ans[i] = stack[l - j]
                    break
                else:
                    stack.pop()
            stack.append(nums[i])
        
        return ans
```

```python
class Solution(object):
    def nextGreaterElements(self, nums):
        dp = [-1] * len(nums)
        stack = []
        for i in range(len(nums)*2):
            while(len(stack) != 0 and nums[i%len(nums)] > nums[stack[-1]]):
                    dp[stack[-1]] = nums[i%len(nums)]
                    stack.pop()
            stack.append(i%len(nums))
        return dp
```


## Reference

[^dt]:Leetcode-739 Daily Temperatures: [https://leetcode.com/problems/daily-temperatures/description/](https://leetcode.com/problems/daily-temperatures/description/).
[^dtSolution]:代码随想录-每日温度: [https://programmercarl.com/0739.每日温度.html](https://programmercarl.com/0739.每日温度.html).
[^ngei]:Leetcode-496 Next Greater Element I: [https://leetcode.com/problems/next-greater-element-i/description/](https://leetcode.com/problems/next-greater-element-i/description/).
[^ngeiSolution]:代码随想录-下一个更大元素I: [https://programmercarl.com/0496.下一个更大元素I.html](https://programmercarl.com/0496.下一个更大元素I.html).
[^ngeii]:Leetcode-503 Next Greater Element II: [https://leetcode.com/problems/next-greater-element-ii/description/](https://leetcode.com/problems/next-greater-element-ii/description/).
[^ngeiiSolution]:代码随想录-下一个更大元素II [https://programmercarl.com/0503.下一个更大元素II.html](https://programmercarl.com/0503.下一个更大元素II.html).

