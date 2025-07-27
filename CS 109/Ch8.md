### Section 1: What Is a Programming Algorithm?

#### Definition

A **programming algorithm** is a **step-by-step set of instructions** that tells a computer exactly how to solve a problem or achieve a goal.
It’s much like a **recipe**:

* **Procedure** = The instructions
* **Inputs** = The ingredients
* **Outputs** = The finished result

Unlike actual code, an algorithm is often written in **plain English**, and it has a **start**, a **middle**, and an **end**.

---

#### Characteristics of an Algorithm

* **Clear and unambiguous** – Every step must be specific
* **Has a defined beginning and end** – It should not run indefinitely
* **Deterministic** – The same input always produces the same output
* **Efficient** – Should solve the problem using as few steps as possible

Although algorithms are **not code**, they can be later converted into any programming language after proper planning.

---

#### Example — Email Collection Algorithm

**Text-Based Version:**

1. Start
2. Create a variable to store user input
3. Clear the variable (reset any old data)
4. Prompt user for an email address
5. Store the input in the variable
6. Validate the email format
7. If valid → proceed to End
   If not → go back to step 3
8. End

**Highlights:**

* Step 7 introduces a **decision** point — we check whether the input is valid.
* If not, the process **loops** until the input meets our criteria.
* An **escape route** should be added to avoid infinite loops.

---

#### Representation Forms

There are several ways to write or visualize an algorithm:

| Method            | Description                                               |
| ----------------- | --------------------------------------------------------- |
| **Plain English** | Step-by-step instructions written in natural language     |
| **Pseudocode**    | Structured, semi-code format resembling programming logic |
| **Flowchart**     | Visual map using arrows and shapes to illustrate flow     |

---

#### Pseudocode vs. Algorithm

While pseudocode and algorithms are related, they’re not the same:

* **Algorithm**: A concept or plan written in plain terms
* **Pseudocode**: A more structured, programming-like representation of the algorithm

---

#### Best Practices for Writing Algorithms

* Be **simple** and **specific**
* Avoid language-specific syntax
* Use **one task per line**
* Make use of **indentation** and **clear formatting**
* Use **capitalized keywords** like `IF`, `THEN`, `DISPLAY`, etc.

---

#### Lesson Summary

* A **programming algorithm** is like a **recipe**: it provides the precise steps a computer needs to follow to solve a task.
* Algorithms are written in **plain language** and later translated into code.
* They use **inputs** (ingredients), **procedures** (instructions), and yield **outputs** (results).
* Algorithms are typically written as **numbered lists**, **pseudocode**, or **flowcharts**.
* They must be **clear**, **unambiguous**, and lead to a **solution**.
* Writing good algorithms helps prevent bugs, organize logic, and simplify code development.

---

#### Key Terms

* **Programming Algorithm**: A detailed plan to solve a problem
* **Procedure**: Step-by-step task list
* **Inputs**: What the program starts with
* **Outputs**: What the program produces
* **Pseudocode**: Semi-programming language used for outlining algorithms

### Section 2: Algorithm Analysis

#### Definition

An **algorithm analysis** is a technique used to **measure the performance** of algorithms. The primary focus is on **speed**, but other important factors include:

* **User-friendliness**
* **Security**
* **Maintainability**
* **Space usage**

To quantify these, two main metrics are used:

* **Time Complexity** – How long the algorithm takes
* **Space Complexity** – How much memory it uses

This analysis helps in identifying whether an algorithm is practical for real-world applications.

---

#### Experimental Analysis of Algorithms

In **experimental analysis**, we study an algorithm by actually **executing it** and measuring its behavior under various conditions. Key elements considered include:

* **Number of loops**
* **Sample input sizes**
* **Execution time**

**Visualization** plays an important role:

* Data points are plotted on **graphs**
* **X-axis** typically represents input size
* **Y-axis** shows the running time

**Highlights:**

* Evaluates **best**, **average**, and **worst-case** time scenarios
* Graphs can take the form of **histograms** or **line charts**
* Experimental analysis **requires the algorithm to be implemented**

---

#### Limitations of Experimental Studies

While experimental analysis provides real-world results, it has certain drawbacks:

* Implementing each algorithm can be **tedious and time-consuming**
* Comparing algorithms fairly requires **identical hardware and software environments**
* Input samples might **not cover all possible cases**

Due to these limitations, theoretical approaches are often preferred.

---

#### Asymptotic Analysis

To overcome the shortcomings of experimental analysis, **asymptotic analysis** is used. It relies on **mathematical notations** to estimate the performance of an algorithm **without implementation**.

This type of analysis provides:

* **Upper bound** – Worst-case performance
* **Lower bound** – Best-case performance
* **Tight bound** – Average-case performance

Asymptotic analysis focuses on how the algorithm behaves as the **input size grows**, often ignoring minor implementation details.

---

#### Asymptotic Notations

There are three primary asymptotic notations:

| Notation      | Description                           | Case Measured |
| ------------- | ------------------------------------- | ------------- |
| **Big O (O)** | Describes the **upper bound**         | Worst-case    |
| **Omega (Ω)** | Describes the **lower bound**         | Best-case     |
| **Theta (θ)** | Describes the **tight (exact) bound** | Average-case  |

These notations help in classifying algorithms based on their growth rates.

---

#### Big O (O)

**Big O** notation is used to describe the **worst-case performance** of an algorithm.

**Formal Definition:**

> Let `f(n)` be the running time of an algorithm. Then:
> `O(f(n)) = { g(n) : ∃ c > 0 and n₀ such that f(n) ≤ c·g(n) ∀ n > n₀ }`

This tells us that `f(n)` does not grow faster than `g(n)` beyond a certain point.

---

#### Omega (Ω)

**Omega (Ω)** notation describes the **best-case performance** — the **minimum** time an algorithm will take.

**Formal Definition:**

> `Ω(f(n)) = { g(n) : ∃ c > 0 and n₀ such that g(n) ≥ c·f(n) ∀ n > n₀ }`

This helps in identifying the most efficient possible scenario.

---

#### Theta (θ)

**Theta (θ)** notation describes a **tight bound**, meaning it captures both the **best** and **worst** cases.

**Formal Definition:**

> `θ(f(n)) = { g(n) : g(n) = O(f(n)) and g(n) = Ω(f(n)) ∀ n > n₀ }`

It represents a **balanced view** of algorithm performance.

---

#### Lesson Summary

* An **algorithm analysis** helps in evaluating how efficiently an algorithm solves a problem.
* **Experimental analysis** involves implementing the algorithm and tracking actual performance over various inputs.
* However, experimental analysis has limitations due to environmental and input variability.
* **Asymptotic analysis** provides a **mathematical model** for understanding algorithm efficiency, without needing to run the code.
* The three major asymptotic notations are:

  * **Big O (O)** – Worst case
  * **Omega (Ω)** – Best case
  * **Theta (θ)** – Tight bound
* These notations are used to express **time complexity** and **space complexity** in a scalable way.

---

#### Key Terms

* **Algorithm Analysis**: Evaluating performance (time/space) of algorithms
* **Experimental Analysis**: Observing actual execution of algorithms
* **Asymptotic Analysis**: Theoretical performance estimation
* **Big O (O)**: Worst-case scenario
* **Omega (Ω)**: Best-case scenario
* **Theta (θ)**: Average-case scenario or tight bound
* **Time Complexity**: How long the algorithm takes
* **Space Complexity**: How much memory the algorithm uses

### Section 3: Common Time Complexity Functions

#### Constant Function — f(n) = c or **O(1)**

A **constant function** describes an algorithm that always takes the **same amount of time**, regardless of input size `n`. It is written as:

* **f(n) = c** where `c` is any constant
* **O(1)** notation describes this in asymptotic terms

**Examples:**

* Comparing two variables
* Accessing an array element by index
* Typing a fixed number of words at a constant speed

> Think of it like following the same short recipe every time — the number of steps doesn’t change, so the time taken stays the same.

---

#### Logarithmic Function — f(n) = log n or **O(log n)**

A **logarithmic function** grows slowly compared to the size of the input. It is typically seen in **divide-and-conquer** algorithms like **binary search**.

**Key Concepts:**

* **f(n) = log₍b₎ n**, where `b > 1`
* `x = log₍b₎ n` means `b^x = n`

**Example:**

* If `n = 81` and `b = 3`, then log₍3₎ 81 = 4
* Binary search repeatedly divides an array by 2: log₂ n steps

> This tells us how many times we can divide `n` until we are left with 1 element.

---

#### Linear Function — f(n) = n or **O(n)**

A **linear function** represents algorithms whose running time grows **proportionally** with the size of the input.

**Key Concepts:**

* **f(n) = cn**, where `c` is a constant
* Time increases directly as `n` increases

**Examples:**

* Counting word occurrences in a book with `n` pages
* Traversing a list of `n` items

> The graph of this function is a straight line with a constant slope.

---

#### N-log-N Function — f(n) = n log n or **O(n log n)**

This complexity combines both linear and logarithmic growth. It appears in more optimized sorting algorithms like **Merge Sort** or **Heap Sort**.

**Applications:**

* Dividing the input into parts (`log n`)
* Doing some linear operation for each part (`n`)

**Example:**

* Searching a phone book with `n = 2000` entries
* Randomly picking a page, then moving forward or backward to find a name

> As the number of choices `n` increases, the complexity increases at a rate of `n log n`.

---

#### Quadratic Function — f(n) = n² or **O(n²)**

**Quadratic complexity** typically arises in algorithms with **two nested loops** — an inner loop inside an outer loop.

**Examples:**

* **Bubble Sort**, **Insertion Sort**, **Selection Sort**
* Comparing every element in an array with every other element

> The number of steps increases with the square of the input size: `n * n`

---

#### Cubic and Polynomial Functions — f(n) = n³ or **O(n³), O(n⁴)... O(nⁿ)**

Polynomial functions result from **three or more nested loops**. As the number of nested iterations increases, the runtime increases significantly.

**Key Concepts:**

* **Cubic**: f(n) = n³ (3 nested loops)
* **Polynomial**: f(n) = nᵏ, where `k` is a positive integer

> These are often inefficient for large input sizes and avoided when possible.

---

#### Exponential Function — f(n) = bⁿ or **O(2ⁿ)**

An **exponential function** describes algorithms where the runtime **doubles** (or more) with each additional input.

**Key Concepts:**

* f(n) = bⁿ, where `b > 1`
* Runtime grows rapidly with input size

**Examples:**

* Brute-force search in a power set
* Solving recursive problems without memoization (e.g., naive Fibonacci)

> These are typically **impractical** for large inputs due to explosive growth.

---

#### Representation of Common Time Complexities

| Function Type   | Notation   | Example Use Case                         |
| --------------- | ---------- | ---------------------------------------- |
| **Constant**    | O(1)       | Array access, variable comparison        |
| **Logarithmic** | O(log n)   | Binary search                            |
| **Linear**      | O(n)       | Looping through array                    |
| **N-log-N**     | O(n log n) | Merge Sort, optimized divide-and-conquer |
| **Quadratic**   | O(n²)      | Nested loops, bubble sort                |
| **Cubic**       | O(n³)      | Triple nested loops                      |
| **Exponential** | O(2ⁿ)      | Brute-force algorithms                   |

---

#### Lesson Summary

* The **time complexity** of an algorithm defines how its runtime scales with the size of the input `n`.
* **Constant time (O(1))** algorithms are the most efficient, as their runtime doesn’t grow.
* **Logarithmic (O(log n))** and **N-log-N (O(n log n))** functions are highly efficient and common in search and sort algorithms.
* **Linear (O(n))** complexity is acceptable for many real-world problems.
* **Quadratic (O(n²))** and **Cubic (O(n³))** algorithms become inefficient quickly as input size increases.
* **Exponential (O(2ⁿ))** algorithms are rarely usable for large inputs due to their extreme growth.

---

#### Key Terms

* **Constant Time – O(1)**: Execution time does not depend on input size
* **Logarithmic Time – O(log n)**: Execution time grows slowly
* **Linear Time – O(n)**: Execution time grows in direct proportion to input
* **N-log-N – O(n log n)**: Combination of linear and logarithmic behavior
* **Quadratic Time – O(n²)**: Execution time grows with square of input size
* **Cubic/Polynomial – O(n³), O(nⁿ)**: Time grows with cube or higher powers
* **Exponential Time – O(2ⁿ)**: Time doubles with each input increase

### Section 4: Big-O Notation and Complexity Analysis

#### Definition

**Big-O notation** is a **standard mathematical representation** used to measure the performance and efficiency of functions — particularly in terms of **time** and **space**. In the context of algorithms, a **function** refers to the structure and flow of operations, loops, and nested loops.

The **"O"** stands for **order**, as Big-O describes the **growth rate** of an algorithm relative to its input size.

> It gives a way to classify algorithms based on how their run-time or memory requirements scale as input size increases.

---

#### Time and Space Complexity

Both **time complexity** and **space complexity** are essential to understanding algorithm performance:

* **Time Complexity** – Measures how long an algorithm takes to complete as a function of input size (`n`)
* **Space Complexity** – Measures how much memory an algorithm requires to run

Big-O notation is used to represent both.

---

#### Common Examples of Big-O Complexity

| Complexity Class | Description           | Example Use Case                   |
| ---------------- | --------------------- | ---------------------------------- |
| **O(1)**         | Constant time & space | Single-step operations             |
| **O(n)**         | Linear time           | One loop through `n` items         |
| **O(n²)**        | Quadratic time        | Nested loops                       |
| **O(2ⁿ)**        | Exponential time      | Recursive calls doubling each time |

---

#### **O(1)** – Constant Time and Space

```java
bool findingNull(ArrayList<String> str)
{
    return str[0] == null;
}
```

**Explanation:**

* This function checks the first element of the list.
* It **does not depend on input size**, so:

  * **Time Complexity = O(1)**
  * **Space Complexity = O(1)**

---

#### **O(n)** – Linear Time and Space

```java
bool hasValue(ArrayList<string> str, string value)
{
    foreach (var element in str)
    {
        if (element == value) return true;
    }
    return false;
}
```

**Explanation:**

* This function loops through all `n` elements of the list.
* Each element is checked once, so:

  * **Time Complexity = O(n)**
  * **Space Complexity = O(n)**

---

#### **O(n²)** – Quadratic Time and Space

```java
bool hasDuplicate(ArrayList<string> str)
{
    for (int out = 0; out < str.length; out++)
    {
        for (var in = 0; in < str.length; in++)
        {
            if (out == in) continue;
            if (str[out] == str[in]) return true;
        }
    }
    return false;
}
```

**Explanation:**

* There are **two nested loops**, both dependent on `n`.
* Total operations ≈ n × n = **n²**
* Memory usage may grow as **n²**, especially with large inputs

**Mathematical Insight:**

* Inner loop executes a series:
  `0 + 1 + 2 + ... + (n - 1) = n(n - 1)/2`
* Hence, **Time Complexity = O(n²)**
* **Space Complexity = O(n²)**

---

#### **O(2ⁿ)** – Exponential Time

```java
int FibonacciSeries(int num)
{
    if (num <= 1) return num;
    return FibonacciSeries(num - 2) + FibonacciSeries(num - 1);
}
```

**Explanation:**

* This is a **recursive Fibonacci function**
* For every call, two more recursive calls are made, forming a **binary recursion tree**
* This leads to exponential growth:

  * **Time Complexity = O(2ⁿ)**
  * **Space Complexity = O(n)** (due to the call stack)

> Each level of recursion splits the tree into two more branches, doubling at each level.

---

#### Lesson Summary

* **Big-O notation** is used to measure how algorithms perform in terms of **execution time** and **memory usage** as the input size (`n`) grows.
* **Time complexity** reflects how fast an algorithm runs, while **space complexity** refers to memory usage.
* Different classes of Big-O define different behaviors:

  * **O(1)** – Constant performance, best case
  * **O(n)** – Grows linearly with input size
  * **O(n²)** – Grows quadratically, often due to nested loops
  * **O(2ⁿ)** – Exponential growth, especially in naive recursion
* In real-world coding, reducing **time and space complexity** is essential — even a small inefficiency in a loop or recursion can lead to **major performance issues** for large inputs.
* Efficient code isn't just about fewer lines — it's about scalable logic.

---

#### Key Terms

* **Big-O Notation**: Mathematical notation for algorithm efficiency
* **Time Complexity**: How algorithm time scales with input
* **Space Complexity**: How memory usage scales with input
* **Constant Time – O(1)**: Unchanging time regardless of input size
* **Linear Time – O(n)**: Time scales directly with input size
* **Quadratic Time – O(n²)**: Time grows with the square of input size
* **Exponential Time – O(2ⁿ)**: Time doubles with each input increase
* **Recursive Tree**: Visual of how recursive calls branch in exponential patterns

### Section 5: Arrays in Java

#### Definition

A **Java array** is a **data structure** that stores a **fixed-size collection** of elements of the **same data type**. It must be **declared with a specific type and size** before it is used.

**Example – One-Dimensional Array:**

```java
int[] numbers = new int[10];
```

This declaration creates an array of integers with 10 elements. If more than 10 values are needed later, a **new array must be created**, and existing elements **copied** over manually.

---

#### Array Indexing and Memory Layout

Arrays in Java store elements in **contiguous memory locations**, which allows for **efficient access** using an **index**.

* The first element is `numbers[0]`
* The second element is `numbers[1]`, and so on

> Indexing starts at 0 and is **offset-based** from the beginning of the memory block.

---

#### Two-Dimensional Arrays

Java allows for **arrays of arrays**, creating a **two-dimensional structure**.

**Example – 2D Array (10 × 10):**

```java
int[][] table = new int[10][10];
```

Each row (`table[0]`, `table[1]`, etc.) is itself an array. To access the value in the **4th row and 6th column**, use:

```java
table[3][5];
```

---

#### Memory Usage

Array memory usage can be broken into several components:

**One-Dimensional Array (`int[] numbers = new int[10]`):**

* 8 bytes – array header
* 4 bytes – stores array length
* 10 × 4 bytes = 40 bytes for `int` elements
* 4 bytes – padding (to align memory to 8-byte boundary)

**Total Memory:**

```plaintext
8 + 4 + 40 + 4 = 56 bytes
```

**Two-Dimensional Array (`int[][] table = new int[10][10]`):**

* 56 bytes for outer array (10 rows)
* Each row is another 56-byte array

**Total Memory:**

```plaintext
56 + (10 × 56) = 616 bytes
```

---

#### Array Performance

Java arrays are **efficient for fixed-size operations**:

* Accessing/assigning elements by index is **fast**
* Traversing the array is simple using a **loop**

**Example – Traversing and Modifying an Array:**

```java
for (int i = 0; i < numbers.length; i++)
    numbers[i] = -1;
```

> This loop assigns `-1` to every element in the `numbers` array.

---

#### Insertions and Deletions

Operations like **inserting** or **removing** elements in the **middle** of an array are **costly**:

**Example – Inserting After Index 5 (Array Size = 10):**

Steps:

1. Move value at index 8 → 9
2. Move index 7 → 8
3. Move index 6 → 7
4. Assign new value to index 6

> Inserting one value may require shifting multiple elements. This can degrade performance, especially for large arrays.

Similarly, **removal** of an element requires **shifting** all values after the deleted element one step to the left to maintain compact storage.

---

#### Resizing Arrays

Arrays in Java are of **fixed size**. To grow an array:

1. Create a **new, larger array**
2. **Copy** existing elements into the new array

> This resizing process is **time-consuming** for large arrays.

---

#### Lesson Summary

* A **Java array** stores elements of the **same type** and has a **fixed size**.
* Memory for **1D arrays** is allocated as a **single block**.
* **2D arrays** are implemented as **arrays of arrays**.
* Memory usage includes:

  * 8 bytes (header) + 4 bytes (length) + data size + padding
* Arrays offer **fast access and traversal** using index-based operations.
* Insertions and deletions are **slow** due to element shifting.
* **Resizing** requires allocating a **new array** and copying existing elements.

---

#### Key Terms

* **Array**: A fixed-size container for storing multiple values of the same type
* **Indexing**: Accessing elements via zero-based positions
* **Contiguous Memory**: A block of memory where array elements are stored sequentially
* **Padding**: Extra bytes added to align memory to specific byte boundaries
* **Two-Dimensional Array**: An array of arrays, resembling a table structure
* **Resizing**: Creating a new array and copying elements to increase capacity
* **Performance**: Fast for access and traversal, but slow for insertion/deletion or resizing

### Section 6: Working with Arrays in Java

#### Array Basics

You've likely seen Java arrays before — they allow you to store **multiple items of the same data type** using square brackets (`[]`).

**Examples – Valid Array Declarations:**

```java
int[] array = {1, 2, 3, 4, 5};
int array[] = {1, 2, 3, 4, 5};
```

Both of these declare an array of integers and assign initial values.

---

#### Sorting Arrays Manually

**Sorting** is one of the most common operations on arrays. To better understand how it works, we can **manually implement a sorting algorithm**, such as **insertion sort**.

**Insertion Sort Logic:**

* Similar to sorting a hand of playing cards
* Iterates through the array
* Compares each new element with the ones before it
* Swaps elements until the correct position is found

**Example Code – Insertion Sort (Ascending Order):**

```java
public class Main {
    public static void main(String[] args) {
        int[] array = {45,12,85,32,89,39,69,44,42,1,6,8};
        int temp;
        for (int i = 1; i < array.length; i++) {
            for (int j = i; j > 0; j--) {
                if (array[j] < array[j - 1]) {
                    temp = array[j];
                    array[j] = array[j - 1];
                    array[j - 1] = temp;
                }
            }
        }
        for (int i = 0; i < array.length; i++) {
            System.out.println(array[i]);
        }
    }
}
```

> This method is efficient for small arrays and easy to remember when library methods aren’t available.

---

#### Using the `java.util.Arrays` Library

Java provides the **`java.util.Arrays`** library, which includes **over 100 methods** to manipulate arrays. Let’s look at some of the most useful ones.

---

#### Arrays.sort()

This method sorts the entire array in **ascending order** using **Dual-Pivot QuickSort**, a fast and optimized sorting algorithm.

**Example:**

```java
import java.util.Arrays;

public class Main {
    public static void main(String[] args) {
        int[] array = {45,12,85,32,89,39,69,44,42,1,6,8};
        Arrays.sort(array);
        for (int i = 0; i < array.length; i++) {
            System.out.println(array[i]);
        }
    }
}
```

> No loops are needed to write your own sorting logic — it’s built-in and efficient.

---

#### Partial Sorting – `Arrays.sort(array, fromIndex, toIndex)`

If you want to sort only part of an array, you can **specify a range** using the `sort` method’s overloaded version.

**Example – Sort from index 4 to 7:**

```java
import java.util.Arrays;

public class Main {
    public static void main(String[] args) {
        int[] array = {45,12,85,32,89,39,69,44,42,1,6,8};
        Arrays.sort(array, 4, 8);
        System.out.println("Partially Sorted: " + Arrays.toString(array));
        Arrays.sort(array);
        System.out.println("Completely Sorted: " + Arrays.toString(array));
    }
}
```

**Output:**

```
Partially Sorted: [45, 12, 85, 32, 39, 44, 69, 89, 42, 1, 6, 8]
Completely Sorted Array: [1, 6, 8, 12, 32, 39, 42, 44, 45, 69, 85, 89]
```

---

#### Arrays.toString()

Instead of printing array elements in a loop, `Arrays.toString()` **converts the entire array to a String**, making it easier to print.

**Example:**

```java
System.out.println(Arrays.toString(array));
```

---

#### Arrays.binarySearch()

This method performs a **binary search** on a sorted array and returns the **index of the searched value**.

**Important:** The array **must be sorted first** for binary search to work correctly.

**Example – Search for value `42`:**

```java
import java.util.Arrays;

public class Main {
    public static void main(String[] args) {
        int[] array = {45,12,85,32,89,39,69,44,42,1,6,8};
        Arrays.sort(array);
        System.out.println("Completely Sorted: " + Arrays.toString(array));
        int index = Arrays.binarySearch(array, 42);
        System.out.println("Position for number 42 is: " + index);
    }
}
```

**Output:**

```
Position for number 42 is: 6
```

> If the value is **not found**, the method returns a **negative number**.

---

#### Lesson Summary

* Java arrays can be created in multiple ways using `[]`.
* Sorting is a fundamental operation for arrays — and can be done **manually** or using **built-in library methods**.
* The **`java.util.Arrays`** library includes powerful methods like:

  * `Arrays.sort()` – full array sort
  * `Arrays.sort(array, from, to)` – partial sort
  * `Arrays.toString()` – convert array to a string
  * `Arrays.binarySearch()` – find value’s index in sorted array
* These tools help write cleaner, faster, and more readable code — without manually managing loops for sorting or searching.

---

#### Key Terms

* **Array**: A fixed-size data structure for storing multiple values of the same type
* **Insertion Sort**: Simple algorithm that places elements in order by comparison
* **java.util.Arrays**: Java library offering advanced array operations
* **Arrays.sort()**: Sorts array elements in ascending order
* **Arrays.toString()**: Converts array to a string for display
* **Arrays.binarySearch()**: Searches for a value in a **sorted** array
* **Partial Sort**: Sorting only a portion of an array by range

### Section 7: Bubble Sort in Java

#### Definition

**Bubble Sort** is a simple sorting algorithm commonly used to sort a collection of values, typically stored in an array. It gets its name because elements **"bubble"** to their correct position — either rising to the top (for descending order) or sinking to the bottom (for ascending order).

Bubble Sort compares **pairs of adjacent elements** and **swaps** them if they are in the wrong order. It continues doing this through multiple passes until the array is completely sorted.

---

#### Arrays Refresher

In Java, an **array** is a collection of values that can be accessed by an index. Indexing starts at 0.

**Example Array:**

```plaintext
Index:   [0] [1] [2] [3] [4] [5] [6]
Values:   7   5  19   3  11   4  88
```

This array is called `mySimpleArray` and has a **length of 7**.

> Bubble Sort compares and swaps adjacent values multiple times over multiple passes until all elements are ordered.

---

#### Step-by-Step: Bubble Sort Pass

**Starting Array:**

```plaintext
[7, 5, 19, 3, 11, 4, 88]
```

**Pass 1:**

1. Compare \[0] and \[1]: 7 > 5 → Swap → `[5, 7, 19, 3, 11, 4, 88]`
2. Compare \[1] and \[2]: 7 < 19 → No change
3. Compare \[2] and \[3]: 19 > 3 → Swap → `[5, 7, 3, 19, 11, 4, 88]`
4. Compare \[3] and \[4]: 19 > 11 → Swap → `[5, 7, 3, 11, 19, 4, 88]`
5. Compare \[4] and \[5]: 19 > 4 → Swap → `[5, 7, 3, 11, 4, 19, 88]`
6. Compare \[5] and \[6]: 19 < 88 → No change

> After multiple passes, the array will be sorted as: `[3, 4, 5, 7, 11, 19, 88]`

---

#### Bubble Sort Java Program

**Full Program Example:**

```java
public class BubbleMySort {

    // Bubble Sort method
    void bubbleSort(int mySimpleArray[]) {
        int n = mySimpleArray.length;
        for (int i = 0; i < n-1; i++) {
            for (int j = 0; j < n-i-1; j++) {
                if (mySimpleArray[j] > mySimpleArray[j+1]) {
                    int temp = mySimpleArray[j];
                    mySimpleArray[j] = mySimpleArray[j+1];
                    mySimpleArray[j+1] = temp;
                }
            }
        }
    }

    // Print array elements
    void printMyArray(int mySimpleArray[]) {
        int n = mySimpleArray.length;
        for (int i = 0; i < n; ++i)
            System.out.print(mySimpleArray[i] + " ");
        System.out.println();
    }

    // Main method
    public static void main(String args[]) {
        BubbleMySort bubble = new BubbleMySort();
        int mySimpleArray[] = {7, 5, 19, 3, 11, 4, 88};
        bubble.bubbleSort(mySimpleArray);
        System.out.println("Sorted mySimpleArray:");
        bubble.printMyArray(mySimpleArray);
    }
}
```

**Output:**

```
Sorted mySimpleArray:
3 4 5 7 11 19 88
```

> The algorithm uses **two nested loops** to complete the sort.

---

#### Performance

* Bubble Sort has a **time complexity of O(n²)** in the worst and average cases.
* The runtime increases **quadratically** with the input size.
* It is **not efficient** for large datasets.
* However, due to its simplicity, it is useful for **small arrays** or educational purposes.

---

#### Lesson Summary

* **Bubble Sort** is a simple and intuitive sorting algorithm.
* It repeatedly compares adjacent items and **swaps them if out of order**.
* Sorting requires **multiple passes** over the array.
* Bubble Sort is implemented using **two nested `for` loops**.
* It is not the most efficient algorithm — **O(n²)** performance means it scales poorly with large input sizes.
* Despite its inefficiency, it’s a great introduction to sorting concepts.

---

#### Key Terms

* **Bubble Sort**: Sorting algorithm that compares and swaps adjacent values
* **Array**: A collection of items indexed from 0
* **Pass**: A full iteration through the array in bubble sort
* **Swap**: Exchanging values to order elements
* **Time Complexity – O(n²)**: Performance measure for bubble sort due to nested loops

### Section 8: Selection Sort in Java

#### Definition

**Selection Sort** is a simple comparison-based sorting algorithm. In this algorithm:

* The **smallest (or largest)** element is selected from the **unsorted** portion of the array
* It is then **swapped** with the **first element** of the unsorted section
* Two subarrays are maintained:

  * **Sorted subarray** (grows from left to right)
  * **Unsorted subarray** (shrinks with each iteration)

> With each pass, the smallest element moves to its correct position in the sorted array.

---

#### Example – Step-by-Step

**Unsorted Array:**

```plaintext
95, 42, 13, 9, 23
```

**Passes:**

1. Find smallest from \[95, 42, 13, 9, 23] → 9 → Swap with 95
   → `9, 42, 13, 95, 23`

2. Find smallest from \[42, 13, 95, 23] → 13 → Swap with 42
   → `9, 13, 42, 95, 23`

3. Find smallest from \[42, 95, 23] → 23 → Swap with 42
   → `9, 13, 23, 95, 42`

4. Find smallest from \[95, 42] → 42 → Swap with 95
   → `9, 13, 23, 42, 95`

> Final sorted array: `9, 13, 23, 42, 95`

---

#### Java Implementation

```java
public class SelectionSort {

    // Sort function using Selection Sort
    void sort(int arr[]) {
        int n = arr.length;

        // Traverse the unsorted subarray
        for (int i = 0; i < n - 1; i++) {
            // Find the index of the minimum element
            int min = i;
            for (int j = i + 1; j < n; j++) {
                if (arr[j] < arr[min]) {
                    min = j;
                }
            }

            // Swap the found minimum element with the current element
            int temp = arr[min];
            arr[min] = arr[i];
            arr[i] = temp;
        }
    }

    // Print the elements of the array
    void printArray(int arr[]) {
        int n = arr.length;
        for (int i = 0; i < n; ++i)
            System.out.print(arr[i] + " ");
        System.out.println();
    }

    // Main method to test the sort
    public static void main(String[] args) {
        SelectionSort ss = new SelectionSort();
        int arr[] = {95, 42, 13, 9, 23};
        ss.sort(arr);
        System.out.println("The sorted array is: ");
        ss.printArray(arr);
    }
}
```

**Output:**

```plaintext
The sorted array is:
9 13 23 42 95
```

---

#### Performance and Usage

* **Time Complexity – O(n²)**
  There are two nested loops: one to traverse the array and another to find the minimum element.

* **Space Complexity – O(1)**
  Selection sort is an **in-place sorting algorithm**, meaning it doesn’t use extra space.

* **Swaps** – It performs at most **(n - 1)** swaps, making it slightly more efficient in swap count than bubble sort.

**Advantages:**

* Simple to understand and implement
* Does not require additional memory
* Performs well on **small datasets**
* Useful for **linked lists** where selection and positioning are easier than swapping large values

---

#### Lesson Summary

* **Selection Sort** builds a sorted array by repeatedly finding the **minimum value** from the unsorted array and **swapping** it with the current element.
* It maintains **two subarrays**: one sorted, one unsorted.
* The process continues for **n - 1 iterations**, where `n` is the array length.
* It is **easy to code** and uses **no extra memory**, making it practical in low-resource scenarios.
* Despite its simplicity, it is not optimal for large datasets due to its **O(n²)** time complexity.

---

#### Key Terms

* **Selection Sort**: Sorting algorithm that selects the minimum and swaps it to its correct position
* **Sorted Subarray**: Part of the array that is already sorted
* **Unsorted Subarray**: Part of the array yet to be sorted
* **In-Place Algorithm**: Sorting done without using extra space
* **Time Complexity – O(n²)**: Quadratic runtime due to nested loops
* **Space Complexity – O(1)**: Constant memory usage

### Section 9: Merge Sort in Java

#### Definition

**Merge Sort** is a **comparison-based sorting algorithm** that follows the **divide and conquer** strategy. It works by:

1. **Dividing** the array into smaller subarrays (down to individual elements),
2. **Sorting** each subarray,
3. **Merging** the sorted subarrays to form a single sorted array.

> Merge Sort is known for its stable and predictable performance, and is frequently used in systems programming and high-performance applications.

---

#### Merge Sort Algorithm – Step-by-Step

1. Divide the original array into two halves.
2. Recursively divide each subarray until each subarray contains only one element.
3. Merge the subarrays in sorted order.

**Example:**

Given the array:

```plaintext
[38, 27, 43, 3, 9, 82, 10]
```

It will be recursively divided and merged in sorted order to become:

```plaintext
[3, 9, 10, 27, 38, 43, 82]
```

---

#### Java Implementation

```java
public class MergeSort {

    // Entry method
    public static void MergeSort(String[] args) {
        int arr[] = {38, 27, 43, 3, 9, 82, 10};
        System.out.println("Unsorted Array");
        printArray(arr);
        MergeSort ms = new MergeSort();
        ms.sort(arr, 0, arr.length - 1);
        System.out.println("\nSorted array");
        printArray(arr);
    }

    // Recursive sort function
    void sort(int arr[], int left, int right) {
        if (left < right) {
            int mid = (left + right) / 2;

            // Sort left and right halves
            sort(arr, left, mid);
            sort(arr, mid + 1, right);

            // Merge the sorted halves
            merge(arr, left, mid, right);
        }
    }

    // Merge two sorted subarrays into one
    void merge(int arr[], int left, int mid, int right) {
        int n1 = mid - left + 1;
        int n2 = right - mid;

        int Left[] = new int[n1];
        int Right[] = new int[n2];

        // Copy data to temp arrays
        for (int i = 0; i < n1; ++i)
            Left[i] = arr[left + i];
        for (int j = 0; j < n2; ++j)
            Right[j] = arr[mid + 1 + j];

        int i = 0, j = 0, k = left;

        // Merge the temp arrays
        while (i < n1 && j < n2) {
            if (Left[i] <= Right[j]) {
                arr[k] = Left[i];
                i++;
            } else {
                arr[k] = Right[j];
                j++;
            }
            k++;
        }

        // Copy remaining elements
        while (i < n1) {
            arr[k] = Left[i];
            i++;
            k++;
        }
        while (j < n2) {
            arr[k] = Right[j];
            j++;
            k++;
        }
    }

    // Print array
    static void printArray(int arr[]) {
        for (int i = 0; i < arr.length; ++i)
            System.out.print(arr[i] + " ");
        System.out.println();
    }
}
```

**Output:**

```
Unsorted Array
38 27 43 3 9 82 10

Sorted array
3 9 10 27 38 43 82
```

---

#### Performance

**Time Complexity (Big-O Notation):**

| Case             | Complexity |
| ---------------- | ---------- |
| **Best Case**    | Ω(n log n) |
| **Average Case** | θ(n log n) |
| **Worst Case**   | O(n log n) |

**Space Complexity:** O(n) — extra space is used for temporary arrays during the merge step.

**Notes:**

* Merge Sort is **stable**, meaning it preserves the order of equal elements.
* Unlike other algorithms, **performance is consistent** regardless of the input's initial order.
* It is preferred for **linked lists** and large datasets.
* Used in real-world systems — e.g., **Linux kernel** for sorting linked lists, and **Python’s `sorted()`** function.

---

#### Lesson Summary

* **Merge Sort** is a divide and conquer algorithm that recursively divides the array and merges the sorted subarrays.
* It guarantees **O(n log n)** performance for all input cases.
* The algorithm is **stable** and works efficiently with both arrays and linked lists.
* A full Java implementation demonstrates the key steps — `divide`, `sort`, and `merge`.
* Merge Sort is **reliable** and **predictable**, which is why it is used in high-performance applications and system libraries.

---

#### Key Terms

* **Merge Sort**: A divide-and-conquer sorting algorithm
* **Divide and Conquer**: Problem-solving strategy of breaking a problem into subproblems
* **Subarray**: A portion of an array created during recursive division
* **Merge Step**: Combines two sorted arrays into one
* **Time Complexity – O(n log n)**: Predictable performance across best, average, and worst cases
* **Space Complexity – O(n)**: Extra memory used for merging
* **Stability**: Maintains the order of equal elements

### Section 10: Quick Sort in Java

#### Definition

**Quick Sort** is a highly efficient **exchange-based sorting algorithm** that uses the **divide and conquer** strategy. It was developed by **Tony Hoare** in the 1960s and remains one of the fastest internal sorting techniques.

> It works by selecting a pivot, partitioning the array around the pivot, and then recursively applying the same strategy to the subarrays.

---

#### Internal vs. External Sorting

There are two main types of sorting approaches:

* **Internal Sorting** – Entire data fits in memory
* **External Sorting** – Data exceeds memory, requires disk access and merge operations

> Quick Sort is an **internal sorting** algorithm — we assume the entire data set fits in memory.

---

#### Quick Sort – Algorithm Steps

1. Choose a **pivot** element (e.g., the first or last item).
2. Partition the array so that:

   * Elements **less than the pivot** go to the left
   * Elements **greater than the pivot** go to the right
3. Recursively apply this process to the left and right subarrays.

---

#### Pseudocode

```plaintext
algorithm qsort(data[], left, right)
    if left >= right
        return

    swap data[left] with data[(left + right) / 2]
    last = left

    for i = left + 1 to right
        if data[i] < data[left]
            swap data[++last] with data[i]

    swap data[left] with data[last]

    qsort(data[], left, last - 1)
    qsort(data[], last + 1, right)
```

---

#### Java Implementation

```java
public class Main {

    // Partitioning logic
    int partition(int a[], int start, int end) {
        int pivot = a[end];
        int i = (start - 1);
        for (int j = start; j <= end - 1; j++) {
            if (a[j] < pivot) {
                i++;
                int t = a[i];
                a[i] = a[j];
                a[j] = t;
            }
        }
        int t = a[i + 1];
        a[i + 1] = a[end];
        a[end] = t;
        return (i + 1);
    }

    // Recursive Quick Sort function
    void quicksort(int a[], int start, int end) {
        if (start < end) {
            int p = partition(a, start, end);
            quicksort(a, start, p - 1);
            quicksort(a, p + 1, end);
        }
    }

    // Print array
    private void printList(int a[], int n) {
        for (int i = 0; i < n; i++)
            System.out.print(a[i] + " ");
    }

    // Main method
    public static void main(String args[]) {
        int a[] = {24, 2, 45, 20, 56, 75, 16, 56, 99, 53, 12};
        int len = a.length;

        System.out.println("Below is the unsorted list.\n");
        Main qs = new Main();
        qs.printList(a, len);

        qs.quicksort(a, 0, len - 1);

        System.out.println("\n\nBelow is the sorted list.\n");
        qs.printList(a, len);
        System.out.println();
    }
}
```

**Output:**

```
Below is the unsorted list.

24 2 45 20 56 75 16 56 99 53 12 

Below is the sorted list.

2 12 16 20 24 45 53 56 56 75 99 
```

---

#### Performance

| Case             | Time Complexity |
| ---------------- | --------------- |
| **Best Case**    | O(n log n)      |
| **Average Case** | O(n log n)      |
| **Worst Case**   | O(n²)           |

**Notes:**

* Quick Sort is faster than most sorting algorithms in practice.
* Performance can degrade to **O(n²)** if the pivot selection is poor (e.g., already sorted list).
* There are two main partitioning schemes:

  * **Hoare’s Scheme** (used above) – starts comparison from both ends.
  * **Lomuto’s Scheme** – uses the last element as pivot and compares sequentially.

---

#### Lesson Summary

* **Quick Sort** is an efficient internal sorting method based on **divide and conquer**.
* It selects a **pivot**, partitions the array, and recursively sorts the subarrays.
* It is implemented using **recursion**, with base cases for when the array section has 0 or 1 elements.
* The algorithm’s **average time complexity is O(n log n)**, making it one of the fastest comparison-based sorting algorithms.
* Different partitioning strategies affect performance, with **Hoare's** and **Lomuto's** being the most common.

---

#### Key Terms

* **Quick Sort**: Divide-and-conquer sorting algorithm using partitioning
* **Pivot**: Element used to partition the array
* **Partitioning**: Rearranging array so elements less than pivot go left; greater go right
* **Recursion**: Function calling itself to break down problems
* **Time Complexity – O(n log n)**: Average and best case
* **Worst Case – O(n²)**: When pivot choice results in unbalanced partitions
* **Internal Sorting**: Sorting done entirely in memory

### Section 11: Sorting Arrays Using Insertion Sort in Java

#### Definition

Sorting is a **fundamental concept** in computer science used to reorder data — for example, **A to Z** or **1 to 10**. When a computer encounters unordered information, it cannot execute it logically without sorting the steps into the proper order.

> Think of a recipe written in the wrong sequence — while humans may rearrange it mentally, a computer needs the steps explicitly sorted.

---

#### Problem Scenario

Imagine you have recipe steps stored as array elements:

```plaintext
[1, 7, 9, 11, 4]
```

These need to be sorted in ascending order to follow the correct procedure. One way to sort this array is with an **Insertion Sort**.

---

#### Insertion Sort – How It Works

* It starts from the second element and moves backward to compare with previous elements.
* If an element is **smaller** than the previous one, it **shifts the larger value one position to the right**.
* This continues until the array is **completely sorted**.

> Insertion sort is intuitive and easy to implement but becomes slow for large arrays.

---

#### Java Implementation

```java
public class Main {
    public static void main(String[] args) {
        int[] steps = {1, 7, 9, 11, 4};

        System.out.println("Before Sort:");
        for (int i = 0; i < steps.length; i++) {
            System.out.print(steps[i] + " ");
        }
        System.out.println();

        // Time check before sorting
        long startTime = System.nanoTime();

        // Call insertion sort method
        sortRecipe(steps);

        // Time check after sorting
        long endTime = System.nanoTime();
        long totalTime = endTime - startTime;

        System.out.println("After Sort:");
        for (int i = 0; i < steps.length; i++) {
            System.out.print(steps[i] + " ");
        }

        System.out.println();
        System.out.println("Time taken: " + totalTime + " ns");
    }

    // Insertion Sort method
    public static void sortRecipe(int[] sortArray) {
        int len = sortArray.length;
        for (int j = 1; j < len; j++) {
            int temp = sortArray[j];
            int i = j - 1;

            while ((i > -1) && (sortArray[i] > temp)) {
                sortArray[i + 1] = sortArray[i];
                i--;
            }

            sortArray[i + 1] = temp;
        }
    }
}
```

---

#### Output

```plaintext
Before Sort:
1 7 9 11 4 

After Sort:
1 4 7 9 11 

Time taken: 3263179 ns
```

> This result shows the sorted steps and how long the sorting operation took.

---

#### Performance and Big-O Notation

* **Time Complexity – O(n²)**
  Because of the **nested loop**, the performance degrades **exponentially** with larger data sets.

* **Space Complexity – O(1)**
  Insertion sort is **in-place** and requires no additional memory.

* **nanoTime() Benchmarking**
  Java’s `System.nanoTime()` can be used to benchmark how long the algorithm takes.

> While efficient for **small arrays**, insertion sort becomes inefficient for **large datasets**, especially in performance-critical applications.

---

#### Lesson Summary

* **Insertion Sort** is a sorting method that repeatedly moves elements into the correct position by shifting larger elements to the right.
* It is simple to implement and performs well for **small or nearly sorted arrays**.
* For large or complex datasets, it is inefficient due to its **O(n²)** time complexity.
* Sorting performance can be measured in Java using `System.nanoTime()` for benchmarking.

---

#### Key Terms

* **Insertion Sort**: Sorting algorithm that builds the final sorted array one item at a time
* **System.nanoTime()**: Java method to measure processing time with nanosecond precision
* **Time Complexity – O(n²)**: Algorithm's performance grows quadratically with input size
* **In-Place Sorting**: Sort that uses no extra memory
* **Shift Operation**: Moving elements to make room for insertion

### Section 12: Binary Search in Java

#### Definition

**Binary Search** is a fast and efficient search algorithm used to find the **position of a target value** within a **sorted array**. It follows the **divide and conquer** approach to narrow down the search space.

> Instead of checking every element linearly, binary search **divides the dataset in half** on each iteration, dramatically improving performance over large datasets.

---

#### How Binary Search Works

1. Identify the **middle element** of the array.
2. Compare the **target value** to the middle element:

   * If equal → return index
   * If less → search the **left half**
   * If greater → search the **right half**
3. Repeat this process recursively or iteratively until the element is found or the subarray size becomes zero.

> **Important:** The array must be **sorted** for binary search to work correctly.

---

#### Example Walkthrough

**Array:**

```plaintext
[20, 30, 40, 50, 80, 90, 100]
```

**Target Value:**
`40`

**Steps:**

1. Middle element = `50` → 50 > 40 → search left half `[20, 30, 40]`
2. Middle element = `30` → 30 < 40 → search right half `[40]`
3. Found target `40` → return index `2`

---

#### Java Implementation

```java
public class BinarySearch {

    // Recursive Binary Search method
    int binarySearch(int arr[], int l, int r, int x) {
        if (r >= l) {
            int mid = l + (r - l) / 2;

            // If element is found at the middle
            if (arr[mid] == x)
                return mid;

            // If target is smaller, search the left subarray
            if (arr[mid] > x)
                return binarySearch(arr, l, mid - 1, x);

            // Else search the right subarray
            return binarySearch(arr, mid + 1, r, x);
        }

        // Element not found
        return -1;
    }

    // Main method to test the search
    public static void main(String args[]) {
        BinarySearch ob = new BinarySearch();
        int arr[] = {20, 30, 40, 50, 80, 90, 100};
        int x = 40;
        int result = ob.binarySearch(arr, 0, arr.length - 1, x);

        if (result == -1)
            System.out.println("Element not present");
        else
            System.out.println("Element found at index " + result);
    }
}
```

**Output:**

```
Element found at index 2
```

---

#### Performance (Big-O Notation)

| Case             | Time Complexity                   |
| ---------------- | --------------------------------- |
| **Best Case**    | O(1) – Found on first try         |
| **Average Case** | O(log n) – Divides list each step |
| **Worst Case**   | O(log n) – Target is not found    |

> Binary search is **much faster** than linear search, especially with large datasets, because it **reduces the search space exponentially**.

---

#### Real-World Applications of Binary Search

* 🔍 **Spell Check & Autocorrect:** Quickly searches large dictionaries for suggested words
* 🎮 **Games:** Used in **pathfinding** and **collision detection** systems
* 📈 **Stock Analysis:** Finds nearest matching prices in sorted datasets
* 💡 **AI Systems:** Efficient filtering or prediction using historical data
* 📚 **Databases & Libraries:** Index lookup and range queries

> Many of these applications fall under modern AI or machine learning systems that rely heavily on **fast lookup** and **matching logic**.

---

#### Lesson Summary

* **Binary Search** efficiently finds the position of a value in a **sorted array**.
* It follows a **divide and conquer** strategy, reducing the search range with each comparison.
* A Java implementation demonstrates its recursive logic.
* The algorithm offers an **average-case performance of O(log n)**.
* Binary search is applied in numerous fields — from **AI** and **games** to **search engines** and **finance**.

---

#### Key Terms

* **Binary Search**: Algorithm to find a target in a sorted array using divide and conquer
* **Middle Element**: The midpoint of the array or subarray currently being searched
* **Divide and Conquer**: Reducing the problem space in half each iteration
* **Time Complexity – O(log n)**: Efficient performance as data size increases
* **Recursive Search**: Function that calls itself with updated parameters
* **Sorted Array**: Required condition for binary search to operate correctly
