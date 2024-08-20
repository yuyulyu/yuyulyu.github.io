---
title: Leetcode Day 1 - Array Basics
description: Focuses on fundamental array operations. Covers binary search and basic element removal, emphasizing efficient searching and modifying arrays.
author: yoyo
date: 2024-07-31 22:56:00 +0800
categories: [Data Structure and Algorithm, Leetcode, Array]
tags: [array, binary search, double pointers]
---

## Array 1[^dmsxl]

| Diff                                                                                                 | Problem                                                                                       | Python | C++ |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                               | [074 Binary Search](#binary-search)  | ✅          | ✅          |
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                               | [27 Remove Element](#remove-element) | ✅          | ✅          |


## Binary Search

> [Link to Leetcode question](https://leetcode.com/problems/binary-search/)[^binarySearch]
{: .prompt-info }

Given an array of integers ```nums``` which is sorted in <ins>ascending order</ins>, and an integer ```target```, write a function to search ```target``` in ```nums```. If ```target``` exists, then return its index. Otherwise, return ```-1```.

You must write an algorithm with O(log n) runtime complexity.

**Example 1**
```Python
Input: nums = [-1,0,3,5,9,12], target = 9
Output: 4
Explanation: 9 exists in nums and its index is 4
```

**Example 2**
```Python
Input: nums = [-1,0,3,5,9,12], target = 2
Output: -1
Explanation: 2 does not exist in nums so return -1
```

### Note
**General Idea**
Use left and right node to define the range for exploration (Initially ```left = 0`` ``right = len(nums)```), so that ``mid`` can be used for binary search. 

**Difficulties**
  * How to define ```mid```.
  * How to update ```left``` and ```right```.
  * Conditions of while loop.

**Variable Scope and Memory Management in Java***
  - **Scope**: The scope of a variable determines where the variable is accessible within the program. In Java, the scope is determined by where the variable is declared.
    - <ins>Local Variables</ins>: Declared inside a method or a code block (like a while loop or for loop) and are only accessible within that block.
    - <ins>Instance Variables</ins>: Declared inside a class but outside any method, accessible to all methods within the class.
Class Variables (Static Variables): Declared with the static keyword inside a class, shared across all instances of the class.
  - **Lifecycle**: The lifecycle of a variable refers to the period during which the variable exists in memory.
    - <ins>Local Variables</ins>: Their lifecycle starts when the block is entered and ends when the block is exited.
    - <ins>Instance Variables</ins>: Their lifecycle starts when an object is created and ends when the object is garbage collected.
    - <ins>Class Variables</ins>: Their lifecycle starts when the class is loaded and ends when the class is unloaded.

**Benefits of Declaring Variables Inside a Loop**

When a variable such as ```int mid``` was decleared inside the ```while loop```.
The variable mid is a local variable with a scope limited to each iteration of the while loop. Here are the benefits:

1. **Automatic Memory Release**: At the end of each iteration, the local variable mid goes out of scope, and Java's garbage collector can reclaim the memory used by mid. This helps in managing memory efficiently.
2. **Memory Reuse**: In the next iteration, the JVM can allocate memory for mid again, potentially reusing the same memory space. This can reduce memory fragmentation and improve overall memory usage.
3. **Avoid Unintentional Modifications**: Declaring variables inside the loop ensures they are re-initialized with each iteration, preventing accidental modifications that might occur if the variable were declared outside the loop.

### Solution
A detail solution explaination[^binarySearchSolution] can be found [here](https://programmercarl.com/0704.二分查找.html#思路)
  * Time complexity: O(log n)
  * Memory complexity: O(1)

#### Python
```python
class Solution(object):
    def search(self, nums, target):
        right = len(nums) - 1
        left = 0

        while (left <= right):
            mid = left + (right - left) // 2
            if (target > nums[mid]):
                left = mid + 1
            elif(target < nums[mid]):
                right = mid - 1
            else:
                return mid
                
        return -1
```

#### C++

```c++
class Solution {
public int search(vector<int>& nums, int target) {
        int left = 0;
        int right = nums.size() - 1;
        while(left <= right){
            int mid = left + (right - left) / 2;
            if(nums[mid] == target) return mid;
            if(nums[mid] < target){
                left = mid + 1;
            }
            else{
                right = mid - 1;
            }
        }
        return -1;
    }
};
```


#### Java
```java
class Solution {
    public int search(int[] nums, int target) {
        int left = 0;
        int right = nums.length - 1;

        while(left <= right){
            int mid = left + (right - left) / 2;

            if(nums[mid] < target){
                left = mid + 1;
            }
            else if (nums[mid] > target){
                right = mid - 1;
            }
            else{
                return mid;
            }
        }
        return -1;
    }
}
```

### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                               | [2529 Maximum Count of Positive Integer and Negative Integer](https://leetcode.com/problems/maximum-count-of-positive-integer-and-negative-integer/)[^mmcopiani] |        |      |



## Remove Element

> [Link to Leetcode question](https://leetcode.com/problems/remove-element/description/)[^removeElement]
{: .prompt-info }

Given an integer array ```nums``` and an integer ```val```, remove all occurrences of ```val``` in ```nums``` in-place. The order of the elements may be changed. Then return the number of elements in ```nums``` which are not equal to ```val```.

Consider the number of elements in ```nums``` which are not equal to ```val``` be ```k```, to get accepted, you need to do the following things:

  - Change the array ```nums``` such that the first ```k``` elements of ```nums``` contain the elements which are not equal to ```val```. The remaining elements of ```nums``` are not important as well as the size of ```nums```.
  - Return ```k```.

**Custom Judge**:

The judge will test your solution with the following code:

```
int[] nums = [...]; // Input array
int val = ...; // Value to remove
int[] expectedNums = [...]; // The expected answer with correct length.
                            // It is sorted with no values equaling val.

int k = removeElement(nums, val); // Calls your implementation

assert k == expectedNums.length;
sort(nums, 0, k); // Sort the first k elements of nums
for (int i = 0; i < actualLength; i++) {
    assert nums[i] == expectedNums[i];
}
```
If all assertions pass, then your solution will be accepted.

**Example 1**
```python
Input: nums = [3,2,2,3], val = 3
Output: 2, nums = [2,2,_,_]
Explanation: Your function should return k = 2, with the first two elements of nums being 2.
It does not matter what you leave beyond the returned k (hence they are underscores).
```

**Example 2**
```python
Input: nums = [0,1,2,2,3,0,4,2], val = 2
Output: 5, nums = [0,1,4,0,3,_,_,_]
Explanation: Your function should return k = 5, with the first five elements of nums containing 0, 0, 1, 3, and 4.
Note that the five elements can be returned in any order.
It does not matter what you leave beyond the returned k (hence they are underscores).
```

### Note
**Two-pointer: fast & slow pointer** [^removeElementSolution]

**Fast pointer**: Find the element of the new array, which is the array that does not contain the target element 
**Slow pointer**: points to the position where the new array subscript is updated

### Solution
A detail solution explaination[^removeElementSolution] can be found [here](https://programmercarl.com/0027.移除元素.html#思路)

#### Python
 - <ins>Brute Force</ins>
   - Time complexity: O(n<sup>2</sup>)
   - Memory complexity: O(1)
  ```python
  class Solution(object):
      def removeElement(self, nums, val):
          nex = 0
  
          for num in nums:
              if num != val:
                  nums[nex] = num
                  nex = nex + 1
          while len(nums) > nex:
              nums.pop()
  ```
  - <ins>Two-pointers</ins>
    - Time complexity: O(n)
    - Memory complexity: O(1)
  ```python
  class Solution(object):
    def removeElement(self, nums, val):
        fast_index = 0
        slow_index = 0

        while fast_index < len(nums):
            temp = nums[fast_index]
            if (temp != val):
                nums[slow_index] = temp
                slow_index += 1
            fast_index += 1
        
        while len(nums) > slow_index:
            nums.pop()
  ```
#### C++

```c++
class Solution {
public:
    int removeElement(vector<int>& nums, int val) {
        int slow = 0;
        
        for(int fast = 0; fast < nums.size();fast++){
            if(nums[fast] != val){
                nums[slow] = nums[fast];
                slow++;
            }
        }
        return slow;
    }
}
```

#### Java

```java
class Solution {
    public int removeElement(int[] nums, int val) {
        int slow = 0;

        for(int fast = 0;fast < nums.length;fast++){
            if(nums[fast] != val){
                nums[slow] = nums[fast];
                slow ++;
            }
        }
        return slow;
    }
}
```

### Similar Questions

| Diff                                                                                                 | Similar Questions                                                                                       | Python | Java |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|--------|------|
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                               | [26 Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/description/)[^rmdfsa] |        |      |
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                               | [203 Remove Linked List Elements](https://leetcode.com/problems/remove-linked-list-elements/description/)[^rlle] |        |      |
| ![Easy](https://img.shields.io/badge/Easy-brightgreen)                                               | [283 Move Zeroes](https://leetcode.com/problems/move-zeroes/description/)[^mz]  |        |      |


## Reference
[^dmsxl]:代码随想录-数组:[https://programmercarl.com/数组理论基础.html](https://programmercarl.com/数组理论基础.html).
[^binarySearch]:Leetcode-074 Binary Search: [https://leetcode.com/problems/binary-search/](https://leetcode.com/problems/binary-search/).
[^binarySearchSolution]:代码随想录-704二分法查找：[https://programmercarl.com/0704.二分查找.html#思路](https://programmercarl.com/0704.二分查找.html#思路).
[^removeElement]:LeetCode-27 Remove Element: [https://leetcode.com/problems/remove-element/description/](https://leetcode.com/problems/remove-element/description/).
[^removeElementSolution]:代码随想录-27移除元素：[https://programmercarl.com/0027.移除元素.html#思路](https://programmercarl.com/0027.移除元素.html#思路).
[^mmcopiani]:Leetcode-2529 Maximum Count of Positive Integer and Negative Integer: [https://leetcode.com/problems/maximum-count-of-positive-integer-and-negative-integer/](https://leetcode.com/problems/maximum-count-of-positive-integer-and-negative-integer/).
[^rmdfsa]:Leetcode-26 Remove Duplicates from Sorted Array: [https://leetcode.com/problems/remove-duplicates-from-sorted-array/description/](https://leetcode.com/problems/remove-duplicates-from-sorted-array/description/).
[^rlle]:Leetcode-203 Remove Linked List Elements: [https://leetcode.com/problems/remove-linked-list-elements/description/](https://leetcode.com/problems/remove-linked-list-elements/description/).
[^mz]:Leetcode-283 Move Zeroes: [https://leetcode.com/problems/move-zeroes/description/](https://leetcode.com/problems/move-zeroes/description/).
