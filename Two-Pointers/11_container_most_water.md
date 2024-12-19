# Leetcode 11: Container with Most Water

## Link

[Leetcode](https://leetcode.com/problems/container-with-most-water/)

## Problem

You are given an integer array `heights` where `heights[i]` represents the height of the **ith** bar.

You may choose any two bars to form a container. Return the maximum amount of water a container can store.

- **Example 1**:

Input: `[1, 7, 2, 5, 4, 7, 3, 6]`

Ouput: `36`

Explanation: The container with most water is composed of bar `7` and `6`, the volume of storage is `6 * 6 = 36`


- **Example 2**:

Input: `[2, 2, 2]`

Ouput: `4`

Explanation: The container with most water is composed of first bar `2` and last bar `2`, the volume of storage is `2 * 2 = 4`

## Solving Process

### Step 1: Understand the Problem

**Reword it:** 

Write a program that, given an input list, for every two possible indexes a and b (assuming a < b) , outputs the `max( min(heights[a], heights[b]) * (b - a) )`.

### Step 2: Plan

- **Sketch User Interface**: Does your program have a user interface, what will it look like and what functionality will it have? **Our solution will be run on Leetcode, so we don't need to implement a user interface.**

- **Inputs**: What inputs your program has and the source of those inputs. **The input will be a list of integer numbers in Python.**

- **Output**: What are the desired outputs? **The desired output is an integer that represents the value of `max( min(heights[a], heights[b]) * (b - a) )` for all the combinations of `(a,b)`.**

- **Between Inputs and Outputs**: What are the necessary steps? Write out an algorithm (Pseudocode) to solve the problem.

### Step 3: Pseudocode

If we try every combination with brute force, it will certainly be a O(n^2) solution.
