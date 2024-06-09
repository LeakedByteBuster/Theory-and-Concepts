# Index
- [Complexity](#complexity)
  - [Type Of Complexity](#type-of-complexity)
  - [Calculation Of Complexity](#calculation-of-complexity)
  - [SalesMan Problem O(n!)](#salesman-problem-o(n!))

# Complexity

## Type Of Complexity

| Big O Notation | Name          | Example                                           |
|----------------|---------------|---------------------------------------------------|
| O(1)           | Constant      |                                                   |
| O(log n)       | Logarithmic   |                                                   |
| O(n)           | Linear        | Find max element in an unsorted array             |
| O(n log n)     | Linearithmic  | Merge sort                                        |
| O(n^2)         | Quadratic     | Bubble sort                                       |
| O(n^3)         | Cubic         |                                                   |
| O(2^n)         | Exponential   | Find all subsets                                  |
| O(n!)          | Factorial     | Find all permutations of a given set/string       |

## Important Constants

- 1 nanosecond = 0.0000000001 seconds

## Types of Complexity: P vs NP

### Polynomial Complexity (P)
- Problems that can be solved in reasonable time.

### Non-Polynomial Complexity (NP)
- Problems that cannot be solved in reasonable time (e.g., O(n!), O(2^n)).
  - Execution time of an instruction: 10 nanoseconds
  - Example: n = 50
    - O(n!)  ==> Time Of Execution: 10^48 years
    - O(n^2) ==> Time Of Execution: 130 days (for n = 250, it would be 10^59 years)

## Calculation Of Complexity

### 1. Rule: Base Operations
- Quantify the number of base operations such as:
  - Arithmetic operations (+, >, *, &&...)
  - Assignment operations (x <- 10)
  - Condition checks
  - Read/Write operations
- Each operation has a constant complexity, O(1).

### 2. Rule: Loops
- The complexity of a loop is the complexity of its body times the number of iterations.

```java
while ((i <- 1) < n) {         // Assignment ==> O(1)
    print "write a number:";   // Writing    ==> O(1)
    read 'a';                  // Reading    ==> O(1)
    print ("a x i", a * i);    // Writing    ==> O(1), Multiplication ==> O(1)
}
```
- The complexity of this while if equal to O(5n) // (O(1) + O(1) + O(1) + O(1) + O(1)) * Number of iterations (n)

### 3. Rule: Conditions

- The complexity of a condition is equal to the complexity of the condition check O(1) plus the maximum complexity between 'then' and 'else' (considering the worst case where the most instructions are executed).

```java
if (n < 5) {                  // Condition ==> O(1)
    write "hey";              // Writing   ==> O(1)
} else {                      // Complexity of the while loop = O(3n)
    while ((i <- 1) < n) {    // Assignment ==> O(1), Condition O(1)
        write "hey";          // Writing    ==> O(1)
    }
}
```
- The complexity of this condition = O(1) + MAX(O(1), O(3n)) = O(3n + 1) ==> O(n)

### 4. Rule: Sequence of Instructions

- The complexity of two blocks of instructions is equal to the maximum of their complexities.
  - For example, considering the while and if statements above:
    - MAX(O(5n), O(3n + 1)) = O(5n)

### 5. Rule: Asymptotic Analysis

- The complexity of an algorithm is determined by its asymptotic performance in the worst case.
  - Asymptotic analysis focuses on large data sets, ignoring constants and lower-order terms.

  - Multiplicative constants are replaced with one: 3n ==> n
  - Additive constants are ignored: n + 1000 ==> n
  - The largest terms are conserved: n^2 + n ==> n^2
 
### Example :

#### Normal :
  - O(3n + n^2 + 5) ==> O(1n + n^2 + 1) ==> O(n + n^2) ==> O(n^2)
  - O(1) + O(1) + O(1) + O(3n) + O(2n) = O(5n + 3) ==> O(n)

### Nested While :
  - O(1) + O(1) + O(1) + 3n^2 + 1 + 3n^2 = O(6n^2 + 4) ==> O(n^2)
  - (1 + 1 + 1) * n * n (nested while) = 3n^2

### Logarithm :
  - Given a while in which i increments by i*2 (1, 2, 4, 8...)
 ```c
  while (i < n) { write 'a'; i*2; }
```
  - (1 + 1 + 1) * (1 + log2(n)) = O(3(1+log2(n))) = O(3 + 3log2(n)) ==> O(log(n))

### Linearithmetic :
 ```c
  while(i < n) {while(j < n){write 'a'; write 'b'; j*4;} i++;}
```
  Inner	- (1 + 1 + 1 + 1) * (1 + log4(n)) = O(4(1 + log4(n))) = O(4 + 4log4(n)) ==> O(log(n))
  Outter	- O(log(n)) * 1n ==> O(n log(n))

### Recursive functions :
  - The goal here is to know how many times the functions will call itself.
```c
    Type	fn(n)
    {
      if (n <= 0)
        return 1;
      else
        return fn(n - 1) + fn(n - 2)
    }
```
   - Since the tree of this function will not be balenced the time complexity is
    O(2^n + c) ==> O(2^n)
   - In case the tree is balenced, there is no need to add or remove a constant. so, the complexity will be
    O(2^n)

## SalesMan Problem O(n!)

Let's say for example we wanna find the ways to visit n cities. ((n - 1)! / 2)


| Nbr of cities (n)	|	Nbr of ways (temps) |
--------------------|--------------------|
|  3				|	1 |
|  4				|	3 |
|  5				|	12 |
|  6				|	60 |
|  10				|	181440 |
|  20				|	6.08 * 10 ^ 16 |
|  64				|	9.91 * 10 ^ 86 |

- The time complexity is defined by the size of the input (n) using the big notation (n).

  - We use big notation 'O' to classify algorithms based on their time of execution, as progressively the size of n increses.
  - the function O reprensents the rate growth in the worst case based on the size of input.
    - 'Omega' ==> Best case
    - 'Theta' ==> Average case
    - 'O'	  ==> Worst case

- Factorial algorithm is the worst algorithm, it is worst than exponential algorithm.


**If number of inputs doesn't change, the complexity of your algorithm doesn't change**
