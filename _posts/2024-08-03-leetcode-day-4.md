---
title: Leetcode Day 4
description: 24 Swap Nodes in Pairs | 19 Remove Nth Node From End of List | 160 Intersection of Two Linked Lists | 142 Linked List Cycle II
author: yoyo
date: 2024-08-03 23:07:00 +0800
categories: [Algorithm, Leetcode, LinkedList]
tags: [linked list,recursion,two pointers,hash table]
---

![Easy](https://img.shields.io/badge/Easy-brightgreen) 
![Medium](https://img.shields.io/badge/Medium-yellow)
![Hard](https://img.shields.io/badge/Hard-red)

| Topic: Linked list[^dmsxl]                                                                          | Problem                                                                                 | Python | Java |
|-----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [24 Swap Nodes in Pairs](#swap-nodes-in-pairs)                                          |        |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [19 Remove Nth Node From End of List](#remove-nth-node-from-end-of-list)                |        |      |
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                              | [160 Intersection of Two Linked Lists](#intersection-of-two-linked-lists)               |        |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [142 Linked List Cycle II](#linked-list-cycle-ii)                                       |        |      |


[^dmsxl]:代码随想录-链表:https://programmercarl.com/链表理论基础.html.

## Swap Nodes in Pairs

> [Link to Leetcode question](https://leetcode.com/problems/swap-nodes-in-pairs/description/)[^snip]

Given a linked list, swap every two adjacent nodes and return its head. You must solve the problem without modifying the values in the list's nodes (i.e., only nodes themselves may be changed.)

**Example 1**

![Desktop View](/assets/image//leetcode-day4-1.jpg){: .normal }

```
Input: head = [1,2,3,4]
Output: [2,1,4,3]
```

**Example 2**
```
Input: head = []
Output: []
```

**Example 3**
```
Input: head = [1]
Output: [1]
```

### Solution[^snipSolution]

### Similar Questions

| Similar Questions                                                                |   Python   |   Java     |
|----------------------------------------------------------------------------------|------------|------------|
| 🟡 [1721 Swapping Nodes in a Linked List](https://leetcode.com/problems/swapping-nodes-in-a-linked-list/description/)[^sniall]                                                                                      |            |            |
| 🔴 [25 Reverse Nodes in k-Group](https://leetcode.com/problems/reverse-nodes-in-k-group/)[^rnikg]                                                                                                                   |            |            |



## Remove Nth Node From End of List

> [Link to Leetcode question](https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/)[^rnnfeol]

Given the `head` of a linked list, remove the `nth` node from the end of the list and return its head.

**Example 1**

![Desktop View](/assets/image//leetcode-day4-2.jpg){: .normal }

```
Input: head = [1,2,3,4,5], n = 2
Output: [1,2,3,5]
```

**Example 2**
```
Input: head = [1], n = 1
Output: []
```

**Example 3**
```
Input: head = [1,2], n = 1
Output: [1]
```

### Solution[^rnnfeolSolution]

### Similar Questions

| Similar Questions                                                                |   Python   |   Java     |
|----------------------------------------------------------------------------------|------------|------------|
| 🟡 [2095 Delete the Middle Node of a Linked List](https://leetcode.com/problems/delete-the-middle-node-of-a-linked-list/)[^dtmnoall]                                                                          |            |            |


##  Intersection of Two Linked Lists
> [Link to Leetcode question](https://leetcode.com/problems/intersection-of-two-linked-lists/description/)[^iotll]

### Solution[^iotllSolution]

### Similar Questions

| Similar Questions                                                                |   Python   |   Java     |
|----------------------------------------------------------------------------------|------------|------------|
| 🟢 [599 Minimum Index Sum of Two Lists](https://leetcode.com/problems/minimum-index-sum-of-two-lists/)[^misowll]                                                                                                    |            |            |

## Linked List Cycle II

> [Link to Leetcode question](https://leetcode.com/problems/linked-list-cycle-ii/description/)[^llc]

### Solution[^llcSolution]


### Similar Questions

| Similar Questions                                                                |   Python   |   Java     |
|----------------------------------------------------------------------------------|------------|------------|
| 🟢 [287 Find the Duplicate Number](https://leetcode.com/problems/find-the-duplicate-number/)[^ftdn]                                                                                                                 |            |            |

## Reference
[^dmsxl]:代码随想录-链表理论基础: [https://programmercarl.com/链表理论基础.html](https://programmercarl.com/链表理论基础.html)
[^snip]:Leetcode-24 Swap Nodes in Pairs: [https://leetcode.com/problems/swap-nodes-in-pairs/description/](https://leetcode.com/problems/swap-nodes-in-pairs/description/)
[^snipSolution]:代码随想录-两两交换链表中的节点: [https://programmercarl.com/0024.两两交换链表中的节点.html](https://programmercarl.com/0024.两两交换链表中的节点.html).
[^rnnfeol]:Leetcode-19 Remove Nth Node From End of List: [https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/](https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/).
[^rnnfeolSolution]:代码随想录-删除链表的倒数第N个节点: [https://programmercarl.com/0019.删除链表的倒数第N个节点.html](https://programmercarl.com/0019.删除链表的倒数第N个节点.html).
[^iotll]:Leetcode-160 Intersection of Two Linked Lists: [https://leetcode.com/problems/intersection-of-two-linked-lists/description/](https://leetcode.com/problems/intersection-of-two-linked-lists/description/).
[^iotllSolution]:代码随想录-面试题 02.07. 链表相交: [https://programmercarl.com/面试题02.07.链表相交.html](https://programmercarl.com/面试题02.07.链表相交.html).
[^llc]:Leetcode-142 Linked List Cycle II: [https://leetcode.com/problems/linked-list-cycle-ii/description/](https://leetcode.com/problems/linked-list-cycle-ii/description/).
[^llcSolution]:代码随想录-环形链表II:[https://programmercarl.com/0142.环形链表II.html](https://programmercarl.com/0142.环形链表II.html).
[^sniall]: Leetcode-1721 Swapping Nodes in a Linked List: [https://leetcode.com/problems/swapping-nodes-in-a-linked-list/description/](https://leetcode.com/problems/swapping-nodes-in-a-linked-list/description/).
[^rnikg]: Leetcode-25 Reverse Nodes in k-Group: [https://leetcode.com/problems/reverse-nodes-in-k-group/](https://leetcode.com/problems/reverse-nodes-in-k-group/).
[^dtmnoall]: Leetcode-2095 Delete the Middle Node of a Linked List: [https://leetcode.com/problems/delete-the-middle-node-of-a-linked-list/](https://leetcode.com/problems/delete-the-middle-node-of-a-linked-list/).
[^misowll]: Leetcode-599 Minimum Index Sum of Two Lists: [https://leetcode.com/problems/minimum-index-sum-of-two-lists/](https://leetcode.com/problems/minimum-index-sum-of-two-lists/).
[^ftdn]: Leetcode-287 Find the Duplicate Number: [https://leetcode.com/problems/find-the-duplicate-number/](https://leetcode.com/problems/find-the-duplicate-number/).

