Look at  109 -> Ch4.md for more content

### Section 1: Simple Justification Techniques for Algorithm Analysis

**Simple justification techniques** are the methods that determine the **correctness of an algorithm** and evaluate **how efficient it is** in terms of time and memory.
The key techniques include:

* **Contra attack** – Using contrapositive and contradiction logic to justify a statement.
* **Induction** – Proving mathematical statements with a finite number of elements.
* **Loop variants** – Analyzing loop correctness based on conditions before and after each iteration.

---

#### Why Analyze an Algorithm?

Algorithms are not executable code. They are abstract instructions that must be converted into working programs.
Understanding their **correctness** and **efficiency** helps determine whether the algorithm is suitable for solving a specific problem.

---

#### Algorithmic Complexity

Algorithmic complexity is generally divided into two categories:

* **Time Complexity**
  The amount of time an algorithm takes to produce the desired output.

* **Space Complexity**
  The total amount of memory used during execution.

> Space complexity depends on:
>
> 1. The **data structures** used
> 2. **Memory allocations** for variables
> 3. The **results** stored after execution

These complexity parameters are used along with justification techniques to evaluate algorithm quality.

---

#### Algorithmic Methods

#### Contra Attack

Contra attack includes two key logic-based proof strategies:

**1. Contrapositive Method**
We prove the **negation** of a statement to show that the original statement must be true.

> *Example:*
> If `m` is even, then `3m + 1` is odd.
> Therefore, if `3m + 1` is even, then `m` must be **odd**.

**2. Contradiction Method**
We **assume the given statement is false**, and then show that this assumption leads to a **logical contradiction**.

---

#### Induction

Mathematical induction is used to prove a statement is true for all positive integers.
This involves:

1. Proving the **base case**
2. Showing that if the statement holds for `k`, then it also holds for `k + 1`

> This is especially useful in proving **recursive** algorithms.

---

#### Loop Variants

Loop variants help prove **loop correctness** by ensuring a condition is true:

* Before the loop starts
* After every iteration
* When the loop ends

> Loop variants ensure the algorithm **progresses** and eventually terminates.

---

#### Lesson Summary

To prove an algorithm's correctness and efficiency, we can use the following techniques:

* **Contra attack** (contrapositive, contradiction)
* **Induction**
* **Loop variants**

These techniques, combined with **time and space complexity**, help us identify whether an algorithm:

* Produces the **correct result**
* Uses **minimal resources**
* Handles **all valid inputs**

> The best algorithm is the one that solves the problem **accurately** and **efficiently**.

### Section 2: Big-O Notation

**Big-O Notation** is a mathematical concept used in computer science to describe the **performance or complexity** of an algorithm. It tells us **how the runtime or space requirements grow** relative to the size of the input.

Big-O is important for choosing the most efficient algorithm when solving a problem, especially with large datasets.

---

#### Common Big-O Complexities

| Complexity Type | Big-O Notation | Description        |
|-----------------|----------------|--------------------|
| Constant Time   | O(1)           | No matter the size of n, the algorithm takes the same amount of time to run. |
| Logarithmic     | O(log n)       | Algorithm reduces the problem size each iteration.          |
| Linear          | O(n)           | Runtime increases proportionally with the input size.       |
| Quasilinear     | O(n log n)     | Common in efficient sorting algorithms (e.g., merge sort).  |
| Quadratic       | O(n²)          | Operations grow quadratically; common in nested loops.      |
| Exponential     | O(2ⁿ)          | Growth doubles with each input increment; extremely slow.   |
| Factorial       | O(n!)          | Grows faster than all others; used in permutations/brute-force. |


#### Constant Time — O(1)

This algorithm always takes the same amount of time, no matter the input size.

```java
public static void main(String[] args) {
    int n = 1000;
    System.out.println("First value is: " + n);
    System.out.println("And n once again: " + n);
    System.out.println("Looks like n is still: " + n);
}
```

> O(1) is ideal — no matter how large the input is, the time to execute stays the same.

---

#### Logarithmic — O(log n)

The input is reduced by half each time — like **binary search**.

```java
public class Main {
    public static int binarySearch(int[] array, int target) {
        int left = 0, right = array.length - 1;
        int steps = 0;

        while (left <= right) {
            steps++;
            int middle = (left + right) / 2;
            if (array[middle] == target) return middle;
            else if (array[middle] < target) left = middle + 1;
            else right = middle - 1;
        }

        return -1;
    }

    public static void main(String[] args) {
        int[] data = {2, 3, 5, 7, 8, 10, 13, 16};
        System.out.println(binarySearch(data, 13));
    }
}
```

---

#### Linear — O(n)

The time grows **linearly** with the size of the input.

```java
for (int i = 0; i < n; i++) {
    System.out.println("Index: " + i);
}
```

> Think of simple loops: time grows step-by-step with input size.

---

#### Quasilinear — O(n log n)

Used in efficient sorting algorithms like **Merge Sort**.

```java
public static void mergeSort(int[] array, int left, int right) {
    if (left < right) {
        int middle = (left + right) / 2;
        mergeSort(array, left, middle);
        mergeSort(array, middle + 1, right);
        merge(array, left, middle, right);
    }
}

public static void merge(int[] array, int left, int mid, int right) {
    int n1 = mid - left + 1;
    int n2 = right - mid;

    int[] L = new int[n1];
    int[] R = new int[n2];

    for (int i = 0; i < n1; i++) L[i] = array[left + i];
    for (int j = 0; j < n2; j++) R[j] = array[mid + 1 + j];

    int i = 0, j = 0, k = left;
    while (i < n1 && j < n2) {
        array[k++] = (L[i] <= R[j]) ? L[i++] : R[j++];
    }
    while (i < n1) array[k++] = L[i++];
    while (j < n2) array[k++] = R[j++];
}
```

---

#### Quadratic — O(n²)

Nested loops. Time grows with **square of the input**.

```java
public static int countOps(int[] dataset) {
    int count = 0;
    for (int i = 0; i < dataset.length; i++) {
        for (int j = 0; j < dataset.length; j++) {
            count++;
        }
    }
    return count;
}
```

> Common in simple sorting: **bubble sort**, **selection sort**.

---

#### Exponential — O(2ⁿ)

Time **doubles** with each increase in input size. Example: **recursive Fibonacci**.

```java
public static int fib(int n) {
    if (n <= 1) return n;
    return fib(n - 1) + fib(n - 2);
}
```

> Very slow for large `n`. Avoid unless `n` is small.

---

#### Factorial — O(n!)

Explores **all permutations** — example: generating all possible orderings.

```java
public static void permute(String str, String result) {
    if (str.length() == 0) {
        System.out.println(result);
        return;
    }
    for (int i = 0; i < str.length(); i++) {
        permute(str.substring(0, i) + str.substring(i + 1),
                result + str.charAt(i));
    }
}
```

> Brutal on performance. Even `n = 10` results in **3.6 million** permutations!

---

#### Lesson Summary

* Big-O Notation helps measure algorithm performance.
* It describes how **input size affects execution time**.
* Efficient code matters — especially at scale.
* Ranges from O(1) (fastest) to O(n!) (slowest).
* Understanding Big-O helps choose better data structures and algorithms.
