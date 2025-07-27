### Section 1: Storing Your Achievements – Introducing Data Types

#### Why Different Data Types?

* In Java, **different types of data** need to be stored in **appropriate containers**, just like awards need different kinds of storage.

  * **Documents** go in **binders**
  * **Medals** go in **frames**
  * **Trophies** go in **display cases**
* Java provides **different data types** to store different types of information **efficiently and logically**.

---

#### Primitive Data Types

* **Primitive data types** are **predefined** by Java.
* The compiler **knows** how to **allocate memory** and **reference** them.
* They also come with a **default value**.

**List of Primitive Data Types:**

* `char` – Holds a **single Unicode character** (16-bit), range: **0 to 65,535**
* `byte` – 8-bit signed integer, range: **-128 to 127**
* `short` – 16-bit signed integer
* `int` – 32-bit signed integer
* `long` – 64-bit signed integer
* `float` – 32-bit **single-precision** decimal
* `double` – 64-bit **double-precision** decimal
* `boolean` – Holds only **true** or **false**

**Example Declaration:**

```java
public static void main(String[] args) {
  int i;
  char c;
  double d;
}
```

---

#### Non-Primitive Data Types

* **Non-primitive data types** are **created by the programmer**.
* Also called **reference variables** — they **point to** memory locations storing data.
* Not built into the language like primitives.

**Types of Non-Primitive Data:**

* **Class**
* **Interface**
* **Array**
* **Abstract Data Type (ADT)**

---

#### Class

* A **class** is a **user-defined blueprint** that defines objects.
* Can include both **variables** and **methods**.

**Example:**

```java
class Accolades {
  char event;
  int year;
  public void addAccolade(char evt, int yr) {}
}

Accolades a = new Accolades();
```

---

#### Interface

* An **interface** defines **abstract methods** (no body).
* Cannot create objects directly from an interface.
* A **class must implement** the interface to use it.

**Example:**

```java
interface Accolades {
  public void accolades_type(char type);
  public void acc_container();
}

class SchoolAcc implements Accolades {
  char acc_type;
  public void accolades_type(char type) {
    acc_type = type;
  }
  public void acc_container() {
    System.out.println("The container for the medal is a clear box");
  }
}
```

---

#### Array

* An **array** stores multiple values of the **same type**.
* Accessed using **index numbers**, starting at **0**.

**Example:**

```java
char[] alpha;         // declaration
alpha = new char[5];  // memory allocated for 5 characters
```

---

#### Identifiers and Literals

* **Identifiers**: Names for **classes**, **methods**, or **variables**
* **Literals**: The **actual values** assigned to variables

**Examples:**

```java
int a_int = 123;       // 123 is a literal; a_int is an identifier
char a_char = 'S';     // 'S' is a literal; a_char is an identifier
```

---

#### Abstract Data Type (ADT)

* An **abstract data type** hides the implementation details.
* The user interacts with the **interface**, not the internal code.
* Common in **object-oriented programming** (OOP).
* Real-world example: A **car's Start button** – you don't need to know how the engine works.

---

#### Summary

* **Primitive data types** are built into Java:

  * `char`, `byte`, `short`, `int`, `long`, `float`, `double`, `boolean`
* **Non-primitive data types** are user-defined:

  * `class`, `interface`, `array`, `abstract data type`
* **Identifiers** are names; **literals** are values.
* **Abstract data types** encapsulate logic and expose only interfaces for use.

### Section 2: Naming Conventions

#### Why Naming Conventions Matter

* **Naming conventions** make Java programs easier to **read**, **debug**, and **maintain**.
* Each **variable** or **constant** must have a **unique name**, just like people with similar-sounding names are still different individuals.
* Conventions **identify the purpose** of the element, e.g., `studentID` is clearly an identifier for a student.

---

#### Rules vs. Conventions

* **Rules**: Must be followed — violations result in **compilation errors**.
* **Conventions**: Widely accepted **best practices** — improve code **clarity** and **consistency**.

---

#### Variable Naming Rules

**1. Variable Names Are Case Sensitive**

* `initialValue`, `InitialValue`, and `Initialvalue` are **different identifiers**.
* Using mismatched capitalization will lead to **undefined variable errors**.

**Example:**

```java
int initialValue = 0;
System.out.println("Initial value: " + InitialValue); // ERROR: InitialValue not declared
```

---

**2. Variable Names Cannot Be Java Keywords**

* Keywords like `int`, `public`, `static`, and `break` have **reserved meanings**.
* Using them as variable names results in **syntax errors**.

**Incorrect:**

```java
int static = 0; // ERROR: "static" is a keyword
```

**Correct:**

```java
int static1 = 0;
```

---

**3. `main` Is Not a Java Keyword**

* `main` can be used as a variable name — it's **not reserved**.

```java
int main = 5; // Valid
```

---

**4. Variable Names Cannot Contain Spaces**

* Java does **not allow spaces** in identifiers.

**Incorrect:**

```java
int initial Value = 5; // ERROR
```

**Correct:**

```java
int initial_Value = 5;
```

---

#### Constants

**1. Use Uppercase with Underscore**

* Constants are named using **ALL CAPS** and **underscores**:

```java
final String FIRST_NAME = "Sandy";
```

* This improves readability and makes it **clear that the value should not change**.

---

**2. Constant Names Cannot Be Java Keywords**

* Same rule as variables: **no keywords**.
* Conventionally safe since keywords don’t use underscores.

---

**3. Constant Names Cannot Contain Spaces**

* Just like variables, **spaces are not allowed** in constant names.

**Incorrect:**

```java
final String FIRST NAME = "Rita"; // ERROR
```

**Correct:**

```java
final String FIRST_NAME = "Rita";
```

---

#### Component Naming Conventions

| Component          | Naming Convention                            | Example                         |
| ------------------ | -------------------------------------------- | ------------------------------- |
| Classes/Interfaces | **Capitalized nouns**, each word capitalized | `Employee`, `RemoteWorker`      |
| Methods            | **Lowercase verb**, camelCase if multi-word  | `enterData()`, `calculateSum()` |
| Variables          | **Short, descriptive**, camelCase            | `userAge`, `accountBalance`     |
| Constants          | **All uppercase**, underscores between words | `MAX_USERS`, `PI_VALUE`         |
| Packages           | **All lowercase**                            | `java.util`, `com.school.main`  |

---

#### Summary

* Java variable names are:

  * **Case-sensitive**
  * Cannot use **keywords**
  * Cannot contain **spaces**
* Constants should:

  * Be **final**
  * Use **uppercase** letters and **underscores**
* **Naming conventions** help clarify the **role** of each element in your code.
* Following both **rules** and **conventions** leads to **cleaner, more reliable programs**.

### Section 3: Java Integer Data Types: `short`, `int`, and `long`

#### Java Data Types Overview

* A **data type** defines what kind of data can be **stored in a variable**.
* Helps ensure **data integrity** (e.g., numbers stay numbers, not text).
* Java’s integer types are all **primitive**, meaning they are **built into the language** and store **simple values**.
* All three types covered here — `short`, `int`, and `long` — store **whole numbers only** (no decimals, no characters).

---

#### Declaring a Variable

* **Declaring** a variable means **creating** it.
* Basic syntax:

  ```java
  data_type variable_name;
  data_type variable_name = value;
  ```
* Always **end with a semicolon (`;`)**.

---

#### The `short` Data Type

* **Size**: 16 bits (2 bytes)
* **Range**: −32,768 to 32,767
* **Signed** (supports positive and negative)
* **Default value**: `0`
* Useful in **low-level programming** like image or sound processing
* Example:

  ```java
  short sn1 = 31000;
  short sn2 = -31000;
  ```

---

#### The `int` Data Type

* **Size**: 32 bits
* **Range**: −2,147,483,648 to 2,147,483,647
* Most **commonly used** integer type in Java
* Good for everyday values like **ages**, **IDs**, **counters**
* Example:

  ```java
  int customer_age = 18;
  ```

---

#### The `long` Data Type

* **Size**: 64 bits
* **Range**: −9,223,372,036,854,775,808 to 9,223,372,036,854,775,807
* Use for **very large numbers** (e.g., world population)
* Must add `L` or `l` when assigning literals
* Examples:

  ```java
  long long_number1 = 4356334286L;
  long long_number2 = 834l;
  ```

---

#### Working Across Data Types

* **Widening (safe)**:

  * `short` → `int` → `long`
* **Narrowing (risky)**:

  * `long` → `int` → `short`
  * Must use **casting** (force the conversion)
* Example:

  ```java
  long value_2 = 5000L;
  int value_1 = (int) value_2; // Manual cast
  ```
* Be careful — **data loss or overflow** can occur when narrowing.

---

#### Summary

* Java provides three **primitive whole-number types**:

  * `short`: smallest, limited range, niche use cases
  * `int`: default for most integer values, widely used
  * `long`: handles very large numbers
* All are **signed integers** and only store **whole numbers**.
* Always use a data type that fits the **expected size of the value**.
* Remember to cast when **converting downward**, and always **add `L`** for long literals.

### Section 4: Floating-Point Numbers in Java

#### What Are Floating-Point Numbers?

* **Floating-point numbers** (or **real numbers**) represent **decimal values** in Java.
* Java has **two floating-point data types**:

  * `float` – single precision (32-bit)
  * `double` – double precision (64-bit)
* Used in scenarios requiring **precision**, such as:

  * **Currency**
  * **Measurements**
  * **Time calculations**

---

#### Float Data Type

* **Precision**: 6–7 digits after the decimal
* **Size**: 4 bytes (32 bits)
* **Default value**: `0.0f`
* Must append with `f` or `F` to declare as float, otherwise treated as double.

**Examples:**

```java
float a = 2.356f;           // Valid
float x = -125.563f;        // Valid
float q = 506.12789f;       // Valid (rounds to ~506.1279)
float r = -101.23;          // Treated as double
float c = 101.123456789123; // Too precise — error
float p = 25f;              // Valid float with no decimal
```

---

#### Double Data Type

* **Precision**: 15–16 digits after the decimal
* **Size**: 8 bytes (64 bits)
* **Default value**: `0.0d` (though `d` is often omitted)

**Examples:**

```java
double a = 2.356;                      // Stored as double
double x = -125.563;                   // Valid
double q = 506.124789;                 // Valid
double r = -101.1234567891234567;      // Valid
double c = 101.123456789123456789;     // Too precise — may truncate
double p = 25;                         // Stored as double
```

---

#### Precision Warning: Float vs. Double

* **Float and double are not ideal for currency** because they can't guarantee exact decimal precision.
* Example:

```java
double k = 3.5 + 4.9;  // Expected: 8.4
System.out.println(k);  // Output: 8.3999999999999999
```

* For precise values (e.g., **dollars and cents**), use **`BigDecimal`** instead.

---

#### Float-to-Double Conversion

* You **can safely convert a float to a double** — no loss of precision.
* Syntax:

```java
float f = 0.25f;
double d = (double) f; // Implicitly safe
```

**Example:**

```java
float a = 32.2578f;
double b = (double) a;
```

---

#### Double-to-Float Conversion

* **Not recommended**, as it may **truncate** precision.
* Must use **explicit casting**:

```java
double x = 123.4567890123456789;
float y = (float) x;  // May lose precision
```

---

#### Dividing by 0.0

* Java allows **division of a double by 0.0**.
* Instead of an error, the result is:

  * `Infinity` (positive)
  * `-Infinity` (negative)
  * `NaN` (if indeterminate)

**Example:**

```java
double d = 5.7 / 0.0;     // Output: Infinity
```

---

#### Summary

* `float` and `double` are **primitive** data types for **decimal values**.

  * `float` → 32-bit, up to **7 digits** of precision
  * `double` → 64-bit, up to **16 digits** of precision
* Append `f` for float literals, `d` is optional for double.
* **Use float when memory is limited**, and precision isn't critical.
* **Use double for most scientific calculations**.
* **Avoid both for currency** — use `BigDecimal`.
* You can **safely convert float to double**, but **not the other way around** without potential data loss.
* **Dividing by 0.0** results in `Infinity`, not an error.

### Section 5: The Java `char` Data Type

#### What Is `char`?

* **`char`** stands for **character** and is a **primitive data type** in Java.
* It stores a **single Unicode character**.
* **Size**: 16 bits (2 bytes) — more than a `byte`, to support global character sets.
* Commonly used for:

  * **Letters**
  * **Digits**
  * **Symbols**
  * **Special characters** (like newline or tab)

---

#### Unicode

* **Unicode** is a **universal character encoding system**.
* Assigns a **unique number** to **every character** in every language.
* Enables consistent character representation **across platforms and languages**.
* Examples:

  * `'A'` = Unicode `65`
  * `'B'` = `66`
  * `'a'` = `97`
  * Special characters: **newline**, **tab**, etc., also have Unicode values.

---

#### Declaring `char` Variables

* You can declare a `char` in **two ways**:

**1. Using single quotes with a character:**

```java
char real_seven = 'M';  // Valid
```

**2. Using a numeric Unicode value (as an integer):**

```java
char seventy_seven = 77;  // 77 = 'M'
System.out.println(seventy_seven); // Output: M
```

* **Incorrect:** Declaring numeric `char` with quotes:

```java
char wrong = '77';  // ERROR — too many characters
```

---

#### `char` and Integers

* Although `char` stores a character, it is also treated as an **integer** — specifically a **Unicode integer**.
* You can **perform arithmetic operations** on a `char`.

**Example:**

```java
char char1 = 'A';        // Unicode 65
System.out.println(char1); // Output: A

char1++;                 // Increment to 66
System.out.println(char1); // Output: B
```

* The `++` operator works because `char` is stored as a **numeric Unicode value** behind the scenes.

---

#### Summary

* The **Java `char` data type** is used to store **a single Unicode character**.
* It uses **16 bits (2 bytes)** and can represent characters from **any human language**.
* `char` values can be **assigned using single characters** (`'A'`) or **Unicode integers** (`65`).
* You can **perform arithmetic operations** on `char` because it's closely related to integers.
* Java treats characters as **numeric Unicode values**, enabling powerful and flexible character manipulation.

### Section 6: Java String Data Type

---

#### 🔤 What Is a String?

* A **String** in Java is a **sequence of characters**, e.g., `"Hello World!"`.
* It is a **class** in the `java.lang` package, not a primitive data type.
* It supports a wide variety of **methods** for manipulation.
* Strings are **immutable**, meaning once created, their value **cannot be changed**.

---

#### 🧱 Declaring Strings

Two common ways to declare strings:

```java
String greeting = new String("Hello World!");  // Using new keyword (object instantiation)
String casual = "Hey World";                   // Using string literal (preferred)
```

---

#### 🔣 Special Characters (Escape Sequences)

Use escape sequences for characters that can't be typed directly:

| Escape Sequence | Meaning      |
| --------------- | ------------ |
| `\n`            | Newline      |
| `\t`            | Tab          |
| `\"`            | Double quote |
| `\\`            | Backslash    |

**Example:**

```java
String message = "She said, \"Hello!\"\nWelcome!";
```

---

#### ➕ Concatenation

Use `+` to join strings:

```java
String part1 = "Hello";
String part2 = "World";
String combined = part1 + " " + part2;  // Output: "Hello World"
```

---

#### 🧰 Common String Methods

| Method          | Description                     | Example Output                              |
| --------------- | ------------------------------- | ------------------------------------------- |
| `length()`      | Returns string length           | `"Hello".length()` → `5`                    |
| `toUpperCase()` | Converts to uppercase           | `"hello".toUpperCase()` → `"HELLO"`         |
| `toLowerCase()` | Converts to lowercase           | `"WORLD".toLowerCase()` → `"world"`         |
| `trim()`        | Removes leading/trailing spaces | `" Java ".trim()` → `"Java"`                |
| `replace(x, y)` | Replaces all `x` with `y`       | `"popcorn".replace("o", "a")` → `"papcarn"` |

---

#### 🧪 Example

```java
public class StringExample {
    public static void main(String[] args) {
        String text = " Hello Java World! ";
        System.out.println("Length: " + text.length());               // 20
        System.out.println("Upper: " + text.toUpperCase());           // " HELLO JAVA WORLD! "
        System.out.println("Lower: " + text.toLowerCase());           // " hello java world! "
        System.out.println("Trimmed: " + text.trim());                // "Hello Java World!"
        System.out.println("Replaced: " + text.replace("Java", "C#"));// " Hello C# World! "
    }
}
```

---

#### 📝 Summary

* **String** is a **non-primitive** data type and a **class** in Java.
* Strings are declared using **quotes** and can be manipulated with **built-in methods**.
* Use **escape characters** for formatting and special symbols.
* Common operations: **concatenation**, **length checking**, **case conversion**, **trimming**, and **replacing**.
* Strings are **powerful tools** in Java and essential for **text handling**.

### Section 7: Java Boolean Data Type

---

#### 🔍 What is a Boolean?

In **Java**, a `boolean` is a **primitive data type** that holds **only two values**:

* `true`
* `false`

It is named after **George Boole**, the mathematician who formalized **Boolean logic**, the foundation of all digital computing.

---

#### 🧬 Boolean Characteristics

| Feature            | Description                                                |
| ------------------ | ---------------------------------------------------------- |
| Size               | 1 bit (though JVM may allocate more)                       |
| Allowed values     | `true` or `false` (no quotes, lowercase only)              |
| Default value      | `false`                                                    |
| Data type category | Primitive (built-in to Java)                               |
| Common usage       | Control flow (`if`, `while`, `for`), flags, toggles, logic |

---

#### ✍️ Syntax

```java
boolean isValid;
boolean flag = true;
boolean stop = false;
```

💡 **Best practice**: Always initialize Boolean variables to avoid unintended defaults.

---

#### ⚙️ Examples in Use

---

🔁 **Example 1: Toggle Stop Flag**

```java
boolean stop = false;
for(int i = 0; i < 10; i++) {
    if(i == 5) {
        stop = true;
    }
}
System.out.println(stop);  // Output: true
```

This loop flips the `stop` flag to `true` when `i` reaches 5.

---

📋 **Example 2: Contract Validity Check**

```java
int contractMonths = 15;
boolean isExpired = true;
boolean signNewContract = false;

if(isExpired == true || contractMonths >= 18) {
    signNewContract = true;
}

System.out.println(signNewContract);  // Output: true
```

This logic checks two conditions using **logical OR (`||`)**:

* If the contract **has expired**, OR
* If it has lasted **18 months or more**,
  Then a **new contract should be signed**.

---

#### 🔗 Boolean with If Statements

```java
boolean loggedIn = true;

if(loggedIn) {
    System.out.println("Access granted.");
} else {
    System.out.println("Access denied.");
}
```

Boolean variables are often used directly in control structures without comparing (`== true`).

---

#### 🔄 Logical Operators

| Operator | Name        | Example      | Description                           |        |   |      |                                  |
| -------- | ----------- | ------------ | ------------------------------------- | ------ | - | ---- | -------------------------------- |
| `&&`     | Logical AND | `if(a && b)` | true only if both conditions are true |        |   |      |                                  |
| \`       |             | \`           | Logical OR                            | \`if(a |   | b)\` | true if either condition is true |
| `!`      | Logical NOT | `if(!a)`     | true if `a` is false                  |        |   |      |                                  |

---

#### 🧠 Lesson Summary

* The `boolean` type stores **only true or false**.
* It is widely used in **decision-making**, **flagging**, and **loop control**.
* Booleans are **defaulted to false** and should be **explicitly initialized**.
* Boolean expressions drive the core of **control flow** in Java (`if`, `while`, `for`, etc.).

> Boolean logic is the **heartbeat** of every conditional operation in programming!

### Section 8: Java Type Conversions: Implicit and Explicit Explained

---

#### 🧱 Primitive Data Types in Java

| **Type**  | **Content**            | **Size** | **Range**                       |
| --------- | ---------------------- | -------- | ------------------------------- |
| `boolean` | `true` or `false`      | 1 bit    | N/A                             |
| `char`    | Unicode character      | 16 bits  | `\u0000` to `\uFFFF`            |
| `byte`    | Signed integer         | 8 bits   | -128 to 127                     |
| `short`   | Signed integer         | 16 bits  | -32,768 to 32,767               |
| `int`     | Signed integer         | 32 bits  | -2,147,483,648 to 2,147,483,647 |
| `long`    | Signed integer         | 64 bits  | ±9×10¹⁸                         |
| `float`   | Single-precision float | 32 bits  | ±1.4E−45 to ±3.4E+38            |
| `double`  | Double-precision float | 64 bits  | ±4.9E−324 to ±1.8E+308          |

Each is optimized to store one of:

* **Numbers** (byte → double)
* **Unicode characters** (char)
* **Boolean logic** (boolean)

---

#### 🔄 Implicit Conversion (Widening)

Java will **automatically convert** a smaller numeric type to a **larger one** **(widening)** without data loss:

```java
byte -> short -> int -> long -> float -> double
```

✅ **Allowed**:

```java
byte myAge = 23;
long someNumber = myAge;
double myAgePlus = someNumber + 0.5;
```

❌ **Not Allowed**:

```java
int anotherNumber = someNumber;      // long to int — error
float anotherAge = myAgePlus;        // double to float — error
```

> 🚫 **Implicit conversion is not allowed** with `char` or `boolean`, even if the target has more bits.

---

#### 🧭 Explicit Conversion (Narrowing or Type Casting)

To convert from a **wider type to a narrower one**, Java requires a **type cast**:

```java
targetType variableName = (targetType) sourceVariable;
```

✅ **Examples**:

```java
long someNumber = 123L;
int anotherNumber = (int) someNumber;  // Cast long to int

char firstLetter = 'A';
short letterValue = (short) firstLetter;  // Unicode 'A' (65) to short
```

🔎 **Note**:

* `char` → numeric: stores Unicode value
* `double` or `float` → int: fractional part is **truncated**

```java
double pi = 3.14159;
int truncatedPi = (int) pi;   // result: 3
```

🚫 **Boolean conversions are never allowed**, not even with casting:

```java
boolean flag = true;
// int x = (int) flag; // ❌ Compile-time error
```

---

#### 📚 Summary

* **Implicit conversions** happen when converting a smaller numeric type to a wider one.
* **Explicit conversions (type casts)** are needed for narrowing — and may cause truncation or data loss.
* **No conversion allowed for `boolean`** — it's logically unique.
* Use **parentheses and target type name** to cast explicitly.

> Conversions change how a value is **stored**, not its **meaning** — just like converting kilometers to miles!

### Section 9: Java Arithmetic Operators

#### 🔢 Arithmetic in Java

Java supports **five key arithmetic operators**:

| **Operator** | **Function**       | **Example**                |
| ------------ | ------------------ | -------------------------- |
| `+`          | Addition           | `input1 + input2 + input3` |
| `-`          | Subtraction        | `sales - taxAmount`        |
| `*`          | Multiplication     | `sales * commissionRate`   |
| `/`          | Division           | `earnings / hours`         |
| `%`          | Modulo (remainder) | `input % 2`                |

---

#### ➕ Addition & ➖ Subtraction

```java
double rate = 10.87;
double taxAmount = 3.25;
double newValue = rate + taxAmount;
System.out.println(newValue);           // Output: 14.12
System.out.println(newValue - taxAmount); // Output: 10.87
```

> 🔍 *Java follows standard order of operations. Results can be negative if subtracting a larger number.*

---

#### ✖️ Multiplication & ➗ Division

```java
double earnings = 36504.87;
double taxRate = 0.05;
double taxBill = earnings * taxRate;   // Annual tax
double netPay = earnings - taxBill;    // Net pay after tax

System.out.println("Tax Bill: " + taxBill);       // Output: ~1825.24
System.out.println("Net Pay: " + netPay);         // Output: ~34679.63
System.out.println("Monthly Amount: " + taxBill / 12);  // Monthly tax
```

> ✅ Use `double` for high-precision operations like tax and financial calculations.

---

#### 🧠 Order of Operations (PEMDAS)

```java
System.out.println((10 - 5) * 3);  // Output: 15
System.out.println(10 - 5 * 3);    // Output: -5
```

> 🧮 Always use **parentheses** to control calculation order. Java respects PEMDAS.

---

#### ➗ Modulo: `%` Operator

**The `%` operator returns the remainder** of integer division:

```java
System.out.println("10 % 5 = " + 10 % 5);     // 0
System.out.println("5 % 10 = " + 5 % 10);     // 5
System.out.println("500 % 36 = " + 500 % 36); // 32
```

> 🎯 Useful in determining:
>
> * **Even/Odd Numbers**:
>
> ```java
> for(int i = 1; i <= 10; i++) {
>     if(i % 2 == 0) {
>         System.out.println(i + " is Even!");
>     }
> }
> ```
>
> * **Circular Queues**, looping, array bounds

---

#### 📚 Summary

* Java provides 5 essential arithmetic operators.
* Use **`double`** or **`float`** for precision-based calculations.
* **Parentheses** affect result based on math order of operations.
* **Modulo `%`** is powerful for remainders, even/odd checks, and circular logic.

### Section 10: Java Relational & Boolean Operators


#### 🔍 **Equality: `==` (Equal To)**

Checks if two values are the same:

```java
int enterMe = 15;
if (enterMe == 15) {
    System.out.println("Value equals 15");
}
```

> ⚠️ **Common Mistake:**
> Using `=` instead of `==` assigns a value rather than compares:

```java
int i = 7;
if (i = 8) {   // ❌ This assigns 8 to i, not compares!
    // error or unexpected behavior
}
```

---

#### ❗ **Inequality: `!=` (Not Equal To)**

Checks if values are *not* the same:

```java
float payRate = 12.5f;
while (payRate != 15) {
    System.out.println("Not 15 yet...");
    payRate += 0.5;
}
```

---

#### 🧭 **Comparative Operators:**

| Operator | Meaning                  | Example              |
| -------- | ------------------------ | -------------------- |
| `<`      | Less than                | `if (age < 18)`      |
| `<=`     | Less than or equal to    | `if (score <= 100)`  |
| `>`      | Greater than             | `if (hours > 40)`    |
| `>=`     | Greater than or equal to | `if (payRate >= 15)` |

---

#### 🧠 **Boolean Logic (AND, OR)**

Boolean expressions always evaluate to `true` or `false`.

---

#### ✅ **AND: `&&`**

Both conditions must be `true`.

```java
float payRate = 16.5f;
if (payRate > 10 && payRate < 20) {
    System.out.println("Pay rate is within range.");
}
```

---

#### 🌀 **OR: `||`**

At least one condition must be `true`.

```java
String empState = "CA";
if (empState == "CA" || empState == "MD") {
    System.out.println("Eligible for sick pay.");
}
```

> ⚠️ **Reminder:** Strings should be compared using `.equals()`:

```java
if (empState.equals("CA") || empState.equals("MD"))
```

---

#### 🔗 **Combining AND and OR**

You can combine logic in nested expressions using parentheses:

```java
if (
   (empState.equals("CA") || empState.equals("MD")) &&
   (payRate > 10 && payRate < 20)
) {
    System.out.println("Sick pay applies.");
}
```

---

#### 🧾 **Lesson Summary**

| Concept              | Use                                          |    |                                    |
| -------------------- | -------------------------------------------- | -- | ---------------------------------- |
| `==`, `!=`           | Compare for equality and inequality          |    |                                    |
| `<`, `>`, `<=`, `>=` | Compare numeric values                       |    |                                    |
| `&&`                 | Combine multiple conditions (all must match) |    |                                    |
| \`                   |                                              | \` | Combine conditions (any can match) |

> 🔐 **Watch for Assignment Errors:**
> Use `==` for comparisons, **not** `=` which assigns a value.

Relational and Boolean operators are **core tools** in Java logic — essential for flow control, decision-making, and program intelligence.

### Section 11: Java APIs

#### What Is an API?

API stands for **Application Programming Interface**. In Java, APIs are collections of prewritten code—classes, interfaces, and methods—that can be imported into a program to extend its capabilities. APIs save developers time and allow programs to use complex functionality without writing it from scratch.

There are three main types of Java APIs:

* **Core API**: Included with the Java Development Kit (JDK)
* **Optional APIs**: Provided by Java, sometimes requiring download
* **Unofficial APIs**: Created by third parties or developers themselves

#### Packages

Java APIs are organized into **packages**, which group related classes and interfaces. A package acts like a folder containing code tools for a specific purpose, such as file handling or user input.

To use a package in your code, use the `import` keyword.

#### Importing Entire Packages

You can import an entire package using the asterisk (`*`) wildcard.

```java
import java.io.*;
```

This gives access to everything in the `java.io` package. It's simple but may include more than you need.

#### Importing a Specific Class

To improve performance or clarity, you may want to import a specific class.

```java
import java.io.DataOutput;
```

This gives access to only the `DataOutput` interface from the `java.io` package.

#### Using the Scanner Class

The `Scanner` class from the `java.util` package is often used to read user input.

```java
import java.util.Scanner;

Scanner input = new Scanner(System.in);
System.out.println("Enter a menu item:");
int inputInt = input.nextInt();
```

This code creates a Scanner object that listens to user input from the keyboard.

> If you forget to import `Scanner`, your program will produce a compile-time error like:
> `Cannot find symbol: class Scanner`

#### Other Common Java APIs

Some other core APIs include:

* `java.util`: Utilities like `Scanner`, `ArrayList`, `HashMap`
* `java.io`: Input and output operations
* `java.math`: High-precision math using `BigDecimal` and `BigInteger`
* `java.awt`: GUI programming components

Each package contains numerous tools to make programming tasks easier.

#### Custom or External APIs

Aside from the standard APIs, developers can use:

* **Downloaded third-party APIs** from developer communities
* **Custom-built APIs** for specific application needs

These are useful for extending Java’s capabilities in advanced or specialized projects.

#### Lesson Summary

* Java APIs are **collections of code tools** provided as packages.
* Use the `import` keyword to access an API's classes and interfaces.
* You can import either a **full package** or just a **single class**.
* The `Scanner` class in `java.util` is commonly used for user input.
* Java comes with **core APIs**, while others can be **optional** or **third-party**.
* APIs simplify development by providing **ready-made, tested functionality**.

### Section 12: Random Number Generation in Java

#### Importing the Random Class

To generate random numbers in Java, you need to **import the `Random` class** from Java's utility library. This class is not automatically available, so we bring it in using the `import` keyword:

```java
import java.util.Random;
```

This line must be placed at the very **top of your program**, before the class declaration.

#### Creating a Random Object

The `Random` class is part of Java’s **object-oriented structure**, so we must create an **instance** of the class before using it. Here's how to do that:

```java
Random randomNum = new Random();
```

This object (`randomNum`) now has access to all methods in the `Random` class.

#### Generating a Random Integer

To generate a number between 0 and a given upper limit, use the `nextInt(n)` method. For example, this generates a number from 0 to 99:

```java
int showMe = randomNum.nextInt(100);
```

To get a number **between 1 and 100**, simply add 1:

```java
int showMe = randomNum.nextInt(100) + 1;
```

#### Full Program Example

Here’s the complete code to generate and print one random number between 1 and 100:

```java
import java.util.Random;

public class Main {
  public static void main(String[] args) {
    // Create instance of Random class
    Random randomNum = new Random();

    // Generate random number between 1 and 100
    int showMe = randomNum.nextInt(100) + 1;

    System.out.println("Random number between 1 and 100: " + showMe);
  }
}
```

#### Pseudorandom Behavior

Java’s `Random` class generates **pseudorandom numbers**, not truly random ones. This means the numbers are **statistically random** but generated by a deterministic algorithm.

* This is **fine for games, simulations, or casual randomness**
* Not suitable for **encryption, cryptography, or secure token generation**

#### Generating Multiple Random Numbers

To test randomness, you can run the generator multiple times using a `for` loop:

```java
for (int i = 1; i < 2500; i++) {
  int showMe = randomNum.nextInt(100) + 1;
  System.out.println(showMe);
}
```

This loop generates and prints **2,499 random numbers** between 1 and 100. If analyzed in Excel or another tool, the distribution should be reasonably uniform.

#### Use Cases for Random Numbers

* **Games**: Dice rolls, enemy actions, loot generation
* **Simulations**: Randomized trials, weather simulations, behavior modeling
* **Testing**: Randomized input for software testing
* **Educational tools**: Practice questions, flashcard apps, etc.

#### Lesson Summary

* The `Random` class in Java is used to generate **pseudorandom numbers**.
* You must **import `java.util.Random`** to use it.
* The method `nextInt(n)` returns a number from **0 to n-1**.
* Adding 1 adjusts the range to **1 through n**.
* Java's random numbers are **good for general programming**, not for cryptography.
* You can loop through random number generation to **test for randomness** or generate multiple values.