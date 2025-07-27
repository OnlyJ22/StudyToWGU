### Section 1: Understanding Sets

#### **Definition of a Set**

A **set** is a *collection of distinct objects*, called **elements** or **members**, enclosed in curly braces `{ }`.
*Example*:
Let `C = {pants, t-shirt, skirt, dress}`
\* `C` is the name of the set (capital letter).
 *The elements* are: pants, t-shirt, skirt, dress.

Sets can include **non-numerical objects** as well as numbers.

#### **Common Set Notation**

* `Z = {..., -3, -2, -1, 0, 1, 2, 3, ...}` represents the **set of all integers**.
* The ellipsis `...` shows that the pattern continues indefinitely.

---

#### **Union of Sets**

*The **union** of two sets* includes **all elements from both sets**, without repetition.
*Symbol:* `∪` (read as "union")
*Example:*
Let `A = {green, blue, pink}`
Let `B = {orange, yellow, black}`
Then:
`A ∪ B = {green, blue, pink, orange, yellow, black}`
\* Includes everything from both A and B.\*

---

#### **Intersection of Sets**

*The **intersection** of two sets* includes **only the elements that are in both sets**.
*Symbol:* `∩` (read as "intersection")
*Example:*
Let `A = {4, 6, 9}`
Let `B = {7, 8, 9}`
Then:
`A ∩ B = {9}`
\* Only the number 9 appears in both A and B.\*

---

#### **Summary**

* A **set** is a group of distinct objects.
* Use **capital letters** to name sets.
* Enclose elements in **curly braces `{}`**.
* A **union (A ∪ B)** combines all unique elements from both sets.
* An **intersection (A ∩ B)** contains only elements common to both sets.

### Section 2: Universal Sets and Subsets

#### **Definition of a Universal Set**

A **universal set** is the *complete set of all elements* relevant to a particular discussion or context.
\* It does not mean “everything in existence,” but rather “everything under consideration.”\*

*Examples*:

* The set of all stars in the Milky Way (for an astronomy discussion).
* The set of natural numbers `N = {1, 2, 3, 4, ...}` (for arithmetic problems).
* The set of all U.S. Presidents (for historical analysis).

\* A universal set can be\* **finite** *or* **infinite**, *depending on the context.*

---

#### **Symbols and Notation**

* Universal sets are typically labeled with a **capital U**.
* Sometimes, a different letter may be used (e.g., `N` for natural numbers), as long as the context is clear.
* Set elements are enclosed in curly braces `{ }`.
* The ellipsis `...` indicates continuation of a pattern in infinite sets.

---

#### **Subsets of a Universal Set**

A **subset** is a set where *every element is also in the universal set*.
*Notation*: If `A` is a subset of `U`, we write `A ⊆ U`.

*Examples*:

* Let `U = {1, 2, 3, 4, 5, 6}`, then `A = {2, 4, 6}` is a subset of `U`.
* Let `U =` all U.S. Presidents, then `A =` those who died in office:
   `A = {Harrison, Taylor, Lincoln, Garfield, McKinley, Harding, F. Roosevelt, Kennedy}`

---

#### **Visual Representation**

* A **rectangle** often represents the universal set `U`.
* A **circle inside the rectangle** represents a subset.
  \* All elements in the circle must also lie inside the rectangle.

---

#### **Mathematical Set Example**

Let `U = {1, 3, 5, 7, ..., 99}` (all positive odd numbers < 100).
Let `B = {3, 5, 7, 11, 13, 17, ..., 97}` be the subset of odd *prime* numbers from `U`.

\* This subset B satisfies:\*
`B = { x ∈ U | x is prime }`
\* Where:\*
 `∈` means “is an element of”
 `|` means “such that”

---

#### **Summary**

* A **universal set** includes *all relevant elements* in a given context.
* **Subsets** are sets made from elements of a universal set.
* Universal sets are useful for defining scope in math problems or real-world categories.
* Symbolic notation (`⊆`, `∈`, `{ }`) helps clearly define these relationships.

### Section 3: Universal Sets, Subsets, and Complements

#### **Universal Set**

A **universal set (U)** is the set of all elements being considered in a particular discussion or problem.

*Examples*:

* For the inequality `-3 < x < 2`, the universal set might be:
   `U = {..., -3, -2, -1, 0, 1, 2, 3, ...}`
* For U.S. geography, the universal set could be:
   `U =` *all 50 U.S. states*

---

#### **Subset**

A **subset (A)** is a set where *every element is also in the universal set*.
*Notation*: `A ⊆ U`

*Examples*:

* If `U = {1, 2, 3, 4, 5, 6, 7}`, then `E = {1, 3, 4}` is a subset of `U`
* If `U =` all U.S. states, then `A =` New England states
    `A = {Connecticut, Maine, Massachusetts, New Hampshire, Rhode Island, Vermont}`

---

#### **Complement of a Set**

The **complement of a set A** (written `A'`, `Aᶜ`, or `U - A`) is the set of all elements in the **universal set** that are **not in A**.

*Notation Examples*:

* `A' = U - A`
* `Aᶜ = { x ∈ U | x ∉ A }`

*Example*:

* If `U = {1, 2, 3, 4, 5, 6, 7}` and `E = {1, 3, 4}`, then:
    `E' = {2, 5, 6, 7}`

*Another example*:

* Let `U =` the integers and `G = {1, 2, 3, 4, ...}` (natural numbers)
    Then, `G' = {…, -3, -2, -1, 0}`

---

#### **Visualizing Complements: Venn Diagram**

* The **rectangle** represents the universal set `U`.
* A **circle inside** represents the subset `A`.
* The area **outside the circle but inside the rectangle** shows the **complement of A**.

---

#### **Operations Involving Complements**

1. **Complement as a Set Difference**:
     `A' = U - A`

2. **Universal Set's Complement**:
     `U - U = Ø` (the **empty set**, a set with no elements)

3. **Complement Properties**:

* `A ∪ A' = U`  (Union of a set and its complement is the universal set)
* `A ∩ A' = Ø`  (Intersection of a set and its complement is the empty set)

---

#### **Empty Set Notation**

* Represented as `Ø` or `{ }`
* A set with **no elements**

---

#### **Summary**

* The **universal set** contains all possible elements in a specific context.
* A **subset** is any collection of elements from the universal set.
* The **complement** of a set consists of all elements in the universal set *not* in the subset.
* Complements are useful for reasoning about what is excluded from a given set.
* They can be expressed through set notation, Venn diagrams, or symbolic expressions like `U - A`.

### Section 4: Review of Sets, Cardinality, and Types of Sets

#### **What Is a Set?**

A **set** is a collection of distinct elements. These elements can be anything: numbers, letters, objects, words, etc.
*Example*:
`V = {car, truck, van, semi}`

---

#### **Element Notation**

An element of a set is represented using the symbol `∈`
*Example*:
If `x ∈ V`, then `x` is an element of set `V`.

---

#### **Cardinality**

The **cardinality** of a set is the number of elements in the set.
Two common notations for cardinality:

* `|A|` (absolute bars)
* `n(A)`

*Example*:
If `V = {car, truck, van, semi}`, then:

* `|V| = 4`
* `n(V) = 4`

---

#### **Empty Set**

An **empty set** has no elements.
*Notation*: `Ø` or `{ }`
*Cardinality*: `|E| = 0`
⚠️ *Note*: The number `0` is **not** an element — it just shows there's nothing in the set.

---

#### **Finite Set**

A **finite set** contains a countable number of elements.
*Example*:
`P = {red, yellow, blue}` is finite.
`|P| = 3`

---

#### **Infinite Set**

An **infinite set** has no end.
There are **two types**:

1. **Countable Infinite Set**
    - Can be listed one by one
    - *Example*: `Z = {..., -2, -1, 0, 1, 2, ...}` (integers)

2. **Uncountable Infinite Set**
    - Too large to list in a sequence
    - *Example*: Real numbers (`ℝ`) — includes both rational and irrational numbers

---

#### **Equal Sets**

Two sets are **equal** if they contain **exactly the same elements**, regardless of order.
*Example*:
`A = {red, blue, orange}`
`B = {orange, red, blue}`
Then `A = B`

---

#### **Equivalent Sets**

Two sets are **equivalent** if they have the **same number of elements**, even if the elements themselves differ.
*Example*:
`Q = {red, blue, orange}`
`R = {3, 4, 6}`
Then `Q` is equivalent to `R`, because `|Q| = |R| = 3`

---

#### **Summary Table**

| **Concept**     | **Definition**                          | **Example**                                |   |       |
| --------------- | --------------------------------------- | ------------------------------------------ | - | ----- |
| Set             | Collection of elements                  | `{apple, banana, cherry}`                  |   |       |
| Element         | Member of a set                         | `apple ∈ fruits`                           |   |       |
| Cardinality     | Number of elements in a set             | \`                                         | A | = 3\` |
| Empty Set       | Set with no elements                    | `Ø`, `{ }`                                 |   |       |
| Finite Set      | Set with a countable number of elements | `{1, 2, 3}`                                |   |       |
| Infinite Set    | Set with endlessly many elements        | `{1, 2, 3, ...}`                           |   |       |
| Equal Sets      | Sets with exactly the same elements     | `{a, b, c} = {c, a, b}`                    |   |       |
| Equivalent Sets | Sets with the same number of elements   | `{1, 2, 3}` and `{x, y, z}` are equivalent |   |       |

### Section 5: Partially Ordered Sets and Lattices in Discrete Mathematics

#### **Set Theory Foundations**

* A **set** is an unordered collection of distinct elements.
   *Example*:
   `B = {oven, baking pan, wire rack, measuring cup, measuring spoon, whisk}`
   `N = {1, 2, 3, 4, 5, ...}`

* An **ordered pair** `(x, y)` is a sequence where order matters:
   `(x, y) ≠ (y, x)` in general.

* A **Cartesian product** `A × B` is the set of all ordered pairs formed by combining each element in A with every element in B.
   *Example*:
   If `A = {a, b}`, `B = {1, 2}`
   Then: `A × B = {(a,1), (a,2), (b,1), (b,2)}`

---

#### **Types of Relations**

Given a relation `R` on a set `A` (i.e., a subset of `A × A`):

* **Reflexive**: Every element relates to itself
    `∀a ∈ A, (a, a) ∈ R`

* **Anti-symmetric**: If `(a, b) ∈ R` and `(b, a) ∈ R`, then `a = b`

* **Transitive**: If `(a, b) ∈ R` and `(b, c) ∈ R`, then `(a, c) ∈ R`

---

#### **Partial Order Relation (POSET)**

A relation `R` on set `A` is a **POSET** if it is:

1. **Reflexive**
2. **Anti-symmetric**
3. **Transitive**

*Example*:
Let `A = {p, q, r}`
Let `R = {(p,p), (q,q), (r,r), (p,r), (q,r)}`
This is a partial order since all three conditions are satisfied.

---

#### **Hasse Diagram**

A **Hasse diagram** is a graphical representation of a POSET with:

* **Vertices** representing elements.
* **Edges** representing immediate relationships (cover relations).
* **Reflexive loops** and **transitive edges** are omitted for clarity.

*Example*:
Let `B = {3, 4, 5, 6}`
Relation `R = {(3,3), (3,4), (3,5), (3,6), (4,4), (4,5), (4,6), (5,5), (5,6), (6,6)}`
Hasse diagram is drawn by eliminating loops and transitive connections, connecting only the minimal necessary edges.

---

#### **Key Concepts in Hasse Diagrams**

* **Maximal element**: No element is above it
   → Example: vertex `6`

* **Minimal element**: No element is below it
   → Example: vertex `3`

* **Least Upper Bound (LUB)**: Smallest element greater than or equal to both
   → Example: LUB of {4, 5} is `6`

* **Greatest Lower Bound (GLB)**: Largest element less than or equal to both
   → Example: GLB of {4, 5} is `3`

---

#### **Semilattices and Lattices**

* A **Join Semilattice**: Every pair has a **least upper bound (LUB)**
   *Example*:
   If `{3, 4}` has LUB `4`, and `{4, 5}` has LUB `5`, then it's a join semilattice.

* A **Meet Semilattice**: Every pair has a **greatest lower bound (GLB)**
   *Example*:
   If `{c, d}` has GLB `b`, and `{a, b}` has GLB `a`, then it's a meet semilattice.

* A **Lattice**: A POSET that is **both a join semilattice and a meet semilattice**
   → Every pair of elements has both a LUB and a GLB.

---

#### **Summary**

* A **relation** over a set can be **reflexive**, **anti-symmetric**, and **transitive**.
* A **POSET** satisfies all three properties.
* A **Hasse diagram** visually represents a POSET by simplifying connections.
* A **join semilattice** has least upper bounds.
* A **meet semilattice** has greatest lower bounds.
* A **lattice** has both, making it a structured and complete form of partial order.

### Section 6:Basics of a Function

#### **What Is a Function?**

A **function** is a rule that **maps each input** (from a domain) to **exactly one output** (in a range).
Think of a function like a **black box**:
 *Input* → `f(x)` → *Output*

 *Example*:
 If `f(x) = 4x` and `x = 5`, then:
  `f(5) = 4 * 5 = 20`
 Every `x` maps to one specific `y`.
 But different `x` values *can* map to the same `y`.

---

#### **Functions in Everyday Life**

*Example – Buying Gas*:

* Let `x` = gallons pumped
* Let `f(x)` = cost in dollars
    If gas costs \$3.80/gallon, then:
    `f(x) = 3.80x`
    If you pump `10.2` gallons:
    `f(10.2) = 3.80 * 10.2 = 38.76`

This function **relates the amount of gas purchased to the total cost**.
 *Independent variable*: gallons (`x`)
 *Dependent variable*: cost (`f(x)`)

---

#### **Mathematical Notation**

We write functions as:

* `y = f(x)` → y is a function of x
* `f(4)` means evaluate the function when x = 4

 *Example*:
  `f(x) = 4x`
  `f(4) = 16`

---

#### **Domain and Range**

* **Domain**: All possible input values (x-values)
* **Range**: All possible output values (y-values)

 *Gas Station Example*:
  `Domain`: `x ≥ 0` (you can't pump negative gas)
  `Range`: `y ≥ 0` (you can't owe negative money)

 *Sine Function Example*:
  `f(x) = sin(x)`
  `Domain`: All real numbers (`-∞ < x < ∞`)
  `Range`: Between `-1` and `1`

---

#### **Piecewise Functions**

Some functions are defined using **different rules** for different parts of the domain.
 *Example*:
  `f(x) = sin(x)` for `x < 0`
  `f(x) = x` for `x > 0`
  `f(x)` is undefined at `x = 0`

This is shown using **open circles** in a graph to indicate undefined points.

---

#### **Graphing Functions**

Graphs allow us to:

* Visualize the relationship between x and y
* Understand behavior like increases, decreases, and discontinuities
* Identify domain and range quickly

A **linear function** like `f(x) = 4x` graphs as a straight line.
A **sine function** oscillates between `-1` and `1`.

---

#### **Lesson Summary**

* A **function** is a rule assigning **one output for every input**.
* The **independent variable** (`x`) lies in the **domain**.
* The **dependent variable** (`y = f(x)`) lies in the **range**.
* Functions model real-world scenarios (e.g., cost, speed, population).
* **Graphing** helps visualize how inputs and outputs are related.


### Section 7: Injections, Surjections, and Bijections

#### Injective Functions (One-to-One)

A function $f: A \rightarrow B$ is **injective** if each input maps to a unique output. No two different inputs map to the same output.

**Formal Definition**:
If $f(x_1) = f(x_2)$, then $x_1 = x_2$

**Example**:
$f(x) = 3x + 2$ is injective over $\mathbb{R}$, since each $x$ gives a different $y$.

**Graph Behavior**:

* Passes the horizontal line test (intersects at most once)
* No repeated $y$-values

---

#### Surjective Functions (Onto)

A function $f: A \rightarrow B$ is **surjective** if every element in $B$ is mapped to by at least one element in $A$.

**Formal Definition**:
For every $y \in B$, there exists $x \in A$ such that $f(x) = y$

**Example**:
$f(x) = x^2$, from $\mathbb{R}$ to $\mathbb{R}_{\geq 0}$, is surjective because every non-negative number has a pre-image.

**Graph Behavior**:

* Entire codomain is covered by outputs
* Multiple $x$-values may map to the same $y$

---

#### Bijective Functions (One-to-One and Onto)

A function is **bijective** if it is both injective and surjective.

**Formal Definition**:
Every $y \in B$ has exactly one $x \in A$ such that $f(x) = y$

**Example**:
$f(x) = x^2$, restricted to $x \in \mathbb{R}^+$, is bijective from $\mathbb{R}^+ \rightarrow \mathbb{R}^+$

**Graph Behavior**:

* Passes both horizontal and vertical line tests
* Perfect one-to-one correspondence between domain and codomain

---

#### Inverse Functions

Only injective (and thus bijective) functions have proper inverses.

**Definition**:
If $f(x) = y$, then the inverse function satisfies $f^{-1}(y) = x$

**Example**:
If $f(x) = 3x + 2$, then $f^{-1}(y) = \frac{y - 2}{3}$

---

#### Isomorphisms

An **isomorphism** is a bijective function that preserves structure between mathematical systems.

**Example**:
The logarithmic identity $\log(xy) = \log x + \log y$ is an isomorphism between multiplication and addition.

---

####Summary Table

| Function Type | Unique Outputs | Full Codomain Used | Invertible |
| ------------- | -------------- | ------------------ | ---------- |
| Injective     | Yes            | Not always         | Yes        |
| Surjective    | Not always     | Yes                | Not always |
| Bijective     | Yes            | Yes                | Yes        |
