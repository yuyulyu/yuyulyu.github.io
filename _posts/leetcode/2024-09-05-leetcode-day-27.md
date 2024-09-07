---
title: "Leetcode Day 27 - Greedy: Advanced Interval & Sequence Problems"
description: 56 Merge Intervals | 738 Monotone Increasing Digits | 968 Binary Tree Cameras
author: yoyo
date: 2024-09-05 20:14:00 +0800
categories: [Data Structure and Algorithm, Leetcode]
tags: [greedy]
---

## Greedy Algorithm

| Diff                                                                                                | Problem                                                                                 | Python | Java |
|-----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [56 Merge Intervals](#merge-intervals)                                                       |✅      |        |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [738 Monotone Increasing Digits](#monotone-increasing-digits)                             |✅      |        |
| ![Hard](https://img.shields.io/badge/Hard-red)                                              | [968 Binary Tree Cameras](#binary-tree-cameras)                                                    |        |        |


## Merge Intervals

> [Link to Leetcode question](https://leetcode.com/problems/merge-intervals/description/)[^mi]
{: .prompt-info }

Given an array of intervals where `intervals[i] = [starti, endi]`, merge all overlapping intervals, and return an array of the non-overlapping intervals that cover all the intervals in the input.

**Example 1**

```
Input: intervals = [[1,3],[2,6],[8,10],[15,18]]
Output: [[1,6],[8,10],[15,18]]
Explanation: Since intervals [1,3] and [2,6] overlap, merge them into [1,6].
```

**Example 2**

```
Input: intervals = [[1,4],[4,5]]
Output: [[1,5]]
Explanation: Intervals [1,4] and [4,5] are considered overlapping.
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0056.合并区间.html)[^miSolution].

#### Python

```python
class Solution(object):
    def merge(self, intervals):

        merged = []

        for start, end in sorted(intervals, key=lambda i: i[0]):
            if len(merged) != 0 and start <= merged[-1][1]:
                merged[-1][1] = max(end, merged[-1][1])
            else:
                merged.append([start, end])
        
        return merged
```



### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [57 Insert Interval](https://leetcode.com/problems/insert-interval/description/)[^ii] |        |      |
| ![Hard](https://img.shields.io/badge/Hard-red)                                                       | [715 Range Module](https://leetcode.com/problems/range-module/)[^rm]          |        |      |


## Monotone Increasing Digits

> [Link to Leetcode question](https://leetcode.com/problems/monotone-increasing-digits/description/)[^mid]
{: .prompt-info }

An integer has monotone increasing digits if and only if each pair of adjacent digits `x` and `y` satisfy `x <= y`.

Given an integer `n`, return the largest number that is less than or equal to `n` with monotone increasing digits.

**Example 1**

```
Input: n = 10
Output: 9
```

**Example 2**

```
Input: n = 1234
Output: 1234
```

**Example 3**

```
Input: n = 332
Output: 299
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0738.单调递增的数字.html)[^midSolution].

#### Python

```python
class Solution(object):
    def monotoneIncreasingDigits(self, n):
        ln = list(str(n))

        if ln == sorted(ln):
            return n
        
        for i in range(len(ln) - 1, 0, -1):
            if ln[i] < ln[i - 1]:
                ln[i - 1] = str(int(ln[i - 1]) - 1)

                for j in range(i, len(ln)):
                    ln[j] = '9'
        
        return int(''.join(ln))
```


### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [402 Remove K Digits](https://leetcode.com/problems/remove-k-digits/)[^dtmnoall] |        |      |


## Binary Tree Cameras

> [Link to Leetcode question](https://leetcode.com/problems/binary-tree-cameras/description/)[^btc]
{: .prompt-info }

You are given the `root` of a binary tree. We install cameras on the tree nodes where each camera at a node can monitor its parent, itself, and its immediate children.

Return the minimum number of cameras needed to monitor all nodes of the tree. 

**Example 1**

[image]: binary-tree-cameras-example-1

```
Input: root = [0,0,null,0,0]
Output: 1
Explanation: One camera is enough to monitor all nodes if placed as shown.
```

**Example 2**

[image]: binary-tree-cameras-example-1

```
Input: root = [0,0,null,0,null,0,null,null,0]
Output: 2
Explanation: At least two cameras are needed to monitor all nodes of the tree. The above image shows one of the valid configurations of camera placement.
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0968.监控二叉树.html)[^btcSolution].



### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [979 Distribute Coins in Binary Tree](https://leetcode.com/problems/distribute-coins-in-binary-tree/)[^dcibt] |        |      |



## Reference
[^mi]:Leetcode-56 Merge Intervals: [https://leetcode.com/problems/merge-intervals/description/](https://leetcode.com/problems/merge-intervals/description/).
[^miSolution]:代码随想录-合并区间: [https://programmercarl.com/0056.合并区间.html](https://programmercarl.com/0056.合并区间.html).
[^ii]: Leetcode-57 Insert Interval: [https://leetcode.com/problems/insert-interval/description/](https://leetcode.com/problems/insert-interval/description/).
[^rm]: Leetcode-715 Range Module: [https://leetcode.com/problems/range-module/](https://leetcode.com/problems/range-module/).
[^mid]:Leetcode-738 Monotone Increasing Digits: [https://leetcode.com/problems/monotone-increasing-digits/description/](https://leetcode.com/problems/monotone-increasing-digits/description/).
[^midSolution]:代码随想录-单调递增的数字: [https://programmercarl.com/0738.单调递增的数字.html](https://programmercarl.com/0738.单调递增的数字.html).
[^btc]:Leetcode-968 Binary Tree Cameras: [https://leetcode.com/problems/binary-tree-cameras/description/](https://leetcode.com/problems/binary-tree-cameras/description/).
[^btcSolution]:代码随想录-监控二叉树: [https://programmercarl.com/0968.监控二叉树.html](https://programmercarl.com/0968.监控二叉树.html).
[^dcibt]:Leetcode-979 Distribute Coins in Binary Tree: [https://leetcode.com/problems/distribute-coins-in-binary-tree/](https://leetcode.com/problems/distribute-coins-in-binary-tree/).
[^rkd]:Leetcode-402 Remove K Digits: [https://leetcode.com/problems/remove-k-digits/](https://leetcode.com/problems/remove-k-digits/).

