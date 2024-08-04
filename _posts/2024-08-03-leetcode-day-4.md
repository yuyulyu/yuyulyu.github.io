---
title: Leetcode Day 4 - Linked List 2
description: 24 Swap Nodes in Pairs | 19 Remove Nth Node From End of List | 160 Intersection of Two Linked Lists | 142 Linked List Cycle II
author: yoyo
date: 2024-08-03 23:07:00 +0800
categories: [Algorithm, Leetcode, LinkedList]
tags: [linked list,recursion,two pointers,hash table]
---

![Easy](https://img.shields.io/badge/Easy-brightgreen) 
![Medium](https://img.shields.io/badge/Medium-yellow)
![Hard](https://img.shields.io/badge/Hard-red)

## Linked List 2[^dmsxl] 

| Diff                                                                                                | Problem                                                                                 | Python | Java |
|-----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [24 Swap Nodes in Pairs](#swap-nodes-in-pairs)                                          |✅      |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [19 Remove Nth Node From End of List](#remove-nth-node-from-end-of-list)                |✅      |      |
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                              | [160 Intersection of Two Linked Lists](#intersection-of-two-linked-lists)               |✅      |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [142 Linked List Cycle II](#linked-list-cycle-ii)                                       |        |      |


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
**Python**

```python
class Solution(object):
    def swapPairs(self, head):
        if head is None or head.next is None:
            return head

        odd = head
        even = head.next
        old = None

        while((even is not None) and (odd is not None)):
            odd.next = even.next
            even.next = odd
            if old is not None:
                old.next = even
            else:
                head = even
            old = odd
            odd = odd.next
            
            if odd is not None:
                even = odd.next
        
        return head
```

### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [1721 Swapping Nodes in a Linked List](https://leetcode.com/problems/swapping-nodes-in-a-linked-list/description/)[^sniall] |        |      |
| ![Hard](https://img.shields.io/badge/Hard-red)                                                       | [25 Reverse Nodes in k-Group](https://leetcode.com/problems/reverse-nodes-in-k-group/)[^rnikg]          |        |      |

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

**Python**

```python
class Solution(object):
    def removeNthFromEnd(self, head, n):
        cur = head
        dummy = ListNode(0)
        dummy.next = head
        prev = dummy
        nth = cur
        i = 1

        while cur.next is not None:
            if i == n:
                prev = nth
                nth = nth.next
            else:
                i += 1
            cur = cur.next
        
        prev.next = nth.next

        return dummy.next
```

### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [2095 Delete the Middle Node of a Linked List](https://leetcode.com/problems/delete-the-middle-node-of-a-linked-list/)[^dtmnoall] |        |      |



##  Intersection of Two Linked Lists
> [Link to Leetcode question](https://leetcode.com/problems/intersection-of-two-linked-lists/description/)[^iotll]

Given the heads of two singly linked-lists `headA` and `headB`, return the node at which the two lists intersect. If the two linked lists have no intersection at all, return `null`.

For example, the following two linked lists begin to intersect at node `c1`:

![Desktop View](/assets/image//leetcode-day4-3.png){: .normal }

The test cases are generated such that there are no cycles anywhere in the entire linked structure.

**Note** that the linked lists must **retain their original structure** after the function returns.

**Example 1:**

![Desktop View](/assets/image//leetcode-day4-4.png){: .normal }

```
Input: intersectVal = 8, listA = [4,1,8,4,5], listB = [5,6,1,8,4,5], skipA = 2, skipB = 3
Output: Intersected at '8'
```

**Example 2**

![Desktop View](/assets/image//leetcode-day4-5.png){: .normal }

```
Input: intersectVal = 0, listA = [2,6,4], listB = [1,5], skipA = 3, skipB = 2
Output: No intersection
```

### Solution[^iotllSolution]

**Python**

```python
class Solution(object):
    def getIntersectionNode(self, headA, headB):
        pA = headA
        pB = headB
        noneA = True
        noneB = True

        while(pA != pB):
            if(pA.next is not None):
                pA = pA.next
            elif(noneA):
                pA = headB
                noneA = False
            else:
                return None
            
            if(pB.next is not None):
                pB = pB.next
            elif(noneB):
                pB = headA
                noneB = False
            else:
                return None
        return pA
```

### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                               | [599 Minimum Index Sum of Two Lists](https://leetcode.com/problems/minimum-index-sum-of-two-lists/)[^misowll] |        |      |

## Linked List Cycle II

> [Link to Leetcode question](https://leetcode.com/problems/linked-list-cycle-ii/description/)[^llc]

Given the `head` of a linked list, return the node where the cycle begins. If there is no cycle, return `null`.

There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the next pointer. Internally, `pos` is used to denote the index of the node that tail's `next` pointer is connected to **(0-indexed)**. It is `-1` if there is no cycle. Note that `pos` **is not passed as a parameter**.

**Do not modify** the linked list.

**Example 1**

![Desktop View](/assets/image//leetcode-day4-6.png){: .normal }

```
Input: head = [3,2,0,-4], pos = 1
Output: tail connects to node index 1
Explanation: There is a cycle in the linked list, where tail connects to the second node.
```

**Example 2**

![Desktop View](/assets/image//leetcode-day4-7.png){: .normal }

```
Input: head = [1,2], pos = 0
Output: tail connects to node index 0
Explanation: There is a cycle in the linked list, where tail connects to the first node.
```

**Example 3**

![Desktop View](/assets/image//leetcode-day4-8.png){: .normal }

```
Input: head = [1], pos = -1
Output: no cycle
Explanation: There is no cycle in the linked list.
```

### Solution[^llcSolution]

**Python**

```python
class Solution(object):
    def detectCycle(self, head):
        if head is None:
            return None

        fast, slow = head, head

        while(fast is not None and fast.next is not None):
            fast = fast.next.next
            slow = slow.next
            if(fast == slow):
                break
        
        if(fast is None or fast.next is None):
            return None

        fast = head
        while(fast != slow):
            fast = fast.next
            slow = slow.next
        
        return fast
```


### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                               | [287 Find the Duplicate Number](https://leetcode.com/problems/find-the-duplicate-number/)[^ftdn]         |        |      |


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

