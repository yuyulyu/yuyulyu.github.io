---
title: Leetcode Day 7 - String
description: 344 Reverse String | 541 Reverse String II | Kama 54 Replace Number
author: yoyo
date: 2024-08-07 14:05:00 +0800
categories: [Algorithm, Leetcode]
tags: [string,]
---

![Easy](https://img.shields.io/badge/Easy-brightgreen) 
![Medium](https://img.shields.io/badge/Medium-yellow)
![Hard](https://img.shields.io/badge/Hard-red)

## String

| Diff                                                                                                | Problem                                                                                 | Python | Java |
|-----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|--------|------|
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                               | [344 Reverse String](#reverse-string)                                          |✅      |      |
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                                | [541 Reverse String II](#reverse-string-ii)                |✅      |      |
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                              | [Kama-54 Replace Numbers](#replace-numbers)               |✅      |      |

## Reverse String

> [Link to Leetcode question](https://leetcode.com/problems/reverse-string/description/)[^rs]
 {: .prompt-info }

Write a function that reverses a string. The input string is given as an array of characters `s`.

You must do this by modifying the input array in-place with `O(1)` extra memory.

**Example 1**

```
Input: s = ["h","e","l","l","o"]
Output: ["o","l","l","e","h"]
```

**Example 2**

```
Input: s = ["H","a","n","n","a","h"]
Output: ["h","a","n","n","a","H"]
```

### Solution
> A detailed explaination of solution can be found [here](https://programmercarl.com/0344.反转字符串.html#算法公开课)[^rsSolution]
#### Python

```python
class Solution(object):
    def reverseString(self, s):
        if s is None:
            return None
        n = len(s)
        for i in range(n // 2 ):
            s[i], s[n - i - 1] = s[n - i - 1], s[i]

        return s
```

### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                                 | [541 Reverse String II](#reverse-string-ii))[^rsii] |✅      |      |
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                                        | [345 Reverse Vowels of a String](https://leetcode.com/problems/reverse-vowels-of-a-string/)[^rvoas]          |        |      |


## Reverse String II

> [Link to Leetcode question](https://leetcode.com/problems/reverse-string-ii/description/)[^rsii]
 {: .prompt-info }

Given a string `s` and an integer `k`, reverse the first `k` characters for every `2k` characters counting from the start of the string.

If there are fewer than `k` characters left, reverse all of them. If there are less than `2k` but greater than or equal to `k` characters, then reverse the first `k` characters and leave the other as original.

**Example 1**

```
Input: s = "abcdefg", k = 2
Output: "bacdfeg"
```

**Example 2**

```
Input: s = "abcd", k = 2
Output: "bacd"
```

### Thinking Process

#### Solution 1



### Solution

#### Python

[**Solution 1**](#solution-1)

```python
class Solution(object):
    def reverseStr(self, s, k):
        if k == 1:
            return s
        res = list(s)
        l = len(res)        

        left = 0
        if(k >= l):
            right = l - 1
        else:
            right = k - 1
        reverse = True
        
        while(right < l):
            if reverse:
                for i in range((right - left + 1) // 2):
                    res[left + i],res[right - i] = res[right - i],res[left + i]

            reverse = not reverse
            
            left += k
            if right != l - 1 and right + k > l - 1 and reverse:
                right = l - 1
            else:
                right += k
        
        return ''.join(res)
```

**Solution 2**[^rsiilSolution]

```python
class Solution(object):
    def reverseStr(self, s, k):
        def reverse_substring(text):
            left, right = 0, len(text) - 1
            while left < right:
                text[left], text[right] = text[right], text[left]
                left += 1
                right -= 1
            return text
        
        res = list(s)

        for cur in range(0, len(s), 2 * k):
            res[cur: cur + k] = reverse_substring(res[cur: cur + k])
        
        return ''.join(res)
```

## Replace Numbers

> [Link to the question](https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/)[^rn]
 {: .prompt-info }

**题目描述**

> 给定一个字符串 `s`，它包含小写字母和数字字符，请编写一个函数，将字符串中的字母字符保持不变，而将每个数字字符替换为`number`。 例如，对于输入字符串 `a1b2c3`，函数应该将其转换为 `anumberbnumbercnumber`。

**输入描述**

> 输入一个字符串 `s`,`s` 仅包含小写字母和数字字符。

**输出描述**

> 打印一个新的字符串，其中每个数字字符都被替换为了`number`

**输入示例**

> `a1b2c3`

**输出示例**

> `anumberbnumbercnumber`


### Solution[^rnSolution]

#### Python 

**My Solution**

```python
s = input()

scaned = ""
number = ['1','2','3','4','5','6','7','8','9','0']

res = list(s)

for c in res:
    if c in number:
        scaned += "number"
    else:
        scaned += c

print(scaned)
```

**Answer**

```python
class Solution:
    def change(self, s):
        lst = list(s) # Python里面的string也是不可改的，所以也是需要额外空间的。空间复杂度：O(n)。
        for i in range(len(lst)):
            if lst[i].isdigit():
                lst[i] = "number"
        return ''.join(lst)
```




## Reference
[^rs]: Leetcode-344 Reverse String: [https://leetcode.com/problems/reverse-string/description/](https://leetcode.com/problems/reverse-string/description/).
[^rsSolution]: 代码随想录-反转字符串: [https://programmercarl.com/0344.反转字符串.html#算法公开课](https://programmercarl.com/0344.反转字符串.html#算法公开课).
[^rsii]: Leetcode-541 Reverse String II: [https://leetcode.com/problems/reverse-string-ii/description/](https://leetcode.com/problems/reverse-string-ii/description/).
[^rvoas]: Leetcode-345 Reverse Vowels of a String: [https://leetcode.com/problems/reverse-vowels-of-a-string/](https://leetcode.com/problems/reverse-vowels-of-a-string/).
[^rsiilSolution]:代码随想录-反转字符串II: [https://programmercarl.com/0541.反转字符串II.html#算法公开课](https://programmercarl.com/0541.反转字符串II.html#算法公开课).
[^rn]:卡码网-54 替换数字: [https://kamacoder.com/problempage.php?pid=1064](https://kamacoder.com/problempage.php?pid=1064).
[^rnSolution]: 代码随想录-替换数字: [https://kamacoder.com/problempage.php?pid=1064](https://kamacoder.com/problempage.php?pid=1064).


