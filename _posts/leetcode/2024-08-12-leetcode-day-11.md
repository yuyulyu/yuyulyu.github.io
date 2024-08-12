---
title: Leetcode Day 11 - Binary Tree
description: 102 Binary Tree Level Order Traversal I & II | 199 Binary Tree Right Side View | 637 Average of Levels in Binary Tree | 429 N-ary Tree Level Order Traversal ...
author: yoyo
date: 2024-08-12 14:12:00 +0800
categories: [Data Structure and Algorithm, Leetcode]
tags: [binary tree]
---

## Binary Tree 

> [Link to note about binary tree](https://yuyulyu.github.io/posts/binary-tree/)
{: .prompt-tip }

| Diff                                                                                                | Problem                                                                                 | Python | Java |
|-----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [102 Binary Tree Level Order Traversal](#binary-tree-level-order-traversal)                                          |        |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [107 Binary Tree Level Order Traversal II](#binary-tree-level-order-traversal-ii)                |        |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                              | [199 Binary Tree Right Side View](#binary-tree-right-side-view)               |        |      |

## Binary Tree Level Order Traversal

> [Link to Leetcode question](https://leetcode.com/problems/binary-tree-level-order-traversal/description/)[^btlot]
{: .prompt-info }

Given the `root` of a binary tree, return the level order traversal of its nodes' values. (i.e., from left to right, level by level).

**Example 1**

![Desktop View](/assets/image/leetcode/leetcode-day-11/binary-tree-level-order-traversal-example-1.jpeg){: .normal }

```
Input: root = [3,9,20,null,null,15,7]
Output: [[3],[9,20],[15,7]]
```

**Example 2**

```
Input: root = [1]
Output: [[1]]
```

**Example 3**

```
Input: root = []
Output: []
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0102.二叉树的层序遍历.html#_102-二叉树的层序遍历)[^solution].

## Binary Tree Level Order Traversal II

> [Link to Leetcode question](https://leetcode.com/problems/binary-tree-level-order-traversal-ii/description/)[^btlotii]
{: .prompt-info }

Given the `root` of a binary tree, return the bottom-up level order traversal of its nodes' values. (i.e., from left to right, level by level from leaf to root).

**Example 1**

![Desktop View](/assets/image/leetcode/leetcode-day-11/binary-tree-level-order-traversal-example-1.jpeg){: .normal }

```
Input: root = [3,9,20,null,null,15,7]
Output: [[15,7],[9,20],[3]]
```

**Example 2**

```
Input: root = [1]
Output: [[1]]
```

**Example 3**

```
Input: root = []
Output: []
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0102.二叉树的层序遍历.html#_107-二叉树的层次遍历-ii)[^solution].

## Binary Tree Right Side View

> [Link to Leetcode question](https://leetcode.com/problems/binary-tree-right-side-view/description/)[^btrsv]
{: .prompt-info }

Given the `root` of a binary tree, imagine yourself standing on the right side of it, return the values of the nodes you can see ordered from top to bottom.

**Example 1**

<image>

```
Input: root = [1,2,3,null,5,null,4]
Output: [1,3,4]
```

**Example 2**

```
Input: root = [1,null,3]
Output: [1,3]
```

**Example 3**

```
Input: root = []
Output: []
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0102.二叉树的层序遍历.html#_199-二叉树的右视图)[^solution].




