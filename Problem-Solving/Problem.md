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

---

## Additional points from Richard Reis
[Link] (https://www.freecodecamp.org/news/how-to-think-like-a-programmer-lessons-in-problem-solving-d1d8bf1de7d2/)

### When Dividing

Do not try to solve one big problem. Instead, break it into sub-problems. These sub-problems are much easier to solve.

Then, solve each sub-problem one by one. Begin with the simplest. Simplest means **you know the answer** (or are closer to that answer). Besides, being simplest means this sub-problem being solved doesn’t **depend on** others being solved.

Once you solved every sub-problem, connect the dots.Connecting all your “sub-solutions” will give you the solution to the original problem. 

This technique is a cornerstone of problem-solving. Remember it (read this step again, if you must).

### An Important Quote about Reducing Problems

“If I could teach every beginning programmer one problem-solving skill, it would be the ‘**reduce the problem** technique.’

For example, suppose you’re a new programmer and you’re asked to write a program that reads ten numbers and figures out which number is the third highest. For a brand-new programmer, that can be a tough assignment, even though it only requires basic programming syntax.

If you’re stuck, you should reduce the problem to something simpler. Instead of the **third-highest** number, what about finding the **highest overall**? Still too tough? What about finding the largest of just three numbers? **Or the larger of two**?

Reduce the problem to the point where **you know how to solve it** and write the solution. Then **expand** the problem slightly and rewrite the solution to match, and keep going until you are back where you started.” — V. Anton Spraul

### What to do When Stuck

- **Take a Deep Breath**: First off, take a deep breath. Second, that’s fair. Don’t worry though, friend. This happens to everyone!

The difference is the best programmers/problem-solvers are more curious about bugs/errors than irritated.

- **Debug**: Go step by step through your solution trying to find where you went wrong. Programmers call this debugging (in fact, this is all a debugger does).

“The art of debugging is figuring out what you really told your program to do rather than what you thought you told it to do.”” — Andrew Singer

- **Reassess**: Take a step back. Look at the problem from another perspective. Is there anything that can be abstracted to a more general approach?

“Sometimes we get so lost in the details of a problem that we overlook **general principles** that would solve the problem at a more general level. […]

The classic example of this, of course, is the summation of a long list of consecutive integers, 1 + 2 + 3 + … + n, which a very young Gauss quickly recognized was simply n(n+1)/2, thus avoiding the effort of having to do the addition.” — C. Jordan Ball

Sidenote: Another way of reassessing is starting anew. **Delete everything and begin again with fresh eyes.** I’m serious. You’ll be dumbfounded at how effective this is.

- **Research**: Ahh, good ol’ Google. You read that right. No matter what problem you have, someone has probably solved it. Find that person/ solution. In fact, do this even if you solved the problem! (You can learn a lot from other people’s solutions).
Caveat: Don’t look for a solution to the big problem. **Only look for solutions to sub-problems.** Why? Because unless you struggle (even a little bit), you won’t learn anything. If you don’t learn anything, you wasted your time.

### Always Practice

Don’t expect to be great after just one week. If you want to be a good problem-solver, solve a lot of problems!

Practice. Practice. Practice. It’ll only be a matter of time before you recognize that “this problem could easily be solved with .”

- **How to Practice**

There are options out the wazoo!

Chess puzzles, math problems, Sudoku, Go, Monopoly, video-games, cryptokitties, bla… bla… bla….

In fact, a common pattern amongst successful people is their habit of practicing “micro problem-solving.” For example, Peter Thiel plays chess, and Elon Musk plays video-games.

“Byron Reeves said ‘If you want to see what business leadership may look like in three to five years, look at what’s happening in online games.’

Fast-forward to today. Elon [Musk], Reid [Hoffman], Mark Zuckerberg and many others say that games have been foundational to their success in building their companies.” — Mary Meeker (2017 internet trends report)

- **Does This Mean You Should Just Play Video-games**

Not at all. But what are video-games all about? That’s right, problem-solving!

So, what you should do is find an outlet to practice. Something that allows you to solve many micro-problems (ideally, something you enjoy).

For example, I enjoy coding challenges. Every day, I try to solve at least one challenge (usually on Coderbyte).

Like I said, all problems share similar patterns.

- **Life is Problems and They Make Life Interesting**
“Just when you think you’ve successfully navigated one obstacle, another emerges. But that’s what keeps life interesting.[…]

Life is a process of breaking through these impediments — a series of fortified lines that we must break through.

Each time, you’ll learn something.

Each time, you’ll develop strength, wisdom, and perspective.

Each time, a little more of the competition falls away. Until all that is left is you: the best version of you.” — Ryan Holiday (The Obstacle is the Way)