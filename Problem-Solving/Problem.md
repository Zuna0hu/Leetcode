# Problem Solving
This .md is based on the tutorial given by [Odin Project] (https://www.theodinproject.com/lessons/foundations-problem-solving)

## Best Way to Improve Problem Solving
The best way to improve your problem solving ability is by building experience by making lots and lots of programs. The more practice you have the better you’ll be prepared to solve real world problems.

It is a good strategy to use the following steps in the problem solving process.

## Steps to Solve the Problem

### Step 1: Understand the Problem
To gain clarity and understanding of the problem, write it down on paper, reword it in plain English until it makes sense to you, and draw diagrams if that helps. When you can explain the problem to someone else in plain English, you understand it.

If you don’t understand the problem, you won’t know when you’ve successfully solved it

### Step 2: Plan
- **Sketch User Interface**: Does your program have a user interface, what will it look like and what functionality will it have?
- **Inputs**: What inputs your program has and the source of those inputs.
- **Output**: What are the desired outputs?
- **Between Inputs and Outputs**: What are the necessary steps? Write out an algorithm (Pseudocode) to solve the problem.

### Step 3: Pseudocode
Pseudocode is writing out the logic for your program in natural language instead of code. 

Example:

```Bash
When the user inputs a number
Initialize a counter variable and set its value to zero
While counter is smaller than user inputted number increment the counter by one
Print the value of the counter variable
```

### Steps 4: Divide and Conquer
Break the big problem down and solve each of the smaller problems until you’ve solved the big problem.

Each of the steps in the algorithm we wrote out in the last section are subproblems.

Getting started with and solving one of the subproblems you have identified in the planning stage often reveals the next subproblem you can work on, so it is okay if the initial algorithm is incomplete.

Don't try to solve the problem in one go. If the problem is sufficiently complex, you’ll get yourself tied in knots. Decomposing problems is a better strategy.

---

## Example

### Problem Description
Link: [Leetcode Problem 412] (https://leetcode.com/problems/fizz-buzz/description/)

Given an integer `n`, return a string array `answer` (1-indexed) where:

`answer[i] == "FizzBuzz"` if `i` is divisible by `3` and `5`.

`answer[i] == "Fizz"` if `i` is divisible by `3`.

`answer[i] == "Buzz"` if `i` is divisible by `5`.

`answer[i] == i` (as a string) if none of the above conditions are true.

### Step 1: Understand the Problem
**Reword it:**

Write a program that allows the user to enter a number, print each number between one and the number the user entered, but for numbers that divide by `3` without a remainder print `Fizz` instead. For numbers that divide by `5` without a remainder print `Buzz` and finally for numbers that divide by both 3 and 5 without a remainder print `FizzBuzz`.

### Step 2: Plan

Does your program have an interface? What will it look like? Our FizzBuzz solution will be a browser console program, so we don’t need an interface. The only user interaction will be allowing users to enter a number.

- **Sketch User Interface**: Does your program have a user interface, what will it look like and what functionality will it have? **Our FizzBuzz solution will be a browser console program, so we don’t need an interface. The only user interaction will be allowing users to enter a number.**

- **Inputs**: What inputs your program has and the source of those inputs. **The user will enter a number from a prompt (popup box).**

- **Output**: What are the desired outputs? **The desired output is a list of numbers from 1 to the number the user entered. But each number that is divisible by 3 will output Fizz, each number that is divisible by 5 will output Buzz and each number that is divisible by both 3 and 5 will output FizzBuzz.**

- **Between Inputs and Outputs**: What are the necessary steps? Write out an algorithm (Pseudocode) to solve the problem.

### Step 3: Pseudocode

```Bash
User enter a number
Count from one to that number:
    if that number divides by 3 without remainder:
        print Fizz
    or if that number divides by 5 without remainder:
        print Buzz
    or if that numbers divides by 15 without remainder, but this should be before judging if it divides by 3 or 5:
        print FizzBuzz
    elsewise print the current number
```

### Steps 4: Divide and Conquer

#### **First Subproblem**: User enter a number

```Python
n = input("What is your number?")
```

#### **Second Subproblem**: Counting from One to that Number
```Python
n = input("What is your number?")
for i in range(1, n+1):
```

#### **Third Subproblem**: Judging if a Number Divides by 3
```Python
n = input("What is your number?")

for i in range(1, n+1):
    if n % 3 == 0:
        print("Fizz")
```

#### **Fourth Subproblem**: Judging if a Number Divides by 5
```Python
n = input("What is your number?")

for i in range(1, n+1):
    if n % 3 == 0:
        print("Fizz")
    elif n % 5 == 0:
        print("Buzz")
```

#### **Fifth Subproblem**: Judging if a Number Divides by 15
```Python
n = input("What is your number?")

for i in range(1, n+1):
    if n % 15 == 0:
        print("FizzBuzz") 
    elif n % 3 == 0:
        print("Fizz")
    elif n % 5 == 0:
        print("Buzz")
```

#### **Sixth Subproblem**: Else
```Python
n = input("What is your number?")

for i in range(1, n+1):
    if n % 15 == 0:
        print("FizzBuzz") 
    elif n % 3 == 0:
        print("Fizz")
    elif n % 5 == 0:
        print("Buzz")
    else:
        print(n)
```

We get the complete code!

#### Time and Space Complexity
- **Time Complexity**: O(n), where n is the inputted number

- **Space Complexity** O(1), if we need to store the results series in a `list`, it would be O(n), where n is the inputted number.