Look at  109 -> Ch2.md for more content

### Section 1: What Is an Abstract Data Type?

#### Understanding ADTs

An **Abstract Data Type (ADT)** is a **programming model** that defines a data structure **by its behavior**, not by its implementation. It includes:

* A **set of values**
* A **set of operations** that can be performed on those values

> Think of an ADT as defining **what** a data type does, but not **how** it does it.

For example, if you’re building a **server usage monitor**, you might define a `Time` data type to track when users log in and out — **without** needing to know how that time is stored or computed internally.

---

#### Key Principle: Encapsulation

**Encapsulation** (also known as **data hiding**) is the practice of **hiding the inner workings** of a data type and only exposing the necessary operations.

> The user of an ADT doesn’t need to understand the internal logic — just like you don’t need to know how a clock works to read the time.

This protects the internal data and ensures the ADT is used as intended.

---

#### Creating a Simple Time ADT in Java

Here’s an example using Java’s `java.time` package to define a simple `Time` ADT:

```java
import java.time.*;

public class Time {
    private int hour;
    private int minute;
    private int second;
    private LocalDateTime time;

    public Time(LocalDateTime time) {
        this.time = time;
    }

    public int getHour() {
        return time.getHour();
    }

    public int getMinute() {
        return time.getMinute();
    }

    public int getSecond() {
        return time.getSecond();
    }

    public static void main(String[] args) {
        Time time_logged = new Time(LocalDateTime.now());
        int this_hour = time_logged.getHour();
        System.out.println(this_hour);
    }
}
```

> This code prints the current hour using `LocalDateTime.now()`.

---

#### Representational Independence

Another important principle of ADTs is **representational independence**. This means an ADT should only do what it’s designed to do — and nothing else.

> A `Time` object should manage time — it shouldn’t also shuffle cards or play music.

Keeping behavior tightly coupled to purpose ensures **code clarity and reliability**.

---

#### Leveraging Abstraction with Interfaces

In many situations, an application might need to **retrieve time from multiple sources** — a company server, a public time API, etc.

Despite different sources, your ADT should always **behave the same** from the outside.

To accomplish this in Java, you use an **interface** to define the **"what"**, and then implement it using different classes for the **"how"**.

---

#### The `Time` Interface in Java

```java
interface Time {
    public int getHour();
    public int getMinute();
    public int getSecond();
}
```

> This interface defines the **contract**: every class that implements `Time` must provide these three methods.

---

#### Implementing the `Time` Interface

Here’s a class that implements `Time` using the public time API (via `LocalDateTime`):

```java
import java.time.*;

interface Time {
    public int getHour();
    public int getMinute();
    public int getSecond();
}

public class PublicTime implements Time {
    private LocalDateTime time;

    public PublicTime(LocalDateTime time) {
        this.time = time;
    }

    public int getHour() {
        return time.getHour();
    }

    public int getMinute() {
        return time.getMinute();
    }

    public int getSecond() {
        return time.getSecond();
    }

    public static void main(String[] args) {
        PublicTime time_logged = new PublicTime(LocalDateTime.now());
        int this_hour = time_logged.getHour();
        System.out.println(this_hour);
    }
}
```

> This version of `Time` uses `LocalDateTime` for its time source, but another version could pull time from a **company server** instead.

---

#### Why Interfaces Matter

Interfaces are **blueprints**. They allow you to **define behavior without locking down implementation**. This results in:

* **Cleaner architecture**
* **Greater flexibility**
* **Easier testing and maintenance**

Once an interface is defined, any class that implements it **must implement all its methods**. This guarantees that your ADT will always expose the **expected behavior**, regardless of how it works internally.

---

#### Lesson Summary

* An **Abstract Data Type (ADT)** defines a **data structure** by its **behavior**, not its implementation.
* Key principles include:

  * **Abstraction** — define what it does, not how
  * **Encapsulation** — hide internal details from the user
  * **Representational Independence** — methods should stay focused on their purpose
* In **Java**, ADTs are commonly implemented via **interfaces**.

  * Use the `interface` keyword to define behavior.
  * Use the `implements` keyword in a class to provide the actual logic.
* This model ensures that you can design programs where components are **modular**, **flexible**, and **easy to update or scale**.

### Section 2: Nested Classes in Java

#### What Is a Nested Class?

A **nested class** in Java is a **class defined within another class**. It behaves like any other member (such as variables or methods) and can be either:

* **Static** — behaves like a static member
* **Non-static** — tied to an instance of the outer class

> Think of a nested class as a **helper class** that logically belongs inside its enclosing class.

---

#### Defining `static`

When you mark a member of a class as **`static`**, it is no longer associated with a specific object. Instead, it becomes a **class-level member**, meaning it:

* Belongs to the **class itself**, not any instance
* Can be accessed without creating an object
* Is **shared** across all instances

This same logic applies to **static nested classes**.

---

#### Static Nested Class — Overview

A **static nested class** is:

* Defined **within another class** using the `static` keyword
* **Independent** of the outer class’s instance
* Accessed using the outer class name (e.g., `OuterClass.NestedClass`)

---

#### Basic Static Nested Class Example

```java
public class OuterClass {
    static class Nested {
        public void display() {
            System.out.println("from the nested class");
        }
    }

    public static void main(String[] args) {
        OuterClass.Nested object = new OuterClass.Nested();
        object.display();
    }
}
```

> Output:

```
from the nested class
```

**Key Points:**

* You do **not** need to instantiate `OuterClass` to use `Nested`.
* Access the nested class via `OuterClass.Nested`.

---

#### Why Use Static Nested Classes?

**Use static nested classes when:**

1. The inner class is **only relevant** to the outer class.
2. You **don't need access** to instance members of the outer class.
3. You want to keep your code **organized and modular**.

> They **act independently**, but are **loaded together**, improving memory efficiency and structure.

---

#### Practical Example — `Employee` and `OvertimeCalculator`

```java
public class Employee {
    private String name;
    private double basePay;

    public Employee(String name, double basePay) {
        this.name = name;
        this.basePay = basePay;
    }

    public double calculatePay(double hoursWorked) {
        return basePay * hoursWorked + 
            OvertimeCalculator.calculateOvertime(hoursWorked, basePay);
    }

    static class OvertimeCalculator {
        private static double overtimeRate = 0.5;

        public static void setOvertimeRate(double rate) {
            overtimeRate = rate;
        }

        public static double getOvertimeRate() {
            return overtimeRate;
        }

        public static double calculateOvertime(double hours, double base) {
            double overtimeHours = Math.max(0, hours - 40);
            return overtimeHours * base * overtimeRate;
        }
    }

    public static void main(String[] args) {
        System.out.println("The current overtime rate is " + 
            OvertimeCalculator.getOvertimeRate());

        Employee emp = new Employee("Kelly Kelly", 5.0);
        double salary = emp.calculatePay(45);
        System.out.println("The salary for " + emp.name + " is " + salary);
    }
}
```

> Output:

```
The current overtime rate is 0.5  
The salary for Kelly Kelly is 225.0
```

---

#### Key Features of Static Nested Classes

* Can be accessed without creating an instance of the outer class
* Cannot access **non-static members** of the outer class
* Encapsulates helper logic that is only relevant to the enclosing class
* Helps with **tight coupling** of related functionality

---

#### Lesson Summary

* A **static nested class** is defined inside another class using the `static` keyword.
* It behaves like a top-level class that is **namespaced** within its enclosing class.
* You do **not** need to instantiate the outer class to use the nested one.
* Static nested classes:

  * Cannot access non-static members of the enclosing class
  * Are useful for **packaging related classes together**
  * Help organize code for **readability and efficiency**

### Section 3: Inner Classes in Java

#### What Is an Inner Class?

An **inner class** (also called a **nested class**) is a **class defined within another class**. Inner classes are often used when the class they support is **only relevant to the outer class**.

> Think of inner classes as **tools or helpers** to their outer class.
> For example, `LogFileDetail` might exist only to support `LogFile`.

Inner classes support **encapsulation** (data hiding). For instance, marking an inner class as `private` restricts its use outside the outer class.

They also help with **readability and maintenance** — but should be used sparingly to avoid excessive complexity.

---

#### Basic Inner Class Example

```java
// Outer class:
public class LogFile {
    // Inner class:
    public class LogFileDetail {
        public void hello() {
            System.out.println("Inner Class!");
        }
    }
}
```

---

#### Types of Inner Classes

There are two main types of inner classes:

1. **Static Nested Classes**
2. **Non-Static Nested Classes** (regular inner classes)

---

#### Non-Static Nested Class

A non-static inner class is **tied to an instance** of the outer class. It has direct access to the outer class's members.

**Creating an instance:**

```java
public static void main(String[] args) {
    LogFile log = new LogFile();
    LogFile.LogFileDetail logDetail = log.new LogFileDetail();
}
```

> Notice how `new` comes **after** the outer class instance (`log.new`).

---

#### Accessing Outer Class Variables

```java
// Outer class:
public class LogFile {
    int counter = 17;

    // Inner class:
    public class LogFileDetail {
        public void hello() {
            System.out.println("Detail: " + counter);
        }
    }
}
```

**Main method:**

```java
public class MyMainClass {
    public static void main(String[] args) {
        LogFile log = new LogFile();
        LogFile.LogFileDetail logDetail = log.new LogFileDetail();
        logDetail.hello();
    }
}
```

> Output:
> `Detail: 17`

---

#### Local Classes

A **local class** is declared **inside a method**, not within a class.

```java
public class LogFile {
    void localMethod() {
        long logID = 2999993984L;

        // Local class
        class LocalClass {
            public void display() {
                System.out.println("Inside the local class: " + logID);
            }
        }

        // Create instance and call method
        LocalClass local = new LocalClass();
        local.display();
    }
}
```

> Local classes are accessible **only inside the method** where they're declared.

---

#### Static Nested Class

A **static nested class**:

* Can be used **without** an outer class instance
* **Cannot access** non-static members of the outer class

```java
public class LogFile {
    public static class LogFileDetail {
        public void hello() {
            System.out.println("Inner Class!");
        }
    }
}
```

**Main method:**

```java
public class Main {
    public static void main(String[] args) {
        LogFile.LogFileDetail detail = new LogFile.LogFileDetail();
        detail.hello();
    }
}
```

> Output:
> `Inner Class!`

---

#### Shadowing

If both the outer and inner class declare a variable with the **same name**, the **inner variable shadows** the outer one.

```java
public class LogFile {
    int counter = 17;

    public class LogFileDetail {
        int counter = 25;

        public void hello() {
            System.out.println("Outer: " + LogFile.this.counter);
            System.out.println("Inner: " + this.counter);
        }
    }
}
```

> Output:
> `Outer: 17`
> `Inner: 25`

---

#### Lesson Summary

* An **inner class** is a class defined inside another class.
* There are **non-static**, **static**, and **local** inner classes.
* **Non-static** inner classes:

  * Are tied to an instance of the outer class
  * Can access outer class variables directly
* **Static** nested classes:

  * Act like top-level classes
  * Must use a reference to access outer members
* **Local classes**:

  * Exist only within a method
* Use **`this`** or `OuterClass.this` to resolve **variable shadowing**.
