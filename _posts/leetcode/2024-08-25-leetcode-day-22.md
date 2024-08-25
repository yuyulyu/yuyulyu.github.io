---
title: Leetcode Day 22 - Backtracking Algorithm
description: 491 Non-decreasing Subsequences | 46 Permutations | 47 Permutations II | 332 Reconstruct Itinerary | 51 N-Queens | 37 Sudoku Solver

author: yoyo
date: 2024-08-25 13:50:00 +0800
categories: [Data Structure and Algorithm, Leetcode]
tags: [backtracking]
---

## Backtracking Algorithm 

| Diff                                                                                                | Problem                                                                                 | Python | Java |
|-----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [491 Non-decreasing Subsequences](#non-decreasing-subsequences)                     |✅      |        |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [46 Permutations](#permutations)                                                 |✅      |        |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                           | [47 Permutations II](#permutations-ii)                                              |✅      |        |
| ![Hard](https://img.shields.io/badge/Hard-red)                                               | [332 Reconstruct Itinerary](#reconstruct-itinerary)                                        |        |        |
| ![Hard](https://img.shields.io/badge/Hard-red)                                               | [51 N-Queens](#n-queens)                                                                           |        |        |
| ![Hard](https://img.shields.io/badge/Hard-red)                                               | [37 Sudoku Solver](#sudoku-solver)                                                                 |        |        |

## Non-decreasing Subsequences

> [Link to Leetcode question](https://leetcode.com/problems/non-decreasing-subsequences/description/)[^nds]
{: .prompt-info }

Given an integer array `nums`, return all the different possible non-decreasing subsequences of the given array with at least two elements. You may return the answer in any order.

**Example 1**

```
Input: nums = [4,6,7,7]
Output: [[4,6],[4,6,7],[4,6,7,7],[4,7],[4,7,7],[6,7],[6,7,7],[7,7]]
```

**Example 2**

```
Input: nums = [4,4,3,2,1]
Output: [[4,4]]
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0491.递增子序列.html)[^ndsSolution].

#### Python

```python
class Solution(object):
    def findSubsequences(self, nums):
        result = set()

        def backtracking(index, group):
            if len(group) > 1:
                result.add(tuple(group))
            
            for i in range(index, len(nums)):
                if len(group) > 0 and nums[i] < group[-1]:
                    continue
                group.append(nums[i])
                backtracking(i + 1, group)
                group.pop()
        
        backtracking(0,[])
        return result
```

### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [646 Maximum Length of Pair Chain](https://leetcode.com/problems/maximum-length-of-pair-chain/)[^mlopc] |        |      |



## Permutations

> [Link to Leetcode question](https://leetcode.com/problems/permutations/description/)[^permu]
{: .prompt-info }

Given an array `nums` of distinct integers, return all the possible permutations. You can return the answer in any order.

**Example 1**

```
Input: nums = [1,2,3]
Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]
```

**Example 2**

```
Input: nums = [0,1]
Output: [[0,1],[1,0]]
```

**Example 3**

```
Input: nums = [1]
Output: [[1]]
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0046.全排列.html)[^permuSolution].

#### Python

```python
class Solution(object):
    def permute(self, nums):
        result = []

        def backtracking(permu,nums):
            if len(nums) == 1:
                permu.append(nums[0])
                result.append(permu[:])
                permu.pop()
                return
            
            remain = nums[:]
            for num in nums:
                remain.remove(num)
                permu.append(num)
                backtracking(permu, remain)
                remain.append(num)
                permu.pop()
        
        backtracking([],nums)
        return result
```


## Permutations II

> [Link to Leetcode question](https://leetcode.com/problems/permutations-ii/description/)[^pii]
{: .prompt-info }

Given a collection of numbers, `nums`, that might contain duplicates, return all possible unique permutations in any order.

**Example 1**

```
Input: nums = [1,1,2]
Output:
[[1,1,2],
 [1,2,1],
 [2,1,1]]
```

**Example 2**

```
Input: nums = [1,2,3]
Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0047.全排列II.html)[^piiSolution].

#### Python

```python
class Solution(object):
    def permuteUnique(self, nums):
        result = []
        nums.sort()

        def backtracking(permu,nums):
            if len(nums) == 1:
                permu.append(nums[0])
                result.append(permu[:])
                permu.pop()
                return
            
            for i in range(len(nums)):
                if i > 0 and nums[i] == nums[i - 1]:
                    continue
                permu.append(nums[i])
                backtracking(permu, nums[:i] + nums[i + 1:])
                permu.pop()
        
        backtracking([],nums)
        return result
```

### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [31 Next Permutation](https://leetcode.com/problems/delete-the-middle-node-of-a-linked-list/)[^np] |        |      |
| ![Hard](https://img.shields.io/badge/Hard-red)                                                | [60 Permutation Sequence](https://leetcode.com/problems/permutation-sequence/)[^ps] |        |      |

## Reconstruct Itinerary

> [Link to Leetcode question](https://leetcode.com/problems/reconstruct-itinerary/description/)[^rl]
{: .prompt-info }

You are given a list of airline `tickets` where `tickets[i] = [fromi, toi]` represent the departure and the arrival airports of one flight. Reconstruct the itinerary in order and return it.

All of the tickets belong to a man who departs from `"JFK"`, thus, the itinerary must begin with `"JFK"`. If there are multiple valid itineraries, you should return the itinerary that has the smallest lexical order when read as a single string.

- For example, the itinerary `["JFK", "LGA"]` has a smaller lexical order than `["JFK", "LGB"]`.
  
You may assume all tickets form at least one valid itinerary. You must use all the tickets once and only once.

**Example 1**

![Desktop View](/assets/image/leetcode/leetcode-day-22/reconstruct-itinerary-example-1.jpeg)

```
Input: tickets = [["MUC","LHR"],["JFK","MUC"],["SFO","SJC"],["LHR","SFO"]]
Output: ["JFK","MUC","LHR","SFO","SJC"]
```

**Example 2**

![Desktop View](/assets/image/leetcode/leetcode-day-22/reconstruct-itinerary-example-2.jpeg)

```
Input: tickets = [["JFK","SFO"],["JFK","ATL"],["SFO","ATL"],["ATL","JFK"],["ATL","SFO"]]
Output: ["JFK","ATL","JFK","SFO","ATL","SFO"]
Explanation: Another possible reconstruction is ["JFK","SFO","ATL","JFK","ATL","SFO"] but it is larger in lexical order.
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0332.重新安排行程.html)[^rlSolution].

#### Python

```python
from collections import defaultdict

class Solution:
    def findItinerary(self, tickets):
        targets = defaultdict(list)  # 创建默认字典，用于存储机场映射关系
        for ticket in tickets:
            targets[ticket[0]].append(ticket[1])  # 将机票输入到字典中
        
        for key in targets:
            targets[key].sort(reverse=True)  # 对到达机场列表进行字母逆序排序
        
        result = []
        self.backtracking("JFK", targets, result)  # 调用回溯函数开始搜索路径
        return result[::-1]  # 返回逆序的行程路径
    
    def backtracking(self, airport, targets, result):
        while targets[airport]:  # 当机场还有可到达的机场时
            next_airport = targets[airport].pop()  # 弹出下一个机场
            self.backtracking(next_airport, targets, result)  # 递归调用回溯函数进行深度优先搜索
        result.append(airport)  # 将当前机场添加到行程路径中
```

### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Hard](https://img.shields.io/badge/Hard-red)                                                 | [1923 Longest Common Subpath](https://leetcode.com/problems/longest-common-subpath/description/)[^lcs] |        |      |
| ![Hard](https://img.shields.io/badge/Hard-red)                                                 | [2097 Valid Arrangement of Pairs](https://leetcode.com/problems/valid-arrangement-of-pairs/)[^vaop] |        |      |


## N-Queens

> [Link to Leetcode question](https://leetcode.com/problems/n-queens/description/)[^nq]
{: .prompt-info }

The n-queens puzzle is the problem of placing `n` queens on an `n x n` chessboard such that no two queens attack each other.

Given an integer `n`, return all distinct solutions to the n-queens puzzle. You may return the answer in any order.

Each solution contains a distinct board configuration of the n-queens' placement, where `'Q'` and `'.'` both indicate a queen and an empty space, respectively. 

**Example 1**

![Desktop View](/assets/image/leetcode/leetcode-day-22/n-queens-example-1.jpeg)

```
Input: n = 4
Output: [[".Q..","...Q","Q...","..Q."],["..Q.","Q...","...Q",".Q.."]]
Explanation: There exist two distinct solutions to the 4-queens puzzle as shown above
```

**Example 2**

```
Input: n = 1
Output: [["Q"]]
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0051.N皇后.html)[^nqSolution].


### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Hard](https://img.shields.io/badge/Hard-red)                                                | [52 N-Queens II](https://leetcode.com/problems/n-queens-ii/)[^nqii] |        |      |



## Sudoku Solver

> [Link to Leetcode question](https://leetcode.com/problems/sudoku-solver/description/)[^ss]
{: .prompt-info }

Write a program to solve a Sudoku puzzle by filling the empty cells.

A sudoku solution must satisfy all of the following rules:

1. Each of the digits `1-9` must occur exactly once in each row.
2. Each of the digits `1-9` must occur exactly once in each column.
3. Each of the digits `1-9` must occur exactly once in each of the 9 `3x3` sub-boxes of the grid.

The `'.'` character indicates empty cells.

**Example 1**

![Desktop View](/assets/image/leetcode/leetcode-day-22/sudoku-solver-example-1.png)

```
Input: board =
[["5","3",".",".","7",".",".",".","."],
["6",".",".","1","9","5",".",".","."],
[".","9","8",".",".",".",".","6","."],
["8",".",".",".","6",".",".",".","3"],
["4",".",".","8",".","3",".",".","1"],
["7",".",".",".","2",".",".",".","6"],
[".","6",".",".",".",".","2","8","."],
[".",".",".","4","1","9",".",".","5"],
[".",".",".",".","8",".",".","7","9"]]
Output:
[["5","3","4","6","7","8","9","1","2"],
["6","7","2","1","9","5","3","4","8"],
["1","9","8","3","4","2","5","6","7"],
["8","5","9","7","6","1","4","2","3"],
["4","2","6","8","5","3","7","9","1"],
["7","1","3","9","2","4","8","5","6"],
["9","6","1","5","3","7","2","8","4"],
["2","8","7","4","1","9","6","3","5"],
["3","4","5","2","8","6","1","7","9"]]
Explanation: The input board is shown above and the only valid solution is shown below:
```

![Desktop View](/assets/image/leetcode/leetcode-day-22/sudoku-solver-example-2.png)


### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0037.解数独.html)[^ssSolution].



### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [36 Valid Sudoku](https://leetcode.com/problems/valid-sudoku/description/)[^vs] |        |      |
| ![Hard](https://img.shields.io/badge/Hard-red)                                                  | [980 Unique Paths III](https://leetcode.com/problems/unique-paths-iii/)[^upiii] |        |      |


## Reference
[^nds]:Leetcode-491 Non-decreasing Subsequences: [https://leetcode.com/problems/non-decreasing-subsequences/description/](https://leetcode.com/problems/non-decreasing-subsequences/description/).
[^ndsSolution]:代码随想录-递增子序列: [https://programmercarl.com/0491.递增子序列.html](https://programmercarl.com/0491.递增子序列.html)
[^mlopc]:Leetcode-646 Maximum Length of Pair Chain: [https://leetcode.com/problems/maximum-length-of-pair-chain/](https://leetcode.com/problems/maximum-length-of-pair-chain/).
[^permu]:Leetcode-46 Permutations: [https://leetcode.com/problems/permutations/description/](https://leetcode.com/problems/permutations/description/).
[^permuSolution]:代码随想录-全排列: [https://programmercarl.com/0046.全排列.html](https://programmercarl.com/0046.全排列.html)
[^pii]:Leetcode-47 Permutations II: [https://leetcode.com/problems/permutations-ii/description/](https://leetcode.com/problems/permutations-ii/description/).
[^piiSolution]:代码随想录-全排列II: [https://programmercarl.com/0047.全排列II.html](https://programmercarl.com/0047.全排列II.html).
[^np]:Leetcode-31 Next Permutation: [https://leetcode.com/problems/next-permutation/description/](https://leetcode.com/problems/next-permutation/description/).
[^ps]:Leetcode-60 Permutation Sequence: [https://leetcode.com/problems/permutation-sequence/](https://leetcode.com/problems/permutation-sequence/).
[^rl]:Leetcode-332 Reconstruct Itinerary: [https://leetcode.com/problems/reconstruct-itinerary/description/](https://leetcode.com/problems/reconstruct-itinerary/description/).
[^rlSolution]:代码随想录-重新安排行程: [https://programmercarl.com/0332.重新安排行程.html](https://programmercarl.com/0332.重新安排行程.html).
[^lcs]: Leetcode-1923 Longest Common Subpath: [https://leetcode.com/problems/longest-common-subpath/description/](https://leetcode.com/problems/longest-common-subpath/description/).
[^vaop]: Leetcode-2097 Valid Arrangement of Pairs: [https://leetcode.com/problems/valid-arrangement-of-pairs/](https://leetcode.com/problems/valid-arrangement-of-pairs/).
[^nq]:Leectode-51 N-Queens: [https://leetcode.com/problems/n-queens/description/](https://leetcode.com/problems/n-queens/description/).
[^nqSolution]:代码随想录-N皇后: [https://programmercarl.com/0051.N皇后.html](https://programmercarl.com/0051.N皇后.html).
[^nqii]:Leectode-52 N-Queens II: [https://leetcode.com/problems/n-queens-ii/](https://leetcode.com/problems/n-queens-ii/).
[^ss]:Leetcode-37 Sudoku Solver: [https://leetcode.com/problems/sudoku-solver/description/](https://leetcode.com/problems/sudoku-solver/description/).
[^ssSolution]:代码随想录-解数独: [https://programmercarl.com/0037.解数独.html](https://programmercarl.com/0037.解数独.html).
[^vs]: Leetcode-36 Valid Sudoku: [https://leetcode.com/problems/valid-sudoku/description/](https://leetcode.com/problems/valid-sudoku/description/).
[^upiii]: Leetcode-980 Unique Paths III: [https://leetcode.com/problems/unique-paths-iii/](https://leetcode.com/problems/unique-paths-iii/).
