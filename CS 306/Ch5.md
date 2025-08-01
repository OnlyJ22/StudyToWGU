### Modern Computer Performance Metrics

#### Evolution of Performance Evaluation

* **Past focus**: Clock speed and core count were primary indicators.
* **Today**: Processors are more complex, requiring multiple performance parameters.

---

#### Why Clock Speed and Core Count Aren’t Enough

#### Clock Speed

* Measured in MHz or GHz.
* Indicates the number of clock cycles per second.
* **Limit**: Only useful for comparing similar processors. Doesn’t reflect real-world or cross-architecture performance.

#### Core Count

* More cores = better multitasking.
* Enables parallel processing.
* **Limit**: Doesn’t directly indicate total system performance.

---

#### Key Performance Metrics

#### MIPs (Million Instructions Per Second)

* Measures how many instructions a CPU can execute per second.
* **Limitations**:

  * No standardized measurement method.
  * Doesn’t reflect actual performance across workloads.
  * Rarely used today; useful mainly for estimating computing cost in enterprise systems.

#### FLOPs (Floating-Point Operations Per Second)

* Measures how many floating-point calculations a processor can perform per second.
* More relevant to **modern applications**: gaming, simulations, scientific computing, real-time graphics.
* **Strength**: Better reflects real-world performance than MIPs or clock speed.
* **Limit**: Ignores integer operations; not a full measure on its own.

---

#### Summary of Metric Strengths and Weaknesses

| Metric          | Measures                      | Strength                                 | Limitation                                    |
| --------------- | ----------------------------- | ---------------------------------------- | --------------------------------------------- |
| **Clock Speed** | Cycles per second             | Good for comparing similar CPUs          | Doesn’t reflect raw or real-world performance |
| **Core Count**  | Parallel task execution       | Improves multitasking                    | Doesn’t account for task type or workload     |
| **MIPs**        | Instruction throughput        | Historical use in cost estimation        | Not reliable for modern performance           |
| **FLOPs**       | Floating-point operation rate | Best for math-heavy and modern workloads | Doesn’t account for integer operations        |

---

#### Final Insights

* No single parameter can accurately reflect computer performance.
* **Accurate evaluation requires multiple metrics used together.**
* Other factors like **hardware bottlenecks** (e.g., RAM, storage) also affect performance.





**Why do we not rely only on clock speed frequencies as a way to measure computer performance today?**
NONE OF THESE
The hardware itself has the potential to bottleneck the computer, which can be an affecting factor on system performance. We need to rely on both hardware and a variety of measurement parameters, such as MIPs and FLOPs to accurately benchmark computer performance.


**What is a big reason why we need a unified method for comparing different CPU ecosystems?**
ALL OF THESE
Since all of these factors make it impossible to properly compare the different CPU ecosystems, we need to figure out an efficient way. FLOP measurement is a much better representation of the raw computations a CPU can accomplish versus clock speed alone.


**In the earlier days of computing, what two deciding factors played the most significant roles in selecting a processor for performance reasons?**
Clock speed and core count.

**Which of the following numbers is an example of a floating point number?**
0.001

**Measuring MIPs is not very useful since there is no real way to gauge system performance. MIP measurement is useful to business however, for which important function?**
It allows business owners to know the cost of computing

### Combinational Logic Circuits

#### Introduction

Computers function using binary: **1s and 0s**, **True and False**, **ON and OFF**. Even complex systems are built from simple on/off switches. Using **Boolean logic**, we can build **combinational logic circuits** — circuits that compute outputs strictly based on current inputs, **without memory**.

> Example: If switch A is ON, light B is ON.
> The circuit doesn’t remember past inputs — it only reacts to current conditions.

---

#### Representing Combinational Logic

We can represent combinational logic using three primary methods:

1. **Logic Diagrams**
2. **Boolean Expressions**
3. **Truth Tables**

These representations are interchangeable — each tells us **when the output is ON**.

---

#### Basic Logic Gates

#### NAND Gate (NOT AND)

* **Symbol**: !\[A · B] — line over A·B
* **Behavior**: If **any** input is OFF, output is ON.

##### Truth Table

| A | B | A · B | NAND Output |
| - | - | ----- | ----------- |
| 0 | 0 | 0     | 1           |
| 0 | 1 | 0     | 1           |
| 1 | 0 | 0     | 1           |
| 1 | 1 | 1     | 0           |

---

#### NOR Gate (NOT OR)

* **Symbol**: !\[A + B] — line over A+B
* **Behavior**: If **any** input is ON, output is OFF.

##### Truth Table

| A | B | A + B | NOR Output |
| - | - | ----- | ---------- |
| 0 | 0 | 0     | 1          |
| 0 | 1 | 1     | 0          |
| 1 | 0 | 1     | 0          |
| 1 | 1 | 1     | 0          |

---

#### Example Circuit: NAND and NOR Combined

We now look at a circuit with inputs **A, B, C** and output **Q**, consisting of:

* A **NAND gate**: !(A · B)
* A **NOR gate**: !(A + B)
* AND gate combining NAND, NOR, and input C

##### Boolean Expression

```
Q = !(A · B) · !(A + B) · C
```

This means Q is only ON when:

* A · B is **not** true
* A + B is **not** true
* C is **true**

---

#### Truth Table for Combined Circuit

| A | B | C | Q |
| - | - | - | - |
| 0 | 0 | 0 | 0 |
| 0 | 1 | 0 | 0 |
| 0 | 0 | 1 | 1 |
| 0 | 1 | 1 | 0 |
| 1 | 0 | 0 | 0 |
| 1 | 1 | 0 | 0 |
| 1 | 0 | 1 | 0 |
| 1 | 1 | 1 | 0 |

Only when **A = 0**, **B = 0**, and **C = 1** do all conditions align to turn **Q = 1**.

---

#### Key Takeaways

* **Combinational circuits** use logic gates and **do not store memory**.
* They are based on **current input values only**.
* **NAND Gate**: Any OFF input → Output ON.
* **NOR Gate**: Any ON input → Output OFF.
* You can move between:

  * **Logic Diagrams**
  * **Boolean Expressions**
  * **Truth Tables**

> Each form answers the same core question:
> **"When is the output ON?"**

### Karnaugh Maps

#### Purpose

Karnaugh Maps (K-Maps) are tools used to **simplify and minimize Boolean expressions**, reducing the number of logical operations required to implement a Boolean function. This is useful in both **hardware logic design** and **software logic conditions**.

---

#### Boolean Functions & Identities

A **Boolean function** is an expression made up of binary variables (0 and 1) using logic operations such as AND, OR, and NOT. Simplification of these expressions can be aided by known Boolean laws and identities (e.g., DeMorgan’s Theorem, Identity Law, Null Law).

---

#### 2-Variable K-Map

* **Inputs**: A, B
* **Output**: F
* The 2-variable K-Map has **4 cells**, each representing a unique input combination.

**Truth Table and Corresponding K-Map:**

| A | B | F |
| - | - | - |
| 0 | 0 |   |
| 0 | 1 |   |
| 1 | 0 |   |
| 1 | 1 |   |

* Cells in the K-Map are arranged in **Gray code** order to ensure only **one bit changes** between adjacent cells.
* **Simplification** is done by grouping adjacent 1s in powers of two (1, 2, or 4).

**Form Used**: **Sum of Products (SOP)** — minimize using 1s.
(**Product of Sums (POS)** form uses 0s instead.)

---

#### 3-Variable K-Map

* **Inputs**: A, B, C
* **Total Combinations**: 8
* The K-Map is arranged in two rows and four columns using Gray code.

**Cell Order (Column-wise)**:
`000, 001, 011, 010, 110, 111, 101, 100`

This arrangement enables **adjacency-based simplification**.

---

#### 4-Variable K-Map

* **Inputs**: A, B, C, D

* **Total Combinations**: 16

* Arranged in a **4x4 grid**, again using Gray code.

* Adjacent cells include horizontal and vertical neighbors.

* The map **wraps around** — cells on edges are adjacent (e.g., top and bottom, left and right).

> This wraparound logic allows for larger groupings and better simplification.

---

#### Logic Simplification

K-Maps allow **visual simplification** of logic by grouping adjacent 1s:

* Group sizes must be **powers of 2** (1, 2, 4, 8...).
* Each group yields a **product term** in the SOP expression.
* **Overlap and wraparound** are allowed and encouraged to minimize terms further.

> Compared to algebraic simplification, K-Maps are **faster, more visual**, and **less error-prone**.

---

#### Higher-Order K-Maps

* **More than 4 variables** become impractical for hand-drawn K-Maps.
* Alternative method: **Map Entered Variable (MEV)**.
* Best practice: use **software tools** like:

  * **Quine-McCluskey**
  * **Espresso heuristic**
  * Online K-Map solvers

---

#### Lesson Summary

* **Karnaugh Maps** are used to minimize Boolean expressions.
* They work by visually grouping adjacent 1s (or 0s for POS) using Gray code layout.
* Most effective for systems with **4 variables or fewer**.
* For complex systems, use **automation tools** to simplify.

### The Quine-McCluskey Algorithm

#### Overview

The **Quine-McCluskey algorithm** is a systematic method used to simplify Boolean functions written in **Sum of Products (SOP)** form. It reduces logical expressions to their minimal equivalent using a tabular approach, ideal for automation and digital logic design.

If the expression is not in minterm form, the first step is to identify the minterms. Minterms are then categorized into:

* **Prime Implicants**: Terms that cannot be further combined or simplified.
* **Essential Prime Implicants**: Terms that uniquely cover certain minterms and are required in the final simplified expression.

---

#### Example: Essential Prime Implicants

Consider the function:

```
x + yz'
```

Here:

* `x` and `yz'` cannot be combined.
* Both are essential prime implicants because neither can be reduced further.

---

#### Simplification Steps

To simplify using the Quine-McCluskey algorithm:

1. **Group minterms** by the number of **1s** in their binary representation.
2. Use binary representation where:

   * **0** = complemented variable
   * **1** = uncomplemented variable
3. **Combine minterms** that differ by only **one bit** (i.e., are 1-bit apart).
4. **Replace differing bits with an underscore** `_` (indicating a variable dropped in simplification).
5. **Continue combining** until only **essential prime implicants** remain.

---

#### Demonstration Example

Given the function:

```
xyz' + xy'z + xy'z' + x'yz + x'y'z
```

1. **Group terms** based on the number of 1s in the binary form.

2. **Binary mapping**:

   * `xyz'` = 110
   * `xy'z` = 101
   * `xy'z'` = 100
   * `x'yz` = 011
   * `x'y'z` = 001

3. **Pair combinations**:

   * Example: `110` and `100` differ in the middle bit → `1_0` → corresponds to `xz'`
   * Replace differing bits with `_` in each pair.

---

#### Reduction Table (Figure Summary)

* Prime implicants are written vertically.
* Original minterms are written horizontally.
* Each implicant is marked with a `*` under the minterms it covers.
* **Essential prime implicants** are those covering a minterm that no other implicant covers.

**Final simplified expression**:

```
xz' + x'z + xy'
```

or

```
xz' + x'z + y'z`
```

(Note: Both are logically equivalent depending on how reduction is grouped.)

---

#### Uses of the Algorithm

* **Speed Optimization**: Simplified logic leads to faster circuits and computations.
* **Resource Efficiency**: Reduces the number of logic gates and paths in digital circuits.
* **Automation**: Basis for digital logic simplifiers in software like logic simulators and compilers.

---

#### Lesson Summary

* The **Quine-McCluskey algorithm** simplifies Boolean expressions by finding and reducing **prime** and **essential prime implicants**.
* It works in a step-by-step method involving binary comparisons and table marking.
* It is useful for optimizing circuit design and is widely implemented in automated tools and websites.


**Which one of the following is a correct boolean representation?**
Your Answer
xy'z:100

Explanation
For every complemented variable, we will use 1. For every non-complemented variable, we will use 0.

**Why do we need to simplify functions?**
To increase speed and performance

**Which of the following expressions has an essential prime implicant**
x+yz'

**What are the two types of minterms?**
Minterms can be classified into two categories : prime implicant and essential prime implicant. Prime implicants are minterms which cannot be grouped or ordered with another minterm for a possible reduction. Essential prime implicants exist where no minterm can be skipped according to the laws of simplification. For this reason, if a minterm has only one prime implicant, then no further reduction of that minterm is possible. This is called an essential prime implicant.

**Which of the following expressions is eligible for a simplification using Quine-McCluskey Algorithm?** 
x'yx+xy'z+xyz' 

**What is the purpose of the Quine-McCluskey algorithm?**
Reduce and simplify a Boolean or digital function

### Combinational Circuits

#### Definition

* **Combinational circuits** are digital circuits with `N` inputs and `M` outputs.
* They have **no memory**: output depends only on current inputs.
* Logic states are binary: `0` (OFF) and `1` (ON).

---

#### Problem Statement

**Design Goal**: Create a combinational circuit where a **light turns ON** when the input is a **prime number between 0 and 10**.

* Prime numbers: `2, 3, 5, 7`
* Output: `1` (ON) for these inputs; `0` (OFF) for all others

---

#### Binary Representation

Inputs must be expressed in binary:

| Decimal | Binary | Output |
| ------- | ------ | ------ |
| 0       | 000    | 0      |
| 1       | 001    | 0      |
| 2       | 010    | 1      |
| 3       | 011    | 1      |
| 4       | 100    | 0      |
| 5       | 101    | 1      |
| 6       | 110    | 0      |
| 7       | 111    | 1      |

---

#### Logic Gate Functions

* **AND Gate**: Output is 1 only if *all* inputs are 1.
* **OR Gate**: Output is 1 if *any* input is 1.
* **NOT Gate**: Inverts the input (0 becomes 1, and vice versa).

---

#### Minterms & Boolean Expression

From the truth table, extract minterms for output = 1:

* Minterms for 2, 3, 5, 7:

  * `010` → `A' B C'`
  * `011` → `A' B C`
  * `101` → `A B' C`
  * `111` → `A B C`

**Boolean Expression (F)**:

```
F = A'BC' + A'BC + AB'C + ABC
```

---

#### Circuit Design Steps

1. **Inputs**: Label switches `A`, `B`, `C`
2. **NOT Gates**: Invert inputs where needed (e.g., `A'`, `C'`)
3. **AND Gates**:

   * Gate G: A' B C'
   * Gate H: A' B C
   * Gate I: A B' C
   * Gate J: A B C
4. **OR Gate**: Combine outputs from all four AND gates

**Final Output (F)**: ON for binary inputs `010`, `011`, `101`, `111`

---

#### Circuit Testing

Test inputs such as:

* Input: `010` → Output: `1` ✅
* Input: `100` → Output: `0` ✅
* Input: `111` → Output: `1` ✅

---

#### Summary

* **Combinational circuits** have no memory and depend entirely on present inputs.
* They are defined using **truth tables**, **Boolean expressions**, and **logic gates**.
* **Minterms** from the truth table are simplified to design an optimized circuit.
* Final circuit is validated by testing binary inputs to confirm logic functionality.

1. Which input will NOT hold true for output F?	
  1000
2. What are combinational circuits?	
  Combinational circuits are  electronic digital circuits with 𝑁 inputs and 𝑀outputs using logic gates
3. Boolean expression for output F?	
  𝐹=AD [C+C(B +AB)]
4. Which input will hold true for output F?	
  1010 
5. How many input switches are needed?	
  4  


### Combinational Circuits Part 2

#### Overview

* **Combinational Circuits (CC)**: Logic gate-based circuits with no memory.
* **Output depends solely on current inputs**.
* Used for data processing and arithmetic in digital systems.

---

#### Types of Combinational Circuits

---

#### Adders

**Adders** perform binary addition.

##### Half Adder

* **Inputs**: A, B
* **Outputs**: Sum (S), Carry (C)
* **Boolean Expressions**:

  * S = A'B + AB'
  * C = AB
* **Use**: Adds 2 single-bit binary numbers.

##### Full Adder

* **Inputs**: A, B, Carry-in (Cin)
* **Outputs**: Sum (S), Carry-out (Co)
* **Boolean Expressions**:

  * S = A'B'Cin + A'BCin' + AB'Cin' + ABCin
  * C = A'BCin + AB'Cin + ABCin' + ABCin
* **Use**: Adds 2 binary digits and a carry input.

---

#### Subtractors

**Subtractors** perform binary subtraction.

##### Half Subtractor

* **Inputs**: X, Y
* **Outputs**: Difference (D), Borrow-out (Bout)
* **Boolean Expressions**:

  * D = X'Y + XY'
  * Bout = X'Y

##### Full Subtractor

* **Inputs**: X, Y, Bin (Borrow-in)
* **Outputs**: Difference (D), Borrow-out (Bout)
* **Boolean Expressions**:

  * D = X'Y'Bin + X'YBin' + XY'Bin' + XYBin
  * Bout = X'Y'Bin + X'YBin' + X'YBin + XYBin

---

#### Multiplexers (MUX)

* **Purpose**: Select one input from multiple data lines to output.
* **Control Lines**: Select which input is routed.
* **Common Types**: 2:1, 4:1, 8:1, 16:1, 32:1

##### 2:1 Multiplexer

* **Inputs**: D0, D1, Select line E
* **Output**: Y
* **Boolean Expression**:
  Y = D1E' + D0E

---

#### De-Multiplexers (DEMUX)

* **Purpose**: Distribute one data input to one of several outputs.
* **Control Lines**: Determine the active output.
* **Example**: 1:4 DEMUX
* **Boolean Expressions**:

  * A = S1'S2'Din
  * B = S1'S2Din
  * C = S1S2'Din
  * D = S1S2Din

---

#### Encoder

* **Purpose**: Converts `2ⁿ` input lines to `n` output lines.
* **Example**: 4:2 Encoder
* **Boolean Expressions**:

  * Y1 = X2 + X3
  * Y2 = X1 + X3

---

#### Decoder

* **Purpose**: Converts `n` input lines to `2ⁿ` outputs.
* **Example**: 2:4 Decoder with Enable (E)
* **Boolean Expressions**:

  * Y1 = EX1X2
  * Y2 = EX1X2'
  * Y3 = EX1'X2
  * Y4 = EX1'X2'

---

#### Summary

* **Combinational Circuits** consist of logic gates, without memory.
* **Adders**: Perform binary addition.
* **Subtractors**: Perform binary subtraction.
* **Multiplexers**: Select one input from many.
* **De-Multiplexers**: Distribute input to one of many outputs.
* **Encoders**: Convert multiple inputs into binary output.
* **Decoders**: Convert binary input into multiple outputs.
* Widely used in **data routing, arithmetic, and digital control systems**.

### Logisim

#### What Is Logisim?

* A **free graphical tool** used to design and simulate logic circuits.
* Ideal for learning **computer architecture** and building digital circuits, including **CPUs**.
* Allows **hierarchical circuit design**—you can create larger circuits from smaller ones.
* **Cross-platform** and easy to use with a **color-coded, intuitive interface**.

#### Key Features

* Design with **logic gates, multiplexers, decoders**, etc.
* Test circuits using **interactive pin values**.
* Save designs as `.circ` files or **images**.
* **Drag-and-drop canvas** with real-time simulation feedback.

---

#### Getting Started

##### Download

* Free download from: [http://www.cburch.com/logisim/download.html](http://www.cburch.com/logisim/download.html)
* Though no longer updated, it remains popular among students and educators.

##### Interface Overview

* **Canvas**: Main area to build circuits.
* **Explorer Pane**: Contains logic components.
* **Attributes Pane**: Change properties (direction, bit width, labels).
* **Toolbar Icons**:

  * Arrow (Select/move)
  * Hand (Test/change inputs)
  * "A" (Add labels)

---

#### Creating a Circuit in Logisim

##### Example: Simple Circuit (A AND (B OR C) → Z)

**Components**:

* 3 Inputs: A, B, C
* OR gate (for B and C)
* AND gate (for A and output of OR)
* Output: Z

##### Step-by-Step:

1. **Add Inputs**: Use pin tool; label A, B, C.
2. **Add OR Gate**: Connect B and C to it; set to 2 inputs.
3. **Add AND Gate**: Connect A and output from OR gate to it.
4. **Add Output Pin (Z)**.
5. **Connect Components**:

   * B and C → OR gate
   * A → AND gate
   * OR gate output → AND gate
   * AND gate output → Z

##### Truth Table:

| A | B | C | Z |
| - | - | - | - |
| 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 0 |
| 0 | 1 | 0 | 0 |
| 0 | 1 | 1 | 0 |
| 1 | 0 | 0 | 0 |
| 1 | 0 | 1 | 1 |
| 1 | 1 | 0 | 1 |
| 1 | 1 | 1 | 1 |

---

#### Testing the Circuit

* Use the **hand icon** to toggle inputs and observe outputs.
* Green lines = active (1); Red lines = errors.
* Validate behavior against the truth table.

---

#### Online Alternatives

If Logisim is unavailable, some online options:

* **Circuit Lab**
* **CircuitVerse**
* **Multisim**

*Note: Official course assignments require Logisim compatibility.*

---

#### Lesson Summary

* **Logisim** is a visual, educational tool for designing digital circuits.
* Useful for simulating logic operations and testing combinations.
* Provides a hands-on understanding of circuit functionality through real-time interaction.
* Supports a wide range of **logic components** and **circuit complexity**.

### Logisim Part 2

#### Overview

* Logisim is a **free Java-based simulator** used to design and test logic circuits through a **graphical user interface**.
* Supports major platforms: **Windows, Linux, and macOS**.
* Released under **GNU Public License**.
* Requires **Java Runtime Environment (JRE) 5 or higher**.

---

#### Installation Steps

1. **Verify JRE**:

   * Install and configure Java if not already present.
2. **Download Logisim**:

   * [Download Link](http://www.cburch.com/logisim/download.html)
3. **Run Logisim**:

   * Run in terminal: `java -jar logisim-XX.jar` (replace `XX` with version).
   * Or double-click the file (macOS users may need to install extra dependencies).

---

#### Logisim Interface

* **Explorer Pane**: Contains component libraries and project circuits.
* **Toolbar**: Frequently used tools and logic components (e.g., AND, OR, NOT gates).
* **Attribute Table**: Displays editable properties of selected components.
* **Canvas**: Main workspace for placing and wiring components.

---

#### Building Circuits in Logisim

##### Basic Steps:

1. **Select a component** from toolbar or explorer pane.
2. **Click on canvas** to place it.
3. **Wire components**:

   * Click and hold from one pin.
   * Drag to another pin and release.
4. **Change attributes** using the attribute table (e.g., number of inputs, direction).
5. **Test** using the poke tool (hand icon).

---

#### Example 1: Half Adder

##### Truth Table

| A | B | S (Sum) | C (Carry) |
| - | - | ------- | --------- |
| 0 | 0 | 0       | 0         |
| 0 | 1 | 1       | 0         |
| 1 | 0 | 1       | 0         |
| 1 | 1 | 0       | 1         |

* **S = A XOR B**
* **C = A AND B**

##### Steps:

1. Insert 2 **inputs**, label as A and B.
2. Add **XOR** and **AND** gates from the “Gates” library.

   * Set inputs of each gate to 2.
3. Add 2 **outputs**, label as S and C.
4. Wire:

   * A and B → XOR → S
   * A and B → AND → C
5. Use **poke tool** to toggle inputs and observe outputs.

---

#### Example 2: Full Adder

##### Truth Table

| A | B | Cin | S | Cout |
| - | - | --- | - | ---- |
| 0 | 0 | 0   | 0 | 0    |
| 0 | 0 | 1   | 1 | 0    |
| 0 | 1 | 0   | 1 | 0    |
| 0 | 1 | 1   | 0 | 1    |
| 1 | 0 | 0   | 1 | 0    |
| 1 | 0 | 1   | 0 | 1    |
| 1 | 1 | 0   | 0 | 1    |
| 1 | 1 | 1   | 1 | 1    |

##### Steps:

1. Rename the **half-adder** circuit.
2. Go to **Project > Add Circuit**, name it `full-adder`.
3. Add **two instances** of the half-adder circuit from the explorer pane.
4. Wire the full-adder using the half-adders:

   * Inputs: A, B, Cin
   * Outputs: S, Cout
5. Use **poke tool** to verify outputs against the truth table.

---

#### Summary

* Logisim is a **versatile, platform-independent** circuit simulator.
* Allows intuitive **drag-and-drop** circuit design with real-time simulation.
* You can build both **simple (half adder)** and **composite (full adder)** circuits.
* Supports modular design and **hierarchical circuit reuse**.
* Ideal for students and educators in **digital logic and computer architecture**.

### 4-Bit Arithmetic Logic Unit (ALU) in Logisim

#### Overview

A 4-bit ALU (Arithmetic Logic Unit) performs logic and arithmetic operations on 4-bit binary inputs. In this build, we'll implement:

* **AND**
* **OR**
* **NOT**
* **Addition/Subtraction**

We'll use **Logisim** to create reusable sub-circuits and combine them into the main ALU circuit.

---

#### Initial Setup

* Create and save a new Logisim file as `4-bit ALU.circ`.
* Right-click the project folder and **Add Circuit** for each sub-circuit:

  * `Full Adder`
  * `4-bit Adder/Subtractor`
  * `4-bit AND`
  * `4-bit OR`

---

#### Full Adder Sub-Circuit

##### Components:

* Input Pins: `A`, `B`, `In`
* Output Pins: `Result`, `Out`
* Gates: 2 XOR, 2 AND, 1 OR

##### Logic:

* `Result = A XOR B XOR In`
* `Out (Carry) = (A AND B) OR (In AND (A XOR B))`

---

#### 4-bit Adder/Subtractor

##### Components:

* 4 Full Adders (from the previous step)
* Input Pins: `A[4-bit]`, `B[4-bit]`, `Add/Subtract Control`
* XOR Gates to flip bits of `B` for subtraction
* Output Pins: `Carry Out`, `Overflow`
* Use of splitters for organizing input/output buses

##### Logic:

* Subtraction handled by XORing `B` with control line and inputting control as the carry-in
* Overflow determined by carry into/out of the MSB

---

#### 4-bit OR / 4-bit AND

##### Shared Structure:

* Inputs: `A[4-bit]`, `B[4-bit]`
* Split inputs into 4 individual bits using splitters
* Logic Gates:

  * For OR: 4 OR gates
  * For AND: 4 AND gates
* Output: `Result[4-bit]`

---

#### ALU Assembly (Main Circuit)

##### Step 1: Inputs

* Add 2 East-facing input pins: `A[4-bit]`, `B[4-bit]`

##### Step 2: Add Sub-Circuits

* Place:

  * `4-bit Adder/Subtractor`
  * `4-bit AND`
  * `4-bit OR`

##### Step 3: Multiplexers

* Add 2 Multiplexers (4-bit each) to choose between operations
* Control line selects between AND, OR, and arithmetic operations

##### Step 4: Control Pins

* Add 2 North-facing input pins (1-bit): control lines `0` and `1`

##### Step 5: Splitter

* Use a splitter to feed the final MUX output into a 4-input OR gate

##### Step 6: OR + NOT Gates

* OR gate to detect if all output bits are `0`
* NOT gate to produce a `ZERO` flag
* Add a `ZERO` output pin

##### Step 7: MUX Result Output

* Add a 4-bit West-facing output pin for final result

##### Step 8: Overflow, Carry, Negative Flags

* Add 3 output pins:

  * `Negative`: MSB of output
  * `Carry`: from Adder/Subtractor
  * `Overflow`: from Adder/Subtractor

---

#### Final Connections

* Carefully wire all components
* Use neat routing and splitters to manage 4-bit buses
* Confirm:

  * MUX selects correct outputs
  * Flags are wired from the correct places

---

#### Testing the ALU

##### Procedure:

* Use **poke tool** to toggle inputs and control bits
* Validate output from:

  * Result pin
  * ZERO flag
  * Carry, Overflow, and Negative flags
* Use test values (e.g., `A = 1111`, `B = 0001`) and toggle between addition, subtraction, AND, and OR

---

#### Lesson Summary

* Created a modular 4-bit ALU using Logisim.
* Designed key sub-circuits: Full Adder, Adder/Subtractor, AND, and OR.
* Used multiplexers to select between logic and arithmetic functions.
* Implemented support for flags: **ZERO**, **CARRY**, **OVERFLOW**, **NEGATIVE**.
* Tested the ALU thoroughly with various inputs and control combinations.
