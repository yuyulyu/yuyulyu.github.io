---
title: Leetcode Day 11 - Binary Tree
description: 102 Binary Tree Level Order Traversal I & II | 199 Binary Tree Right Side View | 637 Average of Levels in Binary Tree | 429 N-ary Tree Level Order Traversal ...
author: yoyo
date: 2024-08-12 14:12:00 +0800
categories: [Data Structure and Algorithm, Leetcode]
tags: [binary tree]
---

![Easy](https://img.shields.io/badge/Easy-brightgreen) 
![Medium](https://img.shields.io/badge/Medium-yellow)
![Hard](https://img.shields.io/badge/Hard-red)

## Binary Tree 

> [Link to note about binary tree](https://yuyulyu.github.io/posts/binary-tree/)
{: .prompt-tip }

| Diff                                                                                                | Problem                                                                                 | Python | Java |
|-----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [102 Binary Tree Level Order Traversal](#binary-tree-level-order-traversal)                                          |        |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [107 Binary Tree Level Order Traversal II](#binary-tree-level-order-traversal-ii)                |        |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                              | [199 Binary Tree Right Side View](#binary-tree-right-side-view])               |        |      |
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                                | [637 Average of Levels in Binary Tree](#average-of-levels-in-binary-tree)                                       |        |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [429 N-ary Tree Level Order Traversal](#n-ary-tree-level-order-traversal)                                       |        |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [515 Find Largest Value in Each Tree Row](#find-largest-value-in-each-tree-row)                                       |        |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [116 Populating Next Right Pointers in Each Node](#populating-next-right-pointers-in-each-node)                                       |        |      |

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



## 107 Binary Tree Level Order Traversal II

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


## Average of Levels in Binary Tree

> [Link to Leetcode question](https://leetcode.com/problems/average-of-levels-in-binary-tree/description/)[^aolib]
{: .prompt-info }

Given the `root` of a binary tree, return the average value of the nodes on each level in the form of an array. Answers within `10<sup>-5</sup>` of the actual answer will be accepted.

**Example 1**

![Desktop View](/assets/image/leetcode/leetcode-day-11/average-of-levels-in-binary-tree-example-2.jpeg){: .normal }

```
Input: root = [3,9,20,null,null,15,7]
Output: [3.00000,14.50000,11.00000]
Explanation: The average value of nodes on level 0 is 3, on level 1 is 14.5, and on level 2 is 11.
Hence return [3, 14.5, 11].
```

**Example 2**

![Desktop View](/assets/image/leetcode/leetcode-day-11/binary-tree-level-order-traversal-example-1.jpeg){: .normal }

```
Input: root = [3,9,20,15,7]
Output: [3.00000,14.50000,11.00000]
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0102.二叉树的层序遍历.html#_637-二叉树的层平均值)[^solution].

## N-ary Tree Level Order Traversal

> [Link to Leetcode question](https://leetcode.com/problems/n-ary-tree-level-order-traversal/description/)[^natlot]
{: .prompt-info }

Given an n-ary tree, return the level order traversal of its nodes' values.

Nary-Tree input serialization is represented in their level order traversal, each group of children is separated by the null value (See examples).

**Example 1**

![Desktop View](/assets/image/leetcode/leetcode-day-11/n-ary-tree-level-order-traversal-example-1.png){: .normal }

```
Input: root = [1,null,3,2,4,null,5,6]
Output: [[1],[3,2,4],[5,6]]
```

**Example 2**

![Desktop View](/assets/image/leetcode/leetcode-day-11/n-ary-tree-level-order-traversal-example-2.png){: .normal }

```
Input: root = [1,null,2,3,4,5,null,null,6,7,null,8,null,9,10,null,null,11,null,12,null,13,null,null,14]
Output: [[1],[2,3,4,5],[6,7,8,9,10],[11,12,13],[14]]
```
 

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0102.二叉树的层序遍历.html#_429-n叉树的层序遍历)[^solution].

## Find Largest Value in Each Tree Row

> [Link to Leetcode question](https://leetcode.com/problems/find-largest-value-in-each-tree-row/description/)[^flvietr]
{: .prompt-info }

**Example 1**

![Desktop View](/assets/image/leetcode/leetcode-day-11/find-largest-value-in-each-tree-row-example-1.jpeg){: .normal }

```
Input: root = [1,3,2,5,3,null,9]
Output: [1,3,9]
```

**Example 2**

```
Input: root = [1,2,3]
Output: [1,3]
```


### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0102.二叉树的层序遍历.html#_515-在每个树行中找最大值)[^solution].

## Populating Next Right Pointers in Each Node

> [Link to Leetcode question](https://leetcode.com/problems/populating-next-right-pointers-in-each-node/description/)[^pnrpien]
{: .prompt-info }

You are given a perfect binary tree where all leaves are on the same level, and every parent has two children. The binary tree has the following definition:

```
struct Node {
  int val;
  Node *left;
  Node *right;
  Node *next;
}
```

Populate each next pointer to point to its next right node. If there is no next right node, the next pointer should be set to `NULL`.

Initially, all next pointers are set to `NULL`.

**Example 1**

![Desktop View](/assets/image/leetcode/populating-next-right-pointers-in-each-node-example-1.png){: .normal }

```
Input: root = [1,2,3,4,5,6,7]
Output: [1,#,2,3,#,4,5,6,7,#]
Explanation: Given the above perfect binary tree (Figure A), your function should populate each next pointer to point to its next right node, just like in Figure B. The serialized output is in level order as connected by the next pointers, with '#' signifying the end of each level.
```

**Example 2**

```
Input: root = []
Output: []
```


### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0151.翻转字符串里的单词.html)[^rhsSolution].


## <2nd problem>

> [Link to Leetcode question](https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/)[^rnnfeol]
{: .prompt-info }


### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0151.翻转字符串里的单词.html)[^rhsSolution].


## <2nd problem>

> [Link to Leetcode question](https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/)[^rnnfeol]
{: .prompt-info }


### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0151.翻转字符串里的单词.html)[^rhsSolution].


## <2nd problem>

> [Link to Leetcode question](https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/)[^rnnfeol]
{: .prompt-info }


### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0151.翻转字符串里的单词.html)[^rhsSolution].



### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [2095 Delete the Middle Node of a Linked List](https://leetcode.com/problems/delete-the-middle-node-of-a-linked-list/)[^dtmnoall] |        |      |



## Reference
[^btlot]:Leetcode-102 Binary Tree Level Order Traversal: [https://leetcode.com/problems/binary-tree-level-order-traversal/description/](https://leetcode.com/problems/binary-tree-level-order-traversal/description/).
[^btlotii]:Leetcode-107 Binary Tree Level Order Traversal II: [https://leetcode.com/problems/binary-tree-level-order-traversal-ii/description/](https://leetcode.com/problems/binary-tree-level-order-traversal-ii/description/).
[^solution]: 代码随想录-二叉树的层序遍历 II: [https://programmercarl.com/0102.二叉树的层序遍历.html](https://programmercarl.com/0102.二叉树的层序遍历.html).
[^btrsv]:Leetcode-199 Binary Tree Right Side View: [https://leetcode.com/problems/binary-tree-right-side-view/description/](https://leetcode.com/problems/binary-tree-right-side-view/description/).
[^aolib]:Leetcode-637 Average of Levels in Binary Tree: [https://leetcode.com/problems/average-of-levels-in-binary-tree/description/](https://leetcode.com/problems/average-of-levels-in-binary-tree/description/).
[^natlot]:Leetcode-429 N-ary Tree Level Order Traversal: [https://leetcode.com/problems/n-ary-tree-level-order-traversal/description/](https://leetcode.com/problems/n-ary-tree-level-order-traversal/description/).
[^flvietr]:Leetcode-515 Find Largest Value in Each Tree Row: [https://leetcode.com/problems/find-largest-value-in-each-tree-row/description/](https://leetcode.com/problems/find-largest-value-in-each-tree-row/description/).
[^pnrpien]:Leetcode-116 Populating Next Right Pointers in Each Node: [https://leetcode.com/problems/populating-next-right-pointers-in-each-node/description/](https://leetcode.com/problems/populating-next-right-pointers-in-each-node/description/).

