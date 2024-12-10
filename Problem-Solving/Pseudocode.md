# Pseudocode

## What is Pseudocode

Pseudocode in data science or web development is a technique used to describe the distinct steps of an algorithm in a way that’s easy for anyone with basic programming knowledge to understand.

We use pseudocode in various fields of programming, whether it be app development, data science or web development. Pseudocode is a technique used to describe the distinct steps of an algorithm in a manner that’s easy to understand for anyone with basic programming knowledge. 

Although pseudocode is a syntax-free description of an algorithm, it must provide a full description of the algorithm’s logic so that moving from pseudocode to implementation is merely a task of translating each line into code using the syntax of any given programming language.

### Main Constructs of Pseudocode

Constructs are also called keywords, which are used to describe the control flow of the algorithm.

It is a good practice to include those constructs in uppercase in your pseudocode to make them more noticeable.

- **SEQUENCE**: For linear tasks sequentially performed one after another, we can use the following keywords:

Input: `READ`, `OBTAIN`, `GET`

Ouput: `PRINT`, `DISPLAY`, `SHOW`

Compute: `COMPUTE`, `CALCULATE`, `DETERMINE`

Initialize: `SET`, `INIT`

Add: `INCREMENT`, `BUMP`

Sub: `DECREMENT`


- **WHILE**: A loop with the condition at its beginning.

General structure:

```Bash
WHILE condition
sequence
ENDWHILE
```

Example: Printing numbers from 1 to 5

```Bash
SET counter TO 1
WHILE counter <= 5
    OUTPUT counter
    INCREMENT counter
ENDWHILE

```


---

- **REPEAT-UNTIL**: A loop with the condition at the bottom.

General structure:

```Bash
REPEAT
sequence
UNTIL condition

```

Example: Asking for the correct password

```Bash
REPEAT
    READ password
UNTIL password = "correct_password"
PRINT "Access Granted"
```

---

- **FOR**: Another way of looping.

General structure:

```Bash
FOR iteration bounds
sequence
ENDFOR
```

Example: Checking if a number is positive or negative

```Bash
GET number
IF number >= 0 THEN
    PRINT "Positive Number"
ELSE
    PRINT "Negative Number"
ENDIF
END
```

---

- **IF-THEN-ELSE**: A conditional statement changing the flow of the algorithm.

General structure:

```Bash
IF condition THEN
    sequence 1
ELSE
    sequence 2
ENDIF
```

Example: 

```Bash
GET number
IF number >= 0 THEN
    PRINT "Positive Number"
ELSE
    PRINT "Negative Number"
ENDIF

```

---

- **CASE**: The generalization form of `IF-THEN-ELSE`. 

General structure:

```Bash
CASE expression OF
    condition 1:
        action for condition 1
    condition 2:
        action for condition 2
    ...
    DEFAULT:
        action if no conditions match
ENDCASE
```
Example:

```Bash
CASE score OF
    90 TO 100:
        OUTPUT "Grade A"
    80 TO 89:
        OUTPUT "Grade B"
    70 TO 79:
        OUTPUT "Grade C"
    BELOW 70:
        OUTPUT "Grade F"
ENDCASE

```

## How to write Pseudocode
1. Always capitalize the initial word (often one of the main six constructs).

2. Make only one statement per line.

3. Indent to show hierarchy, improve readability and show nested constructs.

4. Always end multi-line sections using any of the END keywords (ENDIF, ENDWHILE, etc.).

5. Keep your statements programming language independent. Pseudocode should not use the syntax, specific keywords, or conventions tied to a particular programming language.

6. Use the naming domain of the problem, **not that of the implementation**. For instance: “Append the last name to the first name” instead of “name = first+last.”

7. Keep it simple, concise and readable.