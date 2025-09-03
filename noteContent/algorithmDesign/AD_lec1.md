# Algorithm design

## overview:

in Algorithm design, there are three main aspects

1. **Design Paradigms** – How to come up with algorithms.
2. **Correctness Proof** – How to prove the algorithm is correct.
3. **Complexity Analysis** – How to analyze performance.

### design paredigm:

---

1.  **Brute Force:**

    Enumerate all possible solutions

2.  **Problem Partitioning**

    Break the problem into smaller subproblems.

    -   Divide and Conquer:

        partition a problem of size n into independent subproblems of size ~ n/2.

        -   Example: Merge Sort, Binary Search.

    -   Dynamic Programming:

        partition a problem of size n into overlapping subproblems (often of size n−1) and store results to avoid recomputation.

        -   Example: Fibonacci sequence, Matrix Chain Multiplication.

3.  **Iterative Improvement**

    Start with an initial solution and gradually improve it until reaching an optimal or near-optimal solution.

    -   Greedy Algorithms: make the locally optimal choice at each step, hoping to reach the global optimum.

        -   Example: Huffman Coding, Dijkstra’s Algorithm.

    -   Backtracking:
        build a solution step by step and abandon paths that lead to infeasible or suboptimal solutions.

            - Example: N-Queens Problem, Sudoku Solver.

    -   Randomized Algorithms: use randomness in decision-making or solution exploration.

        -   Example: Randomized QuickSort, Monte Carlo algorithms.

### Correctness Proof

---

to ensure the algorithm always provide correct method

> #### Proof structure:
>
> 1.  define loop invariant
>
> 2.  Structureing written proof
>
> -   initialization
> -   maintenance
> -   termination

### Complexity Analysis

---

Measure efficiency of algorithms.

#### **Complexity Analysis -- Asymptotic Notation**

**Asymptotic Notation**:

> Asymptotic notation is a mathematical tool to describe the growth of functions, especially running time or space usage of algorithms as input size **n** becomes large.
> It helps compare algorithms without focusing on machine or implementation details.

### 1. Big-O Notation (**O**)

-   **Upper bound** (worst-case growth rate).
-   Example: If an algorithm runs in $3n^2 + 2n + 5$, we say its complexity is $O(n^2)$.
    ![big O](data:image/png;base64,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 "big o")

### 2. Big-Omega Notation (**Ω**)

-   **Lower bound** (best-case growth rate).
-   Example: The same algorithm is $\Omega(n^2)$ because it grows at least as fast as $n^2$.
    ![big Omega](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQczaaTmLgRUOhLQHUCRQvQN0i5WwGMyZ_zJarqKzj1jH_VQ3SjgBC-fiaGXq4uHaUWt9Y&usqp=CAU)

### 3. Big-Theta Notation (**Θ**)

-   **Tight bound** (both upper and lower).
-   Example: $3n^2 + 2n + 5$ is $\Theta(n^2)$.
    ![big theta](https://media.geeksforgeeks.org/wp-content/uploads/20210315032119/Untitled-300x229.png)

### 4. Small-o Notation (**o**)

-   **Strictly smaller growth** (looser than Big-O).
-   Example: $n = o(n^2)$, but $n^2$ is **not** $o(n^2)$.

### 5. Small-omega Notation (**ω**)

-   **Strictly larger growth** (looser than Big-Omega).
-   Example: $n^2 = \omega(n)$, but $n = \omega(n)$ is false.

#### 🌰 Five Simple Examples of Asymptotic Notation

##### Big-O and Small-o Examples

##### Example 1

-   f(n) = n
-   $ g(n) = n^2 $

👉 $ f(n) = O(n^2) $, and also $ f(n) = o(n^2)$.  
Because n grows much slower than $n^2$, it will never grow as fast.

---

### Example 2

-   $f(n) = 3n^2 + 2n + 7$
-   $g(n) = n^2$

👉 $f(n) = O(n^2)$, but **not** $o(n^2)$.  
Because $3n^2$ grows at the same rate as $n^2$, the ratio approaches a constant 3, not 0.

---

### Example 3

-   $f(n) = log n$
-   $g(n) = n$

👉 $f(n) = O(n)$, and also $f(n) = o(n)$.  
Because $log n$ grows much slower than $n$, $log n / n → 0$.

---

### Example 4

-   $f(n) = n$
-   $g(n) = n$

👉 $f(n) = O(n)$, but **not** $o(n)$.  
Because they grow at the same rate, $n / n = 1 ≠ 0$.

---

### Example 5

-   $f(n) = n^1.5$
-   $g(n) = n^2$

👉 $f(n) = O(n^2)$, and also $f(n) = o(n^2)$.  
Because $n^1.5$ grows slower than $n^2$, $(n^1.5 / n^2) = 1/√n → 0$.

---

## 🚩 One-Sentence Summary

-   **Big-O**: $f$ grows no faster than $g$, may grow at the same rate.
-   **small-o**: $f$ strictly grows slower than $g$, cannot grow at the same rate.

---

## Small-Omega

### Intuitive Definitions

-   **Big-Ω (Ω)**: lower bound (grows at least as fast as $g$, may grow faster)
-   **small-Ω (ω)**: strict lower bound (grows strictly faster than $g$, cannot grow at the same rate)

Mathematically:

-   $f(n) = Ω(g(n))$ → there exists a constant $c > 0$ such that for large $n$, $f(n) ≥ c * g(n)$.
-   $f(n) = ω(g(n))$ → $lim(n → ∞) f(n)/g(n) = ∞$.  
    (Means $f$ grows much faster than $g$, ratio explodes.)

---

## Big-Ω and Small-ω Examples

### Example 1

-   $f(n) = n^2$
-   $g(n) = n$

👉 $f(n) = Ω(n)$, and also $f(n) = ω(n)$.  
Because $n^2$ grows much faster than $n$, $n^2 / n = n → ∞$.

---

### Example 2

-   $f(n) = n$
-   $g(n) = log n$

👉 $f(n) = Ω(log n)$, and also $f(n) = ω(log n)$.  
Because $n / log n → ∞$.

---

### Example 3

-   $f(n) = 3n + 7$
-   $g(n) = n$

👉 $f(n) = Ω(n)$, but **not** $ω(n)$.  
Because they grow at the same rate, ratio approaches constant 3.

---

### Example 4

-   f(n) = n^2
-   $g(n) = n^2$

👉 $f(n) = Ω(n^2)$, but **not** $ω(n^2)$.  
Because they grow at the same rate, ratio = 1.

---

### Example 5

-   $f(n) = n^3$
-   $g(n) = n^2$

👉 $f(n) = Ω(n^2)$, and also $f(n) = ω(n^2)$.  
Because $n^3 / n^2 = n → ∞$.

---

## 🚩 Summary of the Four Notations

-   **Big-O**: $f$ grows no faster than $g$.
-   **small-o**: $f$ strictly grows slower than $g$.
-   **Big-Ω**: $f$ grows no slower than $g$.
-   **small-Ω**: $f$ strictly grows faster than $g$.

#### **small-omega vs. big-Omega**
