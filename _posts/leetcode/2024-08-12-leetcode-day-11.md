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