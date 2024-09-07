---
title: Dynamic Programming (DP)
description: Dynamic Programming (DP) is a technique that solves complex problems by breaking them into smaller overlapping subproblems and reusing the solutions to avoid redundant computations. It is particularly useful when a problem can be divided into overlapping subproblems or optimal substructure. Two main approaches: top-down (memoization) and bottom-up (tabulation) are introduced. 
author: yoyo
date: 2024-09-07 14:32:00 +0800
categories: [Data Structure and Algorithm, Algorithm]
tags: [dynamic programming (DP)]
---

## Key Concepts

### Overlapping Subproblems

DP is useful when the same subproblems are solved multiple times. Instead of recomputing the solution every time, we store the results and reuse them. This is different from other problem-solving techniques like divide-and-conquer where subproblems are independent.

### Optimal Substructure

A problem exhibits optimal substructure if an optimal solution to the problem can be constructed from optimal solutions of its subproblems. In other words, solving smaller subproblems can help solve the overall problem optimally.


