---
title: Leetcode Day 16 - Binary Tree
description: 530 Minimum Absolute Difference in BST | 501 Find Mode in Binary Search Tree | 236 Lowest Common Ancestor of a Binary Tree | 235 Lowest Common Ancestor of a Binary Search Tree
author: yoyo
date: 2024-08-17 23:07:00 +0800
categories: [Data Structure and Algorithm, Leetcode]
tags: [binary tree]
---

![Easy](https://img.shields.io/badge/Easy-brightgreen) 
![Medium](https://img.shields.io/badge/Medium-yellow)
![Hard](https://img.shields.io/badge/Hard-red)

## <Topic> [^dmsxl] 

| Diff                                                                                                | Problem                                                                                 | Python | Java |
|-----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|--------|------|
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                                | [530 Minimum Absolute Difference in BST](#minimum-absolute-difference-in-bst)                                          |        |      |
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                                | [501 Find Mode in Binary Search Tree](#find-mode-in-binary-search-tree)                |✅      |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                              | [236 Lowest Common Ancestor of a Binary Tree](#lowest-common-ancestor-of-a-binary-tree)               |        |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [235 Lowest Common Ancestor of a Binary Search Tree](#lowest-common-ancestor-of-a-binary-search-tree)                                       |        |      |

## Minimum Absolute Difference in BST

> [Link to Leetcode question](https://leetcode.com/problems/minimum-absolute-difference-in-bst/description/)[^madib]
{: .prompt-info }

Given the `root` of a Binary Search Tree (BST), return the minimum absolute difference between the values of any two different nodes in the tree.

**Example 1**

[image]: minimum-absolute-difference-in-bst-example-1

```
Input: root = [4,2,6,1,3]
Output: 1
```

**Example 2**

[image]: minimum-absolute-difference-in-bst-example-2

```
Input: root = [1,0,48,null,null,12,49]
Output: 1
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0530.二叉搜索树的最小绝对差.html)[^madibSolution].


### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [532 K-diff Pairs in an Array](https://leetcode.com/problems/k-diff-pairs-in-an-array/)[^kdpiaa] |        |      |

## Find Mode in Binary Search Tree

> [Link to Leetcode question](https://leetcode.com/problems/find-mode-in-binary-search-tree/description/)[^fmibst]
{: .prompt-info }

Given the `root` of a binary search tree (BST) with duplicates, return all the mode(s) (i.e., the most frequently occurred element) in it.

If the tree has more than one mode, return them in any order.

Assume a BST is defined as follows:

- The left subtree of a node contains only nodes with keys less than or equal to the node's key.
- The right subtree of a node contains only nodes with keys greater than or equal to the node's key.
- Both the left and right subtrees must also be binary search trees.

**Example 1**

[image]: find-mode-in-binary-search-tree-example-1

```
Input: root = [1,null,2,2]
Output: [2]
```

**Example 2**

```
Input: root = [0]
Output: [0]
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0501.二叉搜索树中的众数.html)[^fmibstSolution].

#### Python

```python
class Solution(object):
    def __init__(self):
        self.dict = {}
        self.ans=[]
        self.mx=-1
    def solve (self,root):
        if root is None: return
        self.dict[root.val] = self.dict.get(root.val, 0) + 1
        if self.dict[root.val]==self.mx:
            self.ans.append(root.val)
        elif self.dict[root.val]>self.mx:
            self.mx=self.dict[root.val]
            self.ans=[]
            self.ans.append(root.val)

        self.solve(root.left)
        self.solve(root.right)
    def findMode(self, root):
        
        self.solve(root)
        return self.ans
```

## Lowest Common Ancestor of a Binary Tree

> [Link to Leetcode question](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/description/)[^rnnfeol]
{: .prompt-info }

Given a binary tree, find the lowest common ancestor (LCA) of two given nodes in the tree.

According to the definition of LCA on Wikipedia: “The lowest common ancestor is defined between two nodes `p` and `q` as the lowest node in `T` that has both `p` and `q` as descendants (where we allow a node to be a descendant of itself).”

**Example 1**

[image]: lowest-common-ancestor-of-a-binary-tree-example-1

```
Input: root = [3,5,1,6,2,0,8,null,null,7,4], p = 5, q = 1
Output: 3
Explanation: The LCA of nodes 5 and 1 is 3.
```

**Example 2**

[image]: lowest-common-ancestor-of-a-binary-tree-example-2

```
Input: root = [3,5,1,6,2,0,8,null,null,7,4], p = 5, q = 4
Output: 5
Explanation: The LCA of nodes 5 and 4 is 5, since a node can be a descendant of itself according to the LCA definition.
```

**Example 3**

```
Input: root = [1,2], p = 1, q = 2
Output: 1
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0236.二叉树的最近公共祖先.html)[^rnnfeolSolution].

## Lowest Common Ancestor of a Binary Search Tree

> [Link to Leetcode question](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/description/)[^lcaoabst]
{: .prompt-info }

Given a binary search tree (BST), find the lowest common ancestor (LCA) node of two given nodes in the BST.

According to the definition of LCA on Wikipedia: “The lowest common ancestor is defined between two nodes `p` and `q` as the lowest node in `T` that has both `p` and `q` as descendants (where we allow a node to be a descendant of itself).” 

**Example 1**

[image]: lowest-common-ancestor-of-a-binary-search-tree-example-1

```
Input: root = [6,2,8,0,4,7,9,null,null,3,5], p = 2, q = 8
Output: 6
Explanation: The LCA of nodes 2 and 8 is 6.
```

**Example 2**

[image]: lowest-common-ancestor-of-a-binary-search-tree-example-2

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

[^lcaoabstSolution]:代码随想录-二叉搜索树的最近公共祖先: [https://programmercarl.com/0235.二叉搜索树的最近公共祖先.html#算法公开课](https://programmercarl.com/0235.二叉搜索树的最近公共祖先.html#算法公开课).
### Similar Questions

## Reference
[^madib]:Leetcode-530 Minimum Absolute Difference in BST: [https://leetcode.com/problems/minimum-absolute-difference-in-bst/description/](https://leetcode.com/problems/minimum-absolute-difference-in-bst/description/).
[^madibSolution]:代码随想录-二叉搜索树的最小绝对差: [https://programmercarl.com/0530.二叉搜索树的最小绝对差.html](https://programmercarl.com/0530.二叉搜索树的最小绝对差.html).
[^kdpiaa]:Leetcode-532 K-diff Pairs in an Array: [https://leetcode.com/problems/k-diff-pairs-in-an-array/](https://leetcode.com/problems/k-diff-pairs-in-an-array/).
[^fmibst]:Leetcode-501 Find Mode in Binary Search Tree: [https://leetcode.com/problems/find-mode-in-binary-search-tree/description/](https://leetcode.com/problems/find-mode-in-binary-search-tree/description/).
[^fmibstSolution]:代码随想录-二叉搜索树中的众数: [https://programmercarl.com/0501.二叉搜索树中的众数.html](https://programmercarl.com/0501.二叉搜索树中的众数.html).
[^lcaoabt]:Leetcode-236 Lowest Common Ancestor of a Binary Tree: [https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/description/](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/description/).
[^rnnfeolSolution]:代码随想录-二叉树的最近公共祖先: [https://programmercarl.com/0236.二叉树的最近公共祖先.html](https://programmercarl.com/0236.二叉树的最近公共祖先.html).
[^lcaoabst]:Leetcode-235 Lowest Common Ancestor of a Binary Search Tree: [https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/description/](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/description/).

