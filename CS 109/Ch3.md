### Section 1: The Importance of Operators

#### What Is an Arithmetic Operator?

An **operator** is a symbol that instructs a computer to perform a particular operation. These can be **arithmetic**, **relational**, or **logical**, and are used in programs to manipulate data and evaluate expressions.

Arithmetic operators specifically **perform mathematical operations** on numeric values. They simulate real-world mathematical behavior, enabling computers to calculate totals, differences, products, and more — just like we do in everyday life.

#### Common Arithmetic Operators in Java

Java supports several arithmetic operators that are commonly used in programming:

| Operator | Description         | Example |
| -------- | ------------------- | ------- |
| `+`      | Addition            | `a + b` |
| `-`      | Subtraction         | `a - b` |
| `*`      | Multiplication      | `a * b` |
| `/`      | Division            | `a / b` |
| `%`      | Modulus (remainder) | `a % b` |

These operators follow **infix notation**, where the operator is placed between operands, like `var1 + var2`.

#### Arithmetic Operator Examples

Let’s say:

```java
int var1 = 11;
int var2 = 5;
int result;
```

* **Addition**:

  ```java
  result = var1 + var2; // 11 + 5 = 16
  ```

* **Subtraction**:

  ```java
  result = var1 - var2; // 11 - 5 = 6
  ```

* **Multiplication**:

  ```java
  result = var1 * var2; // 11 * 5 = 55
  ```

* **Division**:

  ```java
  result = var1 / var2; // 11 / 5 = 2 (integer division truncates the decimal)
  ```

* **Modulus**:

  ```java
  result = var1 % var2; // 11 % 5 = 1 (remainder)
  ```

These basic operators provide the foundation for all numeric computation in Java programs.

#### Operator Variations Across Languages

While Java uses standard symbols similar to C, C++, and C#, other languages like **Pascal** or **Visual Basic** may use different notations. For example:

* In **Pascal**: `div` is used instead of `/` for integer division.
* In **Visual Basic**: `Mod` is used for modulus.

Despite syntactic differences, the underlying arithmetic logic remains consistent across most languages.

#### Lesson Summary

* An **arithmetic operator** tells a computer to perform a mathematical calculation.
* Java provides five key arithmetic operators: `+`, `-`, `*`, `/`, and `%`.
* Operator syntax may vary between languages, but concepts remain the same.
* Operators are foundational in coding and allow for everything from basic math to complex calculations.

### Section 2: The Java If Statement

#### Conditional Logic

* Java uses the `if` statement to control the flow of execution.
* An `if` statement evaluates a Boolean condition — if it's `true`, the code inside runs.
* This introduces decision-making in Java, similar to taking a fork in the road.

#### Basic Program Structure

* Java programs must include:

  * A class declaration
  * A `main()` method
  * Comments (optional but helpful)

#### If Statement Syntax

* The general format is:

```java
if (condition) {
  // code that executes if condition is true
}
```

* Example using a number comparison:

```java
int x = 8;
if (x < 10) {
  System.out.println("x is less than 10");
}
```

#### Comparing Strings

* Strings are compared using `.equals()` instead of `==`
* Example:

```java
String s1 = "red";
if (s1.equals("red")) {
  System.out.println("Your guess is my favorite color!");
}
```

#### Full Program Example

```java
public class Main {
  public static void main(String[] args) {
    try {
      String s1 = args[0];
      System.out.println("Your guess was: " + s1);
      if (s1.equals("red")) {
        System.out.println("Your guess is my favorite color!");
        System.out.println("Good job");
      }
    } catch (Exception e) {
      System.out.println("Error - please include an argument");
    }
  }
}
```

#### If/Else Statement

* The `else` clause runs if the `if` condition is false.
* Example:

```java
public class Main {
  public static void main(String[] args) {
    try {
      String s1 = args[0];
      System.out.println("Your guess was: " + s1);
      if (s1.equals("red")) {
        System.out.println("Your guess is my favorite color!");
        System.out.println("Good job");
      } else {
        System.out.println("That's not my favorite color");
        System.out.println("Try again if you like");
      }
    } catch (Exception e) {
      System.out.println("Error - please include an argument");
    }
  }
}
```

#### Summary

* Java `if` statements evaluate Boolean expressions to control program flow.
* Use `.equals()` for String comparison.
* `if/else` statements offer alternate paths.
* Wrap input logic in a `try-catch` to handle missing or bad input.

### Section 3: The Switch Statement

#### Tracks

* The Java `switch` statement operates like a railroad switch: based on the value of an expression, it redirects the program to a matching `case`.
* It evaluates expressions of specific data types: `int`, `short`, `byte`, `char`, or `String`.
* Data types like `double` or `float` are not allowed due to imprecision.
* Each redirection path is a `case` label that must contain a constant value of the same type as the expression.
* A `default` clause is used to handle unmatched values and prevent the program from executing unintended behavior.

#### Syntax and Examples

##### Syntax

```java
switch(expression) {
  case constant1:
    // statements
    break;
  case constant2:
    // statements
    break;
  ...
  default:
    // default statements
}
```

* The `break` keyword ends each case block to avoid falling through to the next case.
* `switch` is more efficient than multiple `if-else` statements when checking against the same expression.

##### Example: Menu Option

```java
public class Main {
  public static void main(String[] args) {
    Scanner scanner = new Scanner(System.in);
    System.out.println("Enter a Number: ");
    int myAnswer = Integer.parseInt(scanner.next());
    switch(myAnswer) {
      case 1:
        System.out.println("You entered 1!");
        break;
      case 2:
        System.out.println("You entered 2!");
        break;
      case 3:
        System.out.println("Are we there yet?");
        break;
      default:
        System.out.println("I try to think but nothing happens");
    }
  }
}
```

##### Example: Computer Decision

```java
String gameMove;
switch((int)(3 * Math.random())) {
  case 0:
    gameMove = "Monster";
    break;
  case 1:
    gameMove = "Heroine";
    break;
  default:
    gameMove = "Prince in Distress";
    break;
}
System.out.println("The path is " + gameMove);
```

* In this game scenario, a path is chosen randomly.
* The `default` label is intentionally used as a valid case instead of a fallback.

#### Lesson Summary

* The Java `switch` statement evaluates a single expression and routes control to the matching `case`.
* It accepts limited data types: `int`, `short`, `byte`, `char`, and `String`.
* `break` prevents unintentional fall-through.
* A `default` label ensures all possible values are handled.
* Switch is cleaner and more efficient than multiple `if-else` statements when checking a single variable against known values.

### Section 4: While Loop

The `while` loop in Java is used to execute a block of code **repeatedly** as long as a specified condition remains true. It is particularly useful when the number of iterations is not known in advance. Think of it like a roller coaster that keeps looping until the operator flips the switch — or in programming terms, until the Boolean condition becomes false.

---

#### Syntax

```java
while (condition) {
    // code to execute
}
```

* The loop starts by checking the `condition`.
* If `true`, it enters the loop body and executes the code.
* After one full execution, it checks the condition again.
* If `false`, the loop stops and the program continues.

---

#### Compound Conditions

You can use logical operators for more complex conditions:

```java
while (j > 2 && i < 0) {
    // both conditions must be true
}
```

* `&&` means both conditions must be true.
* `||` means at least one condition must be true.

---

#### Example: Even Numbers

This example prints all even numbers from 1 to 999.

```java
public class Main {
    public static void main(String[] args) {
        int myNumber = 1;
        while (myNumber != 1000) {
            if ((myNumber % 2) != 0) {
                myNumber++;
            } else {
                System.out.println(myNumber + " is even");
                myNumber++;
            }
        }
    }
}
```

Alternatively, you can write the condition as:

```java
while (myNumber < 1000) {
    // ...
}
```

---

#### Indefinite While Loop

A while loop is ideal when you **don’t know how many times** it should run. This is known as an *indefinite loop*.

Example: A loop to simulate panic increasing by 2% each minute until it reaches 100%.

```java
public class Main {
    public static void main(String[] args) {
        final double panic_rate = 0.02;
        int minute = 0;
        double total_panic = 0;

        while (total_panic <= 1) {
            total_panic = panic_rate * minute;
            minute++;
        }

        System.out.println("Panic hits 100% after " + minute + " minutes.");
    }
}
```

If you moved `minute++` *before* the panic calculation, the result would be off by one (51 instead of 52).

---

#### Infinite Loop

Be cautious: if your loop’s condition never becomes false, it can run forever. This is called an **infinite loop**.

Example of a broken loop:

```java
int i = 0;
while (i < 1000) {
    i * 1;  // no change to i
    System.out.println(i);
}
```

Since `i` is never updated, the condition `i < 1000` remains true forever.

---

#### Summary

* The `while` loop runs while a condition is true.
* It’s useful for *indefinite repetition*.
* Be careful to update your loop control variables.
* Avoid infinite loops by ensuring conditions will eventually become false.

### Section 5: The Counting Loop

**Loops in Java** are like a roller-coaster loop or a spin cycle on a washing machine: they continue until a specific condition is met. In a `for` loop, that condition is usually a numeric value. For loops are useful when you know when the condition will be met, e.g., a counter reaches a value of 10.

A `for` loop is called the **counting loop** because each step through the loop increases or decreases a counter each time it steps through the code.

Let’s say we have 10 waffles and we need to put a strawberry atop each one. There’s no need to start flinging strawberries until we run out; we only need 10. A `for` loop will work for this operation.

**Syntax**

```java
for (initial start point; stop condition; amount to increment) {
    instructions/code here;
}
```

The counter in Java is usually denoted by an integer value and is usually `i`. The stop condition can be any value, and the counter is incremented by 1, written as `i++`.

```java
for (int i = 0; i < 10; i++) {
    some_value = old_value + 5;
}
```

To decrement instead, you can write `i--`.
For example:

```java
for (int i = 100; i > -100; i--) {
    // code
}
```

**Example: Decorating Waffles**

```java
public class Main {
    public static void main(String[] args) {
        int i; // our waffle counter
        int waffles = 10;
        for(i = 1; i <= waffles; i++) {
            System.out.println("Waffle " + i + " has been decorated!");
        }
    }
}
```

The previous code initializes the counter and the number of waffles. In the conditions of the `for` loop, we start at 1, proceed until `i <= waffles`, and increment by 1 using `i++`. The body displays a message for each decorated waffle.

**For Loops Example: Perfect Numbers**

A perfect number is a number that is the sum of its divisors. An example is `6: (1 + 2 + 3 = 6)`. We can use a Java `for` loop to find all the perfect numbers between 1 and 10,000. This involves **nested loops**.

```java
public class Main {
    public static void main(String[] args) {
        int i; // initial index
        int j; // second index
        int tester; // test value

        for(i = 1; i < 10000; i++) {
            tester = 0;
            for(j = 1; j < i; j++) {
                if(i % j == 0) {
                    tester += j;
                }
            }
            if(tester == i) {
                System.out.println(tester + " is a perfect number!");
            }
        }
    }
}
```

**Step-by-Step Example with 6**

| i | j | tester logic      | tester |
| - | - | ----------------- | ------ |
| 6 | 1 | 6 % 1 == 0 → +1   | 1      |
|   | 2 | 6 % 2 == 0 → +2   | 3      |
|   | 3 | 6 % 3 == 0 → +3   | 6      |
|   | 4 | 6 % 4 != 0        | 6      |
|   | 5 | 6 % 5 != 0        | 6      |
|   | 6 | ends, 6 == tester | ✓      |

**The For Each Loop**

Another variation of the `for` loop is the **for-each** loop. It’s a shortened version mainly used to loop over collections like arrays or ArrayLists.

```java
public class Main {
    public static void main(String[] args) {
        int[] scores = {10, 20, 40, 9000};
        for (int num : scores) {
            System.out.println(num);
        }
    }
}
```

Note:

* This loop **doesn’t maintain the index**.
* You **can’t decrement** or iterate backward.

**Lesson Summary**

This lesson provided an overview of the syntax of a Java `for` loop, the counting loop. A `for` loop runs for a set number of iterations: a counter is used to track the times through the loop.

You can also **nest** `for` loops when needed, or use the **for-each** variation when working with collections.

### Section 6: Nested for Loops in Java

**Nested Loops**

A nested loop is really a loop-within-a-loop. This can be done at two levels, or three, or even more. But as we'll see in this lesson, increased nesting can cause issues and be very hard to maintain. Below is an example of how these nested loops appear:

```java
for (int i = 1; i <= 5; i++) {
    for (int j = 1; j <= i; j++) {
        // do something
    }
}
```

Think of a nested loop as a race track within a race track. When you begin each lap on the main oval, you veer into another track inside the original (the nested track or loop). You may go around any number of times within the smaller track before looping around the main one. Then it starts over again until you've done the required number of laps on the main track.

In Java, nested `for` loops are usually declared with counter variables: typically `i`, `j`, `k`, etc. The outer loop might use `i`, and the inner `j`, keeping track of how many times each loop runs.

Here's how the nested loop works with i and j:

| Run | Value of i | Loops through j |
| --- | ---------- | --------------- |
| 1   | 1          | 1               |
| 2   | 2          | 2               |
| 3   | 3          | 3               |
| 4   | 4          | 4               |
| 5   | 5          | 5               |

A total of 15 inner loop iterations.

**Example: Simple Nested Loops**

```java
public class Main {
    public static void main (String[] args) {
        for (int i = 1; i < 5; i++) {
            System.out.println("Outside loop: i = " + i);
            for (int j = 1; j <= i; j++) {
                System.out.println("  Nested Loop: j = " + j);
            }
        }
    }
}
```

This shows values of both counters. As `i` increases, the nested loop (`j`) executes more times per outer loop.

**Example: Cookie Sheets and Cookies**

We have 10 cookie sheets, each with 10 cookies. We’ll place chips on each cookie using nested loops.

```java
public class Main {
    public static void main (String[] args) {
        int cookieSheets = 10;
        for (int i = 1; i <= cookieSheets; i++) {
            System.out.println("Chips placed on sheet: " + i);
            for(int j = 1; j <= 10; j++) {
                System.out.println("  And on Cookie: " + j);
            }
        }
    }
}
```

Only the first two sheets are shown in sample output, but this continues through all 10.

**Example: Multiplication Table (24 x 24)**

Instead of i and j, we use `row` and `column` for clarity.

```java
public class Main {
    public static void main (String[] args) {
        for (int row = 1; row <= 24; row++) {
            for (int column = 1; column <= 24; column++) {
                System.out.printf("%4d", column * row);
            }
            System.out.println();
        }
    }
}
```

This outputs a multiplication table — 24 rows by 24 columns.

**Common Mistake: Counter Confusion**

It’s easy to mix up counters. For example:

```java
public class Main {
    public static void main (String[] args) {
        for (int i = 1; i < 20; i++) {
            for (int j = 1; i < 10; j++) { // ❌ mistake: uses i instead of j
                System.out.println(j);
            }
        }
    }
}
```

The mistake: the inner loop should use `j < 10`, not `i < 10`. This bug causes an **infinite loop** because `i` doesn't change in the inner loop, and the condition stays true.

Always double-check that you're using the correct loop variable in your condition.

**Lesson Summary**

A nested `for` loop is a loop inside another loop — a race track within a race track. They are typically written with counter variables like `i`, `j`, and `k`, each representing a different loop level. Nested loops are useful for traversing tables or multi-level structures like grids, but nesting beyond three levels becomes hard to maintain.

Be cautious of bugs from misused counters. A misplaced variable or condition can result in infinite loops. Always test your nested loops carefully.

### Section 7:Break, Keep Going, or Give up

#### Break

```java
public class Main {
    public static void main(String[] args) {
        int option = 1;
        switch (option) {
            case 1:
                System.out.println("Option 1");
                break;
            default:
                System.out.println("Outta here!");
                break;
        }
    }
}
```

```java
public class Main {
    public static void main(String[] args) {
        for(int i = 0; i < 15; i++) {
            if(i == 5) {
                System.out.println("Out!");
                break;
            }
        }
    }
}
```

#### Continue

```java
public class Main {
    public static void main(String[] args) {
        for(int i = 0; i < 10; i++) {
            if(i == 5) {
                System.out.println("Out!");
                break;
            } else {
                System.out.println("Still Here!");
                continue;
            }
        }
    }
}
```

#### Return

public class Main {
    public static void main(String[] args) {
        System.out.println(getRate());
    }

    public static double getRate() {
        double rate = 104.83;
        return rate;
    }
}


### Section 8: Do-While

#### Syntax

```java
do {
    // commands
} while (condition);
```

The condition is tested at the end, and a semicolon is required after the closing `while`.

#### Sprinkler Example

```java
public class Main {
    public static void main(String[] args) {
        int sprinkler = 0;
        boolean sunVisible = true;
        boolean sundown = false;
        do {
            sprinkler++;
            if (sunVisible == false) {
                sundown = true;
            }
        } while (sundown == false);
        System.out.println("Sprinkler count: " + sprinkler);
    }
}
```

#### Menu Example

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner keyboard = new Scanner(System.in);
        int userOption;
        do {
            System.out.println("***** MAIN MENU *****");
            System.out.println("1. Option 1");
            System.out.println("2. Option 2");
            System.out.println("3. Exit!");
            System.out.println("\n\nSelect an Option: ");
            userOption = keyboard.nextInt();
            switch(userOption) {
                case 1:
                    System.out.println("Option1!");
                    break;
                case 2:
                    System.out.println("Option 2!");
                    break;
                case 3:
                    System.out.println("Exiting...");
                    break;
                default:
                    System.out.println("Invalid option! Please select again.");
            }
        } while(userOption != 3);
        keyboard.close();
    }
}
```

#### File Finder Example

```java
import java.io.File;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner getFile = new Scanner(System.in);
        String enterFile;
        do {
            System.out.print("Type the name of the file: ");
            enterFile = getFile.nextLine();
        } while (!new File(enterFile).exists());
        getFile.close();
    }
}
```

#### Infinite Loop Warning

If the condition is never met, the loop becomes infinite and may crash the program or system. Always ensure there's a valid exit condition.

#### Summary

* A `do-while` loop runs at least once.
* The condition is tested **after** the code executes.
* Be cautious of infinite loops.
* Common uses include menus and validation loops (e.g., file existence checks).

### Section 9: Infinite While Loops in Java

#### Introduction

An **infinite while loop** in Java is a loop that never terminates unless external action is taken, such as stopping the program manually or shutting down the system. This typically occurs when the loop’s **condition always evaluates to `true`**, and there's **no update or exit mechanism** to change it.

#### Causes of Infinite Loops

* **Unchanged condition variables**
  If variables inside the loop are never updated, the loop condition remains true forever.

* **Incorrect logic in the condition**
  Using a logical condition that always returns `true` due to programmer error.

* **Overwriting counter variables improperly**
  Resetting counters inside the loop in a way that prevents natural progression.

#### Example 1: Basic Infinite Loop

```java
boolean valid = true;
while(valid) {
    System.out.println("Hi");
}
```

This loop runs infinitely because `valid` is never changed to `false`.

#### Example 2: Counter Reset Inside Loop

```java
int counter = 0;
while(counter < 10) {
    counter = 1; // Resets back to 1 every time
    System.out.println("Counter: " + counter);
}
```

This results in an infinite loop because `counter` will always stay at `1`.

#### Example 3: Missing Update

```java
int updater = 1;
while(updater <= 10) {
    System.out.println(updater); // updater is never incremented
}
System.out.println("Quit: updater = " + updater); // This line never executes
```

Despite appearing valid, this code never exits because `updater` is not modified.

#### When Infinite Loops Can Be Useful

Infinite loops can be intentionally used in:

* **Menu systems**
* **Input loops**
* **Background monitors or daemons**

These loops should always include a **controlled exit**, such as a `break` statement or a user input condition.

#### Example: Controlled Infinite Loop for Menu

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        while(true) {
            System.out.println("Enter a menu option (3 to quit): ");
            Scanner scanMenuOption = new Scanner(System.in);
            int menuOption = scanMenuOption.nextInt();

            if(menuOption == 3) {
                System.out.println("Exiting menu...");
                break;
            } else {
                System.out.println("Processing option: " + menuOption);
            }
        }
    }
}
```

This loop runs indefinitely but includes a clear escape path when the user enters `3`.

#### Summary

* An **infinite while loop** keeps running until forcibly terminated.
* Common causes include **static conditions** and **frozen counters**.
* **Proper design** can turn infinite loops into powerful control structures, especially in **menus** and **persistent monitors**.
* Always include a **safe exit condition** to prevent runaway behavior and system crashes.

### Section 10: Lesson Overview & Knowledge Required

#### Control Flow in Java

* Java executes code from top to bottom by default.
* Control flow can be modified using:

  * **Looping statements**: `for`, `while`, `do-while`
  * **Decision-making statements**: `if-then`, `if-then-else`, `switch`
  * **Branching statements**: `break`, `continue`, `return`

#### Programmer’s Role

* A good programmer evaluates:

  * **Advantages/disadvantages** of each control flow tool
  * **Contextual suitability** for readability and efficiency

#### Prior Knowledge Required

* Use of `if`, `if-else`, and nested decision logic in Java
* Understanding of `break`, `continue`, and `return`
* Familiarity with `try-catch` exception handling

---

#### Program Code and Data Types

* The `switch` statement works with:

  * Primitive types: `byte`, `short`, `char`, `int`
  * `String` objects
  * Enumerated types
* Each `case` must use a **unique label**
* Multiple `case` labels can lead to:

  * **Shared execution block** if `break` is not used
* **Important**: The `switch` evaluates once, then jumps to the matching `case`

---

#### Choosing Between `switch` and `if-else`

* Use `switch` for:

  * Many specific discrete values
  * Improved **readability** and **debugging**
* Use `if-else` for:

  * **Range-based** conditions (e.g., `x > 10 && x < 50`)
  * Conditions involving booleans or unsupported types

---

#### Syntax of a Switch Statement

```java
switch(expression) {
  case value1:
    // statements
    break;
  case value2:
    // statements
    break;
  ...
  default:
    // fallback statements
    break;
}
```

* **`break`** exits the switch block (recommended in each case)
* **`default`** is optional but good practice
* Avoid reusing labels or overlapping case expressions

---

#### Example

```java
public class Main {
  public static void main(String[] args) {
    int option = 2;
    switch(option) {
      case 1:
        System.out.println("You chose 1");
        break;
      case 2:
        System.out.println("You chose 2");
        break;
      default:
        System.out.println("Invalid option");
        break;
    }
  }
}
```

* This evaluates `option`
* Executes the corresponding case block
* Stops processing further cases after `break`

### Section 11: Lesson Overview & Knowledge Required

#### Objective

* Create a program that determines all **even divisors** of a given number using Java.
* You will be using:

  * Variable declarations
  * `for` and `while` loops
  * The **modulo operator** (`%`)

#### Assumed Knowledge

* How to create a Java source file (e.g., in NetBeans)
* Basic Java syntax and logic
* Looping structures in Java
* Understanding of constants and the use of the `final` keyword

---


#### Description

This program will:

* Loop through all numbers from 1 to 100
* Check which numbers divide **evenly** into 100
* Use the modulo operator to determine even divisibility

---

#### Java Class Structure

```java
// This program finds all even divisors of 100; it loops through all numbers from 1 to 100
// and tests them to be sure they divide evenly. Change the value of the variable LIMIT if
// using other numbers.

public class Main {
  public static void main(String[] args) {
    // As declared, this is a constant and will not change.
    // Note: public final variables are indicated in all uppercase
    final int LIMIT = 100;
    int var;

    System.out.print(LIMIT + " is evenly divisible by: \n");

    for(var = 1; var <= LIMIT; var++) {
      if(LIMIT % var == 0) {
        System.out.println(var + " ");
      }
    }
  }
}
```

---

#### Output
100 is evenly divisible by: 
1 
2 
4 
5 
10 
20 
25 
50 
100 