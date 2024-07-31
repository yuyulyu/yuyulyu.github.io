---
title: Leet code Day 1
description: Examples of text, typography, math equations, diagrams, flowcharts, pictures, videos, and more.
author: yoyo
date: 2019-08-08 11:33:00 +0800
categories: [Blogging, Demo]
tags: [typography]
---

## Headings

<!-- markdownlint-capture -->
<!-- markdownlint-disable -->
# H1 — heading
{: .mt-4 .mb-0 }

## H2 — heading
{: data-toc-skip='' .mt-4 .mb-0 }

### H3 — heading
{: data-toc-skip='' .mt-4 .mb-0 }

#### H4 — heading
{: data-toc-skip='' .mt-4 }
<!-- markdownlint-restore -->

# Binary Search[^binarySearch]
[^binarySearch]:Leetcode-074 Binary Search: https://leetcode.com/problems/binary-search/.

## Description
Given an array of integers ```nums``` which is sorted in <ins>ascending order</ins>, and an integer ```target```, write a function to search ```target``` in ```nums```. If ```target``` exists, then return its index. Otherwise, return ```-1```.

You must write an algorithm with O(log n) runtime complexity.

**Example 1**
```Python
Input: nums = [-1,0,3,5,9,12], target = 9
Output: 4
Explanation: 9 exists in nums and its index is 4
```
