# Time and Space Complexity Analysis




Output Data
Time Complexity: The time to produce the output is not generally considered in Big O notation, unless the time grows with the input size.

Output data is typically ignored unless it is proportional to the input size. If the output is directly tied to the input size, such as generating an array of the same size, it is included in the space complexity calculation.

You can use [this tutorial by freecodecamp](https://www.freecodecamp.org/news/big-o-cheat-sheet-time-complexity-chart/) and [this article](https://medium.com/@DevChy/introduction-to-big-o-notation-time-and-space-complexity-f747ea5bca58) as references.

## What is Time Complexity

An algorithm's time complexity specifies how long it will take to execute an algorithm **as a function of its input size**. 

Time complexity measures the additional time an algorithm requires as the input size grows. It does not concern itself with the actual runtime (e.g., seconds) but how the time increases relative to the input size. The time complexity expresses how the execution time grows based on the input size.

For example, an algorithm that processes every item in a list takes O(n) time, where n is the size of the input (list).

---

- **Input and Output**:

We don't include the time required to **input** the data itself. Time complexity only focuses on how the time grows as the algorithm processes the input.

The time to produce the **output** is **not** generally considered in Big O notation, unless the time grows with the input size.

## What is Space Complexity

Similarly, an algorithm's space complexity specifies the total amount of space or memory required to execute an algorithm **as a function of the size of the input**.

Space complexity measures the **additional** memory or storage an algorithm needs as the input size grows. Like time complexity, it does not account for the memory already used by the input itself but focuses on the extra memory the algorithm requires to perform its task.

For example, an algorithm that creates an extra array of size n takes O(n) space. If an algorithm uses only a fixed number of variables regardless of input size, it takes O(1) space (constant space).

---

- **Input and Output**:

We don't include the memory used by the **input** itself. Space complexity focuses on how much additional memory is required for the algorithm’s execution beyond the input.

**Output data** is typically **ignored** unless it is proportional to the input size. If the output is directly tied to the input size, such as generating an array of the same size, it is included in the space complexity calculation.

## What is Big O Notation

Big O, also known as Big O notation, represents an algorithm's **worst-case** complexity. It uses algebraic terms to describe the complexity of an algorithm.

Big O notation for time complexity does not account for fixed or constant time factors; it focuses only on how time increases with the input size.

Big O defines the runtime required to execute an algorithm by identifying how the performance of your algorithm will change as the input size grows. But it does not tell you how fast your algorithm's runtime is.

Big O notation measures the efficiency and performance of your algorithm using time and space complexity.