### Section 1: Understanding Sequences

#### What Is a Sequence?

A **sequence** is an ordered list of elements (typically numbers) that follow a particular pattern. Sequences can be:

* **Finite** – they have a definite number of terms (e.g., `-10, -5, 0, 5`)
* **Infinite** – they continue indefinitely (e.g., `1, 2, 3, 4, 5, …`)

Each element in a sequence is called a **term**, and sequences are central to the study of patterns in mathematics.

---

#### Terminology of Sequences

* Terms in a sequence are typically written as `a₁`, `a₂`, `a₃`, ..., `aₙ`

  * `a₁` is the first term
  * `aₙ` is the **nth term**, a general term formula used to find any value in the sequence
* Subscripts identify the position of a term in the sequence

Example:

> In the sequence `5, 10, 20, 40, 80, …`
> `a₁ = 5`, `a₂ = 10`, `a₃ = 20`, etc.

---

#### Types of Sequences

##### Arithmetic Sequences

* Formed by **repeated addition** of a constant value (called the common difference `d`)
* General form:
  `aₙ = a₁ + (n - 1)d`

Example:

> `1, 2, 3, 4, 5, …`
> Common difference `d = 1`

##### Geometric Sequences

* Formed by **repeated multiplication** of a constant value (called the common ratio `r`)
* General form:
  `aₙ = a₁ × rⁿ⁻¹`

Example:

> `5, 10, 20, 40, 80, …`
> Common ratio `r = 2`

---

#### The Fibonacci Sequence

* A famous **recursive sequence**, where each term is the sum of the two preceding terms:

  * `a₁ = 0`, `a₂ = 1`
  * `aₙ = aₙ₋₁ + aₙ₋₂` for `n ≥ 3`

Example:

> `0, 1, 1, 2, 3, 5, 8, 13, 21, 34, …`

* Appears frequently in **nature**, such as:

  * Spiral patterns in **sunflowers, pine cones, and pineapples**
  * The **number of petals** on many flowers
  * The **shape of seashells** modeled by Fibonacci spirals

---

#### Recursive Sequences

A **recursive sequence** is one where each term is defined in relation to previous terms.

* General recursive form:
  `aₙ = f(aₙ₋₁, aₙ₋₂, …)`

Example (Fibonacci):

> `aₙ = aₙ₋₁ + aₙ₋₂`

---

#### Summary

* A **sequence** is a list of terms following a pattern, either **finite** or **infinite**
* Terms are represented using subscript notation (e.g., `aₙ`)
* **Arithmetic sequences** use repeated addition; **geometric sequences** use repeated multiplication
* The **Fibonacci sequence** is a recursive pattern found in nature
* Understanding sequences helps uncover **mathematical structure and real-world patterns**

### Section 2: Sequences

#### What Is a Sequence?

A **sequence** is an ordered list of items, typically numbers or symbols, that follow a specific pattern or rule. Because the elements are arranged in a particular **order**, sequences help us identify structure and predict future terms.

*Example:*
The **counting numbers** {1, 2, 3, 4, 5, …} form one of the most familiar infinite sequences.

---

#### Finite Sequences

A **finite sequence** contains a limited number of elements. These sequences eventually come to an end.

*Examples:*

* `{1, 2, 3, 4, 5, 6, 7, 8, 9, 10}` – counting up by ones, ending at 10
* `{2, 4, 6, 8}` – first four even numbers
* `{10, 8, 6, 4, 2, 0}` – counting down by twos
* `{a, b, c, …, z}` – finite sequence of alphabet letters
* `{s, a, r, a, h}` – letters in the name "Sarah"

Each has a clear starting and ending point, and an identifiable **rule** or pattern.

---

#### Infinite Sequences

An **infinite sequence** continues endlessly without stopping. It is often written using three dots (`...`) to indicate continuation.

*Examples:*

* `{1, 2, 3, 4, …}` – infinite counting numbers
* `{0, 1, 0, 1, 0, 1, …}` – alternating zeros and ones
* `{16, 8, 4, 2, 1, …}` – each term is half of the previous
* `{5, 10, 15, 20, 25, …}` – all multiples of 5

Infinite sequences are especially useful in mathematics when exploring **limits, convergence**, and **series**.

---

#### Why Sequences Matter

Understanding sequences helps us:

* Recognize and extend patterns
* Perform arithmetic operations more efficiently (e.g., on a number line)
* Solve real-world problems in **growth, decay, and prediction**

Sequences show up in numerous areas:

* Number theory
* Algebra
* Computer science
* Economics and finance

---

#### Sample Problem

If a tree starts with **0 oranges** and produces **5 new oranges per day**, we can model the number of oranges with a sequence:

`{0, 5, 10, 15, 20, …, 145}`

* This is a **finite arithmetic sequence** with:

  * First term `a₁ = 0`
  * Common difference `d = 5`
  * Last term `aₙ = 145`

By day 30, the tree will have produced:

`aₙ = 5 × 29 = 145` oranges (since `a₁ = 0`, day 1 = term 1 = 0)

Thus, the tree generates a large number of oranges over time, and a sequence helps us quantify that growth.

### Section 3: The Arithmetic Sequence of Stadium Seating

#### What Is an Arithmetic Sequence?

An **arithmetic sequence** is a list of terms where each term increases (or decreases) by a fixed amount called the **common difference**. This difference is added repeatedly to generate the sequence.

*Examples:*

* `11, 13, 15, 17, 19` → Common difference `+2`
* `30, 20, 10, 0, -10, …` → Common difference `–10`

#### Real-World Context: Stadium Seating

In a stadium, rows often increase in the number of seats to accommodate the growing space toward the back. Consider a theater where:

* 1st row = 35 seats
* Each next row = 4 more seats than the previous one

This creates the arithmetic sequence:
`35, 39, 43, 47, 51, 55, 59, …`

---

#### Using a Formula to Find the *n*th Term

Manually listing terms works for small numbers, but not when calculating rows like the 91st. That’s where the **explicit formula** helps.

#### General Formulas:

1. **Using a₀ (0th term)**

   $$
   a_n = dn + a_0
   $$
2. **Using a₁ (1st term)**

   $$
   a_n = d(n - 1) + a_1
   $$

Where:

* `a_n` = the nth term
* `d` = common difference
* `a_0` or `a_1` = the starting value (0th or 1st term)

---

#### Deriving the Formula from the Seating Example

* 1st term (a₁) = 35
* Common difference (d) = 4
* 0th term (a₀) = 35 – 4 = 31

So we get:

* **Formula with a₀:**

  $$
  a_n = 4n + 31
  $$
* **Formula with a₁:**

  $$
  a_n = 4(n - 1) + 35
  $$

#### Example: Find number of seats in the 91st row

Using either formula:

$$
a_{91} = 4 \cdot 91 + 31 = 364 + 31 = 395
$$

There are **395 seats** in the 91st row.

---

#### Finding the Rule from Two Given Terms

Suppose:

* 5th term (a₅) = 22
* 12th term (a₁₂) = 64

#### Step 1: Find the common difference

There are 7 steps between a₅ and a₁₂:

$$
d = \frac{64 - 22}{7} = 6
$$

#### Step 2: Find the 0th term

Go back 5 steps from a₅:

$$
a_0 = 22 - 5 \cdot 6 = -8
$$

#### Step 3: Write the formula

* **Using a₀:**

  $$
  a_n = 6n - 8
  $$
* **Using a₁ = 6(1) + a₀ = -2:**

  $$
  a_n = 6(n - 1) - 2
  $$

---

#### Lesson Summary

* Arithmetic sequences are built using **repeated addition**, and resemble **linear equations**.
* The general rule is:

  $$
  a_n = dn + a_0 \quad \text{or} \quad a_n = d(n - 1) + a_1
  $$
* The **common difference (d)** is constant between terms.
* You can build a formula from the **first term and common difference**, or from **any two known terms** using simple algebra.
* This method allows quick calculation of any term, even far from the beginning of the sequence.

### Section 4: Geometric Sequences of Views of Cat Videos

#### What Is a Geometric Sequence?

A *geometric sequence* is a numerical pattern where each term is generated by **repeated multiplication**. Every term is obtained by multiplying the previous one by a constant value known as the **common ratio**.

*Examples:*

* Finite: `{5, 10, 20, 40, 80}` (common ratio = 2)
* Infinite: `{8, 4, 2, 1, ½, ¼, …}` (common ratio = ½)

These patterns appear frequently in real-world phenomena, including viral content growth online.

#### Viral Cat Video Views: A Geometric Growth Story

Imagine:

* Day 1: 2 people see your video (you and your girlfriend)
* Day 2: Each tells 3 friends → 6 new hits
* Day 3: Each of those 6 tells 3 more → 18 hits
* And so on...

This results in the sequence:
`a₁ = 2, a₂ = 6, a₃ = 18, a₄ = 54, a₅ = 162, a₆ = 486`

Each day, the number of new views multiplies by 3 — a geometric pattern with:

* First term `a₁ = 2`
* Common ratio `r = 3`

#### Finding a General Formula

By examining the pattern:

* `a₂ = 2 × 3¹`
* `a₃ = 2 × 3²`
* `a₄ = 2 × 3³`
* …
* `a₆ = 2 × 3⁵`

This gives the general rule for any day `n`:

> `aₙ = 2 × 3ⁿ⁻¹`

This formula allows you to compute any term in the sequence directly without calculating previous terms.

#### Example: Views on Day 14

To find new hits on day 14:

> `a₁₄ = 2 × 3¹³ = 2 × 1,594,323 = 3,188,646`

**Result:** 3,188,646 new views on the 14th day — viral status achieved!

#### General Rule for Geometric Sequences

The formula for the nth term of a geometric sequence is:

> `aₙ = a₁ × rⁿ⁻¹`

Where:

* `a₁` = first term
* `r` = common ratio
* `n` = term number

You can verify the common ratio by dividing any term by its previous term.

#### Finding a Geometric Rule from Two Terms

Suppose:

* `a₃ = 9/4`
* `a₆ = 243/32`

**Step 1: Use the formula**
From `a₃ × r³ = a₆`, substitute:

> `9/4 × r³ = 243/32`

Multiply both sides by `4/9`:

> `r³ = (243/32) × (4/9) = 27/8`

Take the cube root of both sides:

> `r = ³√(27/8) = 3/2`

**Step 2: Work backward to find a₁**

Divide by `r = 3/2` twice:

* `a₂ = 9/4 ÷ 3/2 = 3/2`
* `a₁ = 3/2 ÷ 3/2 = 1`

**Final formula:**

> `aₙ = 1 × (3/2)ⁿ⁻¹`
> Or simply:
> `aₙ = (3/2)ⁿ⁻¹`

#### Summary

* A **geometric sequence** is defined by repeated multiplication.
* The **general formula** is `aₙ = a₁ × rⁿ⁻¹`.
* It helps you find any term efficiently — especially when terms are far from the start.
* This pattern is foundational in understanding exponential growth, finance, and viral media trends.

### Section 5: Understanding a Number Series

#### What Is a Series?

A *sequence* becomes a *series* when you **add** all its entries together.
For example:

* Sequence: `5, 6, 7, 8`
* Series: `5 + 6 + 7 + 8`

A series gives us the total accumulation of a pattern, such as the total number of seats in the first 34 rows of a stadium.

#### Series Notation Using Sigma

Instead of writing:

```
35 + 39 + 43 + … + 167
```

We use **sigma notation** (summation notation) as a concise mathematical shorthand.

Sigma notation has three parts:

* **Below the sigma (Σ):** Starting index, e.g., `n = 1`
* **Above the sigma:** Ending index, e.g., `n = 34`
* **To the right of the sigma:** Rule for the nth term, e.g., `4n + 31`

Using this, the total seats in the first 34 rows (with 4 more seats each row, starting from 35) is written as:

```
Σ (4n + 31), from n = 1 to 34
```

#### Building a Series Formula

Consider the geometric sequence:

```
5 + 10 + 20 + 40 + 80 + 160 + 320 + …
```

To express this using summation notation:

* First term: `a₁ = 5`
* Common ratio: `r = 2`
* General term: `aₙ = 5 × 2ⁿ⁻¹`

The full summation notation is:

```
Σ (5 × 2ⁿ⁻¹), from n = 1 to ∞
```

The infinity symbol indicates the series continues indefinitely (an **infinite series**).

#### Breaking Down a Series Formula

Suppose you are given:

```
Σ (n² - 1), from n = 3 to 5
```

This instructs you to compute the sum of the terms from the third to the fifth in the sequence defined by `aₙ = n² - 1`.

* a₃ = 3² - 1 = 8
* a₄ = 4² - 1 = 15
* a₅ = 5² - 1 = 24

Total sum: `8 + 15 + 24 = 47`

#### Summary

* A **series** is the sum of the terms in a sequence.
* **Sigma notation** (summation notation) is used to represent series compactly.
* The format is:

  * Below sigma: starting index (e.g., `n = 1`)
  * Above sigma: ending index or ∞
  * Right of sigma: expression for the nth term

This notation allows for precise and efficient calculation of series without manually listing every term.

### Section 6: What Is an Arithmetic Series?

#### Understanding Arithmetic Series

An **arithmetic sequence** is a list of numbers increasing by the same amount each time, such as:

```
1, 2, 3, 4, 5, …
```

An **arithmetic series** is the result of adding the terms of such a sequence:

```
1 + 2 + 3 + 4 + 5 + …
```

#### Gauss’s Discovery

Karl Friedrich Gauss, while still a child, discovered a pattern that allows arithmetic series to be summed quickly. When asked to find the sum from 1 to 100, he noticed:

* First + last term = 1 + 100 = 101
* Second + second-to-last = 2 + 99 = 101
* Third + third-to-last = 3 + 98 = 101

This repeated for all pairs. With 100 numbers, there are 50 such pairs:

```
50 × 101 = 5050
```

#### The Arithmetic Series Formula

From Gauss's insight, we get the general formula for any arithmetic series:

```
Sₙ = (n / 2) × (a₁ + aₙ)
```

Where:

* `Sₙ` = sum of the series
* `n` = number of terms
* `a₁` = first term
* `aₙ` = last term

This formula applies to **any** arithmetic series.

#### Solving the Michigan Stadium Problem

Suppose each stadium row has a number of seats that increases by 4 seats per row, starting from 35 in the first row. This forms the arithmetic sequence:

```
aₙ = 4n + 31
```

To find the **total number of seats from row 1 to row 96**, we apply the arithmetic series formula.

* First term: `a₁ = 4(1) + 31 = 35`
* Last term: `a₉₆ = 4(96) + 31 = 415`
* Number of terms: `n = 96`

Apply the formula:

```
S₉₆ = (96 / 2) × (35 + 415)
S₉₆ = 48 × 450 = 21,600
```

So, there are **21,600 seats** in that section of Michigan Stadium.

#### Summary

To add the terms of an arithmetic sequence efficiently:

* Pair the first and last terms.
* Multiply their sum by the number of pairs:

```
Sₙ = (n / 2)(a₁ + aₙ)
```

This allows rapid computation of long arithmetic series like the one used in the Michigan Stadium seating example.

### Section 7: How Many Views Will We Get?

#### From Geometric Sequence to Geometric Series

In a previous lesson, we learned that a video getting 2 hits on day 1 and then tripling in views each subsequent day results in over 3,000,000 *new* hits by day 14. But if we want to find the **total** views over the first two weeks, we need to **add up** each day's hits — turning a geometric sequence into a **geometric series**.

#### Proving the Formula for a Finite Geometric Series

Let a geometric sequence begin with a₁. Then the series looks like:

```
S = a₁ + a₁r + a₁r² + a₁r³ + ... + a₁rⁿ⁻¹
```

Multiply both sides by `r`:

```
rS = a₁r + a₁r² + a₁r³ + ... + a₁rⁿ
```

Now subtract the two equations:

```
S - rS = a₁ - a₁rⁿ
```

Factor out both sides:

```
S(1 - r) = a₁(1 - rⁿ)
```

Solve for `S`:

```
S = a₁(1 - rⁿ) / (1 - r)
```

This is the formula for a **finite geometric series**.

#### Applying the Formula: Total Views in Two Weeks

The number of new views each day followed the rule:

```
aᵢ = 2 * 3⁽ⁱ⁻¹⁾
```

So:

* a₁ = 2
* r = 3
* n = 14

Plug into the formula:

```
S = 2(1 - 3¹⁴) / (1 - 3)
```

Evaluate step-by-step:

* 3¹⁴ = 4,782,969
* 1 - 3¹⁴ = -4,782,968
* Denominator: 1 - 3 = -2
* S = 2 × (-4,782,968) / (-2) = 4,782,968

**Total views in 14 days: 4,782,968**

#### Infinite Geometric Series

If `r > 1`, the series grows infinitely and **does not converge**.

But if `0 < r < 1`, the series **converges** and can be summed using:

```
S = a₁ / (1 - r)
```

#### Example: A Bouncing Ball

Suppose a ball travels:

* 2 feet on the first bounce
* Then 1/4 as far on each subsequent bounce

This forms a geometric sequence:

```
aᵢ = 2 * (0.25)⁽ⁱ⁻¹⁾
```

This is an infinite geometric series, so:

```
S = 2 / (1 - 0.25) = 2 / 0.75 = 8 / 3 ≈ 2.6667 feet
```

The ball travels approximately **2.67 feet in total**.

#### Summary

* The sum of a **finite geometric series** is:

  ```
  S = a₁(1 - rⁿ) / (1 - r)
  ```

* The sum of an **infinite geometric series** (only if `0 < r < 1`) is:

  ```
  S = a₁ / (1 - r)
  ```

These formulas make it possible to calculate total values from repeated multiplicative patterns quickly and accurately.

### Section 8: Intro to Practice Problems

#### Key Formulas to Remember

To solve problems involving arithmetic and geometric series, you need to know two essential formulas:

* **Arithmetic Series Formula**:
  `Sₙ = (n / 2)(a₁ + aₙ)`

* **Geometric Series Formula** (finite):
  `Sₙ = a₁(1 - rⁿ) / (1 - r)`

---

#### Practice Problem #1: Arithmetic Series with Custom Start Index

**Problem:**
Evaluate

```
∑ (4i + 1) from i = 3 to 11
```

**Steps:**

* Since the rule is linear (`4i + 1`), this is an arithmetic series.
* Adjust `a₁` → becomes `a₃`, since the series starts at `i = 3`.
* Total number of terms:
  `11 - 2 = 9` terms (include 3, exclude 1 and 2).

**Evaluate:**

* a₃ = `4(3) + 1 = 13`
* a₁₁ = `4(11) + 1 = 45`

Apply the arithmetic series formula:

```
S = (9 / 2)(13 + 45) = 4.5 × 58 = 261
```

---

#### Practice Problem #2: Geometric Bounce Distance with Sigma Notation

**Problem:**
A ball is dropped from height `h` and reaches ¾ of its previous height on each bounce. Represent the **total distance** traveled *between* the 1st and 8th bounces using sigma notation.

**Details:**

* Geometric sequence with `a₁ = h`, `r = ¾`.
* Each bounce includes an **up and down** path → multiply by 2.
* Exclude initial drop and 8th bounce → use `i = 2` to `i = 7`.

**Expression:**

```
∑ from i = 2 to 7 of 2h(¾)^i⁻¹  
OR  
∑ from i = 1 to 6 of 2h(¾)^i
```

---

#### Practice Problem #3: Sum of Odd Integers from 1 to 201

**Problem:**
What is the sum of all odd numbers from 1 to 201?

**Recognize the Pattern:**

* This is an arithmetic sequence:
  Start: 1
  Common difference: 2
  Rule: `aᵢ = 2i - 1`

**Find which term 201 is:**

```
201 = 2n - 1 → n = 101
```

So 201 is the 101st term.

**Apply the Arithmetic Series Formula:**

```
S = (101 / 2)(1 + 201) = (101 / 2)(202) = 101 × 101 = 10,201
```

---

#### Practice Problem #4: Abstract Series Transformation

**Problem:**
Given:

```
∑ aᵢ from i = 1 to 4 = 20  
Find: ∑ (2aᵢ - 1) from i = 1 to 4
```

**Rewrite the New Series:**

```
2a₁ - 1 + 2a₂ - 1 + 2a₃ - 1 + 2a₄ - 1  
= 2(a₁ + a₂ + a₃ + a₄) - 4
```

Substitute the known sum:

```
= 2(20) - 4 = 40 - 4 = 36
```

---

#### Lesson Summary

* When a series does **not** begin at `i = 1`, carefully adjust:

  * Use the new first term for `a₁`
  * Calculate the correct number of terms for `n`

* Use **i** in the exponent of geometric series to shift the start without skipping terms.

* Odd integers can be expressed as `2i - 1` (arithmetic), and even integers as `2i`.

* Abstract problems often test your understanding of **operations on series**, such as transformation or scaling.

Let me know if you'd like additional practice problems for either arithmetic or geometric series.

### Section 9: Mathematical Induction

#### What Is Mathematical Induction?

Mathematical induction is a **proof technique** used to establish that a statement or property holds for **all elements in an infinite set**, typically the positive integers. Rather than verifying each element individually, which is impossible with an infinite set, this method lets us prove the statement for all elements in two steps: the **base case** and the **inductive step**.

---

#### When to Use Mathematical Induction

Use mathematical induction when:

1. The set you're working with is **infinite** (e.g. all positive integers).
2. The property is **easily verified** for a starting value (often `n = 1`).
3. You can assume the property is true for `n = k` and use that to prove it for `n = k + 1`.

If these hold true, mathematical induction is the right tool.

---

#### Example: Sum of the First n Positive Integers

We want to prove:

```
1 + 2 + 3 + ... + n = (n(n + 1)) / 2
```

This is a statement about an **infinite set** (the positive integers), so it’s a good candidate for induction.

---

#### Step 1: Base Case

Let’s prove the statement is true for `n = 1`.

* Left-hand side: `1`
* Right-hand side: `(1(1 + 1))/2 = 2/2 = 1`

Since both sides are equal, the base case is true.

---

#### Step 2: Inductive Step

Assume the formula holds for some arbitrary positive integer `k`. That is:

```
1 + 2 + 3 + ... + k = (k(k + 1)) / 2
```

We must prove it holds for `k + 1`, i.e.,

```
1 + 2 + 3 + ... + k + (k + 1) = ((k + 1)(k + 2)) / 2
```

**Start with the inductive assumption:**

```
1 + 2 + ... + k = (k(k + 1)) / 2
```

**Add (k + 1) to both sides:**

```
(1 + 2 + ... + k) + (k + 1) = (k(k + 1))/2 + (k + 1)
```

Factor out `(k + 1)`:

```
= (k + 1)(k/2 + 1) = (k + 1)((k + 2)/2)
```

Which matches the desired form:

```
((k + 1)(k + 2)) / 2
```

So the inductive step is proven.

---

#### Conclusion

By proving:

1. The base case is true for `n = 1`
2. The statement is true for `n = k + 1` assuming it is true for `n = k`

We conclude by **mathematical induction** that the formula:

```
1 + 2 + 3 + ... + n = (n(n + 1)) / 2
```

holds for all positive integers `n`.

---

#### Lesson Summary

* **Mathematical induction** proves properties for all elements in an infinite set.
* **Base case**: Prove the property is true for the first value.
* **Inductive step**: Assume it’s true for `k` and prove it for `k + 1`.
* When these are both proven, the property holds for all `n ≥ 1`.
* Induction is a fundamental method in discrete mathematics and logic.

Let me know if you’d like to go through more induction examples like proving divisibility, inequalities, or recursive formulas.
