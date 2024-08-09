---
title: Leetcode Day 9 - Stack & Queue
description: 232 Implement Queue using Stacks | 225 Implement Stack using Queues | 20 Valid Parentheses | 1047 Remove All Adjacent Duplicates In String
author: yoyo
date: 2024-08-09 13:50:00 +0800
categories: [Data Structure and Algorithm, Leetcode]
tags: [stack, queue]
---

## Stack & Queue

| Diff                                                                                                | Problem                                                                                 | Python | Java |
|-----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|--------|------|
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                               | [232 Implement Queue using Stacks](#implement-queue-using-stacks)                                          |        |      |
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                               | [225 Implement Stack using Queues](#implement-stack-using-queues)                |        |      |
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                              | [20 Valid Parentheses](#valid-parentheses)               |        |      |
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                               | [1047 Remove All Adjacent Duplicates In String](#remove-all-adjacent-duplicates-in-string)                                       |        |      |

## Implement Queue using Stacks

> [Link to Leetcode question](https://leetcode.com/problems/implement-queue-using-stacks/description/)[^iqus]
{: .prompt-info }

Implement a **first in first out (FIFO)** queue using only two stacks. The implemented queue should support all the functions of a normal queue (`push`, `peek`, `pop`, and `empty`).

Implement the `MyQueue` class:

  - `void push(int x)` Pushes element `x` to the back of the queue.
  - `int pop()` Removes the element from the front of the queue and returns it.
  - `int peek()` Returns the element at the front of the queue.
  - `boolean empty()` Returns `true` if the queue is empty, `false` otherwise.

**Notes:**

  - You must use only standard operations of a stack, which means only `push to top`, `peek/pop from top`, `size`, and `is empty` operations are valid.
  - Depending on your language, the stack may not be supported natively. You may simulate a stack using a list or deque (double-ended queue) as long as you use only a stack's standard operations.
 
**Example 1**

```
Input
["MyQueue", "push", "push", "peek", "pop", "empty"]
[[], [1], [2], [], [], []]
Output
[null, null, null, 1, 1, false]

Explanation
MyQueue myQueue = new MyQueue();
myQueue.push(1); // queue is: [1]
myQueue.push(2); // queue is: [1, 2] (leftmost is front of the queue)
myQueue.peek(); // return 1
myQueue.pop(); // return 1, queue is [2]
myQueue.empty(); // return false
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0232.用栈实现队列.html)[^iqusSolution].


## Implement Stack using Queues

> [Link to Leetcode question](https://leetcode.com/problems/implement-stack-using-queues/)[^isuq]
{: .prompt-info }

Implement a **last-in-first-out (LIFO)** stack using only two queues. The implemented stack should support all the functions of a normal stack (`push`, `top`, `pop`, and `empty`).

Implement the `MyStack` class:

  - `void push(int x)` Pushes element `x` to the top of the stack.
  - `int pop()` Removes the element on the top of the stack and returns it.
  - `int top()` Returns the element on the top of the stack.
  - `boolean empty()` Returns `true` if the stack is empty, `false` otherwise.

**Notes:**

  - You must use only standard operations of a queue, which means that only `push to back`, `peek/pop from front`, `size` and `is empty` operations are valid.
  - Depending on your language, the queue may not be supported natively. You may simulate a queue using a list or deque (double-ended queue) as long as you use only a queue's standard operations.

**Example 1**

```
Input
["MyStack", "push", "push", "top", "pop", "empty"]
[[], [1], [2], [], [], []]
Output
[null, null, null, 2, 2, false]

Explanation
MyStack myStack = new MyStack();
myStack.push(1);
myStack.push(2);
myStack.top(); // return 2
myStack.pop(); // return 2
myStack.empty(); // return False
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0225.用队列实现栈.html)[^isuqSolution].



## Valid Parentheses

> [Link to Leetcode question](https://leetcode.com/problems/valid-parentheses/description/)[^vp]
{: .prompt-info }

Given a string `s` containing just the characters `'('`,` ')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.

An input string is valid if:

  1. Open brackets must be closed by the same type of brackets.
  2. Open brackets must be closed in the correct order.
  3. Every close bracket has a corresponding open bracket of the same type.
 
**Example 1**

```
Input: s = "()"
Output: true
```

**Example 2**

```
Input: s = "()[]{}"
Output: true
```

**Example 3**

```
Input: s = "(]"
Output: false
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0020.有效的括号.html)[^vpSolution].


### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [22 Generate Parentheses](https://leetcode.com/problems/generate-parentheses/description/)[^gp] |        |      |
| ![Hard](https://img.shields.io/badge/Hard-red)                                                | [32 Longest Valid Parentheses](https://leetcode.com/problems/longest-valid-parentheses/description/)[^lvp] |        |      |
| ![Hard](https://img.shields.io/badge/Hard-red)                                               | [301 Remove Invalid Parentheses](https://leetcode.com/problems/remove-invalid-parentheses/)[^rip] |        |      |

## Remove All Adjacent Duplicates In String

> [Link to Leetcode question](https://leetcode.com/problems/remove-all-adjacent-duplicates-in-string/description/)[^raadis]
{: .prompt-info }

You are given a string `s` consisting of lowercase English letters. A duplicate removal consists of choosing two adjacent and equal letters and removing them.

We repeatedly make **duplicate removals** on `s` until we no longer can.

Return the final string after all such duplicate removals have been made. It can be proven that the answer is unique. 

**Example 1**

```
Input: s = "abbaca"
Output: "ca"
Explanation: 
For example, in "abbaca" we could remove "bb" since the letters are adjacent and equal, and this is the only possible move.  The result of this move is that the string is "aaca", of which only "aa" is possible, so the final string is "ca".
```

**Example 2**

```
Input: s = "azxxzy"
Output: "ay"
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/1047.删除字符串中的所有相邻重复项.html)[^raadisSolution].




### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [1209 Remove All Adjacent Duplicates in String II](https://leetcode.com/problems/remove-all-adjacent-duplicates-in-string-ii/description/)[^raadisii] |        |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [2390 Removing Stars From a String](https://leetcode.com/problems/removing-stars-from-a-string/)[^rsfas] |        |      |



## Reference

[^iqus]:Leetcode-232 Implement Queue using Stacks: [https://leetcode.com/problems/implement-queue-using-stacks/description/](https://leetcode.com/problems/implement-queue-using-stacks/description/).
[^iqusSolution]:代码随想录-用栈实现队列: [https://programmercarl.com/0232.用栈实现队列.html](https://programmercarl.com/0232.用栈实现队列.html).
[^isuq]: Leetcode-225 Implement Stack using Queues: [https://leetcode.com/problems/implement-stack-using-queues/](https://leetcode.com/problems/implement-stack-using-queues/).
[^isuqSolution]: 代码随想录-用队列实现栈: [https://programmercarl.com/0225.用队列实现栈.html](https://programmercarl.com/0225.用队列实现栈.html).
[^vp]:Leetcode-20 Valid Parentheses: [https://leetcode.com/problems/valid-parentheses/description/](https://leetcode.com/problems/valid-parentheses/description/).
[^vpSolution]:代码随想录-有效的括号: [https://programmercarl.com/0020.有效的括号.html](https://programmercarl.com/0020.有效的括号.html).
[^gp]: Leetcode-22 Generate Parentheses: [https://leetcode.com/problems/generate-parentheses/description/](https://leetcode.com/problems/generate-parentheses/description/).
[^lvp]: Leetcode-32 Longest Valid Parentheses: [https://leetcode.com/problems/longest-valid-parentheses/description/](https://leetcode.com/problems/longest-valid-parentheses/description/).
[^rip]: Leetcode-301 Remove Invalid Parentheses: [https://leetcode.com/problems/remove-invalid-parentheses/](https://leetcode.com/problems/remove-invalid-parentheses/).
[^raadis]:Leetcode-1047 Remove All Adjacent Duplicates In String: [https://leetcode.com/problems/remove-all-adjacent-duplicates-in-string/description/](https://leetcode.com/problems/remove-all-adjacent-duplicates-in-string/description/).
[^raadisSolution]:代码随想录-删除字符串中的所有相邻重复项: [https://programmercarl.com/1047.删除字符串中的所有相邻重复项.html](https://programmercarl.com/1047.删除字符串中的所有相邻重复项.html).
[^raadisii]: Leetcode-1209 Remove All Adjacent Duplicates in String II: [https://leetcode.com/problems/remove-all-adjacent-duplicates-in-string-ii/description/](https://leetcode.com/problems/remove-all-adjacent-duplicates-in-string-ii/description/).
[^rsfas]: Leetcode-2390 Removing Stars From a String: [https://leetcode.com/problems/removing-stars-from-a-string/](https://leetcode.com/problems/removing-stars-from-a-string/).

