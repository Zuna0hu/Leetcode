# Leetcode 128: Longest Consecutive Sequence

## Link

[Leetcode](https://leetcode.com/problems/longest-consecutive-sequence/)

## Problem

Given an array of integers `nums`, return the **length** of the longest consecutive sequence of elements that can be formed.

A consecutive sequence is a sequence of elements in which each element is exactly 1 greater than the previous element. The elements do not have to be consecutive in the original array.

You must write an algorithm that runs in O(n) time.

- **Example 1**:

```Bash
Input: nums = [2,20,4,10,3,4,5]

Output: 4
```

Explanation: The longest consecutive sequence is `[2, 3, 4, 5]`.

- **Example 2**:

```Bash
Input: nums = [0,3,2,5,4,6,1,1]

Output: 7
```

Explanation: The longest consecutive sequence is `[0, 1, 2, 3, 4, 5, 6]`.

## Solving Process

### Step 1: Understand the Problem

**Reword it:** 

Write a program that, given an input list, outputs the length of its longest subset that is consecutive, like `[1, 2, 3, 4, 5]`.

### Step 2: Plan

- **Sketch User Interface**: Does your program have a user interface, what will it look like and what functionality will it have? **Our solution will be run on Leetcode, so we don't need to implement a user interface.**

- **Inputs**: What inputs your program has and the source of those inputs. **The input will be a list of integer numbers in Python.**

- **Output**: What are the desired outputs? **The desired output is an integer that represents the length of the subset list. Each element in the subset is a number from the input list and it follows a consecutive order.**



- **Between Inputs and Outputs**: What are the necessary steps? Write out an algorithm (Pseudocode) to solve the problem.


### Step 3: Pseudocode

It is like what I would do with paper and pen. I would draw a x-axis and note every number that appears in the `nums`, and moving my pen from left to right to count which line segment is the longest, and output that length.

```Bash
SET dictionary
READ nums
SET maximum_num = nums[0], minimum_num = nums[0]
SET maximum_len = 0
SET left_point, right_point

FOR every num in nums:
    IF the num is NOT IN dictionary:
        ADD the num to dictionary
    ELSE:
        skip
    IF the num > maximum_num:
        maximum_num = num
    IF the num < minimum_num:
        minimum_num = num

left_point = minimum_num

FOR every num in range from minimum_num to maximum_num:
    IF the num is IN dictionary:
        right_point = num
        IF right_point - left_point + 1 > maximum_len:
            maximum_len = right_point - left_point
    ELSE:
        left_point = num + 1

RETURN maximum_len 
```

But because the range from `minimum_num` to 'maximum_num' can be from -10^9 to 10^9 (`-10^9 <= nums[i] <= 10^9`), so this loop can take way longer time than `For every num in nums`, as `0 <= nums.length <= 1000`.

So instead of traversing on the x-axis, it might be a better idea to just traverse on the `dictionary`. We can also use a `set` in place of `dictionary`.