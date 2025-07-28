### Section 1: Recursive Functions

#### Definition

A **recursive function** is a function that refers to itself in its own definition. In mathematics and computer science, this means that the function's output at step `n` depends on one or more previous values, such as `n-1`, `n-2`, etc.

A recursive definition always includes:

* **One or more base cases**, which provide specific initial values.
* **A recursive step**, which expresses a rule to compute the function in terms of previous cases.

---

#### Example: The Fibonacci Sequence

A classic example of a recursive function is the **Fibonacci Sequence**.

**Recursive definition:**

* F(1) = 1
* F(2) = 1
* F(n) = F(n–1) + F(n–2), for n > 2

This means each term is the **sum of the two previous terms**.

**First few terms:**

| n | F(n) |
| - | ---- |
| 1 | 1    |
| 2 | 1    |
| 3 | 2    |
| 4 | 3    |
| 5 | 5    |
| 6 | 8    |

This sequence appears in nature, such as the number of petals on many flowers (5, 8, 13, 21, etc.).

---

#### Expanding a Recursive Function

To evaluate a recursive function:

1. **Start with the base values**.
2. **Apply the recursive rule** using previously computed terms.

For the Fibonacci example:

* F(3) = F(2) + F(1) = 1 + 1 = 2
* F(4) = F(3) + F(2) = 2 + 1 = 3
* F(5) = F(4) + F(3) = 3 + 2 = 5

---

#### Another Example

Let’s look at a different recursive function:

* a(1) = 1
* a(n) = a(n–1) + 2

This function **adds 2 to the previous term**.

**First five terms:**

| n | a(n)      |
| - | --------- |
| 1 | 1         |
| 2 | 1 + 2 = 3 |
| 3 | 3 + 2 = 5 |
| 4 | 5 + 2 = 7 |
| 5 | 7 + 2 = 9 |

This is the sequence of **odd numbers**.

---

#### Summary

* A **recursive function** defines each term in terms of previous terms.
* It requires **initial conditions (base cases)** to begin.
* You calculate later values by **applying the recursive rule** repeatedly.
* Recursive sequences like the **Fibonacci Sequence** have real-world applications, especially in nature and computer algorithms.

### Section 2: First-Order Linear Recurrence

#### Definition

A **first-order linear recurrence relation** is an equation that defines each term in a sequence based on the **immediate previous term**. It typically has the form:

$$
u_n = a \cdot u_{n-1} + c
$$

Where:

* $a$ and $c$ are constants,
* $u_{n-1}$ is the previous value in the sequence.

This form looks **one step back** in time (i.e., it's "first-order"), and is **linear**, meaning the previous term is not raised to any power or placed inside a nonlinear function.

---

#### Example: Snowmelt Water Accumulation

Let’s say the amount of water today, $u_n$, is **twice** the amount from the day before, $u_{n-1}$. If we start with 1 gallon of water:

**Recursive definition:**

* $u_0 = 1$
* $u_n = 2 \cdot u_{n-1}$

**First few terms:**

$$
\begin{align*}
u_1 &= 2 \cdot u_0 = 2 \cdot 1 = 2 \\
u_2 &= 2 \cdot u_1 = 2 \cdot 2 = 4 \\
u_3 &= 2 \cdot u_2 = 2 \cdot 4 = 8 \\
\end{align*}
$$

This results in the sequence: **1, 2, 4, 8, …**

---

#### General Form and Higher-Order Cases

A **first-order recurrence** uses only $u_{n-1}$:

$$
u_n = a \cdot u_{n-1} + c
$$

A **second-order recurrence**, on the other hand, uses both $u_{n-1}$ and $u_{n-2}$:

$$
u_n = a \cdot u_{n-1} + b \cdot u_{n-2}
$$

There are also **nonlinear recurrences**, such as:

* $u_n = a \cdot (u_{n-1})^2$
* $u_n = \cos(u_{n-1})$

---

#### Applications

Recurrence relations appear in various fields:

* Population modeling
* Computer algorithm analysis
* Digital signal processing
* Financial forecasting

---

#### Example 1: Bank Account with Deposits and Interest

Suppose you open a bank account with an initial deposit of \$1,000. Each year:

* You deposit another \$1,000
* The account earns **1% interest**

**Initial condition:**
$u_0 = 1,000$

**Recursive relation:**

$$
u_n = 1.01 \cdot u_{n-1} + 1,000
$$

**Computing balances:**

| Year | Calculation                    | Balance  |
| ---- | ------------------------------ | -------- |
| 1    | $u_1 = 1.01(1,000) + 1,000$    | 2,010    |
| 2    | $u_2 = 1.01(2,010) + 1,000$    | 3,030.10 |
| 3    | $u_3 = 1.01(3,030.10) + 1,000$ | 4,060.40 |
| 4    | $u_4 = 1.01(4,060.40) + 1,000$ | 5,101.01 |
| 5    | $u_5 = 1.01(5,101.01) + 1,000$ | 6,152.02 |

After 5 years, you've deposited **\$6,000** and earned **\$152.02** in interest.

---

#### Example 2: Loan with Interest and Monthly Payments

Suppose you borrow \$15,000 from a bank at **10% annual interest**, repaying **\$800 per month**.

**Monthly interest rate:**

$$
\frac{0.10}{12} = 0.00833 \approx 0.008
$$

**Initial balance:**
$u_0 = 15,000$

**Recursive relation:**

$$
u_n = 1.008 \cdot u_{n-1} - 800
$$

**Computing balances:**

| Month | Calculation                        | Balance     |
| ----- | ---------------------------------- | ----------- |
| 1     | $u_1 = 1.008(15,000) - 800$        | 14,320      |
| 2     | $u_2 = 1.008(14,320) - 800$        | 13,634.56   |
| ...   | ...                                | ...         |
| 20    | Final balance drops below \$315.06 | Loan repaid |

Thus, the loan is paid off in under **2 years**.

---

#### Summary

* A **first-order linear recurrence** models a sequence based on a single previous term.
* The general form is:

  $$
  u_n = a \cdot u_{n-1} + c
  $$
* Applications include:

  * Growth modeling (e.g., population)
  * Financial planning (e.g., compound interest, loan repayment)
  * Algorithm analysis
  * Signal processing
* Understanding these models helps predict future outcomes based on initial conditions and consistent rules.

### Section 3: Linear Recurrences

#### Definition

A **linear recurrence** defines a sequence where each term is a **linear combination of previous terms**, based on given initial values. This allows us to compute future terms step-by-step using only prior values and the recurrence rule.

**Examples of sequences:**

| Sequence                  | Rule                                         | Next Term |
| ------------------------- | -------------------------------------------- | --------- |
| 1, 2, 4, 8, 16, 32, 64, … | Each term is **double** the previous one     | 128       |
| 1, 1, 2, 3, 5, 8, 13, …   | Each term is the **sum of the two previous** | 21        |
| 1, 5, 13, 41, 121, 365, … | Each term is **2×(i–1)th + 3×(i–2)th**       | 1093      |

A sequence is said to be a **homogeneous linear recurrence of order $k$** if:

* It has $k$ initial values.
* The $i$-th term is a **linear combination** of the previous $k$ terms.

---

#### Solving a Homogeneous Linear Recurrence

To find a **closed-form formula** (i.e., directly calculate the $n$-th term), follow three main steps:

1. **Find the characteristic equation.**
2. **Solve the characteristic equation** to find roots.
3. **Use the roots and initial conditions** to calculate solution coefficients.

---

#### Finding the Characteristic Equation

Assume the sequence follows powers of a variable $s$. This leads to forming a polynomial equation from the recurrence relation. The resulting **characteristic equation** helps derive a closed-form.

**Example sequence:**
<1, 5, 13, 41, 121, 365, 1093, …>
Defined by:

$$
u_i = 2u_{i-1} + 3u_{i-2}
$$

This leads to the **characteristic equation**:

$$
s^2 - 2s - 3 = 0
$$

---

#### Finding the Roots

Solving the characteristic equation gives us the **roots** $s_1, s_2, ..., s_k$.

For the example:

$$
s^2 - 2s - 3 = 0 \Rightarrow (s - 3)(s + 1) = 0
$$

**Roots:**
$s_1 = 3$, $s_2 = -1$

---

#### Computing the Solution Coefficients

Next, form a general solution using the roots:

$$
u_i = f_1 \cdot (3)^i + f_2 \cdot (-1)^i
$$

Using the initial values (e.g., $u_0 = 1$, $u_1 = 5$), solve the linear system to determine $f_1$ and $f_2$.

---

#### Non-Homogeneous Linear Recurrences

A **non-homogeneous** recurrence has an extra term $g(i)$, making it dependent on $i$ directly:

$$
u_n = a_1u_{n-1} + a_2u_{n-2} + \dots + a_ku_{n-k} + g(n)
$$

To solve:

1. Find the **homogeneous solution** $h_i$.
2. Find a **particular solution** $b_i$ to the full equation.
3. Combine them:

   $$
   u_i = h_i + b_i
   $$

---

#### Example: Non-Homogeneous Recurrence

**Given sequence:**
<1, 5, 18, 58, 179, 543, …>
**Recurrence rule:**

$$
u_i = 2u_{i-1} + 3u_{i-2} + (2i + 1)
$$

* The homogeneous part is already known (same as previous example).
* Now define $b_i = p \cdot i + q$

Substitute into the recurrence to solve for $p$ and $q$:

$$
0 = (4p + 2)i - 8p + 4q + 1
$$

Solving:

* $p = -\frac{1}{2}$
* $q = -\frac{5}{4}$

Thus,

$$
b_i = \frac{-2i - 5}{4}
$$

---

#### Final Solution

Now combine:

$$
u_i = f_1 \cdot (3)^i + f_2 \cdot (-1)^i + \frac{-2i - 5}{4}
$$

Then, use initial values (e.g., $u_0 = 1$, $u_1 = 5$) to solve for $f_1$ and $f_2$, giving a complete closed-form solution for the sequence.

---

#### Summary

* **Linear recurrence relations** define terms based on previous terms.
* **Homogeneous** ones have no external input (pure recursion).
* **Non-homogeneous** ones include a function of $i$.
* Solving involves:

  * Finding the **characteristic equation**
  * **Solving for roots**
  * **Building closed-form expressions** using initial values and, when needed, a particular solution.

### Section 4: Divide-and-Conquer

#### Definition

**Divide-and-conquer** is a powerful algorithmic strategy that involves **dividing a large problem into smaller sub-problems**, solving each recursively, and then **combining their solutions** to solve the original problem. This method repeats the division process until the sub-problems are small and manageable (usually base cases).

This strategy "divides" a problem into sub-problems and "conquers" the original problem by assembling the results.

---

#### Estimating Complexity

The **computational complexity** of a divide-and-conquer algorithm can often be modeled using a **recurrence relation**. If a problem of size $n$ is divided into $a$ sub-problems of size $n/b$, and if $g(n)$ is the time required to combine the solutions, then the total time $f(n)$ is given by:

$$
f(n) = a \cdot f\left(\frac{n}{b}\right) + g(n)
$$

This recurrence is key to estimating the performance of divide-and-conquer algorithms.

---

#### Example: Binary Search

Binary search works on a **sorted list** and seeks to find a target item:

* It compares the target with the middle element.
* If not found, it eliminates half the list and repeats on the other half.
* This continues until either the item is found or the list is reduced to one element.

**Recurrence relation:**

$$
f(n) = f\left(\frac{n}{2}\right) + 2
$$

Here:

* $a = 1$ (one sub-problem)
* $b = 2$ (problem size halved)
* Two comparisons are added each time.

---

#### Example: Finding Max and Min

To find the **maximum and minimum** in a list of $n$ elements:

* The list is split into two halves.
* Max/min are found in each half recursively.
* Two comparisons are used to find the final max and min from the two halves.

**Recurrence relation:**

$$
f(n) = 2 \cdot f\left(\frac{n}{2}\right) + 2
$$

Here:

* $a = 2$, $b = 2$
* Two extra comparisons are made each level.

---

#### Solving Recurrences: Master Theorem

The **Master Theorem** provides a way to solve recurrences of the form:

$$
f(n) = a \cdot f\left(\frac{n}{b}\right) + O(n^d)
$$

Where:

* $a \geq 1$: number of sub-problems
* $b > 1$: factor by which the problem size is reduced
* $d \geq 0$: rate of work done to combine the results

**Cases:**

1. If $a < b^d$ → $f(n) = O(n^d)$
2. If $a = b^d$ → $f(n) = O(n^d \log n)$
3. If $a > b^d$ → $f(n) = O(n^{\log_b a})$

---

#### Applying the Master Theorem

**Binary Search:**

$$
f(n) = f\left(\frac{n}{2}\right) + 2
$$

* $a = 1$, $b = 2$, $d = 0$
* Since $a = b^d$, Case 2 applies:

  $$
  f(n) = O(\log n)
  $$

---

**Max and Min:**

$$
f(n) = 2 \cdot f\left(\frac{n}{2}\right) + 2
$$

* $a = 2$, $b = 2$, $d = 0$
* $a > b^d$, so Case 3 applies:

  $$
  f(n) = O(n)
  $$

---

**Strassen’s Matrix Multiplication:**

$$
f(n) = 7 \cdot f\left(\frac{n}{2}\right) + O(n^2)
$$

* $a = 7$, $b = 2$, $d = 2$
* Since $7 > 2^2 = 4$, Case 3 applies:

  $$
  f(n) = O(n^{\log_2 7}) \approx O(n^{2.81})
  $$

---

#### Summary

* **Divide-and-conquer** breaks a problem into smaller pieces, solves them recursively, and combines the results.
* **Recurrence relations** model the computational cost.
* The **Master Theorem** helps solve these recurrences by comparing growth rates.
* Examples:

  * **Binary Search**: $O(\log n)$
  * **Max and Min**: $O(n)$
  * **Strassen’s Matrix Multiplication**: $O(n^{2.81})$

### Section 5: Ordinary Generating Functions

#### Definition

An **ordinary generating function (OGF)** is a powerful tool in discrete mathematics used to encode a sequence into a **polynomial-like expression**. This representation helps in analyzing, manipulating, and even finding closed forms of sequences.

If a sequence is:

$$
a_0, a_1, a_2, a_3, \dots
$$

Its ordinary generating function is:

$$
A(x) = a_0 + a_1x + a_2x^2 + a_3x^3 + \dots
$$

This function is not evaluated at any specific value of $x$; rather, it's treated symbolically to capture the behavior of the sequence.

---

#### Example: Natural Numbers

For the sequence $0, 1, 2, 3, 4, \dots$, the generating function is:

$$
A(x) = 0 + 1x + 2x^2 + 3x^3 + 4x^4 + \dots
$$

This series can be expressed in closed form as:

$$
\frac{x}{(1 - x)^2}
$$

---

#### Operations on Generating Functions

There are four key operations you can apply to generating functions. Each corresponds to a simple transformation of the original sequence.

---

#### 1. Scaling a Generating Function

If every term in a sequence is multiplied by a constant $k$, then its generating function is also multiplied by $k$.

**Example:**
Original sequence: $0, 1, 2, 3, 4, \dots$
Generating function: $\frac{x}{(1 - x)^2}$

After scaling by 3:
New sequence: $0, 3, 6, 9, 12, \dots$
New generating function:

$$
3 \cdot \frac{x}{(1 - x)^2}
$$

---

#### 2. Addition of Two Generating Functions

Adding two sequences element-wise results in a new sequence whose generating function is the **sum** of the two original generating functions.

**Example:**
Sequence A: $1, 1, 1, 1, \dots$ → $\frac{1}{1 - x}$
Sequence B: $1, 2, 3, 4, \dots$ → $\frac{x}{(1 - x)^2}$

Sum: $2, 3, 4, 5, \dots$ →
Generating function:

$$
\frac{1}{1 - x} + \frac{x}{(1 - x)^2}
$$

---

#### 3. Right-Shifting a Sequence

Right-shifting a sequence by inserting $z$ zeros at the beginning multiplies its generating function by $x^z$.

**Example:**
Original sequence: $1, 2, 3, 4, \dots$ → $\frac{x}{(1 - x)^2}$
Right-shifted by 1 (new sequence: $0, 1, 2, 3, \dots$):
Generating function becomes:

$$
x \cdot \frac{x}{(1 - x)^2} = \frac{x^2}{(1 - x)^2}
$$

---

#### 4. Multiplication of Two Sequences

Multiplying two sequences using **convolution** gives a new sequence where each term is a sum of products of elements from the original sequences, in reverse index order.

If sequences $A = \{a_0, a_1, a_2, \dots\}$ and $B = \{b_0, b_1, b_2, \dots\}$, then:

$$
c_n = \sum_{i=0}^{n} a_i \cdot b_{n-i}
$$

The generating function of the product sequence $C$ is:

$$
C(x) = A(x) \cdot B(x)
$$

**Example:**

Let:

* Sequence A: $1, 2, 3, 4, 5, 6$
* Sequence B: $1, -1, 1, -1, \dots$

Resulting sequence $C$:

$$
1, 1, 2, 2, 3, 3, \dots
$$

---

#### Summary

* **Ordinary generating functions** encode sequences into power series.
* They simplify manipulation of sequences for:

  * Proving properties
  * Finding closed forms
  * Calculating sums
* **Key operations** on generating functions include:

  * **Scaling:** Multiply the generating function by a constant.
  * **Addition:** Add two generating functions.
  * **Right-shifting:** Multiply by $x^z$ for $z$ shifts.
  * **Multiplication:** Convolve two sequences through generating function multiplication.

### Section 6: Inclusion-Exclusion Principle

#### Definition

The **inclusion-exclusion principle** helps to accurately count the number of elements in the **union of multiple sets**, especially when elements may belong to **more than one set**. It avoids overcounting by **subtracting intersections** appropriately.

---

#### Basic Set Theory

* A **set** is a collection of elements.
* The **cardinality** of a set $A$ is the number of elements in it, denoted $|A|$.
* The **union** $A \cup B$: elements in A or B or both.
* The **intersection** $A \cap B$: elements in both A and B.
* The **universe** $U$: all possible elements under consideration.

---

#### Inclusion-Exclusion with Two Sets

To find the number of elements in $A \cup B$, use:

$$
|A \cup B| = |A| + |B| - |A \cap B|
$$

**Why subtract?** Because elements in both sets are counted twice when summing $|A| + |B|$.

**Example:**

* 10 own dogs (D), 12 own cats (C), 5 own both

$$
|D \cup C| = 10 + 12 - 5 = 17
$$

**Example (Complement):**

* 100 students
* 20 in Discrete Math (D), 30 in Java (J), 6 in both
* Students in neither:

$$
|D \cup J| = 20 + 30 - 6 = 44 \Rightarrow 100 - 44 = 56
$$

**Example (Difference):**

* Students in Discrete Math but not Java:

$$
|D| - |D \cap J| = 20 - 6 = 14
$$

---

#### Inclusion-Exclusion with Three Sets

When working with three sets $A$, $B$, and $C$:

$$
|A \cup B \cup C| = |A| + |B| + |C| - |A \cap B| - |A \cap C| - |B \cap C| + |A \cap B \cap C|
$$

This formula:

* Adds individual set sizes
* Subtracts pairwise intersections
* Adds back the triple intersection

**Example:**

* 100 students
* 20 in D, 30 in J, 25 in W
* 6 in D ∩ J, 8 in D ∩ W, 10 in J ∩ W
* 5 in D ∩ J ∩ W

$$
|D \cup J \cup W| = 20 + 30 + 25 - 6 - 8 - 10 + 5 = 56
$$

---

#### Solving for the Intersection

If you're given $|A \cup B \cup C|$ and all other values except $|A \cap B \cap C|$, you can solve for it by rearranging the formula.

---

#### General Inclusion-Exclusion Formula

For $n$ finite sets $A_1, A_2, \dots, A_n$, the general formula is:

$$
\left|\bigcup_{i=1}^{n} A_i\right| = \sum |A_i| - \sum |A_i \cap A_j| + \sum |A_i \cap A_j \cap A_k| - \dots + (-1)^{n+1} |A_1 \cap A_2 \cap \cdots \cap A_n|
$$

**Example for 4 sets:**

$$
|A \cup B \cup C \cup D| = \sum |A_i| - \sum |A_i \cap A_j| + \sum |A_i \cap A_j \cap A_k| - |A \cap B \cap C \cap D|
$$

---

#### Summary

* The **inclusion-exclusion principle** provides an accurate count of the union of sets with overlapping elements.
* With two or three sets, the principle helps adjust for overcounts.
* The **general formula** applies to any number of sets $n$.
* It is based on alternating sums of intersections of increasing size.
* Essential in **counting problems**, **probability**, and **combinatorics**.
