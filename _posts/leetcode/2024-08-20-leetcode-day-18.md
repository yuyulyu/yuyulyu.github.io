---
title: "Leetcode Day 18 - Binary Search Tree: Transformations and Conversions"
description: Examines BST transformations, such as trimming a tree within a given range, converting a sorted array into a balanced BST, and converting a BST to a greater tree by modifying its node values.
author: yoyo
date: 2024-08-20 23:07:00 +0800
categories: [Data Structure and Algorithm, Leetcode]
tags: [binary tree]
---

## Binary Tree

> [Link to note about binary tree](https://yuyulyu.github.io/posts/binary-tree/)
{: .prompt-tip }

| Diff                                                                                                | Problem                                                                                 | Python | Java |
|-----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [669 Trim a Binary Search Tree](#trim-a-binary-search-tree)                                          |        |      |
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                                | [108 Convert Sorted Array to Binary Search Tree](#convert-sorted-array-to-binary-search-tree)                |        |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                              | [538 Convert BST to Greater Tree](#convert-bst-to-greater-tree)               |✅      |      |


## Trim a Binary Search Tree

> [Link to Leetcode question](https://leetcode.com/problems/trim-a-binary-search-tree/description/)[^tabst]
{: .prompt-info }

Given the `root` of a binary search tree and the lowest and highest boundaries as `low` and `high`, trim the tree so that all its elements lies in `[low, high]`. Trimming the tree should not change the relative structure of the elements that will remain in the tree (i.e., any node's descendant should remain a descendant). It can be proven that there is a unique answer.

Return the root of the trimmed binary search tree. Note that the root may change depending on the given bounds.

**Example 1**

![Desktop View](/assets/image/leetcode/leetcode-day-18/trim-a-binary-search-tree-example-1.jpeg)

```
Input: root = [1,0,2], low = 1, high = 2
Output: [1,null,2]
```

**Example 2**

![Desktop View](/assets/image/leetcode/leetcode-day-18/trim-a-binary-search-tree-example-2.jpeg)

```
Input: root = [3,0,4,null,2,null,null,1], low = 1, high = 3
Output: [3,2,null,1]
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0669.修剪二叉搜索树.html)[^tabstSolution].


## Convert Sorted Array to Binary Search Tree

> [Link to Leetcode question](https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/description/)[^csatbst]
{: .prompt-info }

Given an integer array `nums` where the elements are sorted in ascending order, convert it to a 
height-balanced binary search tree.

**Example 1**

![Desktop View](/assets/image/leetcode/leetcode-day-18/convert-sorted-array-to-binary-search-tree-example-1.jpeg)

```
Input: nums = [-10,-3,0,5,9]
Output: [0,-3,9,-10,null,5]
Explanation: [0,-10,5,null,-3,null,9] is also accepted:
```

![Desktop View](/assets/image/leetcode/leetcode-day-18/convert-sorted-array-to-binary-search-tree-example-2.jpeg)

**Example 2**

![Desktop View](/assets/image/leetcode/leetcode-day-18/convert-sorted-array-to-binary-search-tree-example-3.jpeg)
```
Input: nums = [1,3]
Output: [3,1]
Explanation: [1,null,3] and [3,1] are both height-balanced BSTs.
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0108.将有序数组转换为二叉搜索树.html)[^csatbstSolution].


### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [109 Convert Sorted List to Binary Search Tree](https://leetcode.com/problems/convert-sorted-list-to-binary-search-tree/)[^csltbst] |        |      |


## Convert BST to Greater Tree

> [Link to Leetcode question](https://leetcode.com/problems/convert-bst-to-greater-tree/description/)[^cbtgt]
{: .prompt-info }

Given the root of a Binary Search Tree (BST), convert it to a Greater Tree such that every key of the original BST is changed to the original key plus the sum of all keys greater than the original key in BST.

As a reminder, a binary search tree is a tree that satisfies these constraints:

- The left subtree of a node contains only nodes with keys less than the node's key.
- The right subtree of a node contains only nodes with keys greater than the node's key.
- Both the left and right subtrees must also be binary search trees.
 
**Example 1**

![Desktop View](/assets/image/leetcode/leetcode-day-18/convert-bst-to-greater-tree-example-1.png)

```
Input: root = [4,1,6,0,2,5,7,null,null,null,3,null,null,null,8]
Output: [30,36,21,36,35,26,15,null,null,null,33,null,null,null,8]
```

**Example 2**

```
Input: root = [0,null,1]
Output: [1,null,1]
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0538.把二叉搜索树转换为累加树.html)[^cbtgtSolution].

#### Python

```python
class Solution(object):
    def convertBST(self, root):
        
        def getSum(node, s):
            if node is None:
                return 0

            new_s = s + node.val
            new_s += getSum(node.right,s)
            node.val = new_s
            new_s += getSum(node.left,new_s)

            return new_s - s
        
        getSum(root, 0)
        return root
```

## Reference
[^tabst]:Leetcode-669 Trim a Binary Search Tree: [https://leetcode.com/problems/trim-a-binary-search-tree/description/](https://leetcode.com/problems/trim-a-binary-search-tree/description/).
[^tabstSolution]:代码随想录-修剪二叉搜索树: [https://programmercarl.com/0669.修剪二叉搜索树.html](https://programmercarl.com/0669.修剪二叉搜索树.html).
[^csatbst]:Leetcode-108 Convert Sorted Array to Binary Search Tree: [https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/description/](https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/description/)
[^csatbstSolution]:代码随想录-将有序数组转换为二叉搜索树: [https://programmercarl.com/0108.将有序数组转换为二叉搜索树.html](https://programmercarl.com/0108.将有序数组转换为二叉搜索树.html).
[^csltbst]:Leetcode-109. Convert Sorted List to Binary Search Tree: [https://leetcode.com/problems/convert-sorted-list-to-binary-search-tree/](https://leetcode.com/problems/convert-sorted-list-to-binary-search-tree/).
[^cbtgt]:Leetcode-538 Convert BST to Greater Tree: [https://leetcode.com/problems/convert-bst-to-greater-tree/description/](https://leetcode.com/problems/convert-bst-to-greater-tree/description/).
[^cbtgtSolution]:代码随想录-把二叉搜索树转换为累加树: [https://programmercarl.com/0538.把二叉搜索树转换为累加树.html](https://programmercarl.com/0538.把二叉搜索树转换为累加树.html).
