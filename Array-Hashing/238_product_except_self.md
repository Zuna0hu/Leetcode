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

I thought of getting the product of every element first, then divide by each element.

```Bash
Set the initial product as one
Initialize the output list
Run through the input list:
    multiply initial product by the current element
Run through the input list:
    divide the product by the current element
    push the quotient into output list
return output array
```
This would be a solution with O(n) time complexity. But for the example input of `[-1,0,1,2,3]`, this will not work because a number will be divided by 0.

So instead, we can use (sub)product on the left side and (sub)product on the right side, and multiply them together:

```Bash
Set the initial product as one
Initialize the output list
Run through the input list:
    for the current element, calculate the product of elements on the left, if there is element on the left

    calculate the product of elements on the right, if there is element on the right

    get the corresponding product by multiplying the left product and right product

    push the product into output array
return output array
```

### Steps 4: Divide and Conquer

To solve each subproblem, we can use the steps of problem solving again, but this time it is a smaller and more specific problem.

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
Run through the input array from left to right:
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
    
    ans = [] # final answer
    
    left_product = 1
    left_arr = []

    for i in range(len(nums)):
        if i == 0:
            left_arr.append(1)
            left_product*=nums[i]
        else:
            left_arr.append(left_product)
            left_product*=nums[i]
    # now we get left products
```
#### **Fifth Subproblem**: Get the Right Products

Similar to getting the left products, we can experiment the mathematical processes of getting the right products of list `[-1,0,1,2,3]`.

The result list should be `[0,6,6,3,1]`.

We can know that for the right-most element, its right product will be one. By traversing the input list from right to left one, we can get the right products. And the time complexity will also be O(n).

Pseudocode:

```Bash
Initialize the product as one
Initialize a empty list to put right products
Run through the input array from right to left:
    if it is the last element:
        there is no need to multiply, just push one
        and multiply product by the element
    if it is not the last element:
        push the product to the left of output list
        multiply the product by the element
```
To implement it:

```Python
def productExceptSelf(self, nums: List[int]) -> List[int]:
    
    ans = [] # final answer
    
    left_product = 1
    left_arr = []

    right_product = 1
    right_arr = []

    # get left products
    for i in range(len(nums)):
        if i == 0:
            left_arr.append(1)
            left_product*=nums[i]
        else:
            left_arr.append(left_product)
            left_product*=nums[i]

    # get right products
    for i in range(len(nums)-1,-1,-1): # len(nums) has upper limit, so the process of getting len(nums) can be considered O(1)
        if i == len(nums)-1:
            right_arr.append(1)
            right_product*=nums[i]
        else:
            right_arr.insert(0,left_product) # len(nums) has upper limit, so this step can be considered O(1)
            right_product*=nums[i]
```
#### **Sixth Subproblem**: Multiply Left and Right Products

For this subproblem, we need to multiply each element in the left product list and each corresponding element in the right product list, and put those results into a list.

Now that we have `left_arr` and `right_arr` as inputs.

For example, for `input = [-1,0,1,2,3]`

`left_arr = [1,-1,0,0,0]`

`right_arr = [0,6,6,3,1]`

The result arr should be:

`result_arr = [0,-6,0,0,0]`

This can be done in a simple traversing process by multiplying the elements with the same index.

Pseudocode:

```Bash
Run through left array:
    multiply the current element in left array with the corresponding element in right array
    push the product into the result array
```

Implementation:

```Python
def productExceptSelf(self, nums: List[int]) -> List[int]:
    
    ans = [] # final answer
    
    left_product = 1
    left_arr = []

    right_product = 1
    right_arr = []

    # get left products
    for i in range(len(nums)):
        if i == 0:
            left_arr.append(1)
            left_product*=nums[i]
        else:
            left_arr.append(left_product)
            left_product*=nums[i]

    # get right products
    for i in range(len(nums)-1,-1,-1): # O(1), constant-time operation because Python stores the length of lists internally as metadata.
        if i == len(nums)-1:
            right_arr.append(1)
            right_product*=nums[i]
        else:
            # right_arr.insert(0,right_product) # O(n)
            right_arr.append(right_product)
            right_product*=nums[i]
    
    # reverse it
    right_arr.reverse() # O(n)
    
    # get the answer        
    for i in range(len(nums)):
        ans.append(left_arr[i]*right_arr[i])

    # return output array
    return ans
```

Now it is finished!

### Time and Space Complexity

Time: O(n)
Space: O(n)

