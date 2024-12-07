# Leetcode 238: Product of Array Except Self

## Link
[Leetcode](https://leetcode.com/problems/product-of-array-except-self/)

## Problem
Given an integer array `nums`, return an array `output` where `output[i]` is the product of all the elements of `nums` except `nums[i]`.

Each product is guaranteed to fit in a 32-bit integer.


## Solving Process

### Step 1: Understand the Problem
**Reword it:** 

Write a program that goes through an integer array, calculate the product of all elements in that array except the current one. And push the results into another array.

### Step 2: Plan

- **Sketch User Interface**: Does your program have a user interface, what will it look like and what functionality will it have? **Our solution will be run on Leetcode, so we don't need to implement a user interface.**

- **Inputs**: What inputs your program has and the source of those inputs. **The input will be a list of integer numbers in Python.**

- **Output**: What are the desired outputs? **The desired output is a list of integer numbers. Each number in the output list will be the product of all elements in the input list except the input number that has the same index.**

- **Between Inputs and Outputs**: What are the necessary steps? Write out an algorithm (Pseudocode) to solve the problem.

### Step 3: Pseudocode

```Bash
Set the initial product as one
Initialize the output list
Run through the input list:
    for the current element, calculate the product of elements on the left, if there is element on the left

    calculate the product of elements on the right, if there is element on the right

    get the corresponding product by multiplying the left product and right product

    push the product into answer array
return answer array
```

### Steps 4: Divide and Conquer

#### **First Subproblem**: Set Initial Product
```Python
def productExceptSelf(self, nums: List[int]) -> List[int]:
    product = 1
```

#### **Second Subproblem**: Initialize the Output List
```Python
def productExceptSelf(self, nums: List[int]) -> List[int]:
    product = 1
    ans = []
```

#### **Third Subproblem**: Run Through the Input List
```Python
def productExceptSelf(self, nums: List[int]) -> List[int]:
    product = 1
    ans = []
    for num in nums:
```

#### **Fourth Subproblem**: Get the Left Products

If for each element, we need to run through the array to calculate its left product, its time complexity will be O(0+1+2+...+ (n-1)) = O(n^2), where n is the number of elements in the input list.

Therefore, we need to think of how to implement getting the left products with time complexity of O(n) or less.

Try mimic the process of getting the left product of every element in `[-1,0,1,2,3]` using pen(cil) and paper.

The left product array should be `[1,-1,0,0,0]`.

By exprimenting the mathematical process on paper, I realized we can create the list of left products by running through the input list once. 


Pseudocode:

```Bash
Initialize the product as one
Initialize a empty list to put left products
Run through the input array:
    if it is the first element:
        there is no need to multiply, just push one
        and multiply product by the element
    if it is not the first element:
        push the product
        multiply the product by the element
```
To implement it:

```Python
def productExceptSelf(self, nums: List[int]) -> List[int]:
    product = 1
    ans = []
    for num in nums:
```









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
