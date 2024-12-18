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

```Bash
INIT set
READ nums
SET maximum_len = 0
SET left_index = 0

FOR every num in nums:
    IF the num is NOT IN set:
        ADD the num to set
    ELSE:
        skip

SET sorted_list = sorted version of set

FOR every num in sorted_list:
    IF the subsequence from left index to current num is consecutive: 
        IF the length of current subsequence > maximum_len:
            UPDATE maximum_len
    ELSE:
        SET left_index to current index

RETURN maximum_len 
```

### Steps 4: Divide and Conquer

To solve each subproblem, we can use the steps of problem solving again, but this time it is a smaller and more specific problem.

#### **First Subproblem**: Initialization

```Python
my_set = set()
maximum_len = 0
left_index = 0
```

#### **Second Subproblem**: Push into Set

```Python
my_set = set()
maximum_len = 0
left_index = 0

for num in nums:
    if num not in my_set:
        my_set.add(num)
```

#### **Third Subproblem**: Sort the Set

```Python
my_set = set()
maximum_len = 0
left_index = 0

for num in nums:
    if num not in my_set:
        my_set.add(num)

sorted_list = sorted(my_set)

```

#### **Fourth Subproblem**: Loop Through the Sorted List

```Python
my_set = set()
maximum_len = 0
left_index = 0

for num in nums:
    if num not in my_set:
        my_set.add(num)

sorted_list = sorted(my_set)

for i in range(len(sorted_list)):
    if i - left_index == (sorted_list[i]-sorted_list[left_index]):
        if i - left_index + 1 > maximum_len:
            maximum_len = i - left_index + 1
    
    else:
        left_index = i

return maximum_len
```

### Time and Space Complexity

Time: O(nlogn), n is the length of input list `nums`. It is O(nlogn) because we used the `sorted()` function in Python.

Space: O(n), n is the length of input list `nums`. As in the worst case the set `my_set` will have n elements.

### Result

Runtime: 58 ms, faster than 57.77% of Python3 online submissions for Longest Consecutive Sequence.

Memory Usage: 33.8 MB, less than 20.20% of Python3 online submissions for Longest Consecutive Sequence.


### Optimization

A better solution is to use the following process:

Take `[100, 4, 200, 1, 3, 2]` as an example:

On the axis, it would be like `---- 1, 2, 3, 4 ----- 100 ------ 200 ----`

This process if like my process of drawing a x-axis and note every number that appears in the `nums`, and moving my pen from left to right to count which line segment is the longest, and outputing that length.

But this solution does not create an ordered list to mimic the axis, rather, it just finds the head, aka. the leftmost number of each line segment first, and uses a while loop of keep adding one to the head number to simulate the process of moving the pen from left to right.



```Bash
INIT set
READ nums
SET maximum_len = 0
SET current_len = 0

FOR every num in nums:
    IF the num is NOT IN set:
        ADD the num to set
    ELSE:
        skip

FOR every num in set:
    IF it is the start point of a line segment:
        WHILE it is still at the set:
            ADD one to the num
        calculate the length
        IF the current length > maximum_len:
            UPDATE maximum_len
    ELSE:
        skip

RETURN maximum_len 
```
To find the head, aka. the leftmost number of each line segment, we just need to check if the number to the left of it `num-1` is in the set. If not, it means it is a start point of a line segment.

The implementation is like:

```Python
maximum_len = 0
my_set = set(nums)

for i in my_set:
    if (i-1) not in my_set:
        current_len = 1
        while (i + current_len) in my_set:
            current_len += 1
        maximum_len = max(maximum_len, current_len)

return maximum_len
```

- **Complexity**:

Time: O(n), n is the length of `nums`, as every element in `nums` will at most be visited twice, once to check if it is the start point, the other time - only if it is part of the line segment - it will be checked if it is in `my_set`.

Space: O(n), n is the length of `nums`, as in the worst case every number in `nums` will be stored in `my_set`.

- **Result**:

Runtime: 31 ms, faster than 99.23% of Python3 online submissions for Longest Consecutive Sequence.

Memory Usage: 34.2 MB, less than 15.77% of Python3 online submissions for Longest Consecutive Sequence.