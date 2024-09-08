---
title: "Leetcode Day 30 - DP : Backpack Problem Basic"
description: 背包问题基础，二维dp数组、一维dp数组（滚动数组）
author: yoyo
date: 2024-09-07 23:53:00 +0800
categories: [Data Structure and Algorithm, Leetcode]
tags: [dynamic programming (DP)]
---

## Dynamic Programming

> [Link to note about Dynamic Programming](https://yuyulyu.github.io/posts/dynamic-programming/) 
{: .prompt-tip }

| Problem                                                    | Python | Java |
|------------------------------------------------------------|--------|------|
| [46 携带研究材料](#携带研究材料)                               |✅      |      |

## 携带研究材料

> [Link to the question](https://kamacoder.com/problempage.php?pid=1046)[^携带研究材料]
{: .prompt-info }

#### 题目描述

小明是一位科学家，他需要参加一场重要的国际科学大会，以展示自己的最新研究成果。他需要带一些研究材料，但是他的行李箱空间有限。这些研究材料包括实验设备、文献资料和实验样本等等，它们各自占据不同的空间，并且具有不同的价值。 
小明的行李空间为 `N`，问小明应该如何抉择，才能携带最大价值的研究材料，每种研究材料只能选择一次，并且只有选与不选两种选择，不能进行切割。

#### 输入描述

- 第一行包含两个正整数，第一个整数 `M` 代表研究材料的种类，第二个正整数 `N`，代表小明的行李空间。
- 第二行包含 `M` 个正整数，代表每种研究材料的所占空间。 
- 第三行包含 `M` 个正整数，代表每种研究材料的价值。

#### 输出描述

输出一个整数，代表小明能够携带的研究材料的最大价值。

#### 输入示例

`6 1`

`2 2 3 1 5 2`

`2 3 1 5 4 3`

#### 输出示例

`5`

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/背包理论基础01背包-1.html)[^背包理论基础].

#### 二维dp数组

```python
M, N = map(int, input().split())  
space = list(map(int, input().split()))  
value = list(map(int, input().split()))  

def backpack(M, N, space, value):
    if M == 0: return 0
    
    dp = [[0] * space[0] + [value[0]] * (N - space[0] + 1)] + [[0] * (N + 1) for _ in range (M - 1)]
    
    for item in range(M):
        for remain_space in range(N + 1):
            if remain_space >= space[item]:
                dp[item][remain_space] = max(value[item] + dp[item - 1][remain_space - space[item]], dp[item - 1][remain_space])
            else:
                dp[item][remain_space] = dp[item - 1][remain_space]
    
    return dp[-1][-1]
    
print(backpack(M, N, space, value))
```

#### 一维dp数组（滚动数组）

```python
M, N = map(int, input().split())  
space = list(map(int, input().split()))  
value = list(map(int, input().split()))  

def backpack(M, N, space, value):
    if M == 0: return 0
    
    dp = [0] * space[0] + [value[0]] * (N - space[0] + 1)
    
    for item in range(1, M):
        temp = [0] * (N + 1)
        for remain_space in range(N + 1):
            if remain_space >= space[item]:
                temp[remain_space] = max(value[item] + dp[remain_space - space[item]], dp[remain_space])
            else:
                temp[remain_space] = dp[remain_space]
        dp = temp.copy()
        
    return dp[-1]
    
print(backpack(M, N, space, value))
```

## Reference
[^携带研究材料]:卡码网-46 携带研究材料: [https://kamacoder.com/problempage.php?pid=1046](https://kamacoder.com/problempage.php?pid=1046).
[^背包理论基础]:代码随想录-背包理论基础01: [https://programmercarl.com/背包理论基础01背包-1.html](https://programmercarl.com/背包理论基础01背包-1.html).


