### Section 1: The Command Line

#### What Is a Command-Line Interface?

* A **command-line interface (CLI)** is a **text-based console** used to execute programs and commands manually.
* Common environments:

  * **Windows** → Command Prompt (`cmd`)
  * **Mac** → Terminal (`/Applications/Utilities/Terminal`)

---

#### Java Command-Line Arguments

* Java allows you to **pass arguments into the program** via the **`main(String[] args)`** method.
* These arguments are accessed using:

  * `args[0]`, `args[1]`, `args[2]`, etc.
* Java starts counting at **0**, so `args[2]` is the **third argument**.

```java
public class Example {
public static void main(String[] args) {
int i = Integer.parseInt(args[0]);
double d = Double.parseDouble(args[1]);
String msg = args[2];
System.out.println("i=" + i + " d=" + d + " msg=" + msg);
}
}
```

---

#### Running from the Command Line

* Before running Java programs, ensure you have the **Java Development Kit (JDK)** installed.
* To verify, run:

```bash
javac -version
```

* If successful, you can **compile** your Java file using:

```bash
javac Example.java
```

* This generates a file called `Example.class`.

* To **run** the program with command-line arguments:

```bash
java Example 5 2.8 hello
```

* Output:

```
i=5 d=2.8 msg=hello
```

---

#### Handling Errors

* If not enough arguments are passed, you will get:

```bash
java.lang.ArrayIndexOutOfBoundsException
```

* If non-numeric input is passed where a number is expected, you will get:

```bash
java.lang.NumberFormatException
```

* Example of missing argument:

```bash
java Example 5
```

* Example of invalid input:

```bash
java Example five 2.8 hello
```

---

#### Try-Catch for Safer Argument Handling

* It's good practice to check `args.length` and handle exceptions:

```java
public class Example {
public static void main(String[] args) {
try {
  int i = Integer.parseInt(args[0]);
  double d = Double.parseDouble(args[1]);
  String msg = args[2];
  System.out.println("i=" + i + " d=" + d + " msg=" + msg);
} catch (Exception e) {
  System.out.println("Invalid or missing arguments.");
}
}
}
```

---

#### Summary

* Java programs can **accept command-line arguments** via `String[] args` in the `main()` method.
* Arguments are accessed using `args[index]`.
* Compile using **`javac`**, run using **`java`**, and provide **arguments inline**.
* Always **validate** and **check for errors** when using command-line input.

### Section 2: User Input

#### Import Scanner

* Java doesn’t include all features by default—only what’s needed.
* To allow keyboard input, we import the **`Scanner`** class:

```java
import java.util.Scanner;
```

---

#### Create a Scanner Instance

```java
Scanner readme = new Scanner(System.in);
```

* This creates a Scanner object to **read from standard input** (keyboard).
* Add this **inside the `main()` method.**

---

#### Prompt for Input and Store Values

* Declare variables and read values with `nextDouble()`:

```java
System.out.println("Enter Two Numbers (Press Enter after each):");
double n1, n2, n3;
n1 = readme.nextDouble();
n2 = readme.nextDouble();
n3 = n1 + n2;
System.out.println("Total = " + n3);
```

* Scanner also supports:

  * `nextInt()`, `nextFloat()`, `nextLong()`, etc.

---

#### Full Working Code (No Error Checking)

```java
import java.util.Scanner;
public class Main {
public static void main(String[] args) {
Scanner readme = new Scanner(System.in);
System.out.println("Enter Two Numbers (Press Enter after each):");
double n1, n2, n3;
n1 = readme.nextDouble();
n2 = readme.nextDouble();
n3 = n1 + n2;
System.out.println("Total = " + n3);
}
}
```

---

#### Error Checking with `hasNextDouble()`

* Use a `while` loop to validate input before proceeding.

```java
while (!readme.hasNextDouble()) {
System.out.println("Try entering a number");
readme.next(); // consume invalid input
}
```

---

#### Final Code With Full Error Checking

```java
import java.util.Scanner;
public class Main {
public static void main(String[] args) {
double n1 = 0, n2 = 0, n3 = 0;
Scanner readme = new Scanner(System.in);

// First number input
System.out.println("Enter The First Number:");
boolean valueSuccessfullyRead = false;
while (!valueSuccessfullyRead) {
  if (readme.hasNextDouble()) {
    n1 = readme.nextDouble();
    valueSuccessfullyRead = true;
  } else {
    readme.next(); // consume invalid input
    System.out.println("Try entering a number");
  }
}

// Second number input
System.out.println("Enter The Second Number:");
valueSuccessfullyRead = false;
while (!valueSuccessfullyRead) {
  if (readme.hasNextDouble()) {
    n2 = readme.nextDouble();
    valueSuccessfullyRead = true;
  } else {
    readme.next();
    System.out.println("Try entering a number");
  }
}

// Add and display result
n3 = n1 + n2;
System.out.println("Total = " + n3);
}
}
```

📝 *NOTE:*
The two input blocks are repetitive—this can be improved by extracting the repeated logic into a **method**, which you'll learn about in future lessons.

---

#### Summary

* Java reads user input using the **`Scanner` class**.
* Always **validate** input using `hasNextDouble()` (or similar methods).
* Improves user experience and **prevents crashes** from invalid input.
* Good input handling ensures your program is **robust and professional**.

### Section 3: Input Stream

---

#### Introduction

Java uses **input streams** to read data from the console. The top-level abstract class for reading bytes is `InputStream`. Java provides `System.in` as the standard input stream (also known as *stdin*).
To read input efficiently, two commonly used classes are:

* `Scanner`
* `BufferedReader`

---

#### Scanner

The `Scanner` class (in `java.util`) reads input and splits it into tokens using a delimiter (default is space). It allows easy type conversion.

```java
import java.util.Scanner;

public class Main {
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);   // create Scanner
    int num = sc.nextInt();                // read integer
    boolean bl = sc.nextBoolean();         // read boolean
    String str = sc.nextLine();            // read string (remaining input line)
    System.out.println("integer = " + num + " boolean = " + bl + " string = '" + str + "'");
    sc.close();
  }
}
```

---

#### Input Example

If input is:
`6 true good morning`

Output:
`integer = 6 boolean = true string = ' good morning'`

> Note: The space after `true` is included in the string.

---

#### Common Mistake Example

If input is:

```
6
false
```

Output:
`integer = 6 boolean = false string = ''`

> Explanation: The Enter key after `false` is read as the `nextLine()` string.

---

#### Input Validation Example

```java
import java.util.Scanner;

public class UseScanner2 {
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    int num = 0;
    System.out.println("Enter an integer followed by a string");
    
    if (sc.hasNextInt()) {
      num = sc.nextInt();
    } else {
      System.out.println("Input error, program terminating");
      sc.close();
      return;
    }

    String str = sc.nextLine();
    System.out.println("integer = " + num + " string = '" + str + "'");
    sc.close();
  }
}
```

---

#### Multiple Input Types Example

```java
Scanner sc = new Scanner(System.in);
int totalInt = 0;
double totalDouble = 0;

System.out.println("Enter a list of integers and doubles");

while (sc.hasNextInt()) {
  totalInt += sc.nextInt();
}
while (sc.hasNextDouble()) {
  totalDouble += sc.nextDouble();
}

System.out.println("integer sum = " + totalInt + " double sum = " + totalDouble);
sc.close();
```

> Input: `1 2 3 4.5 6.4 3.8`
> Output: `integer sum = 6 double sum = 14.7`

---

#### Custom Delimiter Example

```java
Scanner sc = new Scanner(System.in);
sc.useDelimiter(";");

int num = sc.nextInt();
boolean bl = sc.nextBoolean();

System.out.println("num = " + num + " boolean = " + bl);
sc.close();
```

> Input: `3;false;`
> Note: Semicolons are used as delimiters.

---

#### BufferedReader

The `BufferedReader` class is part of `java.io` and reads input with buffering for better performance. It's thread-safe and ideal for reading large text inputs.

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class UseBufferedReader {
  public static void main(String[] args) throws IOException {
    System.out.println("Enter integer, boolean, and string");

    BufferedReader r = new BufferedReader(new InputStreamReader(System.in));
    int num = Integer.parseInt(r.readLine());
    boolean bl = Boolean.parseBoolean(r.readLine());
    String str = r.readLine();

    System.out.println("Integer = " + num + " boolean = " + bl + " string = '" + str + "'");
    r.close();
  }
}
```

---

#### Input Example

> Input:

```
7
true
hello class
```

> Output:
> `Integer = 7 boolean = true string = 'hello class'`

---

#### Differences: Scanner vs BufferedReader

| Feature               | Scanner                              | BufferedReader                   |
| --------------------- | ------------------------------------ | -------------------------------- |
| Type checking methods | ✔️ (hasNextInt, hasNextDouble, etc.) | ❌ (parse manually)               |
| Thread-safe           | ❌                                    | ✔️                               |
| Buffer size           | 1 KB                                 | 8 KB                             |
| Parsing flexibility   | Built-in                             | Manual parsing with `parseXXX()` |
| Ease of use           | Very high                            | Medium (requires more setup)     |

---

#### Lesson Summary

* Use **Scanner** for ease of use, quick parsing, and token-based input.
* Use **BufferedReader** for multi-threaded applications and performance.
* Both use **System.in** for input and must be closed properly.
* Always check or handle exceptions for unexpected input.

### Section 4: Standard Output

---

#### Introduction

The standard output in Java is the `PrintStream` class accessed through the `System.out` field. By default, standard output prints to the console.

`PrintStream` allows printing of different data types, converting all data to bytes. Two of its most useful methods include `print` and `println`.

---

#### Print and Println

Both the `print` and `println` methods convert the data to bytes and print to the console.
The difference:

* `print()` prints the value and **keeps the cursor on the same line**
* `println()` prints the value and **moves the cursor to the next line**

```java
System.out.println("String 1 ");
System.out.println("String 2 ");
```

**Output:**

```
String 1 
String 2 
```

```java
System.out.print("String 1 ");
System.out.print("String 2 ");
```

**Output:**

```
String 1 String 2 
```

---

#### Variables in Print Methods

We can print the value of variables directly:

```java
int num = 5;
System.out.println(num);
```

**Output:**

```
5
```

Or concatenate variables with strings:

```java
String name = "Joe";
int grade = 80;
System.out.println("Student name: " + name + " Student grade: " + grade);
```

**Output:**

```
Student name: Joe Student grade: 80
```

> Note: The `+` symbol is used for **concatenation** in strings.

If you're adding numeric values, use parentheses to group the addition:

```java
int num = 5, num2 = 10;
System.out.println("Value=" + num + num2);
```

**Output:**

```
Value=510
```

```java
System.out.println("Value=" + (num + num2));
```

**Output:**

```
Value=15
```

---

#### Special Sequences

You can use escape characters like:

* `\n` – newline
* `\t` – tab

```java
String name = "Joe";
int grade = 80;
System.out.println("Student name: " + name + "\nStudent grade: " + grade);
```

**Output:**

```
Student name: Joe
Student grade: 80
```

```java
System.out.println("Student name: " + name + "\n\tStudent grade: " + grade);
```

**Output:**

```
Student name: Joe
	Student grade: 80
```

---

#### Lesson Summary

* Java uses `System.out`, a `PrintStream` object, to output to the console.
* `print()` and `println()` are the main output methods.
* Variables and literals can be printed directly or concatenated with strings.
* Parentheses are required when performing arithmetic inside a concatenated output.
* Special sequences like `\n` and `\t` help format printed output.

### Section 5: `System.out` and Output Formatting

#### What Is `System.out`?

* `System` is a **Java class** that provides access to system-level resources.
* It contains three key **stream attributes**:

  * `System.err` → Standard error output (`PrintStream`)
  * `System.in` → Standard input (`InputStream`)
  * `System.out` → Standard output (`PrintStream`)

---

#### The `PrintStream` Class

* `System.out` is an instance of the **`PrintStream`** class.
* It supports multiple output methods (like `print`, `println`, `printf`).
* Important traits:

  * It **never throws an IOException**.
  * Errors set an **internal error flag**.
  * The flag can be checked using `checkError()`.

---

#### Using `System.out.printf`

* `System.out.printf()` is used to **format text output**.
* It behaves identically to `System.out.format()`.
* Signature:

```java
System.out.printf(String format, Object... args)
```

* The **format string** includes **literal text** and **format specifiers**.

---

#### Format Specifiers Syntax

* Basic structure:

  ```
  %[flags][width][.precision]conversion  
  ```
* Key components:

  * `%` → Start of a format specifier
  * `flags` → Optional formatting (e.g., left justify `-`)
  * `width` → Minimum number of characters
  * `.precision` → For floating point (e.g., `.2f`)
  * `conversion` → Data type indicator (e.g., `d`, `f`, `s`)

---

#### Example: Formatting Floating Point Numbers

```java
double num = 23.1254;
System.out.printf("printing floating point with precision two and three with fields of 8 characters: %8.2f %8.3f", num, num);
```

* **Output**:

  ```
  printing floating point with precision two and three with fields of 8 characters:   23.13  23.125
  ```

* Explanation:

  * Right justified within 8-character fields
  * Rounded to 2 and 3 decimal places

---

#### Common Conversion Specifiers

| Specifier | Meaning             |
| --------- | ------------------- |
| `%d`      | Decimal integer     |
| `%o`      | Octal integer       |
| `%x`      | Hexadecimal integer |
| `%f`      | Floating point      |
| `%s`      | String              |

---

#### Example Outputs

```java
System.out.printf("integer: %d", 45);
// Output: integer: 45

System.out.printf("string: %s", "hello");
// Output: string: hello
```

---

#### Width and Justification

* Width → Minimum characters for output
* Justification:

  * Positive width = **Right justified**
  * Negative width = **Left justified**

```java
System.out.printf("Right: %10d", 45);   // Output:      45
System.out.printf("Left: %-10d", 45);   // Output: 45
```

---

#### Number Precision

* Used for floating point formatting:

```java
System.out.printf("float: %10.1f", 45.678);
// Output:     45.7
```

* Output is rounded to 1 decimal, right-justified in a 10-character field.

---

#### Special Character Sequences

| Sequence | Meaning |
| -------- | ------- |
| `\n`     | Newline |
| `\t`     | Tab     |

```java
System.out.printf("float: %10.1f", 45.678);
System.out.printf("\nstring: %s", "hello");
```

* Output:

  ```
       45.7
  string: hello
  ```

---

#### Summary

* `System.out` provides standard output through the `PrintStream` class.
* `System.out.printf()` enables **formatted output** similar to C/C++.
* The **format string** uses `%` specifiers for:

  * Width
  * Justification
  * Precision
  * Data types
* Always use proper formatting and handle exceptions like:

  * `NullPointerException` (null format string)
  * `IllegalFormatException` (invalid syntax)

### Section 6: Graphical User Interface (GUI)

#### What Is a GUI?

* A **Graphical User Interface (GUI)** is a **visual-based interface** that allows users to interact with computers through graphical elements.
* It is the **most widely used interface** in modern computer systems.
* GUIs eliminate the need to memorize commands by using:

  * **Windows**
  * **Icons**
  * **Menus**
  * **Pointers**

---

#### WIMP: The Core GUI Elements

| Element     | Description                                                          |
| ----------- | -------------------------------------------------------------------- |
| **Window**  | An independent display area for content or programs.                 |
| **Icon**    | A small visual symbol representing files, applications, etc.         |
| **Menu**    | A list of choices or commands.                                       |
| **Pointer** | A visual cue (often mouse-controlled) to interact with GUI elements. |

* GUIs offer **intuitive interaction** by combining these elements.
* Example: Double-clicking an icon opens a file or application.

---

#### Evolution of GUI in Modern Devices

* Originally developed for **desktop environments** in the 1980s.
* Mobile devices adapted GUI principles with:

  * **Touchscreen gestures** (e.g., pinch, swipe, rotate)
  * Adaptations due to **limited space and input tools**

---

#### Importance of Interface Design

* A well-designed GUI:

  * Enhances **usability**
  * Promotes **efficiency and satisfaction**
  * Supports **natural human-computer interaction**

* ISO standard defines **usability** as:

  > "The extent to which a product can be used by specified users to achieve specified goals with effectiveness, efficiency, and satisfaction in a specified context of use."

---

#### Key Usability Factors

| Factor           | Description                                         |
| ---------------- | --------------------------------------------------- |
| **Learnability** | How quickly users can perform basic tasks           |
| **Efficiency**   | Speed and ease of completing tasks                  |
| **Memorability** | How easily users regain proficiency after time away |
| **Errors**       | Frequency and severity of user mistakes             |
| **Satisfaction** | User enjoyment and experience quality               |

---

#### Interface Development Process

1. **Collect Functionality Requirements**
   – What tasks must the system support?

2. **User Analysis**
   – Who are the users, and what are their skill levels?

3. **Information Architecture**
   – How is the system structured within workflows?

4. **Prototyping**
   – Develop simple interactive mockups.

5. **Usability Testing**
   – Allow real users to interact and provide feedback.

6. **Graphic Design**
   – Finalize the visual appearance and layout.

* Result: A GUI that is **intuitive**, **functional**, and **efficient**.

---

#### Interface Design in Practice

* Applications from the **same company** often have **similar layouts**.

  * Example: Microsoft Word and PowerPoint share many interface elements.

* **Consistency** in design promotes easier learning and usage.

* Many platforms provide **built-in GUI design tools** to streamline development.

---

#### Additional Aspects of GUI Design

| Feature                | Purpose                                                         |
| ---------------------- | --------------------------------------------------------------- |
| **Sign-on Procedures** | Authenticate users with credentials                             |
| **Wizards**            | Guide users through complex tasks via step-by-step instructions |
| **Help Facilities**    | Provide tutorials, search functions, and support documentation  |

* These enhance usability and accessibility, especially for novice users.

---

#### Summary

* A GUI uses **visual elements** to make interaction with a system easier.
* **WIMP** (Window, Icon, Menu, Pointer) forms the foundation of GUI design.
* The **goal** of GUI design is usability: intuitive, error-tolerant, and efficient interfaces.
* Interface design must be considered **early in system development** and validated through **user feedback**.

---

#### Learning Outcome

After reviewing this lesson, you should be able to:

* Identify the **elements** of user interfaces (WIMP).
* Explain how GUIs are **designed and tested** to improve software usability.

### Section 7: The Graphical User Interface in Java

#### What Is a Graphical User Interface?

* A **Graphical User Interface (GUI)** is the **visible part of a program** users interact with.
* Examples include **windows, buttons, textboxes**, and other elements you see in browsers, apps, and desktop environments.
* If you’re navigating the web or using any software right now — you’re already interacting with a GUI!

---

#### GUIs and Programming Languages

* Java is one of many languages that support GUI development.
* Each language has its own **syntax and library** for GUI programming.
* Learning Java’s GUI syntax is important for:

  * Building **user-friendly applications**
  * Ensuring your code is **organized, functional, and adaptable**

---

#### Containers and Components

| Element       | Description                                                                   |
| ------------- | ----------------------------------------------------------------------------- |
| **Container** | The **framework** or window that holds GUI elements (e.g., `JFrame`, `Panel`) |
| **Component** | The **interactive objects** like buttons, labels, checkboxes, etc.            |

* Think of **containers** as the skeleton or structure.
* Think of **components** as the parts that make it **interactive and visual**.
* A working GUI is a **combination** of both.

---

#### GUI Class Hierarchies in Java

Java GUI development is built on two main **class libraries**:

1. **Abstract Window Toolkit (AWT)**

   * **Older** Java GUI framework
   * Provides **basic GUI tools** (e.g., buttons, scrollbars)
   * Known as **"heavyweight components"**
   * Tied to the **platform’s native GUI**

2. **Swing**

   * A **newer**, more flexible GUI framework
   * Built on top of AWT
   * Known as **"lightweight components"**
   * **Platform-independent**, allowing consistent design across systems

---

#### AWT vs. Swing

| Feature        | AWT                   | Swing                     |
| -------------- | --------------------- | ------------------------- |
| Component Type | Heavyweight           | Lightweight               |
| Dependency     | Tied to OS            | Platform-independent      |
| Look & Feel    | Native (varies by OS) | Customizable (Java-based) |
| Examples       | `Button`, `TextField` | `JButton`, `JTextField`   |

* Both are essential for building GUIs in Java.
* **Swing** is generally preferred today due to **greater flexibility and appearance control**.

---

#### Why GUI Matters

* A GUI is **the bridge** between users and your program.
* Without it, users interact with raw code — which is impractical and non-intuitive.
* A good GUI ensures:

  * **Usability**
  * **Accessibility**
  * **Visual appeal**

> Without a graphical interface, a program is **just code** — inaccessible to most users.

---

#### Lesson Summary

* GUIs are the **visible, interactive layer** of a program.
* In Java, GUIs are made using **containers** and **components**.
* Java provides two key GUI libraries:

  * **AWT** (older, OS-dependent)
  * **Swing** (modern, flexible, and platform-independent)
* Understanding and using these libraries allows you to build **effective, user-friendly applications**.

### Section 8: Lines & Shapes in Java GUI

#### Why Use Lines and Shapes?

* Graphics are **fundamental** to modern applications, from **web design** to **video games**.
* Drawing shapes such as **lines, rectangles, arcs, and polygons** enhances the **interactivity and visual design** of a GUI.
* Java offers a robust toolkit via the **Graphics** and **Graphics2D** classes to render these shapes.

---

#### Getting Started: Basic Structure

* You need to **extend `JPanel`** and override the `paint` method.
* A basic setup uses **Swing and AWT** libraries:

```java
import java.awt.*;
import java.awt.geom.*;
import javax.swing.*;

public class Main extends JPanel {
  public static void main(String[] args) {
    JFrame f = new JFrame("Twilight Zone");
    f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    f.getContentPane().add(new Main());
    f.setSize(290, 325);
    f.setLocation(550, 25);
    f.setVisible(true);
  }
}
```

---

#### Drawing a Line

* Use the `drawLine(int x1, int y1, int x2, int y2)` method from the **Graphics** class.

```java
public void paint(Graphics g) {
  String hexColor = "0x45e5B";
  g.setColor(Color.decode(hexColor));
  g.drawLine(10, 10, 40, 10); // Horizontal line
}
```

* To set line **thickness**, cast `Graphics` to `Graphics2D` and use `setStroke`:

```java
Graphics2D g2 = (Graphics2D) g;
g2.setStroke(new BasicStroke(5));
```

---

#### Drawing Rectangles

* Use `drawRect(x, y, width, height)` or `fillRect(...)` for a solid rectangle:

```java
g2.drawRect(10, 20, 150, 40);  // Outline
g2.fillRect(10, 20, 150, 40);  // Filled
```

* Always set color **before** drawing or filling:

```java
g2.setColor(Color.decode(hexColor));
```

---

#### Rounded Rectangles

* Use `RoundRectangle2D` or `fillRoundRect(...)`:

```java
RoundRectangle2D rd = new RoundRectangle2D.Float(10, 20, 150, 40, 5, 5);
g2.draw(rd);  // Outline with rounded edges
```

* For smoother graphics, enable **anti-aliasing**:

```java
g2.setRenderingHint(RenderingHints.KEY_ANTIALIASING, RenderingHints.VALUE_ANTIALIAS_ON);
g2.fillRoundRect(10, 20, 150, 40, 15, 15); // Smoothed filled shape
```

---

#### Drawing Arcs

* Use `fillArc(x, y, width, height, startAngle, arcAngle)`:

```java
g2.fillArc(10, 100, 155, 155, 45, 45);
```

* `drawArc(...)` exists for outlines, like `drawRect` vs `fillRect`.

---

#### Drawing Ovals and Circles

* Use `drawOval(...)` or `fillOval(...)`:

```java
g2.fillOval(10, 200, 150, 110); // Oval
```

* A **circle** is just an oval with equal width and height.

---

#### Drawing Polygons

* Use the `Polygon` class and a loop to define multiple points.

**Example: 9-sided polygon**

```java
Polygon p = new Polygon();
for (int i = 0; i < 9; i++) {
  p.addPoint((int) (200 + 35 * Math.cos(i * 2 * Math.PI / 9)), 
             (int) (200 + 35 * Math.sin(i * 2 * Math.PI / 9)));
}
g2.drawPolygon(p);
```

---

#### Advanced: Complex Polygon with 520 Sides

```java
Polygon s = new Polygon();
for (int i = 0; i < 520; i++) {
  double t = i / 520.0;
  s.addPoint((int) (150 + 50 * t * Math.cos(64 * t * Math.PI)), 
             (int) (150 + 50 * t * Math.sin(64 * t * Math.PI)));
}
g2.drawPolygon(s);
```

* This creates an artistic, spiral-like polygon with **multiple layers**.

---

#### Lesson Summary

* Java provides tools via `Graphics` and `Graphics2D` for **custom drawing**.
* Common drawing methods:

  * `drawLine` – Straight lines
  * `drawRect`, `fillRect` – Rectangles
  * `drawRoundRect`, `fillRoundRect` – Rounded rectangles
  * `drawArc`, `fillArc` – Arcs and pie pieces
  * `drawOval`, `fillOval` – Ovals and circles
  * `drawPolygon` – Multi-point shapes like polygons
* Use `Graphics2D` for:

  * Line thickness (`setStroke`)
  * Anti-aliasing for smoother edges
* All shapes require defining **coordinates and dimensions**, and are rendered in the `paint` method.

### Section 9: What is `JFrame`

#### What Is a `JFrame`?

* A `JFrame` is the **primary container** used to build graphical applications in **Java Swing**.
* It serves as the **foundation** or **window** that holds all GUI components such as buttons, labels, panels, etc.
* Without a `JFrame`, a **GUI application cannot function**.
* Even **Applets** sometimes use `JFrame` to create external windows.

---

#### Characteristics of `JFrame`

* Part of the **Java Swing** library.
* **Lightweight** – uses fewer system resources than older GUI frameworks.
* Requires importing the Swing package:

```java
import javax.swing.*;
```

---

#### Creating a `JFrame`

* You create a `JFrame` by instantiating it:

```java
JFrame f = new JFrame();                        // No title
JFrame f2 = new JFrame("The Twilight Zone");    // With title
```

> But just creating the frame won’t make it appear on screen — it needs size, location, and visibility.

---

#### Setting Size, Location & Visibility

* Use the following methods to configure the frame:

```java
f.setSize(300, 325);           // Width x Height (pixels)
f.setLocation(150, 50);        // X and Y coordinates on the screen
f.setVisible(true);            // Makes the frame visible
```

* Without `setVisible(true)`, the frame won’t display at all.

---

#### Common `JFrame` Methods

| Method                                         | Description                                                    |
| ---------------------------------------------- | -------------------------------------------------------------- |
| `setDefaultCloseOperation(int op)`             | What happens when the window is closed (`EXIT_ON_CLOSE`, etc.) |
| `setSize(int x, int y)`                        | Sets frame dimensions                                          |
| `setTitle(String title)`                       | Changes the window title                                       |
| `setVisible(boolean t)`                        | Shows or hides the frame                                       |
| `setDefaultLookAndFeelDecorated(boolean look)` | Matches the OS’s look and feel                                 |
| `add(Component)`                               | Adds GUI components (e.g., panels)                             |
| `setIconImage(Image img)`                      | Sets the window’s icon                                         |

---

#### Working Example with Label and Panel

```java
import javax.swing.*;
import java.awt.event.*;
import java.awt.*;

public class Main extends JFrame {
  public static void main(String[] args) {
    Main frame = new Main();                            // Custom JFrame subclass
    frame.setLayout(new FlowLayout());                  // Flow layout
    frame.setSize(new Dimension(500, 500));             // Frame size
    frame.setTitle("The Twilight Zone");                // Frame title
    frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE); // Close behavior

    JLabel motto = new JLabel("Not Only of Sight... But of MIND");  // Label
    JPanel panel = new JPanel();                         // Panel container
    panel.add(motto);                                    // Add label to panel
    frame.getContentPane().add(panel);                   // Add panel to frame

    frame.setLocationRelativeTo(null);                   // Center on screen
    frame.setVisible(true);                              // Display window
  }
}
```

* Output: A window titled **“The Twilight Zone”** with a label centered in it.

---

#### Lesson Summary

* The `JFrame` class is the **foundation** for all Java Swing GUI applications.
* When using a `JFrame`:

  * You can **set its size, title, and behavior** using various methods.
  * You must **set visibility** explicitly using `setVisible(true)`.
* `JFrame` supports the addition of multiple GUI components and is highly customizable.
* **Constructors** initialize the frame, while **methods** adjust properties after creation.

### Section 10: The `JLabel`: Uses & Examples

#### What Is a `JLabel`?

* A `JLabel` is a **Swing component** that displays **un-editable information** to users.
* Labels are used for:

  * **Instructions**
  * **Field descriptions**
  * **Static messages**
* `JLabel` text can be updated **programmatically**, but **not by the user**.

> A `JLabel` enhances **usability** by clearly communicating context or messages to the user.

---

#### Basic `JLabel` Setup

* Like all Swing elements, a `JLabel` must be added to a **`JFrame`**:

```java
JFrame f = new JFrame("New Frame");
f.setSize(100, 100);
f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
f.setDefaultLookAndFeelDecorated(true);
f.setVisible(true);
```

* To create a label:

```java
JLabel motto = new JLabel("Not Only of Sight .... But of MIND");
f.add(motto);
```

---

#### Displaying Images with `JLabel`

* You can also display **images** using the `ImageIcon` class:

```java
ImageIcon imgLogo = new ImageIcon("C:\\My_Pictures\\space.jpg");
JLabel lblLogo = new JLabel(imgLogo);
f.add(lblLogo);
f.setLayout(new FlowLayout(FlowLayout.LEFT));  // Ensure proper placement
```

* Tip: Avoid **cluttering** the frame with too many elements. Simplicity improves readability.

---

#### Changing a `JLabel` at Runtime

* Use the `setText(String newText)` method to change the label’s content:

```java
motto.setText("Changed!");
```

* This can be triggered by an event (e.g., button click).

---

#### Full Working Example with Text, Icon, and Button

```java
import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class JFrameExample {
  public static void main(String[] args) {
    JFrame f = new JFrame("The Twilight Zone");
    f.setSize(300, 325);
    f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    f.setDefaultLookAndFeelDecorated(true);

    JLabel motto = new JLabel("Not Only of Sight... But of MIND");
    f.add(motto);

    ImageIcon imgLogo = new ImageIcon("C:\\Users\\MDG13\\Pictures\\space.jpg");
    JLabel lblLogo = new JLabel(imgLogo);
    f.add(lblLogo);

    f.setLayout(new FlowLayout(FlowLayout.LEFT));

    JButton jb = new JButton("Click Here!");
    f.add(jb);

    jb.addActionListener(new ActionListener() {
      public void actionPerformed(ActionEvent e) {
        motto.setText("Changed!");
        jb.setEnabled(false);
      }
    });

    f.setVisible(true);
  }
}
```

* When the button is clicked:

  * The label text changes.
  * The button is **disabled** to prevent further interaction.

---

#### Lesson Summary

* The `JLabel` class provides a way to **display static content** to users in Java Swing.
* It supports:

  * **Text-based labels**
  * **Image-based labels**
  * **Mixed content**
* Although **not editable by the user**, label content can be **updated programmatically** using `setText()`.
* `JLabel`s are critical in building **user-friendly** and **intuitive** interfaces.

### Section 11: Layout Manager in Java

#### Why Use a Layout Manager?

* **Manually positioning GUI components** is tedious and error-prone.
* A **Layout Manager** automates the arrangement of components based on rules.
* Benefits include:

  * **Ease of adjustment**
  * **Consistency in design**
  * **Platform independence**
  * **Reusability** of layout configurations
* Layout Managers are **objects** that implement the **LayoutManager interface**.

---

#### How Layout Managers Work

* When you add components to a container:

  * The **Layout Manager determines** their **size and position**.
  * Resizing the window triggers the **layout manager to reposition components** accordingly.
* Layouts can be:

  * **Global** (frame-level)
  * **Local** (specific panels or inner containers)

> Without a layout manager, you rely on **absolute positioning**, which is rarely recommended.

---

#### Using Layout Managers with Containers

* Layout Managers are typically used with:

  * **`JPanel`** – Often defaults to `FlowLayout`
  * **Content Panes** – Often defaults to `BorderLayout`

```java
JFrame frame = new JFrame("New Frame");
Container contentPane = frame.getContentPane();
contentPane.setLayout(new FlowLayout()); // Or any other layout
```

* While it's possible to **disable layout management** entirely, it is not advisable for complex interfaces.

---

#### Common Layout Manager Classes

| Layout Class       | Description                                                                                          |
| ------------------ | ---------------------------------------------------------------------------------------------------- |
| `BoxLayout`        | Arranges components **horizontally or vertically**; no wrapping                                      |
| `GroupLayout`      | Allows **parallel** and **sequential** positioning; each dimension defined independently             |
| `ScrollPaneLayout` | Layout for components inside a `JScrollPane`, including **scrollbars, headers, and viewports**       |
| `SpringLayout`     | Highly flexible layout manager that defines **constraints** and **relationships** between components |

---

#### Example: Setting a Layout Manager

```java
JFrame frame = new JFrame("New Frame");
Container contentPane = frame.getContentPane();
contentPane.setLayout(new GroupLayout(contentPane));
```

* You can define **different layouts** for different panels inside the same frame.
* Layout managers are responsible for the **visual arrangement** of your UI elements.

---

#### BorderLayout Example (Illustration)

| Region     | Description              |
| ---------- | ------------------------ |
| **NORTH**  | Top of the container     |
| **SOUTH**  | Bottom of the container  |
| **EAST**   | Right side               |
| **WEST**   | Left side                |
| **CENTER** | Takes up remaining space |

```java
frame.setLayout(new BorderLayout());
frame.add(new JButton("North"), BorderLayout.NORTH);
frame.add(new JButton("Center"), BorderLayout.CENTER);
```

---

#### Lesson Summary

* **Layout Managers** in Java Swing determine how components are arranged in a container.
* They offer flexibility, scalability, and consistency in GUI design.
* Popular layout managers include:

  * `FlowLayout`, `BorderLayout`
  * `BoxLayout`, `GroupLayout`, `SpringLayout`, and `ScrollPaneLayout`
* Using layout managers is crucial to designing **responsive, maintainable** GUIs.
* Though **manual positioning** is possible, layout managers are **preferred** for better control and maintainability.

### Section 12: Java Form Elements

#### Making GUIs Interactive

* Labels alone can’t make a form interactive.
* Adding **form elements** like:

  * **Text fields** (`JTextField`)
  * **Buttons** (`JButton`)
  * **Tool tips**

  … makes your Java GUI application functional and user-friendly.

---

#### 1. The `JFrame`

* The **foundation** of any Swing GUI application.
* Every interactive component must be placed inside a `JFrame`.

```java
import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class Main extends JFrame {
  public static void main(String[] args) {
    Main frame = new Main();                                // Extends JFrame
    frame.setLayout(new FlowLayout());                      // Sets layout manager
    frame.setSize(new Dimension(500, 500));                 // Window size
    frame.setTitle("The Twilight Zone");                    // Frame title
    frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);   // Enables X button
  }
}
```

---

#### 2. The `JPanel`

* A **container** that holds multiple GUI elements.
* Helps organize components **before adding them to the frame**.

```java
JPanel panel = new JPanel();  // Creates a panel
```

---

#### 3. `JTextField` – Adding Text Input

* Allows user to **enter data** (e.g., name, email, password).
* Example:

```java
JTextField textField = new JTextField("Enter Name");
textField.setBounds(10, 100, 150, 10);
panel.add(textField);  // Add to panel
```

* To arrange components vertically:

```java
panel.setLayout(new BoxLayout(panel, BoxLayout.Y_AXIS));
frame.getContentPane().add(panel);  // Add panel to frame
```

---

#### Full Working Example: Adding a Text Field

```java
import javax.swing.*;
import java.awt.*;

public class Main extends JFrame {
  public static void main(String[] args) {
    Main frame = new Main();
    frame.setLayout(new FlowLayout());
    frame.setSize(new Dimension(500, 500));
    frame.setTitle("The Twilight Zone");
    frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

    JPanel panel = new JPanel();
    JLabel motto = new JLabel("Not Only of Sight... But of MIND");
    JTextField textField = new JTextField("Enter Name");
    textField.setBounds(10, 100, 150, 10);

    panel.add(motto);
    panel.add(textField);
    panel.setLayout(new BoxLayout(panel, BoxLayout.Y_AXIS));
    frame.getContentPane().add(panel);
    frame.setVisible(true);
  }
}
```

---

#### 4. `JButton` – Adding Buttons

* Used to **trigger actions** via event listeners.
* Creating and adding a button:

```java
JButton b = new JButton("Submit");
b.setBounds(50, 150, 100, 30);
panel.add(b);
```

* Add **action listener** to respond to clicks:

```java
b.addActionListener(new ActionListener() {
  public void actionPerformed(ActionEvent e) {
    String inputText = motto.getText();
    // Additional logic
  }
});
```

* You can also add listeners to `JTextField` elements.

---

#### 5. Tool Tips – Provide User Guidance

* Use `setToolTipText(String tip)` to show helpful text when users hover.
* Works with many GUI components:

```java
motto.setToolTipText("Complete the Twilight Zone Motto!");
b.setToolTipText("Click to Submit");
```

> Tool tips are critical for **clarifying** UI elements without cluttering the screen.

---

#### Lesson Summary

* `JTextField` enables **user input**.
* `JButton` provides **interactivity** via click events.
* `setToolTipText` improves **usability** with hover-based tips.
* All form elements are placed on a **`JPanel`**, which is added to a **`JFrame`**.
* `setBounds(x, y, width, height)` is used to **position and size** these elements.

### Section 13: Event-Driven Programming in Java

#### What Is Event-Driven Programming?

* Event-driven programming is centered around **user interactions**.
* Examples:

  * Clicking a **button**
  * Typing in a **text field**
  * Selecting a **checkbox**
* When an action occurs, it creates an **event**, and if programmed correctly, the application **responds** to that event.

> If your program responds to events, it’s considered **event-driven**.

---

#### Core Concepts

| Term               | Description                                                                     |
| ------------------ | ------------------------------------------------------------------------------- |
| **Event Object**   | The **object** that represents the occurrence of an event (e.g., button click)  |
| **Event Source**   | The **component** that triggers the event (e.g., `JButton`, `JCheckBox`)        |
| **Event Listener** | The **code that listens** for specific types of events and responds accordingly |

---

#### Common Event Listeners in Java

| Listener Type         | Description                                           |
| --------------------- | ----------------------------------------------------- |
| `ActionListener`      | Responds to button clicks or actions                  |
| `ItemListener`        | Detects changes in components like checkboxes         |
| `KeyListener`         | Listens for keyboard input                            |
| `MouseListener`       | Detects mouse clicks and activity                     |
| `MouseMotionListener` | Detects mouse movement                                |
| `WindowListener`      | Handles window events (open, close, etc.)             |
| `ContainerListener`   | Detects changes in containers like `JPanel`           |
| `ComponentListener`   | Reacts to changes in visibility, size, or movement    |
| `AdjustmentListener`  | Used with scrollbars or similar adjustable components |

---

#### Example 1: `ActionListener` for a Button

* Responds when a button is clicked.

```java
import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class Main extends JFrame {
  public static void main(String[] args){
    Main frame = new Main();
    frame.setLayout(new FlowLayout());
    frame.setSize(new Dimension(500, 500));
    frame.setTitle("The Twilight Zone");
    frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

    JPanel panel = new JPanel();
    JLabel motto = new JLabel("... Not only of sight, but of mind ...");
    JLabel lblUserName = new JLabel("Enter User Name");
    JTextField txtUserName = new JTextField(20);
    JButton b = new JButton("Submit");
    JLabel msg = new JLabel();

    panel.add(motto);
    panel.add(lblUserName);
    panel.add(txtUserName);
    panel.add(b);
    panel.add(msg);

    motto.setToolTipText("Complete the Twilight Zone Motto!");
    b.setToolTipText("Click to Submit");

    b.addActionListener(new ActionListener() {
      public void actionPerformed(ActionEvent e) {
        String userName = txtUserName.getText();
        msg.setText("User Name = " + userName);
      }
    });

    panel.setLayout(new BoxLayout(panel, BoxLayout.Y_AXIS));
    frame.getContentPane().add(panel);
    frame.setVisible(true);
  }
}
```

* When the user clicks the **Submit** button, the label is updated with the username.

---

#### Example 2: `ItemListener` for Checkboxes

* Listens for selection events (checked or unchecked):

```java
import javax.swing.*;
import java.awt.event.*;

public class Main implements ItemListener {
  JCheckBox pan, spatula;
  JLabel label;

  Main() {
    JFrame f = new JFrame("Spatula City!");
    f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

    label = new JLabel("Pick an Option");
    label.setSize(400, 100);
    label.setLocation(100, 5);

    pan = new JCheckBox("Pan");
    pan.setBounds(100, 100, 150, 50);

    spatula = new JCheckBox("Spatula");
    spatula.setBounds(100, 150, 150, 50);

    f.add(pan);
    f.add(spatula);
    f.add(label);

    pan.addItemListener(this);
    spatula.addItemListener(this);

    f.setSize(400, 400);
    f.setLayout(null);
    f.setVisible(true);
  }

  public void itemStateChanged(ItemEvent e) {
    if (e.getSource() == pan) {
      label.setText("You picked a Pan");
    }
    if (e.getSource() == spatula) {
      label.setText("That is the Right Choice!");
    }
  }

  public static void main(String[] args) {
    new Main();
  }
}
```

* When the user selects an option, the label is updated accordingly.

---

#### Lesson Summary

* Java Swing applications are built around **event-driven programming**.
* Key elements:

  * **Event Object** – represents the event itself
  * **Event Source** – the GUI component that generates the event
  * **Event Listener** – the code that responds to the event
* You can use listeners to respond to:

  * **Button clicks**, **text entry**, **checkbox selections**, **mouse/keyboard actions**, and more.
* Examples showed how to use:

  * `ActionListener` to respond to a button
  * `ItemListener` to respond to checkboxes

### Section 14: Graphical Tools in Java

#### Enhancing GUI Applications

* A GUI limited to just buttons and text fields lacks functionality and user engagement.
* Java Swing provides **versatile graphical tools** to enhance user interaction:

  * `JCheckBox` – for multiple selections
  * `JComboBox` – for single-choice drop-downs
  * `JRadioButton` with `ButtonGroup` – for exclusive selection
* Make sure to import Swing components:

```java
import javax.swing.*;
```

---

#### `JCheckBox` – Multiple Selections

* A `JCheckBox` lets users **select one or more options** independently.

```java
JCheckBox spatula = new JCheckBox("Spatula");
spatula.setBounds(100, 100, 500, 50);
```

* **Full Example**:

```java
import javax.swing.*;
public class Main {
  Main() {
    JFrame f = new JFrame("Check Boxes Emporium");
    f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

    JCheckBox spatula = new JCheckBox("Spatula");
    JCheckBox saucepan = new JCheckBox("Sauce Pan");
    JCheckBox spatula2 = new JCheckBox("Another Spatula!");

    spatula.setBounds(100, 100, 500, 50);
    saucepan.setBounds(100, 150, 500, 50);
    spatula2.setBounds(100, 200, 500, 50);

    f.add(spatula);
    f.add(saucepan);
    f.add(spatula2);

    f.setSize(400, 400);
    f.setLayout(null);
    f.setVisible(true);
  }

  public static void main(String[] args) {
    new Main();
  }
}
```

---

#### `JComboBox` – Drop-Down Selection

* Use `JComboBox` for a **single-choice menu**.

```java
String utensils[] = {"Spatula", "Sauce Pan", "Knife"};
JComboBox cb = new JComboBox(utensils);
cb.setBounds(50, 50, 175, 50);
```

* **Full Example**:

```java
import javax.swing.*;
public class Main {
  Main() {
    JFrame f = new JFrame("Combo Boxes!");
    f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

    String utensils[] = {"Spatula", "Sauce Pan", "Knife"};
    JComboBox cb = new JComboBox(utensils);
    cb.setBounds(50, 50, 175, 50);

    f.add(cb);
    f.setSize(400, 400);
    f.setLayout(null);
    f.setVisible(true);
  }

  public static void main(String[] args) {
    new Main();
  }
}
```

* Common `JComboBox` Methods:

| Method                    | Description                                  |
| ------------------------- | -------------------------------------------- |
| `addItem(Object item)`    | Adds a new item to the list                  |
| `removeItem(Object item)` | Removes an item from the list                |
| `setEditable(boolean)`    | Allows text editing in the combo box         |
| `addActionListener(...)`  | Adds an event listener to respond to changes |

---

#### `JRadioButton` + `ButtonGroup` – Exclusive Selections

* `JRadioButton` allows selection of **one item only** from a set.
* A `ButtonGroup` **groups radio buttons** so only one can be selected at a time.

```java
JRadioButton r1 = new JRadioButton("Spatula");
JRadioButton r2 = new JRadioButton("Sauce Pan");

ButtonGroup bg = new ButtonGroup();
bg.add(r1);
bg.add(r2);
```

* **Full Example**:

```java
import javax.swing.*;

public class Main {
  Main() {
    JFrame f = new JFrame("Button Groups");

    JRadioButton r1 = new JRadioButton("Spatula");
    JRadioButton r2 = new JRadioButton("Sauce Pan");
    JRadioButton r3 = new JRadioButton("Another Spatula");

    r1.setBounds(75, 50, 150, 30);
    r2.setBounds(75, 100, 150, 30);
    r3.setBounds(75, 150, 150, 30);

    ButtonGroup bg = new ButtonGroup();
    bg.add(r1);
    bg.add(r2);
    bg.add(r3);

    f.add(r1);
    f.add(r2);
    f.add(r3);

    f.setSize(300, 300);
    f.setLayout(null);
    f.setVisible(true);
  }

  public static void main(String[] args) {
    new Main();
  }
}
```

---

#### Understanding Constructors

* When you create:

  * `new JCheckBox("Spatula")`
  * `new JComboBox(array)`
  * `new ButtonGroup()`

  … you are using a **constructor** for that class.
* Constructors:

  * **Share the class name**
  * Can be **overloaded** (accept different arguments)

> Use your IDE’s built-in tools (e.g., **Javadoc**, **IntelliSense**) to explore these constructors and methods further.

---

#### Lesson Summary

* Java Swing provides several **graphical tools** to enrich GUI applications:

  * `JCheckBox` – For multiple, independent selections
  * `JComboBox` – For single-option drop-down lists
  * `JRadioButton` + `ButtonGroup` – For grouped, exclusive choices
* These components are added to a `JFrame`, and may be grouped using a `JPanel`.
* All positioning is done using `setBounds(x, y, width, height)`.
* Constructors are essential in creating these Swing components and follow the class naming convention.

### Section 13: Lesson Overview & Knowledge Required

#### Lesson Objective

* In this practical lesson, you will use **Java Swing utilities** to display output to the screen in a **user-friendly window**.

---

#### Skills & Knowledge Required

* You should be able to:

  * ✅ **Write and compile** Java code
  * ✅ **Import Java utilities** into your code
  * ✅ **Create new instances** of classes
  * ✅ **Add comments** to your code (both single-line and multi-line)

---

#### Java Version SE 11

* This lesson is written for **Java SE 11**.
* Please use this version to ensure compatibility with the example code.

---

#### Program Code – Displaying Output in a `JLabel`

```java
import javax.swing.*;
import java.awt.event.*;

public class Main {
  public static void main(String[] args) {
    JFrame frame = new JFrame("Swing Application");
    frame.setSize(500, 500);
    frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

    JLabel label = new JLabel("Programming Is Usually Taught By Examples");
    frame.getContentPane().add(label);

    frame.setLocationRelativeTo(null);
    frame.setVisible(true);
  }
}
```

---

#### Code Application – Use `JTextArea` Instead of `JLabel`

```java
import javax.swing.*;
import java.awt.event.*;

public class Main {
  public static void main(String[] args) {
    JFrame frame = new JFrame("Swing Application");
    frame.setSize(500, 500);
    frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

    JTextArea text = new JTextArea("Programming Is Usually Taught By Examples");
    frame.getContentPane().add(text);

    frame.setLocationRelativeTo(null);
    frame.setVisible(true);
  }
}
```

---

#### Follow-Up Questions

1. **Use `JOptionPane` to Get Input from the User**

```java
String motto = "Enter Name:";
JOptionPane optionpane = new JOptionPane();
frame.showInputDialog(optionpane, motto);
```

---

2. **What Happens if You Set `setSize(0, 0)`?**

* The window becomes **invisible or extremely small**.
* It may render as just a border or may not display at all.

---

3. **What Happens if `setDefaultCloseOperation()` Is Omitted?**

* Clicking the **X** won’t terminate the application.
* The program **continues running** in the background.
* In IDEs like NetBeans, you will see that the program is **still running** until manually stopped.

---

#### Lesson Summary

* You’ve learned how to build a **simple Swing GUI** using:

  * `JFrame`
  * `JLabel`
  * `JTextArea`
  * `JOptionPane`
* You also saw how window **size** and **close behavior** affect usability and performance.
