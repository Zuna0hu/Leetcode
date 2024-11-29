# Leetcode 238: Product of Array Except Self

## Link
[Leetcode](https://leetcode.com/problems/product-of-array-except-self/)

# Problem
Given an integer array `nums`, return an array `output` where `output[i]` is the product of all the elements of `nums` except `nums[i]`.

Each product is guaranteed to fit in a 32-bit integer.

## Idea

### Idea 1: Get the Product of Every Element Then Divide


## Solution

### Solution 1

### Time and Space Complexities of Solution 1
Time: O()

Space: O()


## Wrong Solutions

### Wrong Solution 1

```Python
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        product = 1
        output = []
        for num in nums:
            product *= num

        for i in range(len(nums)):
            output[i] = product / nums[i]


        return output 
```
Reason: In Python, a list must have elements already present to allow assignment at specific indices. You can only assign to indices that already exist.

If a list is empty, there are no valid indices to assign values to, which causes the "IndexError: list assignment index out of range." 

If the index you try to assign to is out of the current bounds of the list, you'll get an IndexError.
---
Using `.append()` or pre-initializing the list avoids this issue.

```Python
for num in nums:
    output.append(product / num)
```
---
Or:
```Python
output = [0] * len(nums)  # Pre-initialize output with zeros
```
