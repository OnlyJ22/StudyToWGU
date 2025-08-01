### What Is a Byte?

#### Definition

* A **byte** is the **basic unit of information** used in computers.
* It consists of **8 bits**.
* Each **bit** (binary digit) has two possible values: **0 or 1**.
* A byte can represent **256 unique combinations** (2⁸ = 256).

---

#### Bits vs. Bytes

| **Bit**            | **Byte**                                    |
| ------------------ | ------------------------------------------- |
| 1 or 0             | Group of 8 bits                             |
| Smallest data unit | Standard chunk for storing/processing data  |
| Limited use alone  | Used to represent characters, numbers, etc. |

---

#### Why 8 Bits?

* **8-bit grouping** allows representation of:

  * Characters (letters, numbers, punctuation)
  * Instructions, symbols, and control codes
* **256 combinations** = enough for extended character sets like ASCII.

---

#### Origin of the Term "Byte"

* **Invented by**: *Werner Buchholz* (1956)
* Originally called a **“bite”**, but changed to “**byte**” to avoid confusion with “bit.”
* Intended to describe what a computer could "chew" on at once.
* **Alternative term**: *Octet* (rarely used outside of networking).

---

#### Binary and Decimal Comparison

* Computers use **binary** (base-2); humans use **decimal** (base-10).
* **Binary value of 42**:

  * Decimal: 42 = (2×1) + (8×1) + (32×1) = `00101010` in binary
* Byte structure uses **powers of 2** for each bit position (e.g., 1, 2, 4, 8...).

---

#### Common Byte Size Units

| **Unit**       | **Value (Binary)** | **Approx. Value (Decimal)** |
| -------------- | ------------------ | --------------------------- |
| **1 Byte**     | 8 bits             | 1 character                 |
| **1 Kilobyte** | 1,024 bytes        | \~1,000 bytes               |
| **1 Megabyte** | 1,024 KB           | \~1 million bytes           |
| **1 Gigabyte** | 1,024 MB           | \~1 billion bytes           |
| **1 Terabyte** | 1,024 GB           | \~1 trillion bytes          |

> ⚠ **Note**: Storage = powers of 2 (1,024). Data transfer = powers of 10 (1,000).

---

#### Real-World Use of Bytes

* Bytes are used to represent:

  * **Characters** in text files (e.g., "A" = 01000001 in binary)
  * **Pixel color data** in images
  * **Sound samples** in audio files
  * **Instructions** for programs
* Larger byte units help measure:

  * **Memory size**
  * **Storage capacity**
  * **Data file sizes**

---

#### Summary

* A **byte = 8 bits**, used to represent more than just on/off values.
* Enables modern computing by encoding characters, numbers, and media.
* Coined by Werner Buchholz in 1956 to describe the amount a machine could process.
* Grouped into **KB, MB, GB, TB**, and beyond to describe larger capacities.
* Fundamental to computing—bytes power everything from your text messages to video files.

### Analog and Digital Signals

#### Analog Signal

* **Definition**: Continuous wave signal, represented by a **sine wave**.
* **Characteristics**:

  * Varies in **amplitude** (signal strength) and **frequency** (wave cycles over time).
  * Infinite values within a range.
* **Examples**:

  * Human voice (sound waves)
  * Light (vision)
  * Analog clocks (continuous motion of hands)
* **Pros**:

  * Can carry **infinite data**
  * **Lower initial cost** of equipment
  * Easier to control and process in simple systems
* **Cons**:

  * **Sensitive to noise and interference**
  * **Slower transmission speeds**

---

#### Digital Signal

* **Definition**: Discrete signal using **binary values (0s and 1s)**.
* **Characteristics**:

  * **Uniform**, consistent structure
  * No fractional values—only on/off states
* **Examples**:

  * Digital watches
  * Computers, smartphones
* **Pros**:

  * **High speed** of transmission
  * **Reliable**, less affected by interference
* **Cons**:

  * More **complex**
  * Typically **higher upfront cost**

---

#### Modem and Signal Conversion

| **Term**         | **Definition**                                                   |
| ---------------- | ---------------------------------------------------------------- |
| **Modem**        | Device that combines **modulator** and **demodulator** functions |
| **Modulation**   | Converts **digital → analog** signal                             |
| **Demodulation** | Converts **analog → digital** signal                             |

* **Usage**:

  * Needed for **communication** between analog (e.g., voice) and digital (e.g., computer) systems.
  * Enables **data transfer** over standard transmission media (e.g., telephone lines).

---

#### Signal Comparison Table

| **Digital Signal**                               | **Analog Signal**                            |
| ------------------------------------------------ | -------------------------------------------- |
| Uses **binary** (0s and 1s)                      | Uses **continuous sine wave**                |
| **Consistent**, clear structure                  | Varies in **amplitude** and **frequency**    |
| High **transmission speed**                      | Can **carry infinite values**                |
| **Less affected** by noise/interference          | **Susceptible** to noise                     |
| Ideal for **modern computing and communication** | Lower cost, easier to manage for basic needs |

---

#### Summary

* **Analog signals** are continuous and represent real-world data like sound and light.
* **Digital signals** are binary, faster, more reliable, and widely used in modern technology.
* **Modems** enable communication by converting between analog and digital formats.
* While analog has its place in cost-effective and basic uses, **digital is superior** for speed, consistency, and data transmission in today’s systems.

### Number Systems

#### What Is a Number System?

* A **number system** is a method for expressing numbers using symbols and positional value.
* Prevents the need for an infinite number of unique symbols.
* **Uses digit positions ("slots")** to scale values (e.g., units, tens, hundreds).

---

#### Base-Ten (Decimal) System

* Most commonly used system in everyday life.
* Uses **10 digits (0–9)**.
* Place values: **units, tens, hundreds, thousands**, etc.
* Example:

  * 10 = (1 × 10) + (0 × 1)

---

#### Binary System (Base-Two)

* Used by **computers**.
* Only **2 digits**: 0 and 1 (on/off).
* Place values: **1s, 2s, 4s, 8s, 16s**, etc.
* Example:

  * 11 (decimal) = **1011** in binary

    * (1×8) + (0×4) + (1×2) + (1×1)

---

#### Base-Four System

* Uses **digits 0–3**.
* Place values: **1s, 4s, 16s, 64s**, etc.
* Example:

  * 30 (decimal) = **0132** in base-four

    * (0×64) + (1×16) + (3×4) + (2×1)

---

#### Base-Five System

* Uses **digits 0–4**.
* Place values: **1s, 5s, 25s, 125s**, etc.
* Example:

  * 206 (decimal) = **1311** in base-five

    * (1×125) + (3×25) + (1×5) + (1×1)

---

#### Summary Table

| **Term**        | **Explanation**                                             |
| --------------- | ----------------------------------------------------------- |
| Number System   | A structured method to write and represent numbers          |
| Base-Ten        | Standard decimal system using digits 0–9                    |
| Binary (Base-2) | System using only 0 and 1; used in computing                |
| Place Value     | The position of a digit determines its actual numeric value |
| Slots in Binary | 1s, 2s, 4s, 8s, 16s, ...                                    |
| Slots in Base-5 | 1s, 5s, 25s, 125s, ...                                      |

### Binary Number System History

#### Origin of the Binary System

* **Gottfried Wilhelm Leibniz (1703)** published *Explanation of Binary Arithmetic*.
* Introduced a number system using only **0 and 1**.
* Inspired by ancient Chinese philosophy (Fu Xi, \~4000 years earlier).
* Goal: **simplify logic and computation**.

---

#### Binary vs. Decimal

* **Decimal system (base-10)** uses digits 0–9.
* **Binary system (base-2)** uses only digits 0 and 1.
* **Positional logic** is the same:

  * In decimal: 9 → 10, 99 → 100
  * In binary: 1 → 10, 11 → 100

---

#### Binary Counting Example (1–11 Decimal)

| Decimal | Binary |
| ------- | ------ |
| 1       | 1      |
| 2       | 10     |
| 3       | 11     |
| 4       | 100    |
| 5       | 101    |
| 6       | 110    |
| 7       | 111    |
| 8       | 1000   |
| 9       | 1001   |
| 10      | 1010   |
| 11      | 1011   |

---

#### Binary to Decimal Conversion

* Use **place values as powers of 2** (right to left): 1, 2, 4, 8, 16, etc.
* Example: **10101 (binary)** = 1×16 + 0×8 + 1×4 + 0×2 + 1×1 = **21 (decimal)**

---

#### Importance in Computing

* **Computers use binary** because electronics function in two states: **on (1)** and **off (0)**.
* Binary enables **fast, reliable, and logical processing** in hardware.

---

#### Summary Table

| Concept                   | Description                                                 |
| ------------------------- | ----------------------------------------------------------- |
| Binary System             | Number system using only 0 and 1                            |
| Inventor                  | Gottfried Wilhelm Leibniz, 1703                             |
| Logical Structure         | Same as decimal; each digit place increases by a power of 2 |
| Binary in Computing       | Matches electronic on/off states for efficient processing   |
| Binary to Decimal Example | 10101 (binary) = 21 (decimal)                               |

### What Is the Binary System?

#### Definition

* **Binary system (base-2)** is a number system that uses **only two digits: 0 and 1**.
* Each digit is a **bit**.
* Each position represents a **power of 2**:

  * From right to left: 2⁰, 2¹, 2², etc.
  * Example: `1011` = (1×8) + (0×4) + (1×2) + (1×1) = **11 (decimal)**

---

#### Applications of Binary

* **Computers & Digital Encoding**

  * All modern computing is based on binary logic (on = 1, off = 0).
  * Every pixel on a screen can be defined using binary (e.g., **16-bit color** = 2¹⁶ = **65,536 color combinations**).
* **Boolean Algebra**

  * Binary logic used in computing and logic circuits.
  * 0 = False, 1 = True

---

#### Binary Arithmetic

**Addition**

* 0 + 0 = 0
* 0 + 1 = 1
* 1 + 1 = **10** (carry the 1)

**Multiplication**

* 0 × 0 = 0
* 0 × 1 = 0
* 1 × 1 = 1

Compared to base-10:

* **Binary only requires 3 rules** for each operation
* **Decimal requires 100+ rules** for full multiplication/addition tables

---

#### Advantages of the Binary System

* **Simplicity**: Easy to implement using on/off states (ideal for hardware).
* **Reliability**: Minimal room for misinterpretation or signal loss.
* **Efficient for computation**: Fewer operations, easier logic design.
* **Essential for digital systems**: Computers, networks, logic gates, etc.

---

#### Fun Example – Binary Joke Explained

> "There are **10 kinds of people** in the world: those who understand binary and those who don’t."

* In binary, `10` = **2 in decimal**
* So the joke means: **“There are two kinds of people…”**

### ASCII (American Standard Code for Information Interchange)

#### Overview

* **ASCII** is a standardized code developed in the **1960s** to ensure consistency in programming.
* It maps characters (letters, numbers, symbols) to **binary values** that computers can process.

---

#### Binary Basics

* **Binary system (base-2)**: Uses two digits — **0 and 1** (on/off).
* A **bit** = 1 binary digit.
* **8 bits = 1 byte = 1 character** in ASCII.

  * Example: `01001100` = **L**

---

#### ASCII Character Set

* Standard ASCII includes **128 characters**:

  * Uppercase A–Z
  * Lowercase a–z
  * Digits 0–9
  * Special characters (e.g., !, @, #)
* All characters are represented in **binary code** for computer understanding.

---

#### File Sizes & Storage

| Unit        | Size (in bytes)                           |
| ----------- | ----------------------------------------- |
| 1 byte      | 8 bits = 1 character                      |
| 1 kilobyte  | \~1,024 bytes                             |
| 1 megabyte  | \~1,048,576 bytes                         |
| 1 gigabyte  | \~1,073,741,824 bytes                     |
| 1 terabyte  | \~1,099,511,627,776 bytes                 |
| 1 petabyte  | \~1,125,899,906,842,624 bytes             |
| 1 yottabyte | \~1,208,925,819,614,629,174,706,176 bytes |

* Example: A **two-page** double-spaced document ≈ **1,000 characters** ≈ **15 KB**

---

#### Translation Process

* **Input (human-readable)** → **ASCII → Binary** → Computer processing
* **Output (computer binary)** → **Binary → ASCII** → Human-readable response

---

#### Summary Points

* **ASCII bridges human language and binary code**.
* It standardizes how characters are represented and stored as bytes.
* It supports modern **data processing, storage**, and **communication**.
* All computing today builds on **byte-based character encoding** like ASCII.

### Understanding Binary and Decimal

#### Number System Bases

* **Binary system (base-2)**: Uses only 0 and 1.
* **Decimal system (base-10)**: Uses digits 0–9.
* Machines use binary to represent letters, digits, and characters.

---

#### Definitions

* **Bit**: A single binary digit (0 or 1).
* **Byte**: A group of 8 bits.
* **Unsigned binary**: All 8 bits are used to represent the number.
* **Signed binary**: The leftmost bit indicates positive/negative.

---

#### Converting Binary to Decimal — Sum of Weights Method

1. Create a binary table of powers of 2 for 8 bits:

   ```
   2^7  2^6  2^5  2^4  2^3  2^2  2^1  2^0
   128  64   32   16    8    4    2    1
   ```
2. Example binary: `10010100₂`

   ```
   Bits:      1   0   0   1   0   1   0   0
   Weights: 128   x   x  16   x   4   x   x
   Total:   128 + 16 + 4 = 148₁₀
   ```

---

#### Converting Decimal to Binary — Recursive Division Method

1. Start with a decimal number (e.g., **123**).
2. Divide by 2 repeatedly, noting the **remainders**:

   ```
   123 ÷ 2 = 61 r 1  
   61 ÷ 2 = 30 r 1  
   30 ÷ 2 = 15 r 0  
   15 ÷ 2 = 7  r 1  
   7 ÷ 2  = 3  r 1  
   3 ÷ 2  = 1  r 1  
   1 ÷ 2  = 0  r 1  
   ```
3. Read remainders **bottom to top**: `1111011`
4. Pad with leading zero to make 8 bits: `01111011₂`

* Confirm:
  `64 + 32 + 16 + 8 + 2 + 1 = 123₁₀`

---

#### Summary

* **Binary is base-2**, using digits 0 and 1; **decimal is base-10**.
* Use:

  * **Sum of Weights** to convert **binary → decimal**
  * **Recursive Division** to convert **decimal → binary**
* A **byte = 8 bits**.
* Ensure correct conversion by checking values against the binary weight table.

### A Binary Number

#### What Is a Binary Number?

* Binary numbers use only **0** and **1**.
* Computers operate using **machine language** (binary).
* Each digit or character is converted into a binary sequence for processing.
* Binary numbers are usually represented with a subscript ₂ (e.g., `10010010₂`).

---

#### Signed Magnitude Representation

* **Signed magnitude** uses the **most significant bit (MSB)** (leftmost bit) to indicate sign:

  * `0` = positive
  * `1` = negative
* Remaining **n-1 bits** store the value (magnitude).

**Examples (8-bit representation):**

* `+18` → `00010010`
* `-18` → `10010010`

**Range (n-bit):**

* {–(2ⁿ⁻¹ – 1), …, +(2ⁿ⁻¹ – 1)}
* **Zero is represented twice**: `00000000` and `10000000`

---

#### Decimal to Signed Binary (Example: +18)

1. Convert 18 to binary:

   ```
   18 ÷ 2 = 9 r 0
   9 ÷ 2 = 4 r 1
   4 ÷ 2 = 2 r 0
   2 ÷ 2 = 1 r 0
   1 ÷ 2 = 0 r 1
   Binary = 0010010 (7 bits)
   ```
2. Add sign bit:

   * `+18` = `0` + `0010010` → `00010010`
   * `-18` = `1` + `0010010` → `10010010`

---

#### Signed Binary to Decimal

Use powers of 2 for the last 7 bits (n – 1):

* `(00010010)₂ = 16 + 2 = 18` → positive (MSB is 0)
* `(10010010)₂ = 16 + 2 = 18` → negative (MSB is 1) → `–18`

---

#### One’s Complement

* Negative number is formed by **flipping all bits** of the positive version (0 ↔ 1).
* MSB still represents the **sign**.
* **Drawback**: **Zero is represented twice** (like signed magnitude).

**Example (3-bit system):**

* `+2` = `010`
* One’s complement of `+2` = `101` (represents –2)

---

#### Two’s Complement

* Step 1: Take the **one’s complement**.
* Step 2: **Add 1** to it.
* Solves zero duplication and simplifies arithmetic operations.

**Example (+18 in 8 bits):**

* `+18` = `00010010`
* One’s complement: `11101101`
* Add 1 → `11101110` → This is `–18` in two’s complement

**Range (n-bit):**

* {–(2ⁿ⁻¹), …, +((2ⁿ⁻¹) – 1)}
* **Zero is only represented once.**
* **Best for arithmetic operations** in computing.

---

#### Summary

* **Binary** = computer language (0s and 1s), written with subscript ₂.
* **Signed magnitude** uses the MSB to indicate sign but duplicates zero.
* **One’s complement** flips bits to indicate negative values but also duplicates zero.
* **Two’s complement** flips bits then adds one — **most efficient and accurate** system for representing signed integers in computing.

The range for this signed magnitude representation is {-(2n-1-1), +(2n-1-1)}.

The range of 2's complement number is {-(2n-1), +(2n-1-1)}.

### Binary vs Decimal

#### Base Systems Overview

* **Decimal system (base 10)** uses digits **0–9**.

  * Each position is a power of **10**.
  * Example: Multiplying/dividing by 10 shifts the decimal point left or right.
* **Binary system (base 2)** uses digits **0 and 1**.

  * Each position is a power of **2**.
  * Multiplying/dividing by 2 shifts the binary point left or right.

---

#### Fixed Point Binary

* A **fixed point binary number** includes a **binary point** (like a decimal point).

  * Example: `0100.0001`
* Used to represent both whole and fractional values in binary.

---

#### Converting Binary to Decimal

* **Left of the point**: multiply digits by **2ⁿ**, where **n starts at 0** (rightmost) and increases leftward.
* **Right of the point**: multiply digits by **2⁻ⁿ**, where **n starts at 1** and increases rightward.

**Example: Convert `1110.0011` to decimal**

* Integer part (`1110`):
  `1×8 + 1×4 + 1×2 + 0×1 = 14`
* Fractional part (`0011`):
  `0×½ + 0×¼ + 1×⅛ + 1×1/16 = 0.1875`
* **Result:** `14.1875`

---

#### Converting Decimal to Binary

* **Left of decimal**:
  Divide repeatedly by 2, record **remainders right to left**.

**Example: Convert 14 to binary**

```
14 ÷ 2 = 7 R0
7 ÷ 2 = 3 R1
3 ÷ 2 = 1 R1
1 ÷ 2 = 0 R1
→ 1110
```

* **Right of decimal (0.1875)**:
  Multiply repeatedly by 2, record **whole numbers left to right**:

```
0.1875 × 2 = 0.375 → 0  
0.375 × 2 = 0.75   → 0  
0.75 × 2 = 1.5     → 1  
0.5 × 2 = 1.0      → 1  
→ .0011
```

* **Result:** `14.1875` = `1110.0011`

---

#### Summary

* **Decimal (base 10)** uses 0–9; **Binary (base 2)** uses 0 and 1.
* **Fixed point binary** includes a binary point to express fractions.
* **Binary to Decimal**: use powers of 2.
* **Decimal to Binary**:

  * Left of point: divide by 2 → remainders (right to left)
  * Right of point: multiply by 2 → integers (left to right)

**What is the binary fixed point value for the decimal number 13.875?**
cannot be represented

**What is the decimal value for the fixed point binary number 0100.0010?**
4.125

**To convert a decimal to a binary, the value to the _____ is divided by the _____.**
left; base 2


**Decimal numbers are converted to binary using which?**
division by powers of base 2.

**To convert a fixed point binary number to its decimal value, all digits to the _____ of the decimal should be multiplied by _____.**
right; 2-n


### What Is the Floating Point?

#### Definition

* A **floating point number** allows the decimal point to "float" to various positions.
* Enables representation of both **very large** and **very small** real numbers.
* Two main types:

  * **Single precision**: 32 bits (4 bytes)
  * **Double precision**: 64 bits (8 bytes)

---

#### Floating Point Structure (Single Precision)

A 32-bit floating point number consists of:

* **1 bit** for the **sign** (0 = positive, 1 = negative)
* **8 bits** for the **exponent**
* **23 bits** for the **mantissa (fraction)**

**Example:** For -4.124 × 10³

* Sign = 1
* Mantissa = 4.124
* Exponent = 3

---

#### Number Systems Overview

* **Binary (base 2)**: digits 0 and 1
* **Decimal (base 10)**: digits 0–9
* **Hexadecimal (base 16)**: digits 0–9, A–F
* **Octal (base 8)**: digits 0–7

---

#### Steps to Convert Decimal to Binary Floating Point

**Example: Convert 36.890625 to IEEE 754 Single Precision**

**Step 1: Convert Integer Part to Binary**
36 → `100100`

**Step 2: Convert Fractional Part to Binary (Mantissa)**
.890625 → `111001`
Result: `100100.111001`

**Step 3: Normalize the Number**

* Normalize `100100.111001` → `1.00100111001 × 2⁵`
* Exponent = 5
* Add bias (127 for 8-bit exponent):
  5 + 127 = 132 → Binary: `10000100`

**Step 4: Build the Final Representation**

* **Sign bit** = 0 (positive)
* **Exponent** = `10000100`
* **Mantissa** = `00100111001` (drop leading 1 and fill to 23 bits)

**Final Binary**:
`0 10000100 00100111001000000000000`

---

#### Advantages of Floating Point

* Can represent a much **larger range** of values
* **Constant relative error** across magnitudes
* **Easier debugging** in scientific and engineering calculations

#### Disadvantages of Floating Point

* Requires **more storage**
* **Slower** to process than integers
* **Precision limitations** (some numbers are approximated)

---

#### Lesson Summary

* Floating point numbers allow flexible decimal placement.
* They are broken into three parts: **sign, exponent, mantissa**.
* Conversion involves:

  1. Integer-to-binary
  2. Fraction-to-binary
  3. Normalizing
  4. Calculating exponent with bias
  5. Assembling the binary format
* Common number systems used: binary, decimal, hexadecimal, octal.

### Number Systems

#### Decimal System (Base 10)

* Uses digits **0 to 9**.
* Each digit’s place value is a power of **10**:

  * Ones, Tens, Hundreds, Thousands, etc.
* Example:
  `768 = 7×100 + 6×10 + 8×1`

#### Binary System (Base 2)

* Uses only **0 and 1** (bits).
* Each digit’s place value is a power of **2**:

  * 1, 2, 4, 8, 16, 32, etc.
* Binary is used in **computers and electronics** due to two possible states: on/off.

#### Octal System (Base 8)

* Uses digits **0 to 7**.
* Place values are powers of **8**:

  * 1, 8, 64, 512, etc.
* More compact than binary.

#### Hexadecimal System (Base 16)

* Uses digits **0 to 9** and letters **A to F** (representing 10 to 15).
* Place values are powers of **16**:

  * 1, 16, 256, 4096, etc.
* Often used in computing to shorten binary representation.

---

#### Converting Decimal to Other Systems

**Decimal to Binary (Example: 35)**

1. 35 ÷ 32 = 1 (remainder 3) → 1
2. 3 ÷ 16 = 0 (remainder 3) → 0
3. 3 ÷ 8 = 0 (remainder 3) → 0
4. 3 ÷ 4 = 0 (remainder 3) → 0
5. 3 ÷ 2 = 1 (remainder 1) → 1
6. 1 ÷ 1 = 1 (remainder 0) → 1
   **Result**: `35₁₀ = 100011₂`

**Decimal to Octal (Example: 35)**

1. 35 ÷ 8 = 4 (remainder 3)
2. 3 ÷ 1 = 3
   **Result**: `35₁₀ = 43₈`

**Decimal to Hexadecimal (Example: 35)**

1. 35 ÷ 16 = 2 (remainder 3)
2. 3 ÷ 1 = 3
   **Result**: `35₁₀ = 23₁₆`

---

#### Converting Binary to Other Systems

**Binary to Decimal (Example: 01101010)**

* Multiply each bit by its place value:
  `64 + 32 + 8 + 2 = 106`
  **Result**: `01101010₂ = 106₁₀`

**Binary to Octal (Shortcut: group by 3 bits)**

* Example: `01101010` → `01 101 010`
  → `1 5 2`
  **Result**: `01101010₂ = 152₈`

**Binary to Hexadecimal (Shortcut: group by 4 bits)**

* Example: `01101010` → `0110 1010`
  → `6 A`
  **Result**: `01101010₂ = 6A₁₆`

---

#### Converting Octal to Other Systems

**Octal to Decimal (Example: 123₈)**

* `(1×64) + (2×8) + (3×1) = 64 + 16 + 3 = 83`
  **Result**: `123₈ = 83₁₀`

**Octal to Binary**

* Convert each digit to 3 bits:
  `1 = 001`, `2 = 010`, `3 = 011`
  **Result**: `123₈ = 001010011₂`

**Octal to Hexadecimal (via binary)**

* First: `123₈ = 001010011₂`
* Then group into 4s: `0001 0100 11` → `0001 0100 0011`
  → `1 4 3`
  **Result**: `123₈ = 53₁₆`

---

#### Converting Hexadecimal to Other Systems

**Hexadecimal to Decimal (Example: 2F₁₆)**

* `2×16 = 32`, `F (15) × 1 = 15`
  → `32 + 15 = 47`
  **Result**: `2F₁₆ = 47₁₀`

**Hexadecimal to Binary**

* `2 = 0010`, `F = 1111`
  **Result**: `2F₁₆ = 00101111₂`

**Hexadecimal to Octal (via binary)**

* `00101111₂` → group by 3 bits: `00 101 111`
  → `0 5 7`
  **Result**: `2F₁₆ = 57₈`

---

#### Lesson Summary

* **Decimal**: Base 10, digits 0–9
* **Binary**: Base 2, digits 0–1
* **Octal**: Base 8, digits 0–7
* **Hexadecimal**: Base 16, digits 0–9 and A–F

**Conversion Techniques:**

* Decimal to others: repeated division
* Binary to decimal: multiply and add place values
* Binary to octal/hex: group by 3s/4s
* Octal/Hex to binary: expand each digit
* Octal/Hex to decimal: multiply each digit by place value
* Octal ↔ Hex: convert to binary as an intermediate step

### Gray Code

#### Overview

* Also known as **Reflected Binary Code (RBC)**.
* Named after physicist **Frank Gray**.
* **Key feature**: **Only one bit changes** between consecutive numbers (Hamming distance = 1).

#### Purpose

* Minimize **bit errors** in systems where transitions between values occur (e.g., physical switches, encoders).
* Used in **non-arithmetic applications** like digital encoders and finite state machines.

---

#### Binary vs Gray Code

* **Binary code** is **weighted** and **positional**, used for arithmetic.
* **Gray code** is **non-weighted** and **non-arithmetic**, used for error minimization.

---

#### How Gray Code Works

* Only **one bit changes** between adjacent values.
* The **first and last numbers** also differ by one bit → **cyclical** property.
* Commonly shown with **8-bit representations**.

---

#### Binary to Gray Code Conversion

**Steps:**

1. Retain the **most significant bit (MSB)**.
2. For each remaining bit:

   * XOR the current binary bit with the **previous binary bit**.

**Example:**
Binary: `00010110`
Step-by-step XOR:

* MSB: `0`
* `0 XOR 0 = 0`
* `0 XOR 0 = 0`
* `0 XOR 1 = 1`
* `1 XOR 0 = 1`
* `0 XOR 1 = 1`
* `1 XOR 1 = 0`
* `1 XOR 0 = 1`

**Result (Gray Code):** `00011101`

---

#### Arithmeticity of Gray Code

* **Binary**: Supports arithmetic operations.
* **Gray Code**: **Does not support direct arithmetic**.

  * Example: 2 + 3 in binary = 5
  * Doing this in Gray code gives incorrect results.

**Why?**

* Gray code is **not weighted**; values don't correspond directly to positionally weighted digits.

---

#### Applications of Gray Code

* **Rotary encoders**: Ensure minimal transition errors.
* **Analog-to-digital conversion**: Less error-prone with mechanical switches.
* **State machines and counters**: Simplifies hardware transitions.
* **Error correction**: Gray code reduces the risk of multiple-bit faults.

---

#### Advantages

* **Minimal transition errors** (only 1 bit changes).
* **Cyclical property** helps in systems like rotary encoders.
* **Improved reliability** in digital circuitry and position tracking.

---

#### Lesson Summary

* **Gray Code** is a binary-like system where each successive number changes by just one bit.
* It is **non-arithmetic** and **unweighted**, making it unsuitable for direct computation.
* However, its **low Hamming distance** and **cyclical structure** make it ideal for use in **error-prone environments** like switches, encoders, and digital logic.

