---
title: Leetcode Day 3
description: 203  Remove Linked List Elements | 707 Design Linked List | 206 Reverse Linked List
author: yoyo
date: 2024-08-02 15:50:00 +0800
categories: [Algorithm, Leetcode]
tags: [linked list,recursion]
---

**Topic**: Linked list[^dmsxl]
  * [203  Remove Linked List Elements](https://leetcode.com/problems/remove-linked-list-elements/description/) ✅
  * [707 Design Linked List](https://leetcode.com/problems/design-linked-list/description/)
  * [206 Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/description/) ✅

[^dmsxl]:代码随想录-链表:https://programmercarl.com/链表理论基础.html.

## Remove Linked List Elements[^rllr]
Given the ```head``` of a linked list and an integer ```val```, remove all the nodes of the linked list that has ```Node.val == val```, and return the new head.

[^rllr]:Leetcode-203 Remove Linked List Elements: https://leetcode.com/problems/remove-linked-list-elements/description/)

**Example 1**

![Desktop View](/assets/image//leetcode-day3-1.jpg){: .normal }

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

### Solution
```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
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

## Design Linked List[^dll]

[^dll]:Leetcode-707 Design Linked List: https://leetcode.com/problems/design-linked-list/description/

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


## Reverse Linked List[^rll]

[^rll]:Leetcode-206 Reverse Linked List: https://leetcode.com/problems/reverse-linked-list/description/.

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

### Solution

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def reverseList(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
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

