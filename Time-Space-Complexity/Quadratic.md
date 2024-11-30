# How to Judge if an Algorithm is Quadratic

## General Concept of Quadratic Time Complexity

An algorithm is considered quadratic if the total number of operations grows at a rate proportional to the square of the size of the input. This typically occurs when the algorithm involves nested loops or repetitive operations that scale based on the input size. The time complexity of such an algorithm is often \( O(n^2) \), but the space complexity can vary depending on how the algorithm stores or manipulates data.

### Key Indicators of Quadratic Time Complexity

1. **Nested Loops**: If the algorithm has two nested loops where each loop iterates over the entire input, the time complexity is often quadratic. For example:
    - The outer loop runs `n` times.
    - The inner loop runs `n` times for each iteration of the outer loop.
    - In total, the number of operations would be proportional to \( n \times n \), resulting in \( O(n^2) \).

2. **Increasing Size of Operations**: If the size of each operation increases as the algorithm progresses, this can also lead to quadratic time complexity. For example, appending to a growing structure, such as a string or list, where each append operation becomes progressively more expensive because the size of the structure itself grows over time.

### Example of Quadratic Growth:

Suppose you have a process where each step involves working with an increasing portion of the input. The total number of operations would be the sum of a series like:

\[
O(n) + O(n+1) + O(n+2) + \dots + O(n+k)
\]

If this series grows as a sum of increasing numbers, it typically results in a quadratic time complexity, where the total operations are proportional to the square of the size of the input. The complexity in such a case is \( O(n^2) \).

### Time Complexity with Bounded Input

If there is a bounded upper limit on the size of each string or operation (e.g., the length of each string is between 1 and 100), the time complexity can still be considered \( O(n^2) \). This is because the number of operations grows proportionally to \( n^2 \), but the constant factor (due to the fixed upper limit on the string length) does not change the quadratic nature of the overall time complexity.

For example, if the string lengths are bounded between 1 and 100, the time complexity remains \( O(n^2) \), since each concatenation operation still requires copying increasing portions of the string in a nested manner.

### Formalizing with the Squeeze Theorem

We can formalize the time complexity analysis by comparing the series of operations with two other series. Consider the total cost of all concatenations:

\[
O(l1) + O(l1+l2) + O(l1+l2+l3) + \dots + O(l1+l2+\dots+ln)
\]

Where \( l1, l2, \dots, ln \) are the lengths of the strings. This series grows incrementally, but we can bound it between two other series:

1. The lower bound: \( O(1) + O(2) + \dots + O(k') \), where \( k' \) is the number of operations, which grows at least linearly.

2. The upper bound: \( O(100) + O(200) + \dots + O(k'') \), where \( k'' \) is the largest value that the operation length can take (e.g., 100 in your case).

Both of these upper and lower bounds grow as \( O(k^2) \), where \( k \) is the total length of the strings processed. Using the **Squeeze Theorem**, if the series lies between two other series that are both \( O(k^2) \), we can conclude that the overall complexity is also \( O(k^2) \).

Thus, even though the string lengths are bounded (e.g., between 1 and 100), the time complexity remains \( O(n^2) \), as the operations still grow quadratically in terms of the number of strings.

## Space Complexity

While time complexity is typically \( O(n^2) \) in quadratic algorithms, space complexity depends on how the algorithm stores intermediate data or results. For example, if the algorithm stores data in an additional list or array, the space complexity could be \( O(n) \), \( O(n^2) \), or even higher, depending on the structure used. However, if each string's length is bounded (e.g., between 1 and 100), the space complexity is usually manageable and could remain linear or slightly higher, based on the number of strings and their length.

## Conclusion

To determine if an algorithm is quadratic:
- **Time complexity**: If the number of operations grows as the square of the input size, it is \( O(n^2) \). Even with an upper limit on string length, the quadratic growth still holds.
- **Space complexity**: Can vary depending on how data is stored and manipulated. In cases where string length is bounded, space complexity may remain manageable, typically \( O(n) \) or higher depending on the data structure used.
- By applying the **Squeeze Theorem**, we see that the series of operations grows at a rate consistent with \( O(n^2) \), even when the string lengths are bounded.
