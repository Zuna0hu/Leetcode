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