---
title: Leetcode Day 3 - Linked List Basics
description: Introduces fundamental linked list operations. Topics include removing elements from a list, designing a custom linked list with core operations, and reversing a singly linked list, highlighting basic traversal and manipulation.
author: yoyo
date: 2024-08-02 15:50:00 +0800
categories: [Data Structure and Algorithm, Leetcode, Linked List]
tags: [linked list,recursion]
---

## Linked List 1[^dmsxl]

| Diff                                                                                                 | Problem                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|--------|------|
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                               | [203 Remove Linked List Elements](#remove-linked-list-elements)                                | ✅     | ✅   |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [707 Design Linked List](#design-linked-list)                                                  | ✅     |      |
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                               | [206 Reverse Linked List](#reverse-linked-list)                                                | ✅     | ✅   |

## Remove Linked List Elements

> [Link to Leetcode question](https://leetcode.com/problems/remove-linked-list-elements/description/)[^rllr]
{: .prompt-info }

Given the ```head``` of a linked list and an integer ```val```, remove all the nodes of the linked list that has ```Node.val == val```, and return the new head.

**Example 1**


![Desktop View](/assets/image/leetcode/leetcode-day-3/remove-linked-list-elements-example-1.jpg)

```
Input: head = [1,2,6,3,4,5,6], val = 6
Output: [1,2,3,4,5]
```

**Example 2**

```
Input: head = [], val = 1
Output: []
```

**Example 3**

```
Input: head = [7,7,7,7], val = 7
Output: []
```

### Solution[^rllrSolution]

#### Python

```python
class Solution(object):
    def removeElements(self, head, val):
        """
        :type head: ListNode
        :type val: int
        :rtype: ListNode
        """
        node = head
        while(node is not None and node.next is not None):
            next_node = node.next
            if (next_node.val == val):
                node.next = next_node.next
            else:
                node = next_node
        if (head is not None and head.val == val):
            head = head.next
        return head
```

#### Java

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode removeElements(ListNode head, int val) {
        ListNode dummy = new ListNode();
        dummy.next = head;
        ListNode node = head;
        ListNode prev = dummy;
        while(node != null){
            if(node.val == val){
                prev.next = node.next;
            }  
            else{
                prev = node;
            }
            node = node.next;
        }
    return dummy.next;
    }
}
```

### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [237 Delete Node in a Linked List](https://leetcode.com/problems/delete-node-in-a-linked-list/description/)[^dniall] |        |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [2095 Delete the Middle Node of a Linked List](https://leetcode.com/problems/delete-the-middle-node-of-a-linked-list/description/)[^dtmnoall] |        |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [3217 Delete Nodes From Linked List Present in Array](https://leetcode.com/problems/delete-nodes-from-linked-list-present-in-array/description/)[^dnfllpia] |        |      |
                                                  |            |            |

## Design Linked List

> [Link to Leetcode question](https://leetcode.com/problems/design-linked-list/description/)[^dll]
{: .prompt-info }

Design your implementation of the linked list. You can choose to use a singly or doubly linked list.

A node in a singly linked list should have two attributes: ```val``` and ```next```. ```val``` is the value of the current node, and ```next``` is a pointer/reference to the next node.

If you want to use the doubly linked list, you will need one more attribute ```prev``` to indicate the previous node in the linked list. Assume all nodes in the linked list are 0-indexed.

Implement the ```MyLinkedList``` class:

  - ```MyLinkedList()``` Initializes the ```MyLinkedList``` object.
  - ```int get(int index)``` Get the value of the indexth node in the linked list. If the index is invalid, return ```-1```.
  - ```void addAtHead(int val)``` Add a node of value ```val``` before the first element of the linked list. After the insertion, the new node will be the first node of the linked list.
  - ```void addAtTail(int val)``` Append a node of value ```val``` as the last element of the linked list.
  - ```void addAtIndex(int index, int val)``` Add a node of value ```val``` before the indexth node in the linked list. If index equals the length of the linked list, the node will be appended to the end of the linked list. If index is greater than the length, the node will not be inserted.
  - ```void deleteAtIndex(int index)``` Delete the ```index<sup>th</sup>``` node in the linked list, if the index is valid.

**Example 1**

```
Input
["MyLinkedList", "addAtHead", "addAtTail", "addAtIndex", "get", "deleteAtIndex", "get"]
[[], [1], [3], [1, 2], [1], [1], [1]]
Output
[null, null, null, null, 2, null, 3]

Explanation
MyLinkedList myLinkedList = new MyLinkedList();
myLinkedList.addAtHead(1);
myLinkedList.addAtTail(3);
myLinkedList.addAtIndex(1, 2);    // linked list becomes 1->2->3
myLinkedList.get(1);              // return 2
myLinkedList.deleteAtIndex(1);    // now the linked list is 1->3
myLinkedList.get(1);              // return 3
```

### Solution[^dllSolution]

#### Python

```python
lass MyLinkedList(object):

    def __init__(self,val = None,next_ = None,prev = None):
        self.val = val
        self.next = next_
        self.prev = prev

    def get(self, index):
        """
        :type index: int
        :rtype: int
        """
        if(index == 0):
            return self.val if self.val is not None
            return -1
            if(self.val is not None):
                return self.val
            else:
                return -1
        node = self
        for i in range(index):
            if node.next is None:
                return -1
            node = node.next
        return node.val 

    def addAtHead(self, val):
        """
        :type val: int
        :rtype: None
        """
        if(self.val is None):
            self.val = val
        else:
            node = MyLinkedList(self.val,self.next,self)
            self.val = val
            self.next = node        

    def addAtTail(self, val):
        """
        :type val: int
        :rtype: None
        """
        if(self.val is None):
            self.val = val
        else:
            node = self
            while(node.next is not None):
                node = node.next
            node.next = MyLinkedList(val,None,node)

    def addAtIndex(self, index, val):
        """
        :type index: int
        :type val: int
        :rtype: None
        """
        if(self.val is None and index == 0):
            self.val = val
            return
        elif(index==0):
            self.addAtHead(val)
            return
        elif(self.val is not None):
            node = self
            prev = None
            for i in range(index):
                if node.next is None:
                    if (index != i+1):
                        return 
                    else:
                        node.next = MyLinkedList(val,None,node)
                        return
                prev = node
                node = node.next
            if node is not None:
                node.prev = MyLinkedList(val,node,prev)
                if(prev is not None):
                    prev.next = node.prev
            else:
                prev.next = MyLinkedList(val,None,prev)

    def deleteAtIndex(self, index):
        """
        :type index: int
        :rtype: None
        """
        if(index == 0):
            if(self.next is not None):
                self.val = self.next.val
                self.next = self.next.next
                self.prev = None 
                return
            else:
                self.val = None
                return
        else:
            node = self
            prev = None
            for i in range(index):
                if node.next is None:
                    print("delete out of range")
                    return 
                prev = node
                node = node.next
            if node is None:
                return
            if(prev is not None):
                prev.next = node.next
            if (node.next is not None):
                node.next.prev = prev
```

### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Hard](https://img.shields.io/badge/Hard-red)                                                       | [1206 Design Skiplist](https://leetcode.com/problems/design-skiplist/)[^ds]                              |        |      |


## Reverse Linked List

> [Link to Leetcode question](https://leetcode.com/problems/reverse-linked-list/description/)[^rll]
{: .prompt-info }

Given the ···head··· of a singly linked list, reverse the list, and return the reversed list.

**Example 1**

```
Input: head = [1,2,3,4,5]
Output: [5,4,3,2,1]
```

**Example 2**

```
Input: head = []
Output: []
```

### Solution[^rllSolution]


#### Python

```python
class Solution(object):
    def reverseList(self, head):
        if head is not None:
            node = head
            prev_temp = None
            old_head = node
            next_head = node.next
            while(next_head):
                new_head = next_head
                next_head = new_head.next
                new_head.next = old_head
                old_head.next = prev_temp
                prev_temp = old_head
                old_head = new_head
            return old_head
        else:
            return None
```

#### Java

```java
class Solution {
    public ListNode reverseList(ListNode head) {
        if (head == null){
            return null;
        }
        ListNode oldHead = null;
        ListNode nextHead = head.next;
        ListNode newHead = head;

        while(nextHead != null){
            newHead.next = oldHead;
            oldHead = newHead;
            newHead = nextHead;
            nextHead = newHead.next;
            newHead.next = oldHead;
        }
        return newHead;
    }
}
```

### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                               | [234 Palindrome Linked List](https://leetcode.com/problems/palindrome-linked-list/description/)[^pll]   |        |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [92 Reverse Linked List II](https://leetcode.com/problems/reverse-linked-list-ii/description/)[^rllii]  |        |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [2130 Maximum Twin Sum of a Linked List](https://leetcode.com/problems/maximum-twin-sum-of-a-linked-list/description/)[^mtsoall] |        |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [2807 Insert Greatest Common Divisors in Linked List](https://leetcode.com/problems/insert-greatest-common-divisors-in-linked-list/description/)[^igcdill] |        |      |
                                                                        |            |            |

## Reference
[^dmsxl]:代码随想录-链表理论基础: [https://programmercarl.com/链表理论基础.html](https://programmercarl.com/链表理论基础.html)
[^rllr]:Leetcode-203 Remove Linked List Elements: [https://leetcode.com/problems/remove-linked-list-elements/description/](https://leetcode.com/problems/remove-linked-list-elements/description/).
[^rllrSolution]:代码随想录-移除链表元素: [https://programmercarl.com/0203.移除链表元素.html](https://programmercarl.com/0203.移除链表元素.html).
[^dll]:Leetcode-707 Design Linked List: [https://leetcode.com/problems/design-linked-list/description/](https://leetcode.com/problems/design-linked-list/description/).
[^dllSolution]:代码随想录-设计链表：[https://programmercarl.com/0707.设计链表.html#算法公开课](https://programmercarl.com/0707.设计链表.html#算法公开课).
[^rll]:Leetcode-206 Reverse Linked List: [https://leetcode.com/problems/reverse-linked-list/description/](https://leetcode.com/problems/reverse-linked-list/description/).
[^rllSolution]: 代码随想录-翻转链表: [https://programmercarl.com/0206.翻转链表.html](https://programmercarl.com/0206.翻转链表.html).
[^dniall]: Leetcode-237 Delete Node in a Linked List: [https://leetcode.com/problems/delete-node-in-a-linked-list/description/](https://leetcode.com/problems/delete-node-in-a-linked-list/description/).
[^dtmnoall]: Leetcode-2095 Delete the Middle Node of a Linked List: [https://leetcode.com/problems/delete-the-middle-node-of-a-linked-list/description/](https://leetcode.com/problems/delete-the-middle-node-of-a-linked-list/description/).
[^dnfllpia]: Leetcode-3217 Delete Nodes From Linked List Present in Array: [https://leetcode.com/problems/delete-nodes-from-linked-list-present-in-array/description/](https://leetcode.com/problems/delete-nodes-from-linked-list-present-in-array/description/).
[^ds]: Leetcode-1206 Design Skiplist: [https://leetcode.com/problems/design-skiplist/](https://leetcode.com/problems/design-skiplist/).
[^pll]: Leetcode-234 Palindrome Linked List: [https://leetcode.com/problems/palindrome-linked-list/description/](https://leetcode.com/problems/palindrome-linked-list/description/).
[^rllii]: Leetcode-92 Reverse Linked List II: [https://leetcode.com/problems/reverse-linked-list-ii/description/](https://leetcode.com/problems/reverse-linked-list-ii/description/).
[^mtsoall]: Leetcode-2130 Maximum Twin Sum of a Linked List: [https://leetcode.com/problems/maximum-twin-sum-of-a-linked-list/description/](https://leetcode.com/problems/maximum-twin-sum-of-a-linked-list/description/).
[^igcdill]: Leetcode-2807 Insert Greatest Common Divisors in Linked List: [https://leetcode.com/problems/insert-greatest-common-divisors-in-linked-list/description/](https://leetcode.com/problems/insert-greatest-common-divisors-in-linked-list/description/).



