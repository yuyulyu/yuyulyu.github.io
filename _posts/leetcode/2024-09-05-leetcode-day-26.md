---
title: Leetcode 26 - Greedy Algorithm
description: 452 Minimum Number of Arrows to Burst Balloons
author: yoyo
date: 2024-09-05 15:43:00 +0800
categories: [Data Structure and Algorithm, Leetcode]
tags: [greedy]
---

![Easy](https://img.shields.io/badge/Easy-brightgreen) 
![Medium](https://img.shields.io/badge/Medium-yellow)
![Hard](https://img.shields.io/badge/Hard-red)

## Greedy Algorithm

| Diff                                                                                                | Problem                                                                                 | Python | Java |
|-----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [452 Minimum Number of Arrows to Burst Balloons](#minimum-number-of-arrows-to-burst-balloons)       |✅       |        |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [19 Remove Nth Node From End of List](#the-link)                |        |      |
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                              | [160 Intersection of Two Linked Lists](#the-link)               |        |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [142 Linked List Cycle II](#the-link)                                       |        |      |

## Minimum Number of Arrows to Burst Balloons

> [Link to Leetcode question](https://leetcode.com/problems/minimum-number-of-arrows-to-burst-balloons/description/)[^mnoatbb]
{: .prompt-info }

There are some spherical balloons taped onto a flat wall that represents the XY-plane. The balloons are represented as a 2D integer array points where `points[i] = [xstart, xend]` denotes a balloon whose horizontal diameter stretches between xstart and xend. You do not know the exact y-coordinates of the balloons.

Arrows can be shot up directly vertically (in the positive y-direction) from different points along the x-axis. A balloon with `x_start` and `x_end` is burst by an arrow shot at `x` if `x_start <= x <= x_end`. There is no limit to the number of arrows that can be shot. A shot arrow keeps traveling up infinitely, bursting any balloons in its path.

Given the array points, return the minimum number of arrows that must be shot to burst all balloons.

**Example 1**

```
Input: points = [[10,16],[2,8],[1,6],[7,12]]
Output: 2
Explanation: The balloons can be burst by 2 arrows:
- Shoot an arrow at x = 6, bursting the balloons [2,8] and [1,6].
- Shoot an arrow at x = 11, bursting the balloons [10,16] and [7,12].
```

**Example 2**

```
Input: points = [[1,2],[3,4],[5,6],[7,8]]
Output: 4
Explanation: One arrow needs to be shot for each balloon for a total of 4 arrows.
```

**Example 3**

```
Input: points = [[1,2],[2,3],[3,4],[4,5]]
Output: 2
Explanation: The balloons can be burst by 2 arrows:
- Shoot an arrow at x = 2, bursting the balloons [1,2] and [2,3].
- Shoot an arrow at x = 4, bursting the balloons [3,4] and [4,5].
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0452.用最少数量的箭引爆气球.html)[^mnoatbbSolution].

#### Python

```python
class Solution(object):
    def findMinArrowShots(self, points):
        points.sort(key=lambda x: (x[0], x[1]))
        arrow = points[0]
        count = 1

        for p in points:
            if p[0] <= arrow[1]:
                arrow = [max(p[0], arrow[0]), min(p[1], arrow[1])]
            else:
                arrow = p
                count += 1
        
        return count
```

### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [435 Non-overlapping Intervals](https://leetcode.com/problems/non-overlapping-intervals/)[^noi] |        |      |


## <2nd problem>

> [Link to Leetcode question](https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/)[^rnnfeol]
{: .prompt-info }


### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0151.翻转字符串里的单词.html)[^rhsSolution].

### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [2095 Delete the Middle Node of a Linked List](https://leetcode.com/problems/delete-the-middle-node-of-a-linked-list/)[^dtmnoall] |        |      |



## Reference
[^mnoatbb]:Leetcode-452 Minimum Number of Arrows to Burst Balloons: [https://leetcode.com/problems/minimum-number-of-arrows-to-burst-balloons/description/](https://leetcode.com/problems/minimum-number-of-arrows-to-burst-balloons/description/).
[^mnoatbbSolution]:代码随想录-用最少数量的箭引爆气球: [https://programmercarl.com/0452.用最少数量的箭引爆气球.html](https://programmercarl.com/0452.用最少数量的箭引爆气球.html).
[^noi]:Leetcode-435 Non-overlapping Intervals: [https://leetcode.com/problems/non-overlapping-intervals/](https://leetcode.com/problems/non-overlapping-intervals/).


