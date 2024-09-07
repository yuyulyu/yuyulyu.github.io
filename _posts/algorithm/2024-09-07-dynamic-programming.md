---
title: Dynamic Programming (DP)
description: "Dynamic Programming (DP) is a technique that solves complex problems by breaking them into smaller overlapping subproblems and reusing the solutions to avoid redundant computations. It is particularly useful when a problem can be divided into overlapping subproblems or optimal substructure. Two main approaches: top-down (memoization) and bottom-up (tabulation) are introduced. "
author: yoyo
date: 2024-09-07 14:32:00 +0800
categories: [Data Structure and Algorithm, Algorithm]
tags: [dynamic programming (DP)]
math: true
---

## Key Concepts

### Overlapping Subproblems

DP is useful when the same subproblems are solved multiple times. Instead of recomputing the solution every time, we store the results and reuse them. This is different from other problem-solving techniques like divide-and-conquer where subproblems are independent.

### Optimal Substructure

A problem exhibits optimal substructure if an optimal solution to the problem can be constructed from optimal solutions of its subproblems. In other words, solving smaller subproblems can help solve the overall problem optimally.

## Two Main Approaches

There are two ways to approach a DP problem:

### Top-down (Memoization):

- Start by solving the larger problem.
- Whenever a subproblem is encountered, check if it has been solved before.
- If not, solve the subproblem and store the result.
- Reuse the stored results when needed.

Example: Recursive Fibonacci with memoization

```python
def fibonacci(n, memo={}):
    if n in memo:
        return memo[n]
    if n <= 1:
        return n
    memo[n] = fibonacci(n - 1, memo) + fibonacci(n - 2, memo)
    return memo[n]
```

### Bottom-up (Tabulation):
- Solve the smallest subproblems first.
- Use these solutions to build up solutions for larger subproblems.
- This typically involves filling up a table (array) where each cell represents the solution to a subproblem.

Example: Iterative Fibonacci with tabulation

```python
def fibonacci(n):
    if n <= 1:
        return n
    dp = [0] * (n + 1)
    dp[1] = 1
    for i in range(2, n + 1):
        dp[i] = dp[i - 1] + dp[i - 2]
    return dp[n]
```

### Steps to Solve a DP Problem

1. **Define the Subproblems**: 
   Identify the subproblems that are repeated and can be solved independently. These subproblems should contribute to solving the larger problem.

2. **Recurrence Relation**: 
   Formulate the relation that shows how the solution to the larger problem is composed of solutions to smaller subproblems.

   For example, in the Fibonacci sequence:
   \[
   F(n) = F(n-1) + F(n-2)
   \]

3. **Base Case**: 
   Define the base case(s) that solve the simplest possible version of the problem.

4. **Memoization or Tabulation**:
   - **Memoization**: Use a hash map or array to store solutions to subproblems.
   - **Tabulation**: Build up solutions iteratively using a table.
