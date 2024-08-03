---
title: Leetcode Day 4
description: 24 Swap Nodes in Pairs | 707 Design Linked List | 206 Reverse Linked List
author: yoyo
date: 2024-08-03 23:07:00 +0800
categories: [Algorithm, Leetcode]
tags: [linked list,recursion]
---

| **Topic**: Linked list[^dmsxl]                                  |  Python |  Java    |
|-----------------------------------------------------------------|---------|----------|
| [24 Swap Nodes in Pairs](#swap-nodes-in-pairs)                  |✅       |✅        |
| [707 Design Linked List](#design-linked-list)                   |✅       |          |
| [206 Reverse Linked List](#reverse-linked-list)                 |✅       |✅        |

[^dmsxl]:代码随想录-链表:https://programmercarl.com/链表理论基础.html.

## Swap Nodes in Pairs

> [Link to Leetcode question](https://leetcode.com/problems/swap-nodes-in-pairs/description/)[^snip]

Given a linked list, swap every two adjacent nodes and return its head. You must solve the problem without modifying the values in the list's nodes (i.e., only nodes themselves may be changed.)

**Example 1**

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


## Design Linked List

> [Link to Leetcode question](https://leetcode.com/problems/design-linked-list/description/)[^dll]

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

**Python**

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


## Reverse Linked List

> [Link to Leetcode question](https://leetcode.com/problems/reverse-linked-list/description/)[^rll]

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

**Java**

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

## Reference
[^dmsxl]:代码随想录-链表理论基础: [https://programmercarl.com/链表理论基础.html](https://programmercarl.com/链表理论基础.html)
[^snip]:Leetcode-24 Swap Nodes in Pairs: [https://leetcode.com/problems/swap-nodes-in-pairs/description/](https://leetcode.com/problems/swap-nodes-in-pairs/description/)
[^snipSolution]:代码随想录-两两交换链表中的节点: [https://programmercarl.com/0024.两两交换链表中的节点.html](https://programmercarl.com/0024.两两交换链表中的节点.html).

[^dll]:Leetcode-707 Design Linked List: [https://leetcode.com/problems/design-linked-list/description/](https://leetcode.com/problems/design-linked-list/description/).
[^dllSolution]:代码随想录-设计链表：[https://programmercarl.com/0707.设计链表.html#算法公开课](https://programmercarl.com/0707.设计链表.html#算法公开课).
[^rll]:Leetcode-206 Reverse Linked List: [https://leetcode.com/problems/reverse-linked-list/description/](https://leetcode.com/problems/reverse-linked-list/description/).
[^rllSolution]: 代码随想录-翻转链表: [https://programmercarl.com/0206.翻转链表.html](https://programmercarl.com/0206.翻转链表.html).
