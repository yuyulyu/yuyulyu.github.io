---
title: Leetcode Day 17 - Binary Tree
description: 235 Lowest Common Ancestor of a Binary Search Tree | 701 Insert into a Binary Search Tree |450 Delete Node in a BST
author: yoyo
date: 2024-08-19 14:03:00 +0800
categories: [Data Structure and Algorithm, Leetcode]
tags: [binary tree]
---

## Binary Tree

> [Link to note about binary tree](https://yuyulyu.github.io/posts/binary-tree/)
{: .prompt-tip }

| Diff                                                                                                | Problem                                                                                 | Python | Java |
|-----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [235 Lowest Common Ancestor of a Binary Search Tree](#lowest-common-ancestor-of-a-binary-search-tree)                                       |        |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [701 Insert into a Binary Search Tree](#insert-into-a-binary-search-tree)                                          |        |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [450 Delete Node in a BST](#delete-node-in-a-bst)                |        |      |


## Lowest Common Ancestor of a Binary Search Tree

> [Link to Leetcode question](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/description/)[^lcaoabst]
{: .prompt-info }

Given a binary search tree (BST), find the lowest common ancestor (LCA) node of two given nodes in the BST.

According to the definition of LCA on Wikipedia: “The lowest common ancestor is defined between two nodes `p` and `q` as the lowest node in `T` that has both `p` and `q` as descendants (where we allow a node to be a descendant of itself).” 

**Example 1**

![Desktop View](/assets/image/leetcode/leetcode-day-16/lowest-common-ancestor-of-a-binary-search-tree-example-1.png)

```
Input: root = [6,2,8,0,4,7,9,null,null,3,5], p = 2, q = 8
Output: 6
Explanation: The LCA of nodes 2 and 8 is 6.
```

**Example 2**

![Desktop View](/assets/image/leetcode/leetcode-day-16/lowest-common-ancestor-of-a-binary-search-tree-example-2.png)

```
Input: root = [6,2,8,0,4,7,9,null,null,3,5], p = 2, q = 4
Output: 2
Explanation: The LCA of nodes 2 and 4 is 2, since a node can be a descendant of itself according to the LCA definition.
```

**Example 3**

```
Input: root = [2,1], p = 2, q = 1
Output: 2
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0235.二叉搜索树的最近公共祖先.html#算法公开课)[^lcaoabstSolution].


## Insert into a Binary Search Tree

> [Link to Leetcode question](https://leetcode.com/problems/swap-nodes-in-pairs/description/)[^iiabst]
{: .prompt-info }

You are given the `root` node of a binary search tree (BST) and a `value` to insert into the tree. Return the root node of the BST after the insertion. It is guaranteed that the new value does not exist in the original BST.

Notice that there may exist multiple valid ways for the insertion, as long as the tree remains a BST after insertion. You can return any of them.

**Example 1**

![Desktop View](/assets/image/leetcode/leetcode-day-17/insert-into-a-binary-search-tree-example-1.jpeg)

```
Input: root = [4,2,7,1,3], val = 5
Output: [4,2,7,1,3,5]
Explanation: Another accepted tree is:
```

![Desktop View](/assets/image/leetcode/leetcode-day-17/insert-into-a-binary-search-tree-example-2.jpeg)

**Example 2**

```
Input: root = [40,20,60,10,30,50,70], val = 25
Output: [40,20,60,10,30,50,70,null,null,25]
```

**Example 3**

```
Input: root = [4,2,7,1,3,null,null,null,null,null,null], val = 5
Output: [4,2,7,1,3,5]
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0701.二叉搜索树中的插入操作.html)[^iiabstSolution].



## Delete Node in a BST

> [Link to Leetcode question](https://leetcode.com/problems/delete-node-in-a-bst/description//)[^dniab]
{: .prompt-info }

Given a root node reference of a BST and a key, delete the node with the given key in the BST. Return the root node reference (possibly updated) of the BST.

Basically, the deletion can be divided into two stages:
1. Search for a node to remove.
2. If the node is found, delete the node.
 
**Example 1**

![Desktop View](/assets/image/leetcode/leetcode-day-17/delete-node-in-a-bst-example-1.jpeg)

```
Input: root = [5,3,6,2,4,null,7], key = 3
Output: [5,4,6,2,null,null,7]
Explanation: Given key to delete is 3. So we find the node with value 3 and delete it.
One valid answer is [5,4,6,2,null,null,7], shown in the above BST.
Please notice that another valid answer is [5,2,6,null,4,null,7] and it's also accepted.
```

![Desktop View](/assets/image/leetcode/leetcode-day-17/delete-node-in-a-bst-example-2.jpeg)

**Example 2**

```
Input: root = [5,3,6,2,4,null,7], key = 0
Output: [5,3,6,2,4,null,7]
Explanation: The tree does not contain a node with value = 0.
```

**Example 3**

```
Input: root = [], key = 0
Output: []
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0450.删除二叉搜索树中的节点.html)[^dniabSolution].



## Reference
[^lcaoabstSolution]:代码随想录-二叉搜索树的最近公共祖先: [https://programmercarl.com/0235.二叉搜索树的最近公共祖先.html#算法公开课](https://programmercarl.com/0235.二叉搜索树的最近公共祖先.html#算法公开课).
[^lcaoabst]:Leetcode-235 Lowest Common Ancestor of a Binary Search Tree: [https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/description/](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/description/).
[^iiabst]:Leetcode-701 Insert into a Binary Search Tree: [https://leetcode.com/problems/insert-into-a-binary-search-tree/description/](https://leetcode.com/problems/insert-into-a-binary-search-tree/description/).
[^iiabstSolution]:代码随想录-二叉搜索树中的插入操作: [https://programmercarl.com/0701.二叉搜索树中的插入操作.html](https://programmercarl.com/0701.二叉搜索树中的插入操作.html).
[^dniab]:Leetcode-450 Delete Node in a BST: [https://leetcode.com/problems/delete-node-in-a-bst/description/](https://leetcode.com/problems/delete-node-in-a-bst/description/).
[^dniabSolution]:代码随想录-删除二叉搜索树中的节点: [https://programmercarl.com/0450.删除二叉搜索树中的节点.html](https://programmercarl.com/0450.删除二叉搜索树中的节点.html).
[^iiabst]:Leetcode-701 Insert into a Binary Search Tree: [https://leetcode.com/problems/swap-nodes-in-pairs/description/](https://leetcode.com/problems/swap-nodes-in-pairs/description/).

