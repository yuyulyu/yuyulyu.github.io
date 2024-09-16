---
title: "Leetcode Day 34 - DP: House Robber"
description: 198 House Robber | 213 House Robber II | 337 House Robber III
author: yoyo
date: 2024-09-09 14:30:00 +0800
categories: [Data Structure and Algorithm, Leetcode, Dynamic Programming]
tags: [dynamic programming (DP)]
image:
  path: /assets/covers/leetcode/leetcode-day-34.png
  alt: Leetcode Day 34 Cover
---

## Dynamic Programming

| Diff                                                                                                | Problem                                                                                 | Python | Java |
|-----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|--------|--------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [198 House Robber](#house-robber)                                                    |✅      |        |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [213 House Robber II](#house-robber-ii)                                         |✅      |        |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [337 House Robber III](#house-robber-iii)                                        |✅      |        |


## House Robber

> [Link to Leetcode question](https://leetcode.com/problems/house-robber/description/)[^hb]
{: .prompt-info }

You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed, the only constraint stopping you from robbing each of them is that adjacent houses have security systems connected and it will automatically contact the police if two adjacent houses were broken into on the same night.

Given an integer array `nums` representing the amount of money of each house, return the maximum amount of money you can rob tonight without alerting the police.

**Example 1**

```
Input: nums = [1,2,3,1]
Output: 4
Explanation: Rob house 1 (money = 1) and then rob house 3 (money = 3).
Total amount you can rob = 1 + 3 = 4.
```

Example 2:

Input: nums = [2,7,9,3,1]
Output: 12
Explanation: Rob house 1 (money = 2), rob house 3 (money = 9) and rob house 5 (money = 1).
Total amount you can rob = 2 + 9 + 1 = 12.

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0198.打家劫舍.html)[^hbSolution].

#### Python

```python
class Solution(object):
    def rob(self, nums):
        if len(nums) == 0: return 0
        prev1, prev2 = 0, 0  

        for num in nums:
            prev1, prev2 = prev2, max(prev2, prev1 + num) 

        return prev2
```


## House Robber II

> [Link to Leetcode question](https://leetcode.com/problems/house-robber-ii/description/)[^hbii]
{: .prompt-info }

You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed. All houses at this place are arranged in a circle. That means the first house is the neighbor of the last one. Meanwhile, adjacent houses have a security system connected, and it will automatically contact the police if two adjacent houses were broken into on the same night.

Given an integer array `nums` representing the amount of money of each house, return the maximum amount of money you can rob tonight without alerting the police.

**Example 1**

```
Input: nums = [2,3,2]
Output: 3
Explanation: You cannot rob house 1 (money = 2) and then rob house 3 (money = 2), because they are adjacent houses.
```

**Example 2**

```
Input: nums = [1,2,3,1]
Output: 4
Explanation: Rob house 1 (money = 1) and then rob house 3 (money = 3).
Total amount you can rob = 1 + 3 = 4.
```

**Example 3**

```
Input: nums = [1,2,3]
Output: 3
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0213.打家劫舍II.html)[^hbiiSolution].

#### Python

```python
lass Solution(object):
    def rob(self, nums):
        if len(nums) == 0: return 0
        if len(nums) == 1: return nums[0]
        return max(self.r(nums[1:]), self.r(nums[:-1]))

    def r(self, nums):
        prev1, prev2 = 0, 0  

        for num in nums:
            prev1, prev2 = prev2, max(prev2, prev1 + num) 

        return prev2
```


## House Robber III

> [Link to Leetcode question](https://leetcode.com/problems/house-robber-iii/description/)[^hbiii]
{: .prompt-info }

The thief has found himself a new place for his thievery again. There is only one entrance to this area, called `root`.

Besides the `root`, each house has one and only one parent house. After a tour, the smart thief realized that all houses in this place form a binary tree. It will automatically contact the police if two directly-linked houses were broken into on the same night.

Given the `root` of the binary tree, return the maximum amount of money the thief can rob without alerting the police.

**Example 1**

[image]: house-robber-iii-example-1

```
Input: root = [3,2,3,null,3,null,1]
Output: 7
Explanation: Maximum amount of money the thief can rob = 3 + 3 + 1 = 7.
```

**Example 2**

[image]: house-robber-iii-example-2

```
Input: root = [3,4,5,1,3,null,1]
Output: 9
Explanation: Maximum amount of money the thief can rob = 4 + 5 = 9.
```


### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0337.打家劫舍.html#)[^hbSolution].

#### Python

```python
class Solution(object):

    def rob(self, root):
        return self.r(root)[0]

    def r(self, node):
        if node is None: return 0, 0
        if node.left is None and node.right is None: return node.val, 0

        left_child, left_grand_child = self.r(node.left)
        right_child, right_grand_child = self.r(node.right)

        child = left_child + right_child
        grand_child = left_grand_child + right_grand_child

        return max(child, node.val + grand_child), child
```


## Reference

[^hb]:Leetcode-198 House Robber: [https://leetcode.com/problems/house-robber/description/](https://leetcode.com/problems/house-robber/description/).
[^hbSolution]:代码随想录-打家劫舍: [https://programmercarl.com/0198.打家劫舍.html](https://programmercarl.com/0198.打家劫舍.html).
[^hbii]:Leetcode-213 House Robber II: [https://leetcode.com/problems/house-robber/description/](https://leetcode.com/problems/house-robber-ii/description/).
[^hbiiSolution]:代码随想录-打家劫舍II: [https://programmercarl.com/0213.打家劫舍II.html](https://programmercarl.com/0213.打家劫舍II.html).
[^hbiii]:Leetcode-337 House Robber III: [https://leetcode.com/problems/house-robber/description/](https://leetcode.com/problems/house-robber-iii/description/).
[^hbiiiSolution]:代码随想录-打家劫舍III: [https://programmercarl.com/0198.打家劫舍III.html](https://programmercarl.com/0337.打家劫舍OOO.html).
