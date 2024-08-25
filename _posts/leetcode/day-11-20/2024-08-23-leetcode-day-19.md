---
title: "Leetcode Day 19 - Backtracking: Combination"
description:  77 Combinations | 216 Combination Sum III |17 Letter Combinations of a Phone Number
author: yoyo
date: 2024-08-23 23:47:00 +0800
categories: [Data Structure and Algorithm, Leetcode]
tags: [backtracking]
---

## Backtracking Algorithm 

| Diff                                                                                                | Problem                                                                                 | Python | Java |
|-----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [77 Combinations](#combinations)                                                    |✅      |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [216 Combination Sum III](#combination-sum-iii)                                             |✅      |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [17 Letter Combinations of a Phone Number](#letter-combinations-of-a-phone-number)            |✅      |      |

## Combinations

> [Link to Leetcode question](https://leetcode.com/problems/combinations/description/)[^comb]
{: .prompt-info }

Given two integers `n` and `k`, return all possible combinations of `k` numbers chosen from the range `[1, n]`.

You may return the answer in any order.

**Example 1**

```
Input: n = 4, k = 2
Output: [[1,2],[1,3],[1,4],[2,3],[2,4],[3,4]]
Explanation: There are 4 choose 2 = 6 total combinations.
Note that combinations are unordered, i.e., [1,2] and [2,1] are considered to be the same combination.
```

**Example 2**

```
Input: n = 1, k = 1
Output: [[1]]
Explanation: There is 1 choose 1 = 1 total combination.
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0077.组合.html)[^combSolution].

#### Python

```python
class Solution(object):
    def combine(self, n, k):
        result = []
        nums = [i for i in range(1, n + 1)]
        print(nums)

        def comb(group,nums,k):
            if k == 1:
                for num in nums:
                    result.append(group + [num])
                return
            
            for i in range(len(nums)):
                comb(group + [nums[i]], nums[i + 1:], k - 1)
    
        comb([],nums,k)
        return result
```


### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [39 Combination Sum](https://leetcode.com/problems/combination-sum/description/)[^cs] |        |      |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                         | [46 Permutations](https://leetcode.com/problems/permutations/description/)[^pemu]          |        |      |


## Combination Sum III

> [Link to Leetcode question](https://leetcode.com/problems/combination-sum-iii/description/)[^csiii]
{: .prompt-info }

Find all valid combinations of `k` numbers that sum up to `n` such that the following conditions are true:

- Only numbers `1` through `9` are used.
- Each number is used at most once.

Return a list of all possible valid combinations. The list must not contain the same combination twice, and the combinations may be returned in any order.

**Example 1**

```
Input: k = 3, n = 7
Output: [[1,2,4]]
Explanation:
1 + 2 + 4 = 7
There are no other valid combinations.
```

**Example 2**

```
Input: k = 3, n = 9
Output: [[1,2,6],[1,3,5],[2,3,4]]
Explanation:
1 + 2 + 6 = 9
1 + 3 + 5 = 9
2 + 3 + 4 = 9
There are no other valid combinations.
```

**Example 3**

```
Input: k = 4, n = 1
Output: []
Explanation: There are no valid combinations.
Using 4 different numbers in the range [1,9], the smallest sum we can get is 1+2+3+4 = 10 and since 10 > 1, there are no valid combination.
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0216.组合总和III.html)[^csiiiSolution].

#### Python

```python
class Solution(object):
    def combinationSum3(self, k, n):
        nums = [i for i in range(1,10)]
        result = []

        def comb(group,nums, k, n):
            if len(nums) == 0 or nums[0] > n:
                return
            
            if k == 1 and n in nums:
                result.append(group + [n])
            
            for i in range(len(nums)):
                if nums[i] > n:
                    break
                comb(group + [nums[i]], nums[i+1:],k - 1, n - nums[i])
            
        comb([],nums,k,n)
        return result
```

## Letter Combinations of a Phone Number

> [Link to Leetcode question](https://leetcode.com/problems/letter-combinations-of-a-phone-number/description/)[^lcoapn]
{: .prompt-info }

Given a string containing digits from `2-9` inclusive, return all possible letter combinations that the number could represent. Return the answer in any order.

A mapping of digits to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.

![Desktop View](/assets/image/leetcode/leetcode-day-19/letter-combinations-of-a-phone-number-example-1.png)


**Example 1**

```
Input: digits = "23"
Output: ["ad","ae","af","bd","be","bf","cd","ce","cf"]
```

**Example 2**

```
Input: digits = ""
Output: []
```

**Example 3**

```
Input: digits = "2"
Output: ["a","b","c"]
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0017.电话号码的字母组合.html)[^lcoapnSolution].

#### Python

```python
class Solution(object):
    def letterCombinations(self, digits):

        phone = {'2':['a','b','c'],'3':['d','e','f'],'4':['g','h','i'],'5':['j','k','l'],'6':['m','n','o'],'7':['p','q','r','s'],'8':['t','u','v'],'9':['w','x','y','z']}
        result = []
        nums = list(digits)

        def comb(i,string):
            if len(nums) == i:
                return

            if len(nums) == i + 1:
                for c in phone[nums[i]]:
                    result.append(string + c)
            
            for c in phone[nums[i]]:
                comb(i + 1,string + c)
        
        comb(0,"")
        return result
```


### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                                 | [3014 Minimum Number of Pushes to Type Word I](https://leetcode.com/problems/minimum-number-of-pushes-to-type-word-i/description/)[^mnopttwi] |        |  
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [3016 Minimum Number of Pushes to Type Word II](https://leetcode.com/problems/minimum-number-of-pushes-to-type-word-ii/description/)[^mnopttwii]                                 |        |        |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [2266 Count Number of Texts](https://leetcode.com/problems/count-number-of-texts/description/)[^cnot]                |        |        |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [22 Generate Parentheses](https://leetcode.com/problems/generate-parentheses/)[^gp]                |        |        |


## Reference
[^comb]:Leetcode-77 Combinations: [https://leetcode.com/problems/combinations/description/](https://leetcode.com/problems/combinations/description/).
[^combSolution]:代码随想录-组合: [https://programmercarl.com/0077.组合.html](https://programmercarl.com/0077.组合.html).
[^cs]:Leetcode-39 Combination Sum: [https://leetcode.com/problems/combination-sum/description/](https://leetcode.com/problems/combination-sum/description/).
[^pemu]:Leetcode-46 Permutations: [https://leetcode.com/problems/permutations/description/](https://leetcode.com/problems/permutations/description/).
[^csiii]:Leetcode-216 Combination Sum III: [https://leetcode.com/problems/combination-sum-iii/description/](https://leetcode.com/problems/combination-sum-iii/description/).
[^csiiiSolution]:代码随想录-组合总和III: [https://programmercarl.com/0216.组合总和III.html](https://programmercarl.com/0216.组合总和III.html).
[^lcoapn]:Leetcode-17 Letter Combinations of a Phone Number: [https://leetcode.com/problems/letter-combinations-of-a-phone-number/description/](https://leetcode.com/problems/letter-combinations-of-a-phone-number/description/).
[^lcoapnSolution]:代码随想录-电话号码的字母组合: [https://programmercarl.com/0017.电话号码的字母组合.html](https://programmercarl.com/0017.电话号码的字母组合.html).
[^mnopttwi]: Leetcode-3014 Minimum Number of Pushes to Type Word I: [https://leetcode.com/problems/minimum-number-of-pushes-to-type-word-i/description/](https://leetcode.com/problems/minimum-number-of-pushes-to-type-word-i/description/).
[^mnopttwii]: Leetcode-3016 Minimum Number of Pushes to Type Word II: [https://leetcode.com/problems/minimum-number-of-pushes-to-type-word-ii/description/](https://leetcode.com/problems/minimum-number-of-pushes-to-type-word-ii/description/).
[^cnot]: Leetcode-2266 Count Number of Texts: [https://leetcode.com/problems/count-number-of-texts/description/](https://leetcode.com/problems/count-number-of-texts/description/).
[^gp]: Leetcode-22 Generate Parentheses: [https://leetcode.com/problems/generate-parentheses/](https://leetcode.com/problems/generate-parentheses/).
