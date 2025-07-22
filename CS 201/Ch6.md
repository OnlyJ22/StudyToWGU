Look at  109 -> Ch6.md for more content

### Section 1: Understanding Sorting Algorithms

#### What Are Sorting Algorithms?

**Sorting algorithms** are methods used to **rearrange a group of items** into a specific order — such as **alphabetical**, **ascending**, or **descending**.

Each sorting algorithm offers different **strategies, advantages, and drawbacks**, depending on the context and data size.

> Think of sorting algorithms as **organizational tools**:
> They help ensure that data is arranged in a way that makes it easier to search, process, and analyze.

---

#### The Big-O Notation

**Big-O Notation** is used to describe the **performance efficiency** of an algorithm, especially how it behaves as the input size grows.

There are four common time complexities to know:

```
O(1)      → Constant Time  
O(n)      → Linear Time  
O(log n)  → Logarithmic Time  
O(n^2)    → Quadratic Time
```

> Here, **n** represents the number of elements.
> As **n increases**, the **time** or **steps required** can grow dramatically — especially for inefficient algorithms.

**Figure 1: Time Complexity Graph**

*(This graph would visually compare the growth of different Big-O curves as input size increases.)*

---

#### Bubble Sort Algorithm

**Bubble Sort** is a **comparison-based** sorting algorithm. It repeatedly steps through the list, compares adjacent pairs, and **swaps them if they are in the wrong order**. Larger elements “bubble” to the end of the list.

---

#### Bubble Sort: Method

Let’s sort the array `(7, 2, 6, 3, 9)` from **smallest to largest**.

**First Round**

```
(7 2 6 3 9) → (2 7 6 3 9)   [7 > 2, swap]  
(2 7 6 3 9) → (2 6 7 3 9)   [7 > 6, swap]  
(2 6 7 3 9) → (2 6 3 7 9)   [7 > 3, swap]  
(2 6 3 7 9) → (2 6 3 7 9)   [7 < 9, no swap]
```

**Second Round**

```
(2 6 3 7 9) → (2 6 3 7 9)   [6 > 2, no swap]  
(2 6 3 7 9) → (2 3 6 7 9)   [6 > 3, swap]  
(2 3 6 7 9) → (2 3 6 7 9)   [6 < 7, no swap]
```

**Third Round**

```
(2 3 6 7 9) → (2 3 6 7 9)   [3 > 2, no swap]
```

> **Sorted Array:** `(2, 3, 6, 7, 9)`

---

#### Bubble Sort: Performance

```
Best Case:     O(n)  
Worst Case:    O(n^2)
```

*In best-case, the array is already sorted. In worst-case, every pair must be compared and swapped.*

**Strengths**

* Easy to understand
* Simple to implement
* Minimal memory usage
* Output is immediately available for use

**Weaknesses**

* Very slow on large datasets

---

#### Selection Sort Algorithm

**Selection Sort** separates the array into **sorted** and **unsorted** parts. It selects the **minimum element** from the unsorted portion and moves it to the end of the sorted portion.

---

#### Selection Sort: Method

Example array: `(9, 6, 2, 5, 4)`

> Figure 2 would illustrate the step-by-step selection process.

---

#### Selection Sort: Performance

```
Best Case:     O(n^2)  
Worst Case:    O(n^2)
```

*Performance is the same regardless of initial arrangement.*

**Strengths**

* Works predictably regardless of element order
* Fewer data movements; better for costly memory operations

**Weaknesses**

* High number of comparisons for large arrays

---

#### Merge Sort Algorithm

**Merge Sort** is a **divide-and-conquer** algorithm. It splits the array into **smaller sub-arrays**, sorts each one, and **merges** them back together in order.

---

#### Merge Sort: Method

Example:
`(15, 32, 28, 9, 40, 18, 38, 50)`

**Steps 1–4:**
The array is repeatedly **divided** into halves until individual elements are isolated.

**Steps 5–7:**
The **atomic elements** are **merged and sorted** back together, resulting in a final sorted array.

> Figure 3 and 4 illustrate the split and merge phases.

---

#### Merge Sort: Performance

```
Best Case:     O(n log n)  
Worst Case:    O(n log n)
```

**Strengths**

* Excellent for large datasets
* Stable sort — preserves original order of equal elements
* Ideal for sequential data access (e.g., disk/tape storage)

**Weaknesses**

* Requires additional memory (2×N)
* Slower for smaller datasets

---

#### Quick Sort Algorithm

**Quick Sort** also uses the **divide-and-conquer** approach. It selects a **pivot** and partitions the array into elements **less than** and **greater than** the pivot.

This process is recursively applied until the list is sorted.

---

#### Quick Sort: Performance

```
Best Case:     O(n log n)  
Worst Case:    O(n log n)
```

**Strengths**

* Highly efficient
* Widely used in practice
* Great for medium and large lists

**Weaknesses**

* Partitioning can be complex
* Poor choice of pivot can reduce efficiency

---

#### Insertion Sort Algorithm

**Insertion Sort** works by comparing each new element with those before it, and inserting it into the correct position — much like sorting a hand of playing cards.

---

#### Insertion Sort: Method

Example illustrated in **Figure 5** with sequential comparisons and insertions.

---

#### Insertion Sort: Performance

```
Best Case:     O(n)  
Worst Case:    O(n^2)
```

**Strengths**

* Simple and easy to implement
* Efficient for small or nearly sorted datasets

**Weaknesses**

* Not ideal for large datasets

---

#### Lesson Summary

* **Sorting algorithms** reorder elements in an array based on a given condition (e.g., smallest to largest).
* Common algorithms include:

  * **Bubble Sort**
  * **Selection Sort**
  * **Merge Sort**
  * **Quick Sort**
  * **Insertion Sort**
* Performance is evaluated using **Big-O Notation**, which indicates how execution time grows with input size.
* Each algorithm has unique **strengths and weaknesses**, and the best choice depends on the **data size** and **requirements**.
