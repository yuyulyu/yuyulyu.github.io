---
title: Leetcode Day 10 - Stack & Queue
description: 150 Evaluate Reverse Polish Notation | 239 Sliding Window Maximum | 347 Top K Frequent Elements
author: yoyo
date: 2024-08-10 16:09:00 +0800
categories: [Datastructure and Algorithm, Leetcode]
tags: [stack, queue,sliding window]
---

## Stack & Queue 

| Diff                                                                                                | Problem                                                                                 | Python | Java |
|-----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [150 Evaluate Reverse Polish Notation](#evaluate-reverse-polish-notation)                                          |✅      |      |
| ![Hard](https://img.shields.io/badge/Hard-red)                                               | [239 Sliding Window Maximum](#sliding-window-maximum)                |✅      |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                              | [347 Top K Frequent Elements](#top-k-frequent-elements)               |        |      |

## Evaluate Reverse Polish Notation

> [Link to Leetcode question](https://leetcode.com/problems/evaluate-reverse-polish-notation/)[^erpn]
{: .prompt-info }

You are given an array of strings `tokens` that represents an arithmetic expression in a Reverse Polish Notation.

Evaluate the expression. Return an integer that represents the value of the expression.

**Note that**:
  - The valid operators are `'+'`, `'-'`, `'*'`, and `'/'`.
  - Each operand may be an integer or another expression.
  - The division between two integers always truncates toward zero.
  - There will not be any division by zero.
  - The input represents a valid arithmetic expression in a reverse polish notation.
  - The answer and all the intermediate calculations can be represented in a 32-bit integer. 

**Example 1**

```
Input: tokens = ["2","1","+","3","*"]
Output: 9
Explanation: ((2 + 1) * 3) = 9
```

**Example 2**

```
Input: tokens = ["4","13","5","/","+"]
Output: 6
Explanation: (4 + (13 / 5)) = 6
```

**Example 3**

```
Input: tokens = ["10","6","9","3","+","-11","*","/","*","17","+","5","+"]
Output: 22
Explanation: ((10 * (6 / ((9 + 3) * -11))) + 17) + 5
= ((10 * (6 / (12 * -11))) + 17) + 5
= ((10 * (6 / -132)) + 17) + 5
= ((10 * 0) + 17) + 5
= (0 + 17) + 5
= 17 + 5
= 22
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0150.逆波兰表达式求值.html)[^erpnSolution].

#### Python

**Solution 1**: Simply use stack

```python
class Solution(object):
    def evalRPN(self, tokens):
        def div(x, y):
            return int(x / y) if x * y > 0 else -(abs(x) // abs(y))


        stack = []

        for t in tokens:
            try:
                stack.append(int(t))
            except:
                t2 = stack.pop()
                t1 = stack.pop()
                if t == '+':
                    print(t1,'+',t2)
                    stack.append(t1 + t2)
                elif t == '-':
                    print(t1,'-',t2)
                    stack.append(t1 - t2)
                elif t == '*':
                    print(t1,'*',t2)
                    stack.append(t1 * t2)
                elif t == '/':
                    print(t1,'/',t2)
                    stack.append(div(t1,t2))
        
        return stack.pop()
```

**Solution 2**: Stack + operator

```python
from operator import add, sub, mul
class Solution(object):
    def evalRPN(self, tokens):
        def div(x, y):
            return int(x / y) if x * y > 0 else -(abs(x) // abs(y))


        stack = []

        op_map = {'+': add, '-': sub, '*': mul, '/': div}
    
        for token in tokens:
            if token not in {'+', '-', '*', '/'}:
                stack.append(int(token))
            else:
                op2 = stack.pop()
                op1 = stack.pop()
                stack.append(op_map[token](op1, op2))  
        return stack.pop()
```


### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Hard](https://img.shields.io/badge/Hard-red)                                                | [282 Expression Add Operators](https://leetcode.com/problems/expression-add-operators/description/)[^eao] |        |      |
| ![Hard](https://img.shields.io/badge/Hard-red)                                                       | [224 Basic Calculator](https://leetcode.com/problems/basic-calculator/)[^bc]          |        |      |


## Sliding Window Maximum

> [Link to Leetcode question](https://leetcode.com/problems/sliding-window-maximum/description/)[^swm]
{: .prompt-info }

You are given an array of integers `nums`, there is a sliding window of size `k` which is moving from the very left of the array to the very right. You can only see the `k` numbers in the window. Each time the sliding window moves right by one position.

Return the max sliding window.

**Example 1**

```
Input: nums = [1,3,-1,-3,5,3,6,7], k = 3
Output: [3,3,5,5,6,7]
Explanation: 
Window position                Max
---------------               -----
[1  3  -1] -3  5  3  6  7       3
 1 [3  -1  -3] 5  3  6  7       3
 1  3 [-1  -3  5] 3  6  7       5
 1  3  -1 [-3  5  3] 6  7       5
 1  3  -1  -3 [5  3  6] 7       6
 1  3  -1  -3  5 [3  6  7]      7
```

**Example 2**

```
Input: nums = [1], k = 1
Output: [1]
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0239.滑动窗口最大值.html)[^swmSolution].

解释后补

#### Python

```python
from collections import deque

class Solution(object):
    def maxSlidingWindow(self, nums, k):
        que = deque()
        que.append(nums[0])

        for i in range(1,k):
            while len(que) != 0 and que[len(que) - 1]< nums[i]:
                que.pop()
            que.append(nums[i])
        
        record = [que[0]]
        
        for i in range(len(nums) - k):
            if nums[i] == que[0]:
                que.popleft()
            while len(que) != 0 and que[len(que) - 1]< nums[i + k]:
                que.pop()
            que.append(nums[i + k])
            record.append(que[0])

        return record
```


### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [155 Min Stack](https://leetcode.com/problems/min-stack/)[^ms] |        |      |
| ![Hard](https://img.shields.io/badge/Hard-red)                                                | [76 Minimum Window Substring](https://leetcode.com/problems/minimum-window-substring/description/)[^mws] |        |      |

## Top K Frequent Elements

> [Link to Leetcode question](https://leetcode.com/problems/top-k-frequent-elements/description/)[^tkfe].
{: .prompt-info }

Given an integer array `nums` and an integer `k`, return the `k` most frequent elements. You may return the answer in any order.

**Example 1**

```
Input: nums = [1,1,1,2,2,3], k = 2
Output: [1,2]
```

**Example 2**

```
Input: nums = [1], k = 1
Output: [1]
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0347.前K个高频元素.html)[^tkfeSolution].



### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [192 Word Frequency](https://leetcode.com/problems/word-frequency/description/)[^wf] |        |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [215 Kth Largest Element in an Array](https://leetcode.com/problems/kth-largest-element-in-an-array/description/)[^kleiaa] |        |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [659 Split Array into Consecutive Subsequences](https://leetcode.com/problems/split-array-into-consecutive-subsequences/)[^saics] |        |      |



## Reference
[^erpn]:Leetcode-150 Evaluate Reverse Polish Notation: [https://leetcode.com/problems/evaluate-reverse-polish-notation/](https://leetcode.com/problems/evaluate-reverse-polish-notation/).
[^erpnSolution]:代码随想录-逆波兰表达式求值: [https://programmercarl.com/0150.逆波兰表达式求值.html](https://programmercarl.com/0150.逆波兰表达式求值.html).
[^eao]: Leetcode-282 Expression Add Operators: [https://leetcode.com/problems/expression-add-operators/description/](https://leetcode.com/problems/expression-add-operators/description/).
[^bc]: Leetcode-224 Basic Calculator: [https://leetcode.com/problems/basic-calculator/](https://leetcode.com/problems/basic-calculator/).
[^swm]:Leetcode-239 Sliding Window Maximum: [https://leetcode.com/problems/sliding-window-maximum/description/](https://leetcode.com/problems/sliding-window-maximum/description/).
[^swmSolution]:代码随想录-滑动窗口最大值: [https://programmercarl.com/0239.滑动窗口最大值.html](https://programmercarl.com/0239.滑动窗口最大值.html).
[^ms]: Leetcode-155 Min Stack: [https://leetcode.com/problems/min-stack/](https://leetcode.com/problems/min-stack/).
[^mws]: Leetcode-76 Minimum Window Substring: [https://leetcode.com/problems/minimum-window-substring/description/](https://leetcode.com/problems/minimum-window-substring/description/).
[^tkfe]:Leetcode-347 Top K Frequent Elements: [https://leetcode.com/problems/top-k-frequent-elements/description/](https://leetcode.com/problems/top-k-frequent-elements/description/).
[^tkfeSolution]:代码随想录-前K个高频元素: [https://programmercarl.com/0347.前K个高频元素.html](https://programmercarl.com/0347.前K个高频元素.html).
[^wf]: Leetcode-192 Word Frequency: [https://leetcode.com/problems/word-frequency/description/](https://leetcode.com/problems/word-frequency/description/).
[^kleiaa]: Leetcode-215 Kth Largest Element in an Array: [https://leetcode.com/problems/kth-largest-element-in-an-array/description/](https://leetcode.com/problems/kth-largest-element-in-an-array/description/).
[^saics]: Leetcode-659 Split Array into Consecutive Subsequences: [https://leetcode.com/problems/split-array-into-consecutive-subsequences/](https://leetcode.com/problems/split-array-into-consecutive-subsequences/).

