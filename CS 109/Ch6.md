### Section 1: Java Methods

#### What Is a Method in Java?

* A **method** is a **block of code** that performs a task when called.
* Like a **recipe**, it consists of **instructions** that are followed to produce a result.

```java
public int addNumbers(int x, int y) {
  int z = 0;
  z = x + y;
  System.out.println(z);
  return z;
}
```

* `addNumbers` is the method name. When called, it executes and **returns** the value of `z`.

---

#### Parameters of a Method

* **Parameters** are values passed into the method, similar to ingredients in a recipe.
* They're defined within the parentheses after the method name.

```java
public int subtractNumbers(int m, int n) {
  int p = 0;
  p = m - n;
  System.out.println(p);
  return p;
}
```

* `m` and `n` are parameters. They are **used inside** the method to compute and return the result.

---

#### Returning a Value

* A method can **return a value** to the calling code using the `return` keyword.

```java
return p;
```

* The return type is declared **before** the method name:

```java
public int subtractNumbers(int m, int n)
```

* Java methods can return **only one value** at a time.

> To return **multiple values**, use an **array**, object, or collection.

🚫 Invalid example (will cause an error):

```java
public int int subtractNumbers(int m, int n) {
  int p = m - n;
  int q = m + n;
  return p;
  return q;  // Error: only one return allowed
}
```

---

#### Methods That Do Not Return a Value

* Use the keyword **`void`** when no value is returned:

```java
public void subtractNumbers(int m, int n) {
  int p;
  p = m - n;
  System.out.println(p);
}
```

* This method **prints** the result but **does not return** anything.

---

#### Methods Without Parameters

* Not all methods need parameters.

```java
public String printName() {
  final String FIRST_NAME = "Jake";
  System.out.println(FIRST_NAME);
  return FIRST_NAME;
}
```

* The method `printName` declares and returns a variable **without input parameters**.

---

#### The `main` Method

* Java programs always start from the **`main` method**.

```java
public static void main(String[] args) {
}
```

* Key parts:

  * `public` – accessible to JVM
  * `static` – runs without needing an object
  * `void` – no return value
  * `String[] args` – parameter for runtime arguments

---

#### General Syntax of a Method

```java
[Visibility] [static] Return-Type Method-Name (Parameter-List) {
  // Statements
}
```

| Part             | Description                                              |
| ---------------- | -------------------------------------------------------- |
| `public`         | Access modifier (also `private`, `protected`)            |
| `static`         | Optional; used to call method without creating an object |
| `Return-Type`    | Type of value returned (`int`, `String`, `void`, etc.)   |
| `Method-Name`    | Name used to call the method                             |
| `Parameter-List` | Variables passed into the method                         |

---

#### Example: Full Method in Use

```java
public class Main {
  // Method to add two numbers
  public int addNumbers(int x, int y) {
    int z = x + y;
    System.out.println(z);
    return z;
  }

  public static void main(String[] args) {
    Main main = new Main();              // Create an object
    int result = main.addNumbers(5, 3);  // Call the method
    // Output is printed inside addNumbers
  }
}
```

---

#### Lesson Summary

* A **method** is a reusable block of code that performs a specific task.
* It can:

  * Take **parameters**
  * **Return a value** (or not)
* Key terms:

  * `public`, `static`, `void`, `return`
* The **`main` method** is the **entry point** for every Java program.
* Well-written methods increase **modularity**, **reusability**, and **readability**.

### Section 2: Main Method Structure

---

#### 🔑 What Is the `main` Method?

* The `main` method is the **entry point** for any Java program.
* It has a specific declaration:

```java
public static void main(String[] args) {
  // Your code goes here
}
```

---

#### 📘 Breakdown of the Main Method Declaration

| Keyword         | Meaning                                                   |
| --------------- | --------------------------------------------------------- |
| `public`        | The method is accessible from anywhere (e.g., the JVM)    |
| `static`        | JVM can call this method **without creating an instance** |
| `void`          | The method does **not return** any value                  |
| `main`          | This is the **method name** JVM expects to find and call  |
| `String[] args` | **Command-line arguments** passed in as a String array    |

---

#### 💡 Using `args[]` in the Main Method

* `args.length` – returns the number of arguments
* `args[0]`, `args[1]`, `args[2]`, etc. – individual arguments passed
* If no arguments are provided, `args.length == 0`

---

#### 💬 Command-Line Input Example

Command used to run a Java program:

```bash
java SortWordFile words.txt sortedwords.txt descending
```

What each part means:

| Argument          | Description                       |
| ----------------- | --------------------------------- |
| `SortWordFile`    | Java class to run                 |
| `words.txt`       | `args[0]` = input file name       |
| `sortedwords.txt` | `args[1]` = output file name      |
| `descending`      | `args[2]` = sort order (optional) |

---

#### ✅ Sample Code: Main Method with Argument Handling

```java
public static void main(String[] args) {
  String inFile;
  String outFile;
  String sortOption = "Ascending"; // Default

  if ((args.length >= 2) && (args.length <= 3)) {
    inFile = args[0];
    outFile = args[1];

    if (args.length == 3) {
      sortOption = args[2];
    }

    if (sortOption.equalsIgnoreCase("Ascending")) {
      SortAscending(inFile, outFile);
      return; // success
    } else if (sortOption.equalsIgnoreCase("Descending")) {
      SortDescending(inFile, outFile);
      return; // success
    }
  }

  // Command line syntax error!
  System.out.println("Usage: java SortWordFile <inputFile> <outputFile> [ascending|descending]");
}
```

---

#### ⚠️ Important Notes

* Use `.equalsIgnoreCase()` for string comparisons—not `==`
* Always validate command-line input for **length** and **content**
* Return control to the JVM gracefully using `return;` at the end

---

#### 🧠 Lesson Summary

* The **main method** is the first method executed in any Java application.
* It must follow the exact syntax `public static void main(String[] args)`
* `args[]` stores **command-line arguments** passed to the program
* This allows flexibility in configuring how the program behaves at runtime
* Once all logic is done, the program exits by reaching the end of `main`

### Section 3: Protecting Objects and Classes

---

#### 🔐 Purpose of Access Control in Java

Java offers powerful access control mechanisms to:

* **Protect sensitive data**
* **Enforce encapsulation**
* **Enable modular and secure code reuse**

Java uses the keywords: `public`, `protected`, and `private` to manage this.

---

#### 🔓 `public` – Least Restrictive Access

* Accessible from **anywhere**
* Used for general/shared information

```java
public class Employee_Public_View {
    public String employeeName = new String();
    public int jobCode;
}
```

Use Case: Basic employee details that don’t require confidentiality.

---

#### 🛡️ `protected` – Restricted to Package and Subclasses

* Accessible from:

  * Same package (e.g., `Employee`)
  * Subclasses even in other packages (with limitations)
* NOT accessible from **non-subclass code outside the package**

```java
package Employee;

public class Employee_Union {
    public int ID; // visible everywhere
    protected int unionCode; // limited visibility
    protected void getUnion() {
        // internal method
    }
}

class Employee_Bargain_Unit extends Employee_Union {
    void getBargainUnit() {
        Employee_Union union = new Employee_Union();
        // Can use protected members here
    }
}
```

Attempting to use these protected elements outside the `Employee` package:

```java
import Employee.*;

package newUnion;

class New_Union extends Employee_Union {
    // ❌ Cannot access protected variables from another package directly
}
```

---

#### 🔒 `private` – Most Restrictive Access

* Accessible **only within the same class**
* Perfect for **sensitive data**, like pay or health info

```java
private class Employee_Pay {
    private double payRate;
    private double fte;

    double getPayRate(double payRate) {
        return payRate; // No access from outside
    }
}
```

✅ Best practice: Start with `private` and loosen access only when needed.

---

#### 📊 Access Level Comparison Table

| Keyword     | Global Access | Same Package | Subclass Access | Same Class |
| ----------- | ------------- | ------------ | --------------- | ---------- |
| `public`    | ✅             | ✅            | ✅               | ✅          |
| `protected` | ❌             | ✅            | ✅               | ✅          |
| `private`   | ❌             | ❌            | ❌               | ✅          |

---

#### 🧠 Lesson Summary

* Java provides tools to **protect and manage access** to data in classes.
* Use:

  * `public` for open access
  * `protected` for internal reuse (package/subclass)
  * `private` for maximum security
* 🔐 Start restrictive (`private`) and gradually open up (`protected`, `public`) as needed.
* This helps ensure modular, secure, and clean code design.

Perfect — now I have exactly what you want.

I will reformat your **"Final in Java"** lesson using the **exact same structure** you just provided:

---

### Section 4: The `final` Keyword in Java

#### What Is `final` in Java?

* The `final` keyword is used to **protect classes, methods, and variables**.
* It prevents **modification**, **overriding**, or **inheritance**, depending on how it's applied.
* This improves **security**, **readability**, and **error prevention** in Java programs.

---

#### Final Classes

* A class declared `final` **cannot be subclassed**.
* This protects it from being inherited and potentially misused.

```java
final class Employee {
  // class code here
}
```

* Attempting to extend this class will cause a **compile-time error**:

```java
final class Employee {
  private float payRate = 10;
}

private class UnionEmployee extends Employee {
  // ❌ Compiler Error: Cannot inherit from final 'Employee'
}
```

* The `String` class in Java is final — to protect it from being altered.

---

#### Final Methods

* A method marked `final` **cannot be overridden** in subclasses.
* Useful when you want to allow subclassing, but **restrict behavior modification**.

```java
public class Employee {
  final void getPayRate(Employee employee, float payRate, int hours) {
    // method code here
  }
}
```

* Subclasses of `Employee` can inherit the method but **cannot override it**.

---

#### Final Variables

* A `final` variable means its **value cannot change once assigned**.
* This helps maintain **immutable values** and avoids accidental reassignment.

```java
final String tester = "Hi Joe";
tester = new String("Uh-oh");  // ❌ Error: cannot assign a value to final variable
```

* However, if a `final` variable is declared but **not initialized**, it can be set once:

```java
public boolean ExpiredCredential(int counter) {
  final boolean isExpired;
  if (counter < 0 || counter > MAX_VAL) {
    isExpired = false;
  } else {
    isExpired = true;
  }
  return isExpired;
}
```

* Once assigned, even this late-bound `final` variable **cannot be reassigned**.

---

#### Why Use `final`?

* **Security** – Protect critical classes from being extended (e.g., `String`).
* **Stability** – Prevent unwanted overrides in core methods.
* **Readability** – Makes intent explicit to other developers.
* **Encapsulation** – Ensures local method variables stay protected and unchangeable.

---

#### Lesson Summary

* The `final` keyword can apply to **classes**, **methods**, and **variables**:

  * **Final Class** – Cannot be inherited
  * **Final Method** – Cannot be overridden
  * **Final Variable** – Value cannot be changed once set
* Helps prevent **logic errors**, **security flaws**, and increases **code clarity**.
* Start restrictive (`final`) and **relax only if needed**.

### Section 5: Static Methods in Java

#### What Is a Static Method?

* A **static method** belongs to the **class**, not an object (instance) of the class.
* You can call static methods **without creating an instance**.
* The `main` method is a classic example of a static method.

```java
public class Example {
  public static void printMessage() {
    System.out.println("Message from static method");
  }
}
```

* The keyword `static` is placed before the return type in the method declaration.
* This method can be called using `Example.printMessage();`

---

#### Calling a Static Method

* You should call static methods using the **class name**, not an instance.

```java
Example.printMessage();  // ✅ Preferred
```

* However, Java allows calling them via an instance (though not recommended):

```java
Example ex = new Example();
ex.printMessage();  // ✅ Works, but not preferred
```

* If `printMessage` is **not declared static**, calling it through the class will cause a **compile error**:

> ❌ "Cannot make a static reference to the non-static method printMessage() from the type Example"

---

#### Static Method Return Types

* Just like instance methods, static methods can:

  * Return values like `int`, `String`, `double`, etc.
  * Use `void` if no return is required.

```java
public static void printMsg() {
  System.out.println("This message just prints to the console");
}
```

---

#### Capabilities of Static Methods

* Static methods **can**:

  * Have **zero or more parameters**
  * Call **other static methods**
  * Use and modify **static variables**
  * Be **overloaded** (different parameters)
  * Exist alongside instance methods with the same name

* Static methods **cannot**:

  * Directly access **instance variables or methods**
  * Use the `this` keyword
  * Be **overridden** (they are hidden, not overridden)

> Static methods are **resolved at compile time**, while instance methods are resolved at runtime.

---

#### Why Use Static Methods?

* Use static methods when the logic:

  * **Does not depend on an instance**
  * Is **utility-based**, like helper or math functions

* Examples include:

  * `Math.pow()`, `System.out.println()`
  * Test methods
  * Library functions

---

#### Lesson Summary

* A **static method**:

  * Is declared with the `static` keyword
  * Belongs to the **class**, not the object
  * Can be called using the **class name**
  * Cannot access instance members directly
  * Cannot use `this` keyword
  * Is best used for functionality **independent of object state**

* Use static methods when you don’t need object-specific behavior.

### Section 6: Static vs Non-Static Methods

#### What Are Java Methods?

* A **method** is a collection of statements grouped to perform a task.
* You call a method by its **name** to execute the group of statements.

---

#### Static vs Non-Static Analogy

* Think of a **static method** as the **original dress** (the blueprint).
* Think of a **non-static method** as a **pattern** made from the original dress.

---

#### What Is a Static Method?

* Declared using the `static` keyword.
* Belongs to the **class**, not the instance.
* Can be accessed **without creating an object**.

```java
class Calc {
  static int product(int x, int y) {
    return x * y;
  }

  public static void main(String[] args) {
    int ans = Calc.product(5, 3);
    System.out.println(ans);
  }
}
```

* Called using `ClassName.methodName()`.

---

#### What Is a Non-Static Method?

* **No** `static` keyword.
* Belongs to an **object** of the class.
* Must create an **instance** to call it.

```java
class Calc {
  int product(int x, int y) {
    return x * y;
  }

  public static void main(String[] args) {
    Calc calc = new Calc();
    int ans = calc.product(5, 3);
    System.out.println(ans);
  }
}
```

---

#### Characteristics of Static Methods

* Can call **only other static methods**
* Can access **only static variables**
* Can be called **directly using class name**
* Cannot use `this` keyword
* Cannot override (but can be hidden)

---

#### Characteristics of Non-Static Methods

* Can access **both static and non-static** members
* Can use `this` to refer to the current object
* Must be called via an **instance** of the class

---

#### Calling Static & Non-Static Methods

```java
class Main {
  public static void main(String[] args) {
    int result = Calc.cube(5); // Static method call
    System.out.println(result);

    Calc calc = new Calc();    // Instance created
    int result2 = calc.cube2(3); // Non-static method call
    System.out.println(result2);
  }
}

class Calc {
  static int cube(int x) {
    return x * x * x;
  }

  int cube2(int y) {
    return cube(3); // Calls static method
  }
}
```

---

#### Accessing Static Variables

```java
class Calc {
  static int a = 2;

  public static void main(String[] args) {
    System.out.println(Calc.a); // Static variable from static method
  }
}
```

---

#### Accessing Non-Static Variables from Static Methods

```java
class Calc {
  int a = 0;

  public static void main(String[] args) {
    Calc calc = new Calc(); // Must create instance
    System.out.println(calc.a); // Access non-static variable
  }
}
```

---

#### Accessing Static Members from Non-Static Methods

```java
class Calc {
  static int a = 2;

  static int cube(int x) {
    return x * x * x;
  }

  int cube2(int y) {
    return cube(3); // Access static method
  }

  int cube3() {
    return a; // Access static variable
  }
}
```

* Non-static methods can access **all static members** directly.

---

#### Static `main` Method in Java

```java
class HelloWorld {
  public static void main(String[] args) {
    System.out.println("Hello World!");
  }
}
```

* The `main` method is static so the JVM can run it **without creating an object**.

---

#### Lesson Summary

* **Static methods** belong to the **class**; called without an object.
* **Non-static methods** belong to an **instance**; require an object to call.
* Static methods:

  * Can only access static members.
  * Cannot use `this` or access instance members directly.
* Non-static methods:

  * Can access both static and instance members.
* The `main` method is static to serve as the program's entry point.

### Section 7: Modular & Object-Oriented Programming

---

#### What Is Modular Programming?

* **Modular programming** breaks a large program into smaller, independent **modules**, each with a specific functionality.
* Each module is easier to test, reuse, maintain, and debug.

---

#### Benefits of Modular Programming

* ✅ **Decreases complexity** — Focus on one small task at a time.
* ♻️ **Reusability** — Use one method in many places.
* 👥 **Team collaboration** — Different developers can work on different modules.
* 🧪 **Easier testing** — Modules can be tested independently.

---

#### Example: GPA Calculator (Modular Method)

```java
double calculateGradeAverage(double[] grades) {
  double sum = 0;
  for (int i = 0; i < grades.length; i++)
    sum = sum + grades[i];
  return (sum / grades.length);
}
```

* This method **calculates the GPA** based on an array of grade values.
* Example input: `{3.5, 3.0, 4.0}` ➜ Output: `3.5`

---

#### What Is Object-Oriented Programming?

* Java is an **object-oriented language** — everything is based on **objects**.
* An **object** has:

  * **Attributes** (data or characteristics)
  * **Methods** (behaviors or actions)
* A **class** is a **template** or blueprint for creating objects.

---

#### Declaring a Class

```java
public class Student {
  private String name;
  private Integer studentId;
  private Double currentGPA;
  private String emailAddress;
}
```

* Attributes are declared as **private** to encapsulate and protect the data.

---

#### Example: Method Inside a Class

```java
public void calculateGradeAverage(double[] grades) {
  double sum = 0;
  for (int i = 0; i < grades.length; i++)
    sum += grades[i];
  currentGPA = sum / grades.length;
}
```

* This method **updates the `currentGPA`** attribute for the object.

---

#### Getters and Setters

```java
public String getName() {
  return name;
}

public void setName(String n) {
  name = n;
}
```

* `getName()` returns the value.
* `setName()` assigns a new value.

---

#### Setter with Validation

```java
public void setEmailAddress(String address) {
  if (!address.contains("@"))
    throw new IllegalArgumentException();
  emailAddress = address;
}
```

* Prevents assigning an invalid email.

---

#### Creating Instances (Objects)

```java
Student s1 = new Student();
s1.setName("Alice");

Student s2 = new Student();
s2.setName("Mary");
```

* Each **object** holds its own set of attribute values.

---

#### Static Methods

```java
public static double calculateAverage(double sum, int count) {
  if (count == 0)
    throw new IllegalArgumentException();
  return sum / count;
}
```

* Called using the **class name**:

```java
MyMath.calculateAverage(100, 50);
```

* No object is needed to use the method.

---

#### The `main` Method

```java
public static void main(String[] args) {
  // Entry point for all Java programs
}
```

* Must be **static** so the JVM can run it without creating an object first.

---

#### Java Packages Overview

| Package      | Description                                                 |
| ------------ | ----------------------------------------------------------- |
| `java.util`  | Lists, maps, queues, sets, arrays, dates, Scanner, etc.     |
| `java.lang`  | Core types (`System`, `Math`, `Integer`, `Character`, etc.) |
| `java.awt`   | Graphics, GUI components, user interface design             |
| `java.swing` | GUI components (buttons, labels, windows, forms, etc.)      |

---

#### Lesson Summary

* **Modular programming** simplifies large applications by using independent methods.
* Java is **object-oriented** — it uses **classes** and **objects** to model real-world behavior.
* A **class** contains attributes and methods. Attributes are often private and accessed via **getters and setters**.
* **Static methods** belong to the class and can be called without creating objects.
* The **main method** is static and serves as the **entry point** for every Java program.
* Java includes many **standard packages** for input/output, math, collections, and GUI functionality.

### Section 8: Passing Parameters and Arrays in Java

---

#### Passing Simple Variables to a Method

* Java uses **pass-by-value** — even when you pass a variable, only its **value** is sent to the method, **not** the original variable.
* Any changes to parameters inside the method **do not affect** the original variable outside the method.

```java
public class Main {
  public static void main(String[] args) {
    Example ex = new Example();
    int total = 10;
    ex.sum(total, 5);
    System.out.println("total=" + total); // total is still 10
  }

  public static class Example {
    public int sum(int total, int add) {
      total = total + add;
      return total;
    }
  }
}
```

* To **retain the modified value**, assign the result back:

```java
total = ex.sum(total, 5);  // Now total becomes 15
```

---

#### What Is a Java Array?

* An **array** is a Java object used to store **multiple values** of the same data type.
* Array declaration:

```java
int[] numbers = new int[3];
```

* Array indexing starts at 0:

```java
numbers[0] = 1;
numbers[1] = 2;
numbers[2] = 3;

System.out.println("numbers= " + numbers[0] + " " + numbers[1] + " " + numbers[2]);
// Output: numbers= 1 2 3
```

---

#### Passing an Array to a Method

* When an array is passed to a method, its **reference** is passed — **not a copy**.
* Any changes made inside the method **affect the original array**.

```java
public class Main {
  public static void main(String[] args) {
    Example ex = new Example();
    int[] numbers = {1, 2, 3};
    System.out.println("numbers= " + numbers[0] + " " + numbers[1] + " " + numbers[2]);

    int total = ex.sum(numbers);

    System.out.println("numbers= " + numbers[0] + " " + numbers[1] + " " + numbers[2]);
    System.out.println("total=" + total);
  }

  public static class Example {
    public int sum(int[] x) {
      x[0] = x[0] + 1;
      x[1] = x[1] + 1;
      x[2] = x[2] + 1;
      return x[0] + x[1] + x[2];
    }
  }
}
```

* Output:

```
numbers= 1 2 3
numbers= 2 3 4
total=9
```

---

#### Reassigning Array Reference Inside a Method

* If you assign a **new array inside the method**, it no longer points to the original array:

```java
x = new int[] {1, 2, 3};  // New memory, old array remains unchanged
```

* Result:

```
numbers= 1 2 3
numbers= 1 2 3
total=9
```

---

#### Returning an Array From a Method

* Arrays can be **returned from methods**, just like any object or value.

```java
public class Main {
  public static void main(String[] args) {
    Example ex = new Example();
    int[] numbers = ex.populate();
    System.out.println("numbers= " + numbers[0] + " " + numbers[1] + " " + numbers[2]);
    int total = ex.sum(numbers);
    System.out.println("total=" + total);
  }

  public static class Example {
    public int[] populate() {
      int[] x = new int[3];
      x[0] = 1; x[1] = 2; x[2] = 3;
      return x;
    }

    public int sum(int[] x) {
      x[0]++; x[1]++; x[2]++;
      return x[0] + x[1] + x[2];
    }
  }
}
```

* Output:

```
numbers= 1 2 3
total=9
```

---

#### Lesson Summary

* Simple variables are passed **by value** — the original remains unchanged.
* Arrays are passed by **reference**, so their contents can be **modified permanently** inside methods.
* Arrays can be **returned from methods** and used like any locally defined array.
* Key takeaways:

  * Use returned values for primitive types if you want changes retained.
  * Use caution when modifying arrays — changes affect the original.

### Section 9: Recursion in Java

---

#### What Is Recursion?

* **Recursion** is when a method **calls itself** to solve a smaller part of a problem until a stopping condition is met.
* Like a **revolving door**, recursion continues until told to stop.
* Recursive methods must always include a **base case** to prevent infinite loops and program crashes.

---

#### Example: Calculating Factorials

* A **factorial** is the product of an integer and all the integers below it.

```
n! = n × (n-1) × (n-2) × … × 1
```

* For example:

```
5! = 5 × 4 × 3 × 2 × 1 = 120
```

```java
public class Main {
  public static void main(String[] args) {
    double tester = 11.0;
    System.out.println("The factorial of " + tester + " = " + calcFactorial(tester));
  }

  public static double calcFactorial(double input) {
    if (input == 1.0) {
      return 1.0;
    }
    return input * calcFactorial(input - 1.0);
  }
}
```

* Output:
  `The factorial of 11.0 = 39916800.0`

---

#### Example: Fibonacci Series

* A **Fibonacci series** starts with 1, 1, and every next number is the **sum of the previous two**:

```
1, 1, 2, 3, 5, 8, ...
```

```java
public class Main {
  public static void main(String args) {
    System.out.println("\n***** FIBONACCI SERIES *****\n");
    int count = 15;
    int a = 1, b = 1, c = 0;
    System.out.print(a + " " + b);
    printFibonacci(count - 2, c, b, a);
    System.out.println();
  }

  static void printFibonacci(int count, int c, int b, int a) {
    if (count > 0) {
      c = b + a;
      a = b;
      b = c;
      System.out.print(" " + c);
      printFibonacci(count - 1, c, b, a);
    }
  }
}
```

* Output:
  `1 1 2 3 5 8 13 21 34 55 89 144 233 377 610`

---

#### Example: Tower of Hanoi

* Puzzle with **3 pegs** and **n disks**:

  * Move all disks from Peg 1 to Peg 3 using Peg 2 as helper.
  * Rules:

    * Move only **one disk at a time**
    * Never place a **larger disk on a smaller disk**

```java
public class TowerOfHanoi {
  public void solvePuzzle(int n, String begin, String temp, String end) {
    if (n == 1) {
      System.out.println(begin + " ---> " + end);
    } else {
      solvePuzzle(n - 1, begin, end, temp);
      System.out.println(begin + " ---> " + end);
      solvePuzzle(n - 1, temp, begin, end);
    }
  }

  public static void main(String[] args) {
    TowerOfHanoi tower = new TowerOfHanoi();
    int disks = 3;
    tower.solvePuzzle(disks, "Peg 1", "Peg 2", "Peg 3");
  }
}
```

* Output:

```
Peg 1 ---> Peg 3
Peg 1 ---> Peg 2
Peg 3 ---> Peg 2
Peg 1 ---> Peg 3
Peg 2 ---> Peg 1
Peg 2 ---> Peg 3
Peg 1 ---> Peg 3
```

---

#### Lesson Summary

* **Recursion** allows a method to solve a problem by calling itself repeatedly.
* Must include a **base case** to stop recursion.
* Useful for:

  * Calculating **factorials**
  * Generating **Fibonacci sequences**
  * Solving **recursive puzzles** like **Tower of Hanoi**
* Pros:

  * Elegant, clean solutions to complex problems
* Cons:

  * Can be **resource-intensive**
  * Risk of **stack overflow** if not terminated properly

### Section 10: Recursion & Iteration

---

#### What Are Recursion and Iteration?

* **Recursion**: A method that **calls itself** until a stopping condition (exit point) is met.
* **Iteration**: Uses **loops** (like `for`, `while`) to repeat code execution until a condition is no longer true.
* Both require an **exit condition** to prevent infinite repetition and system crashes.

---

#### Recursive Name Reversal

* This recursive method reverses a string by calling itself:

```java
private static String reverseNameRecursive(String theName) {
  if (theName.length() == 0)
    return "";
  else
    return reverseNameRecursive(theName.substring(1)) + theName.charAt(0);
}
```

* Calling the method:

```java
System.out.println(reverseNameRecursive("yoda"));
```

* Output:
  `adoy`

---

#### Recursive Factorial Calculation

* Computes factorial using a recursive call until the number equals 1:

```java
private static long factorialRecursive(int theNumber) {
  if (theNumber == 1)
    return 1;
  else
    return theNumber * factorialRecursive(theNumber - 1);
}
```

* Calling the method:

```java
System.out.println(factorialRecursive(3));
```

* Output:
  `6`

---

#### Iterative Name Reversal

* The same string reversal implemented using a `for` loop:

```java
private static String reverseNameIterative(String theName) {
  StringBuilder reverseName = new StringBuilder();
  char[] strChars = theName.toCharArray();
  int len = theName.length() - 1;
  for (int i = len; i >= 0; i--) {
    reverseName.append(strChars[i]);
  }
  return reverseName.toString();
}
```

* Calling the method:

```java
System.out.println(reverseNameIterative("yoda"));
```

* Output:
  `adoy`

---

#### Iterative Factorial Calculation

* Computes factorial using a loop from 1 to the input number:

```java
private static long factorialIterative(int theNumber) {
  int theFactorial = 1;
  for (int i = 1; i <= theNumber; i++) {
    theFactorial = theFactorial * i;
  }
  return theFactorial;
}
```

* Calling the method:

```java
System.out.println(factorialIterative(3));
```

* Output:
  `6`

---

#### Key Differences: Recursion vs. Iteration

| Aspect          | Recursion                                                    | Iteration                            |
| --------------- | ------------------------------------------------------------ | ------------------------------------ |
| **Definition**  | Method calls itself                                          | Loops through code block             |
| **Control**     | Exit via base case                                           | Exit via loop condition              |
| **Performance** | More memory due to call stack                                | Often more efficient memory-wise     |
| **Readability** | Can be elegant but harder to follow                          | Typically more explicit and readable |
| **Best For**    | Problems naturally defined recursively (e.g. trees, puzzles) | Simple repetitive tasks              |

---

#### Lesson Summary

* **Recursion** and **iteration** both repeat blocks of code until a condition is met.
* Recursive methods are compact and elegant but use more memory.
* Iterative methods are more common, straightforward, and efficient for simple tasks.
* The choice depends on:

  * **Performance**
  * **Readability**
  * **Programmer preference**