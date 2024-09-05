---
title: "Leetcode 26 - Greedy: Intervals"
description: 452 Minimum Number of Arrows to Burst Balloons | 435 Non-overlapping Intervals | 763 Partition Labels
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
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [452 Minimum Number of Arrows to Burst Balloons](#minimum-number-of-arrows-to-burst-balloons)      |✅       |       |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [435 Non-overlapping Intervals](#non-overlapping-intervals)                                      |✅      |        |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [763 Partition Labels](#partition-labels)                                                         |✅      |        |

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


## Non-overlapping Intervals

> [Link to Leetcode question](https://leetcode.com/problems/non-overlapping-intervals/)[^noi]
{: .prompt-info }

Given an array of intervals intervals where `intervals[i] = [starti, endi]`, return the minimum number of intervals you need to remove to make the rest of the intervals non-overlapping. 

**Example 1**

```
Input: intervals = [[1,2],[2,3],[3,4],[1,3]]
Output: 1
Explanation: [1,3] can be removed and the rest of the intervals are non-overlapping.
```

**Example 2**

```
Input: intervals = [[1,2],[1,2],[1,2]]
Output: 2
Explanation: You need to remove two [1,2] to make the rest of the intervals non-overlapping.
```

**Example 3**

```
Input: intervals = [[1,2],[2,3]]
Output: 0
Explanation: You don't need to remove any of the intervals since they're already non-overlapping.
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0435.无重叠区间.htmll)[^noiSolution].



1. The first critical insight is that to maximize the number of intervals we can keep, it is beneficial to always pick the interval that finishes the earliest (i.e., the one with the smallest end time). This is because, by choosing the interval that ends the earliest, we leave the maximum possible space for subsequent intervals. This "greedy" approach ensures that we maximize the number of remaining non-overlapping intervals.
2. Once an interval is chosen (i.e., it is kept), the next interval we pick must have a start time that is after the current interval's end time to ensure there is no overlap. By iterating over intervals sorted by their end time, we can efficiently check if the current interval overlaps with the last one we decided to keep.

#### Python

```python
class Solution(object):
    def eraseOverlapIntervals(self, intervals):
        end, removed = float('-inf'), 0
        for s, e in sorted(intervals, key=lambda x: x[1]):
            if s >= end: 
                end = e
            else: 
                removed += 1
        return removed
```

## Partition Labels

> [Link to Leetcode question](https://leetcode.com/problems/partition-labels/description/)[^pl]
{: .prompt-info }

You are given a string `s`. We want to partition the string into as many parts as possible so that each letter appears in at most one part.

Note that the partition is done so that after concatenating all the parts in order, the resultant string should be `s`.

Return a list of integers representing the size of these parts.

**Example 1**

```
Input: s = "ababcbacadefegdehijhklij"
Output: [9,7,8]
Explanation:
The partition is "ababcbaca", "defegde", "hijhklij".
This is a partition so that each letter appears in at most one part.
A partition like "ababcbacadefegde", "hijhklij" is incorrect, because it splits s into less parts.
```

**Example 2**

```
Input: s = "eccbbbbdec"
Output: [10]
````

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0763.划分字母区间.html)[^plSolution].



### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [2095 Delete the Middle Node of a Linked List](https://leetcode.com/problems/delete-the-middle-node-of-a-linked-list/)[^dtmnoall] |        |      |



## Reference
[^mnoatbb]:Leetcode-452 Minimum Number of Arrows to Burst Balloons: [https://leetcode.com/problems/minimum-number-of-arrows-to-burst-balloons/description/](https://leetcode.com/problems/minimum-number-of-arrows-to-burst-balloons/description/).
[^mnoatbbSolution]:代码随想录-用最少数量的箭引爆气球: [https://programmercarl.com/0452.用最少数量的箭引爆气球.html](https://programmercarl.com/0452.用最少数量的箭引爆气球.html).
[^noi]:Leetcode-435 Non-overlapping Intervals: [https://leetcode.com/problems/non-overlapping-intervals/](https://leetcode.com/problems/non-overlapping-intervals/).
[^pl]:Leetcode-763 Partition Labels: [https://leetcode.com/problems/partition-labels/description/](https://leetcode.com/problems/partition-labels/description/).
[^plSolution]:代码随想录-划分字母区间: [https://programmercarl.com/0763.划分字母区间.html](https://programmercarl.com/0763.划分字母区间.html).
[^noiSolution]:代码随想录-无重叠区间: [https://programmercarl.com/0435.无重叠区间.html](https://programmercarl.com/0435.无重叠区间.html).


