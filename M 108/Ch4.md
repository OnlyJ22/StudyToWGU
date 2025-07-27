### Section 1: Calculating Possible Outcomes

#### Definition

The process of **calculating possible outcomes** involves determining the number of potential results that can occur in a given event or sequence of events. The approach used depends on the **type of event** (single or multiple) and its **structure** (e.g., independent events, arrangements). This forms the basis for understanding probability and combinatorics in mathematics.

#### Fundamental Counting Principle: Multiple Events

The **Fundamental Counting Principle (FCP)** states that if one event has `p` outcomes and another has `q` outcomes, then the total number of outcomes for both events occurring in sequence is:

```
Total Outcomes = p × q
```

If additional events are added, the formula extends:

```
Total Outcomes = p × q × r × ...
```

#### Example: Ice Cream Cones

A shop offers:

* **4 ice cream flavors**: vanilla, chocolate, pistachio, mint
* **2 cone types**: regular, cinnamon

**Number of combinations** = 4 × 2 = **8**

If **3 toppings** are added, the combinations expand:

**Total** = 4 × 2 × 3 = **24**

#### Example: License Plate

A license plate consists of:

* **4 digits** (0–9): 10 choices each
* **2 letters** (A–Z): 26 choices each

**Total combinations**:

```
10 × 10 × 10 × 10 × 26 × 26 = 6,760,000
```

#### Fundamental Counting Principle: Permutations

A **permutation** is an arrangement of objects **where order matters**.

#### Example: Horse Race with 6 Horses

* 6 choices for 1st stall
* 5 choices for 2nd
* 4 choices for 3rd
* … down to 1

**Total permutations**:

```
6 × 5 × 4 × 3 × 2 × 1 = 720
```

#### Example: Selecting and Arranging 3 of 7 Plants

* 7 choices for the 1st spot
* 6 for the 2nd
* 5 for the 3rd

**Total permutations**:

```
7 × 6 × 5 = 210
```

This applies when a subset of a larger group is selected and **order matters**.

#### Lesson Summary

* The **Fundamental Counting Principle** is the key rule for calculating total outcomes.
* If there are multiple independent choices, multiply their possible outcomes:
  `p × q × r × …`
* **Permutations** involve arrangements where **order is important**.
* For permutations of all `n` objects: `n!` (n factorial)
* For permutations of `r` out of `n` distinct objects:
  `P(n, r) = n × (n – 1) × ... × (n – r + 1)`
  or
  `P(n, r) = n! / (n – r)!`

### Section 2: Combinatorics

#### Glove Problem Example

At a carnival, you're asked: *If you have 8 red gloves and 8 green gloves in a laundry basket (16 total), what's the minimum number of gloves you must pull out to guarantee a matching pair?*

If you pull:

* 1 glove: no guarantee of a pair
* 2 gloves: could be red and green (still no guarantee)
* 3 gloves: must include a matching color

Thus, **the minimum number is 3**. This is a basic application of **combinatorics**, the mathematics of counting.

#### The Pigeonhole Principle

This glove scenario demonstrates the **pigeonhole principle**:

> If more items (pigeons) are placed into fewer categories (pigeonholes) than there are items, at least one category must contain more than one item.

In the glove example:

* 2 glove colors (pigeonholes)
* Pulling 3 gloves (pigeons)

By the pigeonhole principle, at least two gloves must be the same color.

#### More Pigeonhole Principle Examples

**1. Paragraph Words and Alphabet Letters**

Any paragraph with **27 or more words** must have **at least two words starting with the same letter**.

* 26 possible first letters → 26 pigeonholes
* 27 words → 27 pigeons

Since 27 > 26, at least one letter must be the first letter of **two or more words**.

**2. Shared Birthdays**

At any gathering of **more than 366 people**, at least **two people must share a birthday**.

* 366 days (in a leap year) → 366 pigeonholes
* > 366 people → more pigeons than holes

So, at least one birthday is shared.

#### Lesson Summary

* **Combinatorics** is the branch of math focused on **counting techniques**.
* The **pigeonhole principle** states that if more items are distributed across fewer categories, at least one category must contain multiple items.
* This principle is simple yet widely applicable in both mathematics and real-world problem solving.

### Section 3: Calculating a Permutation

#### What Is a Permutation?

A **permutation** is an arrangement of items or events **in which order matters**. For example, in a poker hand, changing the order of the cards results in a different arrangement.

#### Card Arrangement Example

John receives 5 different cards in a poker game:

* Ace of spades
* 7 of clubs
* 7 of diamonds
* Jack of hearts
* 2 of clubs

To determine how many ways he can arrange them:

* 5 choices for the 1st card
* 4 choices for the 2nd card
* 3 choices for the 3rd card
* 2 choices for the 4th card
* 1 choice for the 5th card

**Total permutations**:

```
5 × 4 × 3 × 2 × 1 = 120
```

There are **120** ways to organize his hand.

---

#### Factorials

A **factorial** is the product of all positive integers less than or equal to a number.

* **Notation**: `n!`
* **Example**:
  `5! = 5 × 4 × 3 × 2 × 1 = 120`
  `10! = 10 × 9 × 8 × 7 × 6 × 5 × 4 × 3 × 2 × 1 = 3,628,800`

---

#### Permutation Notation

We use the formula:

```
nPr = n! / (n - r)!
```

Where:

* `n` is the total number of items
* `r` is the number of items selected
* `P` denotes permutation

---

#### Example 1: Selecting Poker Players

From a group of 6 poker players, how many ways can 4 players be selected (order matters)?

```
6P4 = 6! / (6 - 4)! = 6! / 2!
```

Calculate:

* `6! = 720`
* `2! = 2`

```
720 / 2 = 360
```

There are **360** ways to select and arrange 4 players.

---

#### Example 2: Pizza Toppings

At the snack bar, there are **10 toppings**, and John wants a pizza with **4 toppings** (order matters):

```
10P4 = 10! / (10 - 4)! = 10! / 6!
```

We can cancel out `6!` from both numerator and denominator:

```
(10 × 9 × 8 × 7) = 5,040
```

John can create **5,040** different four-topping pizzas.

---

#### Lesson Summary

* A **permutation** is an ordered arrangement of items.
* **Factorials** are used to calculate permutations:
  `n! = n × (n - 1) × ... × 1`
* The **permutation formula** is:
  `nPr = n! / (n - r)!`
* Permutations are used when **order matters**, such as:

  * Arranging cards
  * Selecting people for roles
  * Creating ordered pizza combinations with distinct ingredients

### Section 4: Probability and Permutations

#### Understanding Probability

**Probability** is the **likelihood** that a particular event will occur. It is calculated as:

```
Probability = (Number of favorable outcomes) / (Total number of outcomes)
```

##### Example: Gumballs

Jimmy’s bag contains:

* 20 red
* 15 blue
* 12 yellow

**Total gumballs** = 20 + 15 + 12 = 47
**Favorable outcomes** (red) = 20

```
Probability of red = 20 / 47
```

This fraction is already in simplest form.

---

#### Permutations and Factorials

A **permutation** is an **arrangement** of items where **order matters**. The formula for permutations is:

```
nPr = n! / (n - r)!
```

Where:

* `n` = total items
* `r` = items selected
* `!` = factorial (e.g., `5! = 5 × 4 × 3 × 2 × 1 = 120`)

##### Example: Student Government Election

At Rockland University:

* 20 students (n = 20)
* 4 positions (r = 4)

```
20P4 = 20! / (20 - 4)! = 20! / 16!
```

Canceling shared terms:

```
20 × 19 × 18 × 17 = 116,280
```

There are **116,280** possible ways to assign the positions.

---

#### Calculating Probability Using Permutations

To combine probability and permutations:

1. **Use permutation** to find the total number of outcomes
2. **Use probability formula** to find the likelihood of a specific outcome

##### Example: Smartphone Passcode

Jim’s 5-digit passcode:

* Uses digits 0–9 (n = 10)
* No repeats (r = 5)

```
10P5 = 10! / (10 - 5)! = 10! / 5!
```

Cancel out 5!:

```
10 × 9 × 8 × 7 × 6 = 30,240
```

There are **30,240** possible unique passcodes.

Since only **one** passcode will work, the probability Jim guesses correctly is:

```
1 / 30,240
```

---

#### Lesson Summary

* **Probability** = favorable outcomes ÷ total outcomes
* Use **permutations** to find total outcomes when **order matters**
* Formula for permutations:
  `nPr = n! / (n - r)!`
* Use **factorials** to simplify complex counting problems
* Combine both concepts to solve problems involving **specific selections from many possible ordered arrangements**

### Section 5: What Is a Permutation?

#### Linear Permutations

A **permutation** is an **arrangement of items where order matters**. For example, arranging the letters A, B, C, and D in different sequences produces unique permutations:

**List of permutations of A, B, C, D**:

* ABCD, ABDC, ACBD, ACDB, ADBC, ADCB
* BACD, BADC, BCAD, BCDA, BDAC, BDCA
* CABD, CADB, CBAD, CBDA, CDAB, CDBA
* DABC, DACB, DBAC, DBCA, DCAB, DCBA

**Total permutations**:

```
4! = 4 × 3 × 2 × 1 = 24
```

#### Circular Permutations

If the items are arranged in a **circle**, rotations of the same order count as **duplicates**. In a **fixed circle** (cannot be flipped), each set of linear permutations has `n` equivalent circular arrangements.

**Formula for circular permutations**:

```
(n - 1)!
```

**Example with 4 items**:

```
4! / 4 = 3! = 6 distinct circular permutations
```

This is because:

* ABCD
* BCDA
* CDAB
* DABC
  … are all equivalent in a circular setup.

#### Free Circle Permutations

If the circle is **free** (can be flipped), then **clockwise and counterclockwise** arrangements are also considered identical. This further divides the count by 2.

**Formula**:

```
(1/2) × (n - 1)!
```

#### Example Problem

**Question**: How many ways can 5 differently colored chairs be arranged…

* **In a fixed circle**:

  ```
  (5 - 1)! = 4! = 24 ways
  ```

* **In a free circle**:

  ```
  (1/2) × (5 - 1)! = 4! / 2 = 24 / 2 = 12 ways
  ```

#### Lesson Summary

To calculate permutations correctly, identify the context:

* **Linear permutations** (order matters in a line):

  ```
  n!
  ```

* **Fixed circular permutations** (rotation duplicates not allowed):

  ```
  (n - 1)!
  ```

* **Free circular permutations** (rotation and reflection duplicates not allowed):

  ```
  (1/2) × (n - 1)!
  ```

These principles apply to arranging **letters, objects, people**, and more, and are essential in combinatorics and probability.

### Section 6: Combinations in Basketball Season

#### Combinations Overview

A **combination** is an arrangement of items **where order does not matter**. In sports contexts, such as basketball matchups, the sequence of teams playing each other is irrelevant—what matters is simply **which teams play**, not **who plays first**.

#### Combination Formula

The formula for calculating combinations is:

```
nCr = n! / (r!(n - r)!)
```

Where:

* `n` = total number of items
* `r` = number of items selected
* `!` = factorial, the product of all positive integers up to that number

---

#### Example 1: Total District Games

**Scenario**: There are 8 teams in the district. Each team plays every other team once. How many total games are played?

This is a **combination**, because game order doesn’t matter. We are choosing **2 teams out of 8**:

```
n = 8  
r = 2  
```

Apply the formula:

```
8C2 = 8! / (2!(8 - 2)!)  
     = 8! / (2! × 6!)  
     = (8 × 7 × 6!) / (2 × 1 × 6!)  
     = (8 × 7) / 2  
     = 56 / 2  
     = 28 games
```

So, **28 total games** will be played in the district.

---

#### Factorials Refresher

A **factorial** is defined as:

```
n! = n × (n - 1) × (n - 2) × ... × 1
```

Examples:

* `6! = 6 × 5 × 4 × 3 × 2 × 1 = 720`
* `11! = 11 × 10 × 9 × ... × 1 = 39,916,800`

---

#### Example 2: Forming 3-on-3 Practice Teams

**Scenario**: The coach wants to form **3-player teams** from **12 players**.

This is another **combination**:

```
n = 12  
r = 3  
```

Apply the formula:

```
12C3 = 12! / (3! × (12 - 3)!)  
      = 12! / (3! × 9!)  
      = (12 × 11 × 10 × 9!) / (3 × 2 × 1 × 9!)  
      = (12 × 11 × 10) / 6  
      = 1,320 / 6  
      = 220 combinations
```

So, **220 different 3-player teams** can be formed.

---

#### Lesson Summary

* A **combination** is a selection **without regard to order**.
* The combination formula is:

  ```
  nCr = n! / (r!(n - r)!)
  ```
* Use **factorials** to expand the numerator and denominator.
* **Cancel common terms** when simplifying for efficient calculation.
* Combinations are useful in scenarios like:

  * Game matchups
  * Team selection
  * Group assignments where order doesn’t matter
