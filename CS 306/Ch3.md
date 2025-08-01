### Binary Multiplication and Division

#### Prerequisite: Binary Addition & Subtraction

* Essential to understand binary addition and subtraction for performing multiplication and division.
* Binary math only uses **0** and **1**, simplifying logic operations.

---

#### Binary Multiplication

##### Basic Method

* Multiply as you would in decimal.
* Each **1** in the multiplier results in the multiplicand being added after shifting left.
* Each **0** results in skipping the addition.

##### Example: 4 × 3

* Decimal: 4 = `100`, 3 = `011`
* Multiply:

  * `100 × 1` = `100`
  * `100 × 1 (shifted left)` = `1000`
  * Add:

    ```
    0100
    ```

##### Example: 12 × 15

* Decimal: 12 = `1100`, 15 = `1111`
* Multiply each bit with shifts:

  ```
      1100
     1100
    1100
   +1100
   -------
   10110100 = 180 (Decimal)
  ```

##### Key Rules

* Multiplication by **0** → skip
* Multiplication by **1** → copy the multiplicand and shift
* Add all resulting values

---

#### Binary Division

##### Method: Four Steps

1. **Divide**: Check if divisor fits in current portion of dividend
2. **Multiply**: Multiply divisor by result of division
3. **Subtract**: Subtract result from current portion
4. **Next Digit**: Bring down next digit from dividend

##### Example: 18 ÷ 3

* Decimal: 18 = `10010`, 3 = `11`
* Steps:

  * `100` ÷ `11` → 1
  * `100 - 11 = 1`
  * Bring down next digit → `11` ÷ `11` → 1
  * `11 - 11 = 0`
  * Bring down 0 → `0` ÷ `11` → 0
  * Result = `110` = 6 (Decimal)

##### Key Rules

* Subtraction of binary values follows same borrowing rules as decimal.
* Division continues until no digits are left to bring down.

---

#### Lesson Summary

* **Binary Multiplication**:

  * Multiply each digit of multiplier with multiplicand
  * Shift left for each new bit
  * Add all shifted results

* **Binary Division**:

  * Use four steps: divide, multiply, subtract, bring down next digit
  * Result builds one bit at a time

Understanding binary operations is crucial for low-level computing, data processing, and digital logic design.

