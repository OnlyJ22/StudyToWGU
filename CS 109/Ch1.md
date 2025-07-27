### Section 1: Introduction to Programming

#### What Is Programming?

* **Programming**: Writing instructions (called code) that tell a **computer what to do**.
* Computers are powerful but **useless without instructions** — they’re just **metal and plastic**.
* **Programmers** create the logic that enables computers to solve problems and perform tasks.

#### Roles of a Programmer

* **Analyze a problem** and break it into smaller steps.
* **Describe those steps** in a programming language the computer understands.
* Act as the **bridge between a problem and its automated solution**.

#### Importance of Programming

* Computers help solve problems — from **industrial automation** to **space travel**.
* Without programming, computers are just **“doorstops”** or **“boat anchors.”**
* Programming turns computers into **intelligent tools** by giving them **specific, logical instructions**.

#### Programming Analogy: Making Pancakes

* Telling a computer to make pancakes isn’t simple — it needs step-by-step **explicit instructions**.

* The robot (e.g., **Foobar**) must know:

  * What a **griddle**, **bowl**, and **spoon** are
  * Where to **find ingredients**
  * How to **mix**, **measure**, and **flip pancakes**

* The programmer must break this process into **tiny, clear steps** the robot can follow.

#### Key Concepts in Pancake Programming

* **Step decomposition**: Break the task down into actions like:

  * Heat griddle
  * Mix ingredients
  * Pour batter
  * Flip when ready
  * Serve and clean up

* **Language comprehension**: The robot understands only **programming languages**, so we must write instructions in one like **Python**, **Java**, or **C**.

#### What Makes a Program Run?

* **Programming Language**: Used to write the solution (e.g., Python, Java, C)
* **Compiler or Interpreter**:

  * Converts written code into **machine-executable instructions**
  * Required to **run the program**
* **Programming Tools**:

  * Software like **Replit** or full-featured **IDEs**
  * May include **AI features** to debug or suggest code

#### Key Skills for Programming

* Ability to **analyze problems logically**
* Ability to **translate real-world processes into code**
* Understanding:

  * **Algorithms**
  * **Math and logic**
  * The **5 basic types of programming instructions**

#### Summary

* Programming enables computers to **solve problems automatically**.
* A programmer must:

  * **Understand the problem**
  * **Break it into steps**
  * **Write those steps as code**
* Tools like **compilers** and **IDEs** make writing and testing code easier.
* Programming is the reason computers do anything useful at all.


### Section 2: Five Basic Programming Elements

#### Overview

* Programming is like building with blocks — with a small number of elements, you can create highly complex systems.
* There are **five basic elements** found in nearly every program:

  * **Input**
  * **Output**
  * **Loops and Conditionals**
  * **Mathematical Operations**
  * **Variables and Data Structures**

#### Input

* **Input**: Getting **data and commands** into the computer.
* Examples: Keyboard, touchscreen, text file, or data from another program.
* Input is **required in every program**.
* **ATM Example**:

  * You insert your **ATM card** → contains ID info
  * You enter your **PIN** → verifies your identity
  * You choose **Fast Cash** → system receives your request

#### Arithmetic

* **Arithmetic operations** perform math on input or stored data.
* May include:

  * **Addition, subtraction, multiplication, division**
  * **Complex mathematical functions**
* **ATM Example**:

  * Checks your account balance
  * Subtracts `$40` for withdrawal
  * This step processes your input and updates your balance

#### Output

* **Output**: Delivering the result of a program.
* Can be:

  * Text, graphics, sound, printed data
  * Data passed to another system
* **ATM Example**:

  * Dispenses `$40` in cash
  * Prints a receipt with withdrawal details and new balance

#### Looping and Conditionals

* **Loops**: Repeat a set of instructions until a condition is met.
* **Conditionals**: Decide what to do based on whether something is **true** or **false**.
* Used in:

  * Data processing
  * Control flow in algorithms

**Two types of loops**:

* **Event-controlled loops**:

  * Run until a specific **event** occurs (e.g., reaching end of file)
* **Counter-controlled loops**:

  * Run a **fixed number of times**

**Example: Event-Controlled Loop**

```bash
while read name
do {
  print(name)
}
done < namelist
```

* Reads each name from `namelist` and prints it, stopping at end of file.

**Example: Counter-Controlled Loop**

```bash
count=10
while (count >= 0) {
  print(count)
  (( count-- ))
}
print("Hello, World!")
```

* Prints numbers 10 to 0, then prints “Hello, World!”

#### Variables and Data Structures

* **Variables**: Store **changing information** (e.g., account balances, counters)
* **Data Structures**: More complex storage (e.g., arrays, lists, dictionaries)
* In loops:

  * Variables keep track of progress
  * Data can change with each iteration
* **ATM Example**:

  * Your balance is a variable that updates with every transaction

#### Summary

* The **five basic elements of programming** are:

  * **Input**: Get data and commands into the program
  * **Output**: Show or return results
  * **Arithmetic**: Perform calculations
  * **Looping & Conditionals**: Repeat actions and make decisions
  * **Variables & Data Structures**: Store and manage changing data
* Every program uses **input and output**.
* Arithmetic enables logic and data manipulation.
* Loops and conditionals provide **control and flexibility**.
* Variables let data **persist and evolve** during program execution.

### Section 3: Comments in Java Programming

#### What Are Comments?

* **Comments** are **notes within code** meant for **human readers**, not the computer.
* **Ignored by the compiler**, so they don’t affect how the program runs.
* Useful for:

  * Explaining **what the code does**
  * Leaving **reminders** for yourself
  * Helping **other developers** understand your logic

#### Why Use Comments?

* Months later, it’s easy to **forget** what parts of code do.
* Comments help programmers **remember their logic** and **plan future edits**.
* They act as **internal documentation** directly within the code.

---

#### Single Line Comments

* Start with **`//`** — anything after it on the same line is treated as a comment.
* Example:

```java
//my first comment
public class HelloWorld {
  public static void main(String[] args) {
    System.out.println("Hello World!");
  }
}
```

* Can be **nested inside blocks** of code (still ignored by compiler):

```java
public class HelloWorld {
  //my nested comment
  public static void main(String[] args) {
    System.out.println("Hello World!");
  }
}
```

* Multiple single-line comments can be stacked:

```java
//my first comment
public class HelloWorld {
  //my second comment
  public static void main(String[] args) {
    //my third comment
    System.out.println("Hello World!");
  }
}
```

---

#### Multi-Line Comments

* Used for longer explanations, like **paragraphs**.
* Begin with `/*` and end with `*/`.
* Example:

```java
/* This is the beginning of a
multi-line comment
this is the end */
public class HelloWorld {
  public static void main(String[] args) {
    System.out.println("Hello World!");
  }
}
```

* Can be placed **inside code blocks**:

```java
public class HelloWorld {
  /* The Beginning
  This is my first computer program
  written entirely in Java.
  I am so proud of myself
  The End */
  public static void main(String[] args) {
    System.out.println("Hello World!");
  }
}
```

* You **can** nest single-line comments inside multi-line ones, but **cannot** nest one multi-line inside another:

```java
public class HelloWorld {
  /* The Beginning
  of a multi-line comment
  // This is a nested single line comment
  this is the End */
  public static void main(String[] args) {
    System.out.println("Hello World!");
  }
}
```

---

#### Documentation Comments

* Also called **doc comments**.
* Begin with `/**` and end with `*/`.
* Used to generate **external documentation** using `Javadoc` (part of JDK).
* Example:

```java
/** This is an example of a
documentation comment */
```

* Javadoc reads these comments and **creates a reference guide** for your code — like a **user manual**.
* Common in professional environments and open-source projects.

---

#### Summary

* **Comments** are essential for making your code **understandable** and **maintainable**.
* There are **three types of comments in Java**:

  * **Single-line comments**: `// comment`
  * **Multi-line comments**: `/* comment */`
  * **Documentation comments**: `/** doc comment */`
* **Javadoc** uses documentation comments to generate **external documentation** for Java programs.
* Well-commented code improves collaboration, debugging, and long-term usability.

### Section 4: Requirements Gathering in Software Development

#### What Is Requirements Gathering?

* **Requirements gathering** is the process of identifying what a program needs to do before writing any code.
* It ensures both the **developer and the customer** are aligned on the program's objectives.
* The information collected is used to create a **requirements document**, reviewed by the customer.

#### Four Requirements Gathering Tools

* The following tools are used to collect program requirements:

  * **Document Review**
  * **Observation**
  * **Meetings/Interviews**
  * **Surveys**

---

#### Case Study: The Pancake House

* Fred is considering using the Foobar program for his grill-bot, **Foober**, to replace his retiring cook.
* Before starting development, it's critical to determine **exactly what Fred wants Foober to do**.

---

#### Document Review

* The **menu** provides a list of dishes Foober must learn to prepare.
* **Recipes** outline the necessary ingredients, preparation, and cooking steps.
* This helps define:

  * **What dishes** Foober must cook
  * **How to prepare** each item

---

#### Observation

* Observing the current cook reveals tasks not captured by documents:

  * Cooks pancakes and **other grill items** (e.g., bacon, sausage, eggs)
  * **Plates and garnishes** each dish
  * **Places orders** at the pickup station and **notifies servers**
  * **Does not** perform prep work (e.g., mixing batter, slicing fruit)

* Observation clarifies **real-world responsibilities** and workflow.

---

#### Meetings and Surveys

* **Meetings** with Fred help define:

  * Project scope
  * Timeline (**3 months** before Foober arrives)
  * Budget considerations

* **Customer surveys** gather feedback on:

  * What customers **like/dislike** about the menu
  * Potential **menu updates** before automating the process

---

#### The Requirements Document

* A **draft requirements document** is prepared to summarize findings and define expectations.
* Fred will **review and comment** on the draft before finalization.

**Preliminary Requirements Outline:**

* Foober must:

  * Know how to make each pancake dish on the menu
  * Prepare other grill items (e.g., eggs, sausage, bacon)
  * Plate and garnish dishes appropriately
  * Place completed orders at the pickup station
  * Notify the correct server

* Foober **will not**:

  * Mix pancake batter
  * Perform prep tasks (e.g., slicing fruit, whipping cream)

* Additional documentation will include:

  * Detailed list of pancake dishes
  * Descriptions of other grill items
  * Instructions for plating and garnishing
  * Process for placing and notifying orders

---

#### Summary

* All **four tools** were used to draft requirements for Foober:

  * **Document Review**: Examined menu and recipes
  * **Observation**: Watched the grill cook in action
  * **Meetings**: Discussed expectations with Fred
  * **Surveys**: Collected customer opinions

* A **draft requirements document** was created and given to Fred for feedback.

* Next step: **Requirements validation and review** to ensure accuracy and completeness.


### Section 5: Writing Pseudocode

#### What Is Pseudocode?

* **Pseudocode** is a **plain English description** of the steps a program will follow.
* It’s not a programming language, but it mimics programming **logic and structure**.
* Used to:

  * Plan the **logic** of a program
  * Help **non-programmers** understand how a program works
  * Prepare for writing real **code** in any language

#### Steps to Writing a Program

1. Understand the problem you are trying to solve
2. Design a solution
3. Draw a flow chart
4. Write pseudocode
5. Write actual code
6. Test and debug
7. Test with real-world users
8. Release the program
9. Iterate the steps for future versions

---

#### Why Use Pseudocode?

* Programming languages have **complex syntax**.
* Pseudocode lets you:

  * Focus on **logic**, not language-specific details
  * Think through each step clearly
  * Communicate your ideas easily with others

---

#### Pseudocode Example

**Scenario**: A bank customer uses an ATM to withdraw \$100.

```plaintext
Display "Enter withdrawal amount"
Read amount
If amount <= balance then
  Subtract amount from balance
  Dispense cash
  Print receipt
Else
  Display "Insufficient funds"
End if
```

* Reads like regular English
* Uses **programming constructs** like `if`, `else`, and `then`
* Emphasizes **one action per line**

---

#### Key Characteristics of Pseudocode

* **Each line = one instruction**
* Uses **action verbs**: `read`, `calculate`, `print`
* Shows **control logic**: `if`, `else`, `while`, etc.
* Avoids syntax from specific programming languages

---

#### Guidelines for Writing Pseudocode

**Guideline 1: One Step per Line**

```plaintext
Read account balance
Read withdrawal amount
If withdrawal amount <= account balance then
  Subtract withdrawal amount from balance
  Dispense cash
End if
```

* Avoid combining multiple actions into a single step

---

**Guideline 2: Maintain Logical Order**

Incorrect pseudocode:

```plaintext
Calculate new balance
Dispense cash
```

Correct order:

```plaintext
Dispense cash
Calculate new balance
```

* Computers follow instructions **exactly in order**, so sequencing matters

---

**Guideline 3: Leave Out Unnecessary Details**

```plaintext
If withdrawal is approved then
  Deduct amount (fees calculated later)
  Dispense cash
End if
```

* Skip fine details like fee calculations until later in development

---

#### Summary

* **Pseudocode** helps structure your thinking and logic before writing real code.
* It is:

  * **Readable by humans**
  * **Ignored by compilers**
  * **Not language-specific**
* Follow these **three guidelines**:

  * Write one instruction per line
  * Maintain logical order
  * It's okay to leave out minor details for clarity

### Section 6: Flowchart Symbols in Programming

#### What Are Flowchart Symbols?

* **Flowchart symbols** are **specific shapes** used to create a **visual representation** of a software program.
* These symbols represent different **steps, actions, or decisions** in a program’s logic.
* Just like a **stop sign** communicates an action without words, flowchart symbols provide a **universal language** for programmers.

---

#### Functions of Flowchart Symbols

* Each flowchart symbol serves a **specific function** in mapping out program logic:

  * **Start/End Symbol**: Indicates the **beginning** or **end** of a program
  * **Process Symbol**: Represents a **task or operation** (e.g., calculating values)
  * **Input/Output Symbol**: Used for **entering data**, **displaying** on screen, or **printing**
  * **Display Symbol**: Indicates that information is being **shown to the user**
  * **Decision Symbol**: Used for **if/else logic**, where a decision must be made
  * **Connector Symbol**: Indicates a **jump in the flow**, allowing you to connect chart sections with a number

---

#### Example: Displaying Your Name

**Basic Flowchart Steps:**

1. Start
2. Input name
3. Display name
4. End

This simple program allows a user to enter their name, and then the computer displays it on screen — visually represented with input/output and display symbols.

---

#### The Decision Symbol

* Used to model **conditional logic**:

  * Example: `If grade >= 70, display "Passing"; else, display "Failing"`
* Helps direct the program flow based on **true/false outcomes**

---

#### The Connector Symbol

* Used when:

  * You need to **break the flow** (e.g., due to limited space)
  * You’re continuing the process on a **different part of the chart**
* Contains a **number or label** to indicate **exit/re-entry** points in logic

---

#### Benefits of Using Flowchart Symbols

* **Prepares you before writing code**
* Helps **visualize logic and sequence**
* Makes your program:

  * **Easier to understand**
  * **Less error-prone**
  * **Faster to troubleshoot**

---

#### Summary

* **Flowchart symbols** simplify complex logic into **visual diagrams**.
* Each symbol has a **unique meaning** and purpose:

  * **Start/End**: Beginning or end of the program
  * **Process**: Operation or task
  * **Input/Output**: Receiving or displaying data
  * **Display**: Outputs shown to the user
  * **Decision**: Conditional logic (yes/no)
  * **Connector**: Jump between different flowchart sections
* A well-drawn flowchart makes the **program logic clear** before any code is written.

---

#### Key Terms

* **Flowchart symbols** – Shapes used to visually represent program logic
* **Start/End symbol** – Indicates the start or finish of a program
* **Process symbol** – Represents an instruction or function
* **Input/Output symbol** – Indicates data being received or displayed
* **Display symbol** – Represents on-screen output to the user
* **Decision symbol** – Models conditional (if/else) logic
* **Connector symbol** – Connects different parts of a flowchart for clarity


### Section 7: Writing a Software Program

#### Steps to Writing a Program

* **Understand the problem** you’re trying to solve.
* **Design a solution** to address the problem.
* **Draw a flow chart** to visually map the solution.
* **Write pseudo-code** that outlines the logic in simple terms.
* **Write code** using a programming language.
* **Test and debug** to find and fix issues.
* **Test with real-world users** to ensure it behaves correctly.
* **Release the program** for general use.
* **Iterate the steps** to update or improve the software.

#### Writing Code

* Code is a **list of instructions** a computer can execute.
* Written in **plain text** and saved with a **specific file extension** (e.g., `.py` for Python).
* **Compilers** read the text; extra formatting causes **syntax errors**.
* While code can be written in a **basic text editor**, using a **code editor** or **IDE** is much more effective.

#### The Purpose of a Code Editor

* Just as a **word processor** helps you write better English, a **code editor** helps you write better code.
* A **code editor** or **IDE** provides tools like:

  * **Syntax checking**
  * **Auto-formatting**
  * **Error detection**
  * **Testing and debugging tools**

#### What Is an IDE?

* An **IDE (Integrated Development Environment)** is a software application made specifically for coding.
* It often supports multiple programming languages.
* Think of it as a **specialized word processor** for programmers.
* Helps you **format**, **run**, **test**, and **debug** your code in one place.

#### Syntax Highlighting

* A feature in IDEs where **different parts of the code appear in different colors**.
* Makes it easier to distinguish:

  * **Keywords** (e.g., `for`, `in`, `print`)
  * **Variables**
  * **Strings**
* **Improves readability** but doesn’t affect how the code runs.
* Purely for **human understanding** — compilers ignore colors.

#### Syntax Checking and Autocompletion

* IDEs check code for **syntax errors**, similar to **spell check** in writing.
* They **highlight errors** and **show where** they occur.
* **Autocompletion (intelligent code completion)** helps:

  * Suggest likely keywords or variable names as you type.
  * Reduce **typing time** and **typos**.
  * Offer **multiple suggestions**, not just one.

#### Online Compilers

* Useful for quick code writing, testing, and collaboration — especially for **students or remote teams**.
* Examples include **Replit** ([https://replit.com/](https://replit.com/)\~).
* Online compilers also offer:

  * **Syntax highlighting**
  * **Autocompletion**
  * Ability to **export code** into full IDEs

#### Testing Code

* Even if code is **free of syntax errors**, it must be **tested** to ensure it behaves correctly.
* Testing involves:

  * Creating **sample input files**
  * Running the program
  * Checking if the **output is correct** and **formatting is accurate**
* Start with **simplified test data**, then move to **real-world data**.

#### Debugging

* A **bug** is a defect that stops code from working properly.
* **Debugging** is the process of finding and fixing bugs.
* Reading through code manually can be difficult, especially with **thousands of lines**.
* IDEs often include a **debugger**, which:

  * Helps **step through code** one line at a time
  * Shows **where things go wrong**
* While debuggers identify **where the error occurs**, **you still have to fix it** yourself by understanding the logic.

#### Summary

* A **code editor or IDE** makes writing and testing code easier and more efficient.
* **Syntax highlighting**, **autocompletion**, and **debuggers** are powerful features that improve clarity and reduce errors.
* Once syntax errors are resolved, programs must still be **tested** to ensure they work correctly.
* **Debugging tools** allow you to locate and resolve logical issues in code quickly and systematically.

### Section 8: Debugging, Compiling, and Executing Code

#### Writing Code

* **Code** is a **list of instructions** a computer can execute.
* Written using **high-level programming languages** such as **Python**, **Java**, or **C++**.
* Though possible in a **basic text editor**, code is best written in an **IDE (Integrated Development Environment)**.
* Like a word processor for documents, an IDE helps with:

  * **Syntax checking**
  * **Code formatting**
  * **Running and debugging programs**
* IDEs may be **locally installed** or **cloud-based** for online access.

#### Testing and Debugging

* A program with **no syntax errors** can be **executed**, but that doesn’t guarantee correctness.
* **Testing** ensures the program behaves as intended.
* For example, when processing a **payroll file**:

  * Does the output file have the correct data and format?
  * Were all lines processed correctly?
  * Are calculations accurate?
* If output is wrong, the program likely contains a **bug** — an error in the logic or flow.
* **Debugging** is the process of identifying and removing bugs.
* While reading through thousands of lines of code is possible, it’s inefficient.
* A **debugger** (a tool within most IDEs) helps:

  * **Walk through code line-by-line**
  * **Observe variables and behavior**
  * **Identify where execution breaks down**
* Debuggers point out **where** the issue is, but not **how to fix it**.

#### Machine Code vs. High-Level Languages

* Computers understand only **machine code**, written in **binary (1s and 0s)**.
* An example of machine code:

  * `10010101100101001111101010011011100101`
* This is **unreadable for humans**, so we use **high-level languages** instead.
* **High-level languages** use familiar **English and math-like syntax** (e.g., `print("Hello")`).
* Common high-level languages:

  * **C++**, **Java**, **Fortran**, **Python**
* Since computers can’t run high-level code directly, it must be **translated** into machine code.

#### Compiler

* A **compiler** converts **entire high-level programs** (source code) into **machine code** before execution.
* The output is a **compiled file**, often with an `.EXE` extension.
* Steps:

  * Write source code → Compile → Run the resulting executable.
* Benefits:

  * **Fast execution**
  * Code can be **run repeatedly without re-compiling**
* Examples of compiled languages:

  * **C**, **C++**, **C#**, **COBOL**, **Fortran**

#### Interpreter

* An **interpreter** translates **source code line-by-line** during execution.
* Each line is read, translated, and executed on the spot.
* No standalone executable is created — code must be interpreted **every time** it runs.
* Benefits:

  * **Immediate feedback**
  * Easier for **experimentation and learning**
* Examples of interpreted languages:

  * **Python**, **JavaScript**, **Perl**, **Ruby**

#### Compiled vs. Interpreted

* **Compiled programs**:

  * Faster execution
  * Must compile before running
  * Ideal for large-scale, performance-critical applications
* **Interpreted programs**:

  * Slower execution
  * Flexible and interactive
  * Better for scripting and rapid development

#### Summary

* An **IDE** assists with writing, testing, and debugging code.
* Once syntax errors are fixed, the program must be **tested** to ensure it performs as expected.
* **Debuggers** help locate bugs efficiently.
* Computers understand only **machine code**, so high-level languages must be **translated**.
* A **compiler** translates all code at once before execution.
* An **interpreter** translates code line-by-line during execution.
* Choosing between a **compiler or interpreter** depends on speed, flexibility, and project requirements.

### Section 9: A Brief Overview of Java

#### What Is Java?

* **Java** is one of the **most widely-used programming languages**, first released on **January 23, 1996**.
* Known for being **beginner-friendly**, **cross-platform**, and **high-performing**.
* Java can run on **virtually any OS and hardware** due to its flexibility.
* It’s not just a language — **Java is also a platform**, powered by the **Java Virtual Machine (JVM)**.

#### The Role of the Java Virtual Machine (JVM)

* Java code runs on the **JVM**, which allows it to be executed on different devices without rewriting code.
* The JVM acts as an intermediary between the **Java code** and the **hardware/OS**.
* Because of the JVM, Java programs are **"write once, run anywhere."**

#### Java and Android

* **Android**, the world’s most widely used mobile OS, was largely built using Java.
* Companies like **Google** and **Amazon** rely on Java to create robust mobile and enterprise applications.
* Java’s compatibility and power made it integral to **Android's rise to global dominance**.

---

#### Getting Started with Java

* To start coding in Java, you need either:

  * An **online compiler** (e.g., Replit)
  * A **fully installed development environment** (IDE + JDK)

#### Using Replit (Online Compiler)

* Visit: [https://replit.com/\~](https://replit.com/~)
* Under **Create**, select **Java**.
* Click **+ Create Repl** to start a new project (Java 11).
* A **Hello World** program will be auto-loaded; click **Run** to test it.
* Output appears on the right — great for quick coding and learning.

---

#### Installing Java Locally (JDK + IDE)

##### Step 1: Install the Java SE Development Kit (JDK)

* Download link: [https://www.oracle.com/java/technologies/javase-jdk11-downloads.html](https://www.oracle.com/java/technologies/javase-jdk11-downloads.html)
* Choose the correct installer for your OS.
* **Accept the license agreement**, then download and install using default options.
* The **JDK** includes all the **core Java files** needed to start writing Java code.

##### Step 2: Install an IDE (Eclipse)

* Java code requires a **code editor and compiler**, which an IDE provides.
* **Eclipse IDE** is a popular, full-featured environment for Java development.
* Download Eclipse: [https://www.eclipse.org/downloads/eclipse-packages/](https://www.eclipse.org/downloads/eclipse-packages/)
* Select your **OS version**, install Eclipse using default options.
* Eclipse requires **Java 11 or newer**, which is why you installed the JDK first.

#### Why Use an IDE?

* An IDE provides a **graphical user interface (GUI)** to:

  * **Write** and **edit** Java code
  * **Compile** code into executable form
  * **Debug** and identify code errors
* Makes Java development **faster, easier, and more professional**.

---

With the **JDK** and **Eclipse IDE** installed, you’re now ready to start coding in **Java** — a language that's powerful, portable, and used around the world.

### Section 10: What Is Java Programming?

#### Java Overview

* **Java** is a **programming language** used to give **instructions to a computer**.
* You can use it to create **computer programs** that are compiled and then **executed** by the computer.
* A **Java compiler** translates Java code into **machine code** the computer understands.
* You can use either:

  * A **local compiler**
  * A **free online compiler** like **Replit**

#### Compiling Code

* **Compiling** is the process of converting **Java code** (written by humans) into **machine code** (understood by computers).
* All programming languages must be **compiled** before they can run.
* In **Replit**, the **Run button** handles compiling and execution automatically in the background.

#### Hello World Java Program

```java
/*
* The HelloWorld Java program
* prints "Hello World!" on the computer screen
*/
public class Main {
  public static void main(String[] args) {
    System.out.println("Hello, World!");
  }
}
```

#### Components of the Hello World Program

* **Comments**:

  * Written between `/*` and `*/`
  * Ignored by the compiler
  * Help **humans understand the code**

* **Program Name**:

  * Defined using `public class Main`
  * In Replit, the class **must be named `Main`**

* **Main Method**:

  * Required in every Java program:

    ```java
    public static void main(String[] args)
    ```
  * Tells Java where the **program starts**
  * Must be written **exactly** — missing parts (like `String[] args`) will cause **errors**

* **Print Method**:

  * `System.out.println("Hello, World!");` displays output
  * You can modify the message:

    ```java
    System.out.println("Welcome, World!");
    ```

#### Java Syntax

* **Syntax** refers to the **rules** of how Java code must be written.
* Statements must end with a **semicolon (`;`)**.
* Missing a semicolon results in a **syntax error**.
* Example of incorrect code:

  ```java
  System.out.println("Hello, World!")
  ```
* This will **fail to compile** due to the missing `;`.

#### Summary

* **Java** lets you create programs by writing **human-readable instructions**.
* A **compiler** is required to **translate and run** the program.
* Each Java program must have:

  * A **main class**
  * A **main method** with the correct syntax
* Use `System.out.println()` to **display output**.
* Follow correct **syntax rules** — even small mistakes like missing semicolons will prevent your program from working.

public static void main(String[] args)

### Section 11: Public Static Void Main in Java

#### What Is `public static void main`?

* **`public static void main`** is the **entry point** of every standard Java application.
* It’s the **method** where the Java Virtual Machine (JVM) begins execution.
* Each keyword in this line has a **specific purpose**, and none of them are optional for the program to compile and run properly.

#### `public`

* Makes the **main method accessible** from **anywhere** in the application.
* Required so that the **JVM can call the method** when starting the program.
* You could write `static public`, but **`public static` is the common convention**.

#### `static`

* Declares the method as **belonging to the class**, not to an instance of the class.
* Allows the JVM to **run the method without creating an object** of the class.
* Needed because **`main` must run before any objects are instantiated**.

#### `void`

* Indicates that the method **does not return any value**.
* The program **starts** from this method but doesn’t **return anything** to the JVM.
* Other methods in Java can return values, but the `main` method cannot.

#### `main`

* The **name of the method** that serves as the **starting point** of the application.
* Every Java program must include a `main` method or it will **fail to compile**.
* All other methods and functionality are usually **called from this method**.

#### `String[] args`

* **`args`** is a parameter passed to the `main` method — it is an **array of strings**.
* These values are **passed from the command line** when running the program.
* Example:

  ```bash
  java ProgramName Dave Sally
  ```

  In this case, `args` would contain `["Dave", "Sally"]`.

#### Why Is It All Necessary?

* **Each keyword** in `public static void main(String[] args)` plays a **critical role**:

  * `public`: makes it **accessible**
  * `static`: makes it **runnable without creating an object**
  * `void`: specifies **no return value**
  * `main`: is the **JVM's entry point**
  * `String[] args`: allows **parameter input** from the command line
* Omitting or miswriting any part will result in **compilation or runtime errors**.

#### Summary

* `public static void main(String[] args)` is the **core method** in every Java application.
* It serves as the **starting point** for program execution and can **accept parameters** for command-line processing.
* Every keyword in this method declaration is **required** and plays a **specific, non-negotiable role**.
* Understanding each part ensures you know **how and why Java programs run** the way they do.

### Section 12: Java Statements

#### What Are Java Statements?

* **Java statements** are **instructions** that tell the computer **what to do**.
* Every Java statement must **end with a semicolon (`;`)**, unless it opens a **block of code using curly brackets `{}`**.
* A **basic example** of a Java statement is an **assignment**:

  ```java
  double entryFee = 15.75;
  ```

#### Java Methods

* A **Java method** is a **block of code** that performs a specific **task**.
* Methods are often used to **reuse logic** like printing messages:

  ```java
  System.out.println("Line 1");
  System.out.println("Line 2");
  ```
* Each `System.out.println()` is a **statement**, and each ends with a **semicolon**.

#### String Statement Example

* Java also allows **string declaration**:

  ```java
  String entryCode = new String();
  ```
* This statement **creates a string object** and assigns it to a variable.

#### Java Exceptions to the Semicolon Rule

* **Control structures** like `if`, `while`, and `for` do **not require semicolons** at the end of their declarations.
* However, the **statements inside their curly brackets must** end in semicolons.

#### If Statement

* An **if statement** checks if a condition is true:

  ```java
  if (ticker > 15) {
    System.out.println("Over the limit!");
  }
  ```
* The **code block** starts with `{` and ends with `}`, but the **print statement ends with a semicolon**.

#### While Statement

* A **while loop** repeats a block of code **while a condition is true**:

  ```java
  while (continueLoop = true) {
    if (ticker > 15) {
      System.out.println("Over the limit!");
      continueLoop = false;
    }
  }
  ```
* Statements **inside both the `while` and `if` blocks** are terminated with semicolons.

#### For Loop Statement

* A **for loop** repeats a task a **specific number of times**:

  ```java
  for (counter = 1; counter < 15; counter++) {
    System.out.println("Counter = " + counter);
  }
  ```
* The **loop header** uses **semicolons** to separate initialization, condition, and update expressions.
* The **body of the loop** still uses semicolons to terminate statements.

#### Summary

* **Java statements** are instructions like **assignments**, **method calls**, and **control flows**.
* Statements **must end in semicolons**, unless they are control structures like `if`, `while`, or `for` — which use **brackets**.
* Examples include:

  * **Assignment statements** (`double price = 10.5;`)
  * **String declarations** (`String name = new String();`)
  * **If statements**
  * **While loops**
  * **For loops**
* The key is: **Statements inside code blocks still require semicolons** even if the block itself doesn’t.

### Section 13: Code Application in Java

#### Multi-Line Comments

* A **multi-line comment** is used to describe the **purpose** of a program or method.
* It begins with `/*` and ends with `*/`.
* It is useful for:

  * **Program documentation**
  * **Version tracking**
  * **Explaining major logic blocks**

```java
/*
This is my first Java program.
It displays Hello World.
Version 1.1 adds a new line of text,
a variable and a for loop.
I am very proud of this program!
*/
```

#### Printing Text

* To **display a message** on a new line, use:

  ```java
  System.out.println("This is my first Java program");
  ```
* The `ln` in `println` causes a **line break** after printing.
* Use `System.out.print()` if you **do not** want a new line after the message.

#### Full Java Program with Output

```java
/*
This is my first Java program.
It displays Hello World.
Version 1.1 adds a new line of text,
a variable and a for loop.
I am very proud of this program!
*/
class Main {
  public static void main(String[] args) {
    int userCount = 10;
    for (int i = 0; i < userCount; i++) {
      System.out.println("Hello world!");
      System.out.println("This is my first Java program");
    }
  }
}
```

* This program prints:

  * `"Hello world!"`
  * `"This is my first Java program"`
* Repeats both lines **10 times**, using a **for loop** controlled by `userCount`.

#### Single-Line Comment

* A **single-line comment** starts with `//`.
* Used for **brief explanations** beside or above a line of code.

```java
// Below is the main program that will display the results
```

#### Declaring a Variable

* To declare an **integer variable** and assign it a value:

  ```java
  int userCount = 10;
  ```
* This variable controls the **loop iteration count**.

#### Styling Your Code

* Use **consistent indentation** for readability.
* Separate **methods and logic blocks** with white space.
* Name variables meaningfully:

  * Avoid vague names like `x1`, `temp2`
  * Use names like `userCount`, `totalSum`
* A well-styled program is:

  * **Easier to debug**
  * **Easier for others to read**
  * **Easier to maintain**

#### Summary

* Java supports **multi-line and single-line comments** for documentation.
* **Print statements**, **variables**, and **loops** form the building blocks of a Java program.
* A **well-structured**, **styled** program is essential for readability and collaboration.
* Practice good habits early — **readability is as important as functionality**.
