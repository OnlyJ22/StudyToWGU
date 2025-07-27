Look at  109 -> Ch5.md for more content

### Section 1: Complexity Analysis of Algorithms

The complexity of an algorithm estimates the resources it will consume during execution. These resources are typically divided into two categories:

* **Time Complexity**: Measures the number of operations executed.
* **Space Complexity**: Measures the amount of memory used.

When analyzing **non-recursive algorithms**, we focus on how loops (iterations) behave. For **recursive algorithms**, we must examine how each recursive call behaves and builds upon previous ones.

Big-O notation expresses the **asymptotic upper bound** of an algorithm’s growth — that is, what ultimately dominates the runtime as input size increases. For example:

> If an expression is `6n³ + 2n² + 4n + 7`, the term `6n³` dominates, so Big-O is `O(n³)` — constants and lesser-order terms are ignored.

---

#### Time Complexity of Algorithms

The **time complexity** refers to the number of basic operations needed for an algorithm to complete. Let's examine this using a simple **recursive factorial function**.

**Java Code Example:**

```java
class Main {
  public static void main(String[] args) {
    int n = 25;
    System.out.println("Factorial " + Factorial(n));
  }

  public static long Factorial(long n) {
    if (n == 0)
      return 1;
    else
      return n * Factorial(n - 1);
  }
}
```

This function performs **3 operations per call**:

1. A comparison (`if n == 0`)
2. A multiplication (`n * ...`)
3. A subtraction (`n - 1`)

We define the time complexity as:

```
T(n) = T(n - 1) + 3
T(0) = 1
```

This solves to **T(n) = O(n)** — linear time complexity.

---

#### Space Complexity

To evaluate **space complexity**, we analyze how much memory is used during execution. For the factorial example, each recursive call adds a new stack frame, consuming a constant amount of memory `k`. Since the number of calls is `n`, the space complexity is:

```
S(n) = k * n = O(n)
```

Again, this is **linear space complexity**.

---

#### Fibonacci Sequence Example

The Fibonacci sequence is defined as:

```
F(0) = 1, F(1) = 1
F(n) = F(n - 1) + F(n - 2)
```

**Java Code Example:**

```java
class Main {
  public static void main(String[] args) {
    int n = 12;
    System.out.println("Fib " + Fib(n));
  }

  public static long Fib(long n) {
    if ((n == 0) || (n == 1)) {
      return 1;
    } else {
      return Fib(n - 1) + Fib(n - 2);
    }
  }
}
```

Each call to `Fib(n)` results in:

* 2 comparisons
* 2 recursive calls (`Fib(n - 1)` and `Fib(n - 2)`)
* 2 subtractions
* 1 addition

So the recursive time complexity is:

```
T(n) = T(n - 1) + T(n - 2) + 5
```

Assuming worst case (`T(n - 1) ≈ T(n - 2)`), this simplifies to:

```
T(n) = 2 * T(n - 1) + c  ⇒  T(n) = O(2ⁿ)
```

This is **exponential time complexity**.

Space complexity here follows the maximum depth of the recursion, which is `n`, giving:

```
S(n) = O(n)
```

But for **worst-case upper bound**, exponential branching can result in exponential space as well in the naive approach.

---

#### Lesson Summary

* **Time Complexity**: Describes how the number of operations grows with input size.
* **Space Complexity**: Describes how memory usage grows with input size.
* **Big-O Notation**: Captures the dominant term affecting growth.
* **Factorial Example**: Shows linear complexity `O(n)` for both time and space.
* **Fibonacci Example**: Shows exponential time complexity `O(2ⁿ)` due to multiple recursive calls.

These principles help determine whether an algorithm is suitable and efficient for large-scale problems.

### Section 2: Sequential Search

Imagine that you have an Excel sheet with 75 rows, and you need to find the value `$7.33` within the data. You would scan through each row until the value is found or confirmed missing. This is called a **sequential search** (also known as a **linear search**), which starts from the first item and checks each one in order until a match is found — or not.

If your worksheet had 500 rows or more, you'd likely want to use a built-in search function or write code to do this for you.

---

#### Sequential Search Algorithm

The process of a sequential search is straightforward:

> Every item is checked one-by-one until a match is found or the end of the list is reached.

**Algorithm Steps** (Assuming `Q` is the list, `z` is the target value, `i` is the index):

1. Set starting position to first element (`i = 0`)
2. If `i` is greater than the number of elements, go to Step 7
3. If `Q[i] == z`, go to Step 6
4. Update `i = i + 1`
5. Return to Step 2
6. Element `z` found at index `i`
7. Element not found — exit

---

#### Implementing the Search in Java

Sequential searches do **not** require sorted data. Below is a sample array and a search method.

```java
public class Searches {
  public static void main(String[] args) {
    // Create an array of payments
    double[] payments = {3.35, 12.07, 122.76, 7.33, 6.04, 681.78, -0.05,
                         45.25, 107.33, 6.25, 3.45, 3.45, 0.52};

    // What are we looking for?
    double searchKey = 7.33;
    System.out.println("Search Key found at: " + sequentialSearch(payments, searchKey));
  }

  public static int sequentialSearch(double[] arr, double key) {
    int arraySize = arr.length;
    for (int i = 0; i < arraySize; i++) {
      if (arr[i] == key) {
        return i;
      }
    }
    return -1;
  }
}
```

**Output:**

```
Search Key found at: 3
```

Note that `7.33` was found at index `3`.

If the value does **not** exist in the array, the method returns `-1`.

---

#### Big O Notation

Sequential search has a **time complexity** of:

> **O(n)** — Linear Time
> Where `n` is the number of elements in the list or array.

This means that in the **worst-case scenario**, the algorithm will compare the target value against every item.

**Performance Table:**

| Situation         | Best Case | Worst Case | Average Case |
| ----------------- | --------- | ---------- | ------------ |
| 7.33 is Found     | 1         | n          | n / 2        |
| 7.33 is NOT Found | n         | n          | n            |

As the dataset grows in size — for example, to millions of entries — the performance impact becomes more significant, especially when the sought item is at the end or missing entirely.

---

#### Lesson Summary

A **sequential search** checks each element in an array or list one by one. It works on both sorted and unsorted data. The performance of this algorithm is classified as **O(n)**, meaning it scales linearly with the size of the input. While acceptable for small lists, this method becomes inefficient for large datasets due to its potential to require every element to be checked.

### Section 3: Exponential Search

Exponential search is a hybrid search technique that combines two methods:

1. **Finding a range** in which the target element may exist.
2. **Performing a binary search** within that identified range.

This approach is particularly efficient for searching in **sorted arrays**, especially large or potentially unbounded ones.

---

#### How It Works

1. Check if the element is at index 0.
2. Increase index `i` exponentially (i.e., 1, 2, 4, 8, …) until either:

   * `i` exceeds the size of the array, or
   * The element at index `i` is greater than the search key.
3. Once the potential range is identified (`i/2` to `i`), perform a binary search within that range.

---

#### Java Implementation

```java
import java.util.*;
import java.math.*;

public class ExponentialSearch {
  public static void main(String[] args) {
    int array[] = {5, 10, 15, 20, 25, 30, 35, 40, 45, 50, 55, 60};
    int searchValue = 50;
    int result = expSearch(array, array.length, searchValue);
    System.out.println("Element is present at index: " + result);
  }

  static int expSearch(int array[], int n, int searchValue) {
    if (array[0] == searchValue) {
      return 0;
    }

    int i = 1;
    while (i < n && array[i] <= searchValue) {
      i = i * 2;
    }

    return Arrays.binarySearch(array, i / 2, Math.min(i, n), searchValue);
  }
}
```

**Output:**

```
Element is present at index: 9
```

---

#### Big O Notation

| Step                       | Time Complexity |
| -------------------------- | --------------- |
| Finding the range          | O(log i)        |
| Binary search within range | O(log i)        |
| **Total (combined)**       | **O(log n)**    |

> Exponential search has logarithmic performance, just like binary search, but it begins by **finding bounds** before performing a binary search.

---

#### Lesson Summary

Exponential search is a two-part search process for **sorted arrays**:

* **Step 1**: It exponentially increases the search interval until it identifies a valid range.
* **Step 2**: A binary search is performed within that range.

This algorithm is ideal for very large or **unbounded datasets**, such as memory management systems or massive datasets. Its overall time complexity is **O(log n)**, making it highly efficient when compared to linear search algorithms.
