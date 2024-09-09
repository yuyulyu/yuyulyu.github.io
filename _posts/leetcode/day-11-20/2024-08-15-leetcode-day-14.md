---
title: "Leetcode Day 14 - Binary Tree: Path and Construction Problems"
description: Focuses on finding specific nodes or values in binary trees, such as the bottom-left value and path sums. Also covers reconstructing binary trees from inorder and postorder traversal.
author: yoyo
date: 2024-08-15 16:27:00 +0800
categories: [Data Structure and Algorithm, Leetcode, Binary Tree]
tags: []
---

## Binary Tree 

> [Link to note about binary tree](https://yuyulyu.github.io/posts/binary-tree/)
{: .prompt-tip }


| Diff                                                                                                | Problem                                                                                 | Python | Java |
|-----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [513 Find Bottom Left Tree Value](#find-bottom-left-tree-value)                                 |✅      |      |
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                               | [112 Path Sum](#path-sum)                                                                      |✅      |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                              | [106 Construct Binary Tree from Inorder and Postorder Traversal](#construct-binary-tree-from-inorder-and-postorder-traversal)                                                                                                      |✅      |      |

## Find Bottom Left Tree Value

> [Link to Leetcode question](https://leetcode.com/problems/find-bottom-left-tree-value/description/)[^fbltv]
{: .prompt-info }

Given the `root` of a binary tree, return the leftmost value in the last row of the tree.

**Example 1**

![Desktop View](/assets/image/leetcode/leetcode-day-14/find-bottom-left-tree-value-example-1.jpeg)

```
Input: root = [2,1,3]
Output: 1
```

**Example 2**

![Desktop View](/assets/image/leetcode/leetcode-day-14/find-bottom-left-tree-value-example-2.jpeg)

```
Input: root = [1,2,3,4,null,5,6,null,null,7]
Output: 7
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0513.找树左下角的值.html)[^fbltvSolution].

#### Python

```python
class Solution(object):
    def findBottomLeftValue(self, root):
                
        def find(node):
            if node is None:
                return None, 0
            
            if node.left is None and node.right is None:
                return node.val, 1
            
            if node.left is not None:
                left, left_depth = find(node.left)
                left_depth += 1
            
                if node.right is None:
                    return left, left_depth
                else:
                    right, right_depth = find(node.right)
                    right_depth += 1
                    if right_depth > left_depth:
                        return right, right_depth
                    else:
                        return left, left_depth
            right, right_depth = find(node.right)
            return right, right_depth + 1
        
        re, temp = find(root)
        return re
```

## Path Sum

> [Link to Leetcode question](https://leetcode.com/problems/path-sum/description/)[^ps]
{: .prompt-info }

Given the `root` of a binary tree and an integer `targetSum`, return `true` if the tree has a root-to-leaf path such that adding up all the values along the path equals `targetSum`.

A leaf is a node with no children.

**Example 1**

![Desktop View](/assets/image/leetcode/leetcode-day-14/path-sum-example-1.jpeg)

```
Input: root = [5,4,8,11,null,13,4,7,2,null,null,null,1], targetSum = 22
Output: true
Explanation: The root-to-leaf path with the target sum is shown.
```

**Example 2**

![Desktop View](/assets/image/leetcode/leetcode-day-14/path-sum-example-2.jpeg)

```
Input: root = [1,2,3], targetSum = 5
Output: false
Explanation: There two root-to-leaf paths in the tree:
(1 --> 2): The sum is 3.
(1 --> 3): The sum is 4.
There is no root-to-leaf path with sum = 5.
```

**Example 3**

```
Input: root = [], targetSum = 0
Output: false
Explanation: Since the tree is empty, there are no root-to-leaf paths.
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0112.路径总和.html)[^psSolution].

#### Python

```python
class Solution(object):
    def hasPathSum(self, root, targetSum):

        def find(node,s):
            if node is None:
                return False
            
            if node.left is None and node.right is None and node.val == targetSum - s:
                return True
            
            s += node.val

            if node.left is not None:
                if find(node.left, s):
                    return True
            
            if node.right is not None:
                if find(node.right,s):
                    return True
            
            return False
    
        return find(root,0)
```

### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [113 Path Sum II](https://leetcode.com/problems/path-sum-ii/description/)[^psii] |        |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [437 Path Sum III](https://leetcode.com/problems/path-sum-iii/description/)[^psiii] |        |      |
| ![Hard](https://img.shields.io/badge/Hard-red)                                               | [124 Binary Tree Maximum Path Sum](https://leetcode.com/problems/binary-tree-maximum-path-sum/description/)[^btmps] |        |      |

## Construct Binary Tree from Inorder and Postorder Traversal

> [Link to Leetcode question](https://leetcode.com/problems/construct-binary-tree-from-inorder-and-postorder-traversal/description/)[^cbtfiapt]
{: .prompt-info }

Given two integer arrays `inorder` and `postorder` where `inorder` is the inorder traversal of a binary tree and `postorder` is the postorder traversal of the same tree, construct and return the binary tree.

**Example 1**

![Desktop View](/assets/image/leetcode/leetcode-day-14/construct-binary-tree-from-inorder-and-postorder-traversal-example-1.jpeg)

```
Input: inorder = [9,3,15,20,7], postorder = [9,15,7,20,3]
Output: [3,9,20,null,null,15,7]
```

**Example 2**

```
Input: inorder = [-1], postorder = [-1]
Output: [-1]
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0106.从中序与后序遍历序列构造二叉树.html)[^cbtfiaptSolution].

#### Python

```python
class Solution(object):
    def buildTree(self, inorder, postorder):

        def construct(inorder, postorder):
            if not inorder:
                return None

            mid = postorder.pop()
            i = inorder.index(mid)
            
            right_node = construct(inorder[i + 1:], postorder)
            left_node = construct(inorder[:i], postorder)

            return TreeNode(mid, left_node, right_node)
        
        return construct(inorder, postorder)
```

### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [105 Construct Binary Tree from Preorder and Inorder Traversal](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/)[^cbtfpait]               |        |      | 

## Reference
[^fbltv]:Leetcode-513 Find Bottom Left Tree Value: [https://leetcode.com/problems/find-bottom-left-tree-value/description/](https://leetcode.com/problems/find-bottom-left-tree-value/description/).
[^fbltvSolution]:代码随想录-找树左下角的值: [https://programmercarl.com/0513.找树左下角的值.html](https://programmercarl.com/0513.找树左下角的值.html).
[^ps]:Leetcode-112 Path Sum: [https://leetcode.com/problems/path-sum/description/](https://leetcode.com/problems/path-sum/description/).
[^psSolution]:代码随想录-路径总和: [https://programmercarl.com/0112.路径总和.html](https://programmercarl.com/0112.路径总和.html).
[^psii]: Leetcode-113 Path Sum II: [https://leetcode.com/problems/path-sum-ii/description/](https://leetcode.com/problems/path-sum-ii/description/).
[^psiii]: Leetcode-437 Path Sum III: [https://leetcode.com/problems/path-sum-iii/description/](https://leetcode.com/problems/path-sum-iii/description/).
[^btmps]: Leetcode-124 Binary Tree Maximum Path Sum: [https://leetcode.com/problems/binary-tree-maximum-path-sum/description/](https://leetcode.com/problems/binary-tree-maximum-path-sum/description/).
[^cbtfiapt]:Leetcode-106 Construct Binary Tree from Inorder and Postorder Traversal: [https://leetcode.com/problems/construct-binary-tree-from-inorder-and-postorder-traversal/description/](https://leetcode.com/problems/construct-binary-tree-from-inorder-and-postorder-traversal/description/).
[^cbtfiaptSolution]:代码随想录-从中序与后序遍历序列构造二叉树: [https://programmercarl.com/0106.从中序与后序遍历序列构造二叉树.html](https://programmercarl.com/0106.从中序与后序遍历序列构造二叉树.html).
[^cbtfpait]:Leetcode-105 Construct Binary Tree from Preorder and Inorder Traversal: [https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/).

