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

## Hypothesis: Upper Limit of Operations

In many real-world cases, the growth of the number of operations is limited. Specifically, the total number of operations might not increase indefinitely. If there is an upper limit on the size of operations (for example, the length of the strings being processed), this can influence the time complexity.

### Bounded Operations:

If each operation grows but has an upper bound, the algorithm may appear to be quadratic based on the operations but is constrained to a linear or logarithmic growth due to the limit on the size of each step.

For instance, if the number of elements or size of each operation has an upper limit, the algorithm might run in \( O(n) \) or \( O(n \log n) \), even if the algorithm involves nested iterations or growing operations.

## Space Complexity

While time complexity is typically \( O(n^2) \) in quadratic algorithms, space complexity depends on how the algorithm stores intermediate data or results. For example, if the algorithm stores data in an additional list or array, the space complexity could be \( O(n) \), \( O(n^2) \), or even higher, depending on the structure used. If only a small amount of space is used for temporary variables, the space complexity might be much lower.

## Conclusion

To determine if an algorithm is quadratic, observe:
- If the algorithm involves nested operations or operations that grow larger with each iteration.
- If the total number of operations grows as the square of the size of the input (time complexity is \( O(n^2) \)).
- Be mindful of the hypothesis that each operation or operation size might have an upper limit, which can impact whether the algorithm truly exhibits quadratic complexity.
- Space complexity can vary, depending on how the algorithm stores or manipulates data.
