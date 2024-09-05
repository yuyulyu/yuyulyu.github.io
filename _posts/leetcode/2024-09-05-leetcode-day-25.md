---
title: Leetcode Day 24 - Greedy Algorithm
description: 134 Gas Station | 135 Candy | 860 Lemonade Change | 406 Queue Reconstruction by Height
author: yoyo
date: 2024-09-05 09:58:00 +0800
categories: [Data Structure and Algorithm, Leetcode]
tags: [greedy]
---

## Greedy Algorithm 

| Diff                                                                                                | Problem                                                                                 | Python | Java |
|-----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [134 Gas Station](#gas-station)                                                       |✅      |       |
| ![Hard](https://img.shields.io/badge/Hard-red)                                                      | [135 Candy](#candy)                                                                        |✅      |       |
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                              | [860 Lemonade Change](#lemonade-change)                                             |✅      |       |
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                               | [406 Queue Reconstruction by Height](#queue-reconstruction-by-height)                    |        |        |

# the link

## Gas Station

> [Link to Leetcode question](https://leetcode.com/problems/gas-station/description/)[^gs]
{: .prompt-info }

There are `n` gas stations along a circular route, where the amount of gas at the ith station is `gas[i]`.

You have a car with an unlimited gas tank and it costs `cost[i]` of gas to travel from the ith station to its next (i + 1)th station. You begin the journey with an empty tank at one of the gas stations.

Given two integer arrays `gas` and `cost`, return the starting gas station's index if you can travel around the circuit once in the clockwise direction, otherwise return `-1`. If there exists a solution, it is guaranteed to be unique.
 
**Example 1**

```
Input: gas = [1,2,3,4,5], cost = [3,4,5,1,2]
Output: 3
Explanation:
Start at station 3 (index 3) and fill up with 4 unit of gas. Your tank = 0 + 4 = 4
Travel to station 4. Your tank = 4 - 1 + 5 = 8
Travel to station 0. Your tank = 8 - 2 + 1 = 7
Travel to station 1. Your tank = 7 - 3 + 2 = 6
Travel to station 2. Your tank = 6 - 4 + 3 = 5
Travel to station 3. The cost is 5. Your gas is just enough to travel back to station 3.
Therefore, return 3 as the starting index.
```

**Example 2**

```
Input: gas = [2,3,4], cost = [3,4,3]
Output: -1
Explanation:
You can't start at station 0 or 1, as there is not enough gas to travel to the next station.
Let's start at station 2 and fill up with 4 unit of gas. Your tank = 0 + 4 = 4
Travel to station 0. Your tank = 4 - 3 + 2 = 3
Travel to station 1. Your tank = 3 - 3 + 3 = 3
You cannot travel back to station 2, as it requires 4 unit of gas but you only have 3.
Therefore, you can't travel around the circuit once no matter where you start.
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0134.加油站.html)[^gsSolution].

There are three key cases to consider:

1. **No solution exists**: If the sum of `gas`  is less than the sum of `cost`, it is impossible to complete the circuit.
2. **Sufficient gas to complete the route**: With `cur_sum += gas[i] - cost[i]` as the remaining gas in tank. If `cur_sum >= 0` throughout the journey, starting at `i = 0` will be able to complete the circuit.
3. **Restart when cur_sum becomes negative**: If at any point `cur_sum < 0`, it means that starting from any station between `0` and the current station `i` won't be able to complete the journey. So, the next possible starting station must be `i + 1`.

#### Python

```python
class Solution(object):
    def canCompleteCircuit(self, gas, cost):
        if sum(gas) < sum(cost):
            return -1
        cur_sum = 0
        index = 0

        for i in range(len(gas)):
            cur_sum += gas[i] - cost[i]
            if cur_sum <= 0:
                index = i + 1
                cur_sum = 0
        
        return index % len(gas)
```

### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [2202 Maximize the Topmost Element After K Moves](https://leetcode.com/problems/maximize-the-topmost-element-after-k-moves/)[^mtteakm] |        |      |


## Candy

> [Link to Leetcode question](https://leetcode.com/problems/candy/description/)[^candy]
{: .prompt-info }

There are `n` children standing in a line. Each child is assigned a rating value given in the integer array `ratings`.

You are giving candies to these children subjected to the following requirements:

- Each child must have at least one candy.
- Children with a higher rating get more candies than their neighbors.
- Return the minimum number of candies you need to have to distribute the candies to the children.

**Example 1**

```
Input: ratings = [1,0,2]
Output: 5
Explanation: You can allocate to the first, second and third child with 2, 1, 2 candies respectively.
```

**Example 2**

```
Input: ratings = [1,2,2]
Output: 4
Explanation: You can allocate to the first, second and third child with 1, 2, 1 candies respectively.
The third child gets 1 candy because it satisfies the above two conditions.
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0135.分发糖果.html)[^candySolution].

The problem can be solved by focusing on two important conditions for distributing candies:

1. **Left to right rule**: If a child has a higher rating than the child directly to their left, they should receive more candies than the left neighbor.
2. **Right to left rule**: Similarly, if a child has a higher rating than the child directly to their right, they should receive more candies than the right neighbor.

To solve the problem, we can approach it in two steps:

1. **First pass (left to right)**: Start by assigning `1` candy to each child. Then, traverse the ratings array from left to right. If a child’s rating is higher than the child before them, give them one more candy than the previous child.
2. **Second pass (right to left)**: After the first pass, traverse the array again, but this time from right to left. If a child’s rating is higher than the child to their right, and they don't already have more candies, give them one more candy than the right child.
   
By making these two passes, we ensure that all children satisfy the two conditions. 

#### Python

```python
class Solution(object):
    def candy(self, ratings):
        l = len(ratings)
        candies = [1] * l
        
        for i in range(1, l):
            if ratings[i] > ratings[i - 1]:
                candies[i] = candies[i - 1] + 1
        
        for i in range(l - 2, -1, -1):
            if ratings[i] > ratings[i + 1] and candies[i] <= candies[i + 1]:
                candies[i] = candies[i + 1] + 1

        return sum(candies)
```

## Lemonade Change

> [Link to Leetcode question](https://leetcode.com/problems/lemonade-change/description/)[^lc]
{: .prompt-info }

At a lemonade stand, each lemonade costs `$5`. Customers are standing in a queue to buy from you and order one at a time (in the order specified by bills). Each customer will only buy one lemonade and pay with either a `$5`, `$10`, or `$20` bill. You must provide the correct change to each customer so that the net transaction is that the customer pays `$5`.

Note that you do not have any change in hand at first.

Given an integer array bills where `bills[i]` is the bill the ith customer pays, return true if you can provide every customer with the correct change, or false otherwise.

**Example 1**

```
Input: bills = [5,5,5,10,20]
Output: true
Explanation: 
From the first 3 customers, we collect three $5 bills in order.
From the fourth customer, we collect a $10 bill and give back a $5.
From the fifth customer, we give a $10 bill and a $5 bill.
Since all customers got correct change, we output true.
```

**Example 2**

```
Input: bills = [5,5,10,10,20]
Output: false
Explanation: 
From the first two customers in order, we collect two $5 bills.
For the next two customers in order, we collect a $10 bill and give back a $5 bill.
For the last customer, we can not give the change of $15 back because we only have two $10 bills.
Since not every customer received the correct change, the answer is false.
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0860.柠檬水找零.html)[^lcSolution].

#### Python

```python
class Solution(object):
    def lemonadeChange(self, bills):
        five, ten = 0, 0
        for bill in bills:
            if bill == 5:
                five += 1
            elif bill == 10:
                if five == 0:
                    return False
                five -= 1
                ten += 1
            else:
                if ten > 0 and five > 0:
                    ten -= 1
                    five -= 1
                elif five >= 3:
                    five -= 3
                else:
                    return False
        return True
```


## Queue Reconstruction by Height

> [Link to Leetcode question](https://leetcode.com/problems/queue-reconstruction-by-height/description/)[^qrbh]
{: .prompt-info }

You are given an array of people, people, which are the attributes of some people in a queue (not necessarily in order). Each `people[i] = [hi, ki]` represents the `i<sup>th<sup>` person of height `h_i` with exactly `k_i` other people in front who have a height greater than or equal to `h_i`.

Reconstruct and return the queue that is represented by the input array people. The returned queue should be formatted as an array queue, where `queue[j] = [hj, kj]` is the attributes of the `j<sup>th</sup>` person in the queue (`queue[0]` is the person at the front of the queue).

**Example 1**

```
Input: people = [[7,0],[4,4],[7,1],[5,0],[6,1],[5,2]]
Output: [[5,0],[7,0],[5,2],[6,1],[4,4],[7,1]]
Explanation:
Person 0 has height 5 with no other people taller or the same height in front.
Person 1 has height 7 with no other people taller or the same height in front.
Person 2 has height 5 with two persons taller or the same height in front, which is person 0 and 1.
Person 3 has height 6 with one person taller or the same height in front, which is person 1.
Person 4 has height 4 with four people taller or the same height in front, which are people 0, 1, 2, and 3.
Person 5 has height 7 with one person taller or the same height in front, which is person 1.
Hence [[5,0],[7,0],[5,2],[6,1],[4,4],[7,1]] is the reconstructed queue.
```

**Example 2**

```
Input: people = [[6,0],[5,0],[4,0],[3,2],[2,2],[1,4]]
Output: [[4,0],[5,0],[2,2],[3,2],[1,4],[6,0]]
```

### Solution

> A detailed explaination of solution can be found [here](https://programmercarl.com/0406.根据身高重建队列.html)[^qrbhSolution].



### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Medium](https://img.shields.io/badge/Medium-yellow)                                                | [2512 Reward Top K Students](https://leetcode.com/problems/reward-top-k-students/description/)[^rtks] |        |      |
| ![Hard](https://img.shields.io/badge/Hard-red)                                                | [315 Count of Smaller Numbers After Self](https://leetcode.com/problems/count-of-smaller-numbers-after-self/description/)[^cosnas] |        |      |




## Reference
[^gs]:Leetcode-134 Gas Station: [https://leetcode.com/problems/gas-station/description/](https://leetcode.com/problems/gas-station/description/).
[^gsSolution]:代码随想录-加油站: [https://programmercarl.com/0134.加油站.html](https://programmercarl.com/0134.加油站.html).
[^mtteakm]:Leetcode-2202 Maximize the Topmost Element After K Moves: [https://leetcode.com/problems/maximize-the-topmost-element-after-k-moves/](https://leetcode.com/problems/maximize-the-topmost-element-after-k-moves/).
[^candy]:Leetcode-135 Candy: [https://leetcode.com/problems/candy/description/](https://leetcode.com/problems/candy/description/).
[^candySolution]:代码随想录-分发糖果: [https://programmercarl.com/0135.分发糖果.html](https://programmercarl.com/0135.分发糖果.html).
[^lc]:Leetcode-860 Lemonade Change: [https://leetcode.com/problems/lemonade-change/description/](https://leetcode.com/problems/lemonade-change/description/).
[^lcSolution]:代码随想录-柠檬水找零: [https://programmercarl.com/0860.柠檬水找零.html](https://programmercarl.com/0860.柠檬水找零.html).
[^qrbh]:Leetcode-406 Queue Reconstruction by Height: [https://leetcode.com/problems/queue-reconstruction-by-height/description/](https://leetcode.com/problems/queue-reconstruction-by-height/description/).
[^qrbhSolution]:代码随想录-根据身高重建队列: [https://programmercarl.com/0406.根据身高重建队列.html](https://programmercarl.com/0406.根据身高重建队列.html).
[^rtks]:Leetcode-2512 Reward Top K Students: [https://leetcode.com/problems/reward-top-k-students/description/](https://leetcode.com/problems/reward-top-k-students/description/).
[^cosnas]:Leetcode-315 Count of Smaller Numbers After Self: [https://leetcode.com/problems/count-of-smaller-numbers-after-self/description/](https://leetcode.com/problems/count-of-smaller-numbers-after-self/description/).

