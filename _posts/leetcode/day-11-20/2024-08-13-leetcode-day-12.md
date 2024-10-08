---
title: "Leetcode Day 12 - Binary Tree: Tree Structure and Depth"
description: Involves manipulating binary tree structures, such as inverting a binary tree and determining symmetry. Also covers finding the maximum and minimum depth of a tree.
author: yoyo
date: 2024-08-13 14:58:00 +0800
categories: [Data Structure and Algorithm, Leetcode, Binary Tree]
tags: [binary tree, DFS, BFS]
---

## Binary Tree 

> [Link to note about binary tree](https://yuyulyu.github.io/posts/binary-tree/)
{: .prompt-tip }


| Diff                                                                                                | Problem                                                                                 | Python | Java |
|-----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|--------|------|
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                               | [226 Invert Binary Tree](#invert-binary-tree)                                          |✅      |      |
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                               | [101 Symmetric Tree](#symmetric-tree)                                              |✅      |      |
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                                | [104 Maximum Depth of Binary Tree](#maximum-depth-of-binary-tree)                    |✅      |      |
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                                | [111 Minimum Depth of Binary Tree](#minimum-depth-of-binary-tree)                    |✅      |      |


## Invert Binary Tree

> [Link to Leetcode question](https://leetcode.com/problems/invert-binary-tree/description/)[^ibt]
{: .prompt-info }

Given the `root` of a binary tree, invert the tree, and return its root.

![Desktop View](/assets/image/leetcode/leetcode-day-12/invert-binary-tree-example-1.jpeg)

```
Input: root = [4,2,7,1,3,6,9]
Output: [4,7,2,9,6,3,1]
```

**Example 2**

![Desktop View](/assets/image/leetcode/leetcode-day-12/invert-binary-tree-example-2.jpeg)

```
Input: root = [2,1,3]
Output: [2,3,1]
```

**Example 3**

```
Input: root = []
Output: []
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0226.翻转二叉树.html)[^ibtSolution].

### Python

```python
class Solution(object):
    def invertTree(self, root):
        if root is None:
            return
        
        temp = root.left
        root.left = root.right
        root.right = temp

        self.invertTree(root.left)
        self.invertTree(root.right)

        return root
```

### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [2415 Reverse Odd Levels of Binary Tree](https://leetcode.com/problems/reverse-odd-levels-of-binary-tree/)[^rolobt] |✅      |      |

## Symmetric Tree

> [Link to Leetcode question](https://leetcode.com/problems/symmetric-tree/description/)[^rnnfeol]
{: .prompt-info }

Given the `root` of a binary tree, check whether it is a mirror of itself (i.e., symmetric around its center).

**Example 1**

![Desktop View](/assets/image/leetcode/leetcode-day-12/symmetric-tree-example-1.jpeg)

```
Input: root = [1,2,2,3,4,4,3]
Output: true
```

**Example 2**

![Desktop View](/assets/image/leetcode/leetcode-day-12/symmetric-tree-example-2.jpeg)

```
Input: root = [1,2,2,null,3,null,3]
Output: false
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0101.对称二叉树.html#算法公开课)[^stSolution].

#### Python

```python
class Solution(object):
    def isSymmetric(self, root):
        """
        :type root: TreeNode
        :rtype: bool
        """
        
        def compare(left, right):
            if left is None and right is None:
                return True
            elif left is None and right is not None:
                return False
            elif right is None and left is not None:
                return False
            elif left.val != right.val:
                return False
            
            outside = compare(left.left, right.right)
            inside = compare(left.right, right.left)
            return outside and inside
        
        return compare(root.left, root.right)
```

## Maximum Depth of Binary Tree

> [Link to Leetcode question](https://leetcode.com/problems/maximum-depth-of-binary-tree/description/)[^mdobt]
{: .prompt-info }

**Example 1**

![Desktop View](/assets/image/leetcode/leetcode-day-11/maximum-depth-of-binary-tree-example-1.jpeg)

```
Input: root = [3,9,20,null,null,15,7]
Output: 3
```

**Example 2**

```
Input: root = [1,null,2]
Output: 2
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0102.二叉树的层序遍历.html#_104-二叉树的最大深度)[^solution].

#### Python

```python
class Solution(object):
    def maxDepth(self, root):
        def depth_of(node, depth):
            if node is None:
                return depth
            
            return 1 + max(depth_of(node.left, depth), depth_of(node.right, depth))
        
        return depth_of(root, 0)
```

## Minimum Depth of Binary Tree

> [Link to Leetcode question](https://leetcode.com/problems/minimum-depth-of-binary-tree/description/)[^minidepth]
{: .prompt-info }

Given a binary tree, find its minimum depth.

The minimum depth is the number of nodes along the shortest path from the root node down to the nearest leaf node.

**Note**: A leaf is a node with no children.

**Example 1**

![Desktop View](/assets/image/leetcode/leetcode-day-11/maximum-depth-of-binary-tree-example-1.jpeg)

```
Input: root = [3,9,20,null,null,15,7]
Output: 2
```

**Example 2**

```
Input: root = [2,null,3,null,4,null,5,null,6]
Output: 5
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0102.二叉树的层序遍历.html#_111-二叉树的最小深度)[^solution].

#### Python

```python
class Solution(object):
    def minDepth(self, root):
        if root is None:
                return 0
        depth = 1
        if root.left is not None and root.right is not None:
            depth += min(self.minDepth(root.left), self.minDepth(root.right))
        elif root.left is not None:
            depth += self.minDepth(root.left)
        elif root.right is not None:
            depth += self.minDepth(root.right)

        return depth
```

## Reference
[^ibt]:Leetcode-226 Invert Binary Tree: [https://leetcode.com/problems/invert-binary-tree/description/](https://leetcode.com/problems/invert-binary-tree/description/).
[^rolobt]:Leetcode-2415 Reverse Odd Levels of Binary Tree: [https://leetcode.com/problems/reverse-odd-levels-of-binary-tree/](https://leetcode.com/problems/reverse-odd-levels-of-binary-tree/).
[^ibtSolution]:代码随想录-翻转二叉树: [https://programmercarl.com/0226.翻转二叉树.html](https://programmercarl.com/0226.翻转二叉树.html).
[^st]:Leetcode-101 Symmetric Tree: [https://leetcode.com/problems/symmetric-tree/description/](https://leetcode.com/problems/symmetric-tree/description/).
[^stSolution]:代码随想录-对称二叉树: [https://programmercarl.com/0101.对称二叉树.html#算法公开课](https://programmercarl.com/0101.对称二叉树.html#算法公开课).
[^mdobt]:Leetcode-104 Maximum Depth of Binary Tree: [https://leetcode.com/problems/maximum-depth-of-binary-tree/description/](https://leetcode.com/problems/maximum-depth-of-binary-tree/description/).
[^mdobt]:Leetcode-104 Maximum Depth of Binary Tree: [https://leetcode.com/problems/maximum-depth-of-binary-tree/description/](https://leetcode.com/problems/maximum-depth-of-binary-tree/description/).
[^minidepth]:Leetcode-111 Minimum Depth of Binary Tree: [https://leetcode.com/problems/minimum-depth-of-binary-tree/description/](https://leetcode.com/problems/minimum-depth-of-binary-tree/description/).
[^solution]: 代码随想录-二叉树的层序遍历 II: [https://programmercarl.com/0102.二叉树的层序遍历.html](https://programmercarl.com/0102.二叉树的层序遍历.html).


