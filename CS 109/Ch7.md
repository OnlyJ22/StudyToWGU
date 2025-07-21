### Section 1: A World of Objects

---

#### Object-Oriented Design Overview

Object-Oriented Design (OOD) structures programs using **objects**, which are instances of **classes**. Everything around us — trees, shrubs, animals — can be modeled as objects in a program.

OOD is based on **five core principles**:

* Classes and Objects
* Encapsulation (Data Hiding)
* Inheritance
* Polymorphism
* Interfaces and Methods

---

#### Classes and Objects

* A **class** is a **blueprint** or **template**. Example: `Maple` is a class.
* An **object** is an **instance** of a class. Example: `Maple maple = new Maple();`
* Every object created from a class contains the properties and behaviors defined in that class.

---

#### Inheritance

* Inheritance allows a **child class** to reuse fields and methods from a **parent class**.

* Example:

  * `Tree` is the parent class
  * `Evergreen` inherits from `Tree`
  * `Pine` inherits from `Evergreen`
  * `RedPine` inherits from `Pine`, and therefore also from `Tree`

* Inheritance creates a **class hierarchy**, allowing reuse and logical structure.

---

#### Encapsulation

* **Encapsulation** means **hiding internal details** and only exposing necessary parts.
* Attributes like `age` or `payRate` can be made **private** and accessed only through **methods**.
* This protects data from accidental or malicious changes.
* Example:

  * Method `fallChanges()` exists only in `Deciduous` and is not accessible from `Evergreen`.

---

#### Interfaces and Methods

* **Methods** are functions that perform actions (e.g., `grow()`, `fallChanges()`).
* **Interfaces** define a set of actions that a class **must** implement.
* For example:

  * Interface `TreeFeatures` defines `grow()`
  * All tree classes that implement this interface must provide their own `grow()` method

---

#### Polymorphism

* **Polymorphism** means that **one interface or method** behaves **differently depending on the object**.

* Example:

  * `Squirrel` and `Coyote` are subclasses of `Animal`
  * Both have a `communicate()` method
  * Each class implements it differently: a squirrel may chirp, a coyote may howl

* Another example:

  * Method `fallChanges()` can behave differently in `Maple`, `Elm`, and `Ash`, though all are subclasses of `Deciduous`

---

#### Lesson Summary

* In OOD:

  * A **class** is a template
  * An **object** is an instance of that template
* **Inheritance** enables reuse of traits from parent classes
* **Encapsulation** protects data by restricting direct access
* **Interfaces** define behavior contracts that classes must follow
* **Polymorphism** allows the same method name to behave differently based on object context

### Section 2: What is an Object in Programming?

---

#### Object-Oriented Programming (OOP) Overview

Object-Oriented Programming (OOP) is a paradigm in which problems are solved through the interaction of **objects**.
An **object** is a self-contained component of a program that contains both data (properties) and behavior (methods). For example:

* A **person** is an object

  * **Properties**: name, age
  * **Methods**: walk(), drive()

In OOP, code is structured around these objects, and they communicate to accomplish tasks.

---

#### Classes and Objects

* A **class** is the **blueprint** of an object.

  * Example: `Person` is a class
* An **object** is an **instance** of a class.

  * Example: `Person p = new Person();`

The **class** defines what an object looks like and how it behaves, while the **object** is a working version of that class in a program.

> You can use the same class to create many objects, like creating 100 `Person` objects from the same `Person` class.

---

#### Methods vs. Functions

* A **method** is a procedure that defines the **behavior** of an object.

  * Example: `walk()` in the `Person` class
  * Methods are **bound to classes**

* A **function** is a standalone block of code that performs a task.

  * Example: a function that calculates mileage
  * Functions are **not bound** to a class and can be reused globally

> When a function becomes associated with a class, it becomes a method.

---

#### OOP Concepts

OOP is supported by four fundamental principles:

---

##### 1. Abstraction

* Focuses on **essential features** and hides unnecessary details
* Simplifies complex systems by showing only the relevant information

Example:
For a `Person` object, we may only need the `name` and `age`, not full biometric details.

---

##### 2. Encapsulation

* **Protects internal data** and methods by hiding them from outside access
* Achieved using access modifiers like `private`, `protected`, and `public`

Example:
An object `Car` may allow you to **drive** it but restrict direct changes to the **engine** or **color**.

---

##### 3. Inheritance

* Allows a new class to **reuse** the properties and methods of an existing class

Example:

* `Person` class can be extended into `Man` and `Woman`
* Both subclasses inherit basic properties like `name`, `age`

This promotes **code reusability** and **hierarchical relationships**.

---

##### 4. Polymorphism

* Means “**many forms**”
* The same method or object behaves **differently based on context**

Example:

* `Person` object acts as an **owner** inside a `Car`
* The same `Person` acts as an **employee** at an `Office`

Polymorphism allows flexibility in how methods and objects behave depending on their usage.

---

#### Lesson Summary

* **Object-Oriented Programming** structures a program around **objects**, which are instances of **classes**.
* A **class** defines the blueprint; an **object** is the live implementation.
* Objects have **properties** and **methods**.
* **Methods** are associated with classes; **functions** are independent.
* OOP is built around **abstraction**, **encapsulation**, **inheritance**, and **polymorphism**.
* These principles make OOP a powerful and popular approach to modern software development.

### Section 3: Java Objects

#### What Is an Object?

At its core, Java is an **object-oriented programming language**. This means that Java programs are made up of **objects** — self-contained modules that contain both **data (variables)** and **instructions (methods)**. For example, an `Employee` object may hold information like salary, wage, and benefit balances, and it can perform tasks with this information.

#### What Is a Class?

A **class** is the blueprint for creating objects. It defines the structure and behavior that its objects will have.

> **Mantra to remember**:
> An object is an instance of a class.

Here's an example of a simple Java class:

```java
public class Employee {
  public String empName; // Employee name
  public double hourly_rate, hours_worked;

  public double getWeeklyHours() {
    return (hourly_rate * hours_worked);
  }
}
```

In this example, the `Employee` class has three attributes and one method. When we create an `Employee` object, it will use this structure.

#### Information Hiding (Encapsulation)

A key concept in object-oriented programming is **encapsulation**, also called **information hiding**. This means that internal details of a class (like `pay rate`) are kept hidden from other parts of the program. Only necessary details are exposed.

Encapsulation allows:

* Protection of data integrity
* Better modularity
* Cleaner interfaces

So while variables like `hourly_rate` exist inside the `Employee` class, external code doesn't need to know how the class works internally.

#### Object Instantiation

**Instantiation** is the process of creating an object from a class.

Although objects come and go during runtime, **classes are persistent** in the codebase. When we use a class to create an object, we say it has been **instantiated**.

To instantiate an object, we use a **constructor**.

#### Constructor

A **constructor** is a special method used to create and initialize objects. Here's how it works:

```java
Employee newEmp = new Employee();
```

To pass in data like name, pay rate, and hours worked, we modify the constructor:

```java
public class Main {
  public static class Employee {
    public String empName;
    public double hourly_rate, hours_worked;

    // Constructor
    Employee(String name, double pay, double hours) {
      empName = name;
      hourly_rate = pay;
      hours_worked = hours;
      System.out.println("Name = " + name + ", Pay = " + pay);
    }
  }

  public static void main(String[] args) {
    Employee newEmployee = new Employee("Joe", 10.50, 40.00);
  }
}
```

In this example:

* The constructor initializes the object with custom data.
* Each object created can have unique values for its variables.

This means you can have thousands of employee objects in a program — each with its own encapsulated data.

#### Inheritance

**Inheritance** allows a class to receive properties and methods from another class. The class that inherits is called the **subclass**, and the one being inherited from is the **parent class**.

For example:

```java
class Paperback extends Publication {}
```

In this case, `Paperback` inherits everything from `Publication`. It can also define its own unique features.

Inheritance allows:

* Code reuse
* Logical hierarchy
* Simplified maintenance

#### Lesson Summary

* Java uses **objects** to organize code into reusable and logical units.
* A **class** is a blueprint for an object.
* Objects are created from classes through a process called **instantiation**.
* A **constructor** is used to create and initialize new object instances.
* **Encapsulation** hides internal data and ensures security and modularity.
* **Inheritance** allows one class to acquire the properties and methods of another, enabling reuse and extensibility.

### Section 4: Object Orientation

#### What Is an Object?

Java objects are analogous to real-world objects — entities with both **state** and **behavior**. Objects can be:

* **Physical (tangible)**: like a table, pen, chair, or car
* **Logical (intangible)**: like a bank account

For example, a **pen** named "Bic" with a white color and 5-inch length has a *state*. Its *behavior* is writing.
An **emotion**, on the other hand, is **not** an object because it lacks clearly defined state and behavior.

In Java, all objects exist as **data structures in memory**, simulating real-world entities. They include:

* **State**: The data values associated with the object
  *(e.g., make, model, color, horsepower for a car)*
* **Behavior**: The methods that define what the object can do
  *(e.g., start, accelerate, turn)*
* **Identity**: A unique internal reference that differentiates each object
  *(similar to a car's VIN number)*

#### Classes in Java

A **class** is a **template or blueprint** used to define a group of similar objects. It contains:

* **Data Members**: Variables representing the object’s state
* **Methods**: Code blocks implementing the object’s behavior
* **Constructors**: Special methods used to initialize the object

To accomplish tasks in Java:

1. You **define a class**.
2. You **create objects** from that class.
3. You **call the object's methods** to perform actions.

Example — `Rectangle` class:

```java
class Rectangle {
  // State: height and width
  private double height;
  private double width;

  // Constructor
  public Rectangle(double h, double w) {
    height = h;
    width = w;
  }

  // Behavior: Methods
  public double Perimeter() {
    return 2.0 * (height + width);
  }

  public double Area() {
    return height * width;
  }
}
```

This class defines a rectangle’s state using `height` and `width`, and includes methods to calculate its **perimeter** and **area**.

#### Creating Objects

To use the `Rectangle` class, we create an object with specified dimensions and call its methods:

```java
// Create a Rectangle object
Rectangle myRect = new Rectangle(2.5, 3.5);

// Call the Perimeter method
double outside = myRect.Perimeter();
System.out.println("outside = " + outside);
```

**Output:**

```
outside = 12.0
```

**What happens in the code:**

1. A variable `myRect` is declared to hold the object.
2. The `new` operator allocates memory for the object.
3. The `Rectangle` constructor initializes the height and width.
4. The `Perimeter()` method is called using dot notation.

#### Lesson Summary

* A **Java object** represents an entity and implements its behavior.
* All objects have:

  * **State** (group of values)
  * **Behavior** (series of methods)
  * **Identity** (unique memory reference)
* A **class** defines the structure and functionality of related objects.
* A **constructor** initializes new objects.
* The **`new` operator** is used to create specific object instances from class templates.

### Section 5: Instantiation in Java

#### What Is Instantiation?

Java is an **object-oriented programming language**, and at its core is the idea that an **object is an instance of a class**.
For example, the `Employee` class serves as a **template**. When you create a new `Employee` like Jane, she becomes an **instance** of that class — this is called **instantiation**.

> Think of the class as a general description (e.g., name, ID, job title).
> Think of the object as a specific individual with those details filled in (e.g., Jane with ID #001).

This approach allows Java to reuse structure and behavior for different objects without repeating code. Java simply processes each instance as needed, making the language efficient and powerful.

#### Inheritance and Reusability

Each new object created from a class **inherits** its properties and behaviors. In the `Employee` example, all instances:

* Share the structure and methods of the `Employee` class
* Can store unique values (e.g., different names, pay rates, hours)

While every instance shares methods like `calculateWages()`, the actual data (pay rate, hours) will vary per instance. Java handles this seamlessly.

#### Java Syntax for Instantiation

To instantiate (create) a new object, use the `new` keyword:

```java
Employee thisEmployee = new Employee();
```

This line:

* Declares a variable to hold the object
* Uses `new` to allocate memory
* Calls a constructor to initialize the object

#### Constructors

A **constructor** is a special method used to initialize objects. It looks similar to a method but:

* Has the same name as the class
* Does not return a value
* Is called when an object is created

Example of a constructor inside a class:

```java
public Employee(double payRate, double hoursWorked) {
  // constructor logic
}
```

Even if you don't create a constructor, Java automatically provides a **default constructor**. However, once you define a constructor with parameters, Java no longer provides the default — unless you define it manually.

#### Complete Example

Here’s a complete example showing instantiation and constructor usage:

```java
public class Main {
  public static class Employee {
    public String empName;
    public double hourly_rate, hours_worked;

    // Constructor
    Employee(String name, double pay, double hours) {
      empName = name;
      hourly_rate = pay;
      hours_worked = hours;
      System.out.println("Name = " + name + ", Pay = " + pay);
    }
  }

  // Main function creates an instance
  public static void main(String[] args) {
    Employee newEmployee = new Employee("Joe", 10.50, 40.00);
  }
}
```

This example:

* Declares the `Employee` class
* Defines a constructor that takes three parameters
* Instantiates a new `Employee` object with actual values

#### Using `this` in Constructors

To make code clearer and avoid confusion, Java allows the use of the `this` keyword to distinguish class variables from parameters:

```java
class Employee {
  double payRate;
  double hoursWorked;

  public Employee(double payRate, double hoursWorked) {
    this.payRate = payRate;
    this.hoursWorked = hoursWorked;
  }
}
```

To instantiate the class and use the constructor:

```java
Employee thisEmployee = new Employee(15.75, 40);
System.out.println("Pay Rate: " + thisEmployee.payRate);
```

This prints:

```
Pay Rate: 15.75
```

If a constructor with parameters exists, it **must be used** when instantiating objects. You cannot use the default constructor unless you explicitly define one.

#### Lesson Summary

* **Instantiation** creates a new object (instance) from a class.
* Objects inherit properties and behaviors from their class.
* The **`new` keyword** allocates memory and invokes the constructor.
* If no constructor is defined, Java uses a **default constructor**.
* If a parameterized constructor is defined, it must be used.
* **Constructors** are essential for initializing object data during creation.
* Instantiation + inheritance are core principles of Java's object-oriented model.

### Section 6: Constructor

#### Why a Constructor Is Needed

In Java, an **object cannot exist** without a **constructor** — just like a house can't be built without a builder.
A **class** serves as the blueprint, but a **constructor** is what turns that blueprint into a functioning **object**.

To create a new object:

```java
Employee emp = new Employee();
```

This line of code works only **if a constructor exists**. If no constructor is defined by the programmer, **Java automatically provides a default constructor** behind the scenes.

#### Default Constructor

When you don’t explicitly write one, Java supplies a **default constructor** like this:

```java
public Employee() { }
```

Rules to remember:

* The **constructor name must exactly match** the class name.
* The constructor has **no return type**, not even `void`.
* It can include code between `{ }` to set default values or perform setup operations.

#### Constructor Accessibility

Constructors can be made more or less accessible using **access modifiers**:

| Modifier    | Description                                                                |
| ----------- | -------------------------------------------------------------------------- |
| `public`    | Can be accessed from anywhere in the program or other programs             |
| `protected` | Can be accessed only within the same package                               |
| `private`   | Can only be accessed within the same class (often used in design patterns) |

These modifiers define **where and how** the constructor can be used.

#### Example — Custom Constructor

Let’s look at a class `Trees` with a user-defined constructor that sets a value for a `species` variable:

```java
public class Trees {
  String species;

  // Constructor
  public Trees() {
    species = "Elm";
  }
}
```

This constructor initializes every new `Trees` object with `"Elm"` as its default species.

The constructor is:

* **Public**, so it can be called externally.
* **Parameterless**, meaning it doesn’t require input arguments.
* Used to assign a value to the object’s internal variable.

You can extend this further by creating **multiple constructors** with different parameters for flexibility.

### Section 7: Overload!

#### What Is Overloading?

In Java, **overloading** means having **multiple versions of a method or constructor** with the same name, but different **argument lists**. These differences may be in:

* The **number** of arguments
* The **types** of arguments

Overloading provides flexibility by allowing methods or constructors to handle various input formats. It's a powerful feature that eliminates the need to create multiple uniquely named methods that do similar things.

#### Overloaded Constructors

Constructors are the special methods used to initialize new objects. Overloading constructors allows us to create different types of objects using the same class.

Example — overloaded constructors:

```java
public class Conversion {
  public double conversionRate;
  public double modifier;

  // Constructor with one parameter
  public Conversion(double c) {
    conversionRate = c;
  }

  // Constructor with two parameters
  public Conversion(double c, double m) {
    conversionRate = c;
    modifier = m;
    modifier = 0.00587;
  }
}
```

In this example:

* One constructor accepts **one parameter**.
* The other accepts **two parameters**.

#### Using Overloaded Constructors

You choose which constructor to call based on the number of arguments:

```java
Conversion conversion1 = new Conversion(48.056465584);         // Calls the 1-arg constructor
Conversion conversion2 = new Conversion(43.23, 388.888);        // Calls the 2-arg constructor
```

Java automatically selects the correct constructor depending on the arguments passed.

#### Overloaded Methods

Methods — blocks of code that perform specific tasks — can also be overloaded in the same way. This allows the same method name to be reused for various input types and numbers.

Example — overloaded `setRate` methods:

```java
public double setRate(double c) {
  conversionRate = c;
  return conversionRate;
}

public double setRate(double c, double m) {
  conversionRate = c;
  modifier = m;
  double newRate = conversionRate * modifier;
  return newRate;
}
```

In this example:

* The first method sets only the **conversion rate**.
* The second sets the **rate and modifier**, and then returns a new value.

#### Argument Type Overloading

You can also overload methods based on **argument types**, even if the number of arguments stays the same:

```java
public static int addTotals(int counter, int bonusCount) {
  return counter + bonusCount;
}

public static long addTotals(long bigCount, long bonusPlus) {
  return bigCount + bonusPlus;
}
```

Here, both methods have **two arguments**, but the data types differ (`int` vs. `long`).

#### Calling Overloaded Methods

Java intelligently determines **which version to call** by checking both the number and types of arguments:

```java
public static void main(String[] args) {
  long c = 1248344837L;
  long b = 883838493L;
  long finalValue = addTotals(c, b);
  System.out.println(finalValue);   // Calls the long version

  int z = 15;
  int y = 20;
  System.out.println("z + y = " + addTotals(z, y)); // Calls the int version
}
```

Java matches the method call to the correct version at **compile time**, ensuring smooth execution — **as long as a matching method exists**.

#### Lesson Summary

* A **constructor** is the engine that builds new instances of a class.
* A **method** performs operations and can take arguments.
* **Overloading** means having multiple versions of a constructor or method with:

  * Different **number of arguments**, or
  * Different **data types**
* Java automatically selects the correct method or constructor based on the arguments passed.
* You **cannot overload** methods or constructors with the **same number and types of arguments** — doing so will cause a compilation error.

### Section 8: Overriding

#### What Is Overriding?

**Overriding** is a key feature of Java’s object-oriented programming model. It allows a **child class** to **inherit** methods from a **parent class** and then redefine them to perform different tasks. This is a direct result of **inheritance** — the ability to build one class upon another.

For example:

```java
public class Employee {
  double hoursWorked;
  public double calcOvertime() {
    return 1.5 * (hoursWorked - 40);
  }
}
public class UnionEmployee extends Employee {
}
```

In the above example, the `UnionEmployee` class inherits everything from the `Employee` class — including the `calcOvertime()` method.

#### Overriding a Method

To **override** a method, you create a method in the **child class** with the **same name and parameters** as one in the parent class, but with a **different implementation**.

```java
public class UnionEmployee extends Employee {
  public double calcOvertime() {
    return (1.5 * (hoursWorked - 40)) - candyBarAllowance;
  }
}
```

In this override:

* Method name is the same: `calcOvertime()`
* Return type is the same: `double`
* The logic is different: it subtracts a `candyBarAllowance`

This tells Java: "Use **this** version of `calcOvertime()` when called on a `UnionEmployee`."

#### Using `super` to Call the Parent Method

If you override a method but still want access to the **original version** from the parent class, use the `super` keyword:

```java
return super.calcOvertime();
```

This lets you **invoke the parent’s version** even inside an overridden method.

#### Full Example

```java
public class Main {
  public static void main(String[] args) {
    Employee myEmployee = new Employee();
    System.out.println("Employee main method: " + myEmployee.calcOvertime());

    UnionEmployee myUnion = new UnionEmployee();
    System.out.println("Employee override: " + myUnion.calcOvertime());
  }

  public static class Employee {
    double hoursWorked = 46;
    double candyBarAllowance = 5.25;

    public double calcOvertime() {
      return 1.5 * (hoursWorked - 40);
    }
  }

  public static class UnionEmployee extends Employee {
    public double calcOvertime() {
      return (1.5 * (hoursWorked - 40)) - candyBarAllowance;
    }
  }
}
```

**Output:**

```
Employee main method: 9.0
Employee override: 3.75
```

* The first output uses the original `Employee` method.
* The second output uses the overridden method from `UnionEmployee`.

#### Lesson Summary

* **Overriding** allows a child class to redefine a method from its parent.
* The **method name and parameters must match exactly**.
* The **new implementation** replaces the parent version for that child class.
* Use the **`super` keyword** to call the parent’s original method when needed.
* Overriding is part of Java’s **inheritance system** and supports polymorphism — different objects responding differently to the same method call.

### Section 9: Classes and Methods

#### What Is a Class?

A **class** in Java is a **blueprint** or **plan** for creating objects. For example, a class named `Products` can define the structure and behaviors (methods) common to all product types. Any new object, such as a **book** or a **bicycle**, will inherit from the `Products` class and share its attributes and behaviors.

Classes often contain **methods** — reusable blocks of code that define **actions** or **behaviors**. For example:

* `updatePrice()`
* `setQuantity()`
* `retrieveUPCCode()`

These methods are defined **inside** the class.

#### What Is a Subclass?

A **subclass** (or **child class**) is a class that **inherits** all variables and methods from a **parent class**. You define a subclass using the `extends` keyword.

Example:

```java
public class Products {
  public void updateProduct(long itemID) {
    // this is a method
  }
}

public class CorrosiveProducts extends Products {
  // this is a child class
}
```

In this example:

* `CorrosiveProducts` inherits from `Products`.
* It has access to all the methods and properties defined in `Products`.

#### Overloading Methods

**Overloading** means creating **multiple methods with the same name**, but **different parameter lists**. This lets you perform similar operations with different input configurations.

Example — overloaded methods in the `Products` class:

```java
public class Products {
  public void updateProduct(long itemID) {
    // update product using only itemID
  }

  public void updateProduct(long itemID, double price) {
    // update product using itemID and price
  }
}
```

In this example:

* Both methods share the name `updateProduct`
* The **number** and **type** of parameters are different
* Java uses the correct version depending on the arguments passed when the method is called

#### Overriding Methods

**Overriding** occurs when a **child class redefines a method** from its **parent class** using the **same method signature** — same name and parameters.

Example:

```java
public class CorrosiveProducts extends Products {
  public void updateProduct(long itemID) {
    // override the parent method with new behavior
  }
}
```

In this override:

* The method has the **same name** and **same parameter** as in the parent class
* The logic is **different**, allowing the subclass to specialize the behavior

Key Rule: The overridden method must maintain the **same return type** and **parameters** as the original.

#### Summary Table

| Feature   | Overloading                               | Overriding                          |
| --------- | ----------------------------------------- | ----------------------------------- |
| Location  | Within the same class                     | Between parent and child class      |
| Signature | Same method name, different parameters    | Same method name and parameters     |
| Purpose   | Add flexibility to handle multiple inputs | Modify or extend inherited behavior |

#### Lesson Summary

* A **class** defines the structure and behavior of objects in Java.
* A **subclass** inherits all methods and variables from its parent class using `extends`.
* **Methods** represent actions and are defined inside classes.
* **Overloading** creates multiple methods with the same name but different parameters within a class.
* **Overriding** redefines an inherited method inside a child class using the same method signature to change or extend its behavior.

### Section 10: Inheritance

#### What Is Inheritance?

**Inheritance** is a foundational concept in Java and other object-oriented languages. It allows a **child class** (subclass) to gain access to the **variables and methods** of a **parent class** (superclass).

> Think of it like this:
> *A union employee is an employee.*
> *A paperback book is a book.*

The subclass inherits **all properties and behaviors** of the parent class — it can also define its **own variables and methods**. Inheritance promotes **code reuse**, avoids redundancy, and simplifies the overall program structure.

#### Syntax of Inheritance

To make one class inherit from another, use the `extends` keyword:

```java
public class ClassName extends ParentClass {
  // new methods or variables
}
```

#### Example — Employee and UnionEmployee

```java
public class Employee {
  private double payRate;
  private String fullName;
  private double FTE;

  public void calculatePay() {
    // logic to calculate pay
  }
}

public class UnionEmployee extends Employee {
  private String barganingUnit;
  private String unionCode;
  private double unionDues;

  public void calculateUnionDues() {
    // union-specific calculations
  }
}
```

In this example:

* `UnionEmployee` inherits **everything** from `Employee`
* It also adds **union-specific fields and methods**

Note: The **parent class does not inherit** anything from the child class.

#### Overriding a Method

When a subclass **redefines** a method from its parent, that’s called **overriding**. The new version **must match** the parent’s method name and parameters.

```java
public class Employee {
  private double payRate;
  private String fullName;
  private double FTE;
  float hoursWorked;

  public double calculatePay() {
    return getPayRate() * getFTE() * getHoursWorked();
  }

  public double getPayRate() { return payRate; }
  public double getFTE() { return FTE; }
  public float getHoursWorked() { return hoursWorked; }
}
```

Here’s how we **override** `calculatePay()` in `UnionEmployee`:

```java
public class UnionEmployee extends Employee {
  private String barganingUnit;
  private String unionCode;
  private double unionDues;

  private double getUnionDues() {
    return unionDues;
  }

  public double calculatePay() {
    return (super.calculatePay() - getUnionDues());
  }
}
```

We use the `super` keyword to **call the parent class’s method** and then apply additional logic (e.g., subtracting union dues).

#### Full Example with Setters and Output

```java
public class Main {
  public static void main(String[] args) {
    // Regular Employee
    Employee Sally = new Employee();
    Sally.setPayRate(53.24);
    Sally.setFTE(1.0);
    Sally.setHoursWorked(40);
    System.out.println("Net Pay = " + Sally.calculatePay());

    // Union Employee
    UnionEmployee Jim = new UnionEmployee();
    Jim.setPayRate(63.30);
    Jim.setFTE(1.0);
    Jim.setHoursWorked(30);
    Jim.setUnionDues(3.34);
    System.out.println("Net Pay = " + Jim.calculatePay() + " Union Dues = " + Jim.getUnionDues());
  }
}

class Employee {
  private double payRate;
  private String fullName;
  private double FTE;
  float hoursWorked;

  public double calculatePay() {
    return getPayRate() * getFTE() * getHoursWorked();
  }

  public double setPayRate(double r) {
    payRate = r;
    return payRate;
  }

  public double getPayRate() {
    return payRate;
  }

  public double setFTE(double f) {
    FTE = f;
    return FTE;
  }

  public double getFTE() {
    return FTE;
  }

  public float setHoursWorked(float hrs) {
    hoursWorked = hrs;
    return hoursWorked;
  }

  public float getHoursWorked() {
    return hoursWorked;
  }
}

class UnionEmployee extends Employee {
  private String barganingUnit;
  private String unionCode;
  private double unionDues;

  public double setUnionDues(double ud) {
    unionDues = ud;
    return unionDues;
  }

  public double getUnionDues() {
    return unionDues;
  }

  public double calculatePay() {
    return (super.calculatePay() - getUnionDues());
  }
}
```

#### Lesson Summary

* **Inheritance** allows one class to access the variables and methods of another.
* A **child class** (subclass) is created using the `extends` keyword.
* The subclass can add its own **unique fields and methods**.
* **Overriding** lets a subclass provide a new version of a method from its parent.
* Use the `super` keyword to **reference the parent’s method** inside an override.
* Inheritance supports **modularity**, **code reuse**, and the principles of **object-oriented programming**.

### Section 11: Multiple Inheritance

#### What Is Multiple Inheritance?

In programming, **multiple inheritance** refers to a class inheriting **from more than one parent class**. It’s a concept borrowed from real life — for example, a child inherits traits from **both parents**.

Let’s say you have:

* A `Device` class
* A `Scanner` class
* A `Copier` class

You’d naturally want a `ComboDevice` class that can inherit **both** `scan()` and `copy()` methods. Sounds ideal — but **not in Java**.

#### The Diamond Problem

Java **does not support multiple inheritance** to avoid what's called the **diamond problem**.

```
        Device
        /    \
   Scanner   Copier
        \    /
     ComboDevice
```

Here’s what happens:

* Both `Scanner` and `Copier` override the method `processDoc()` from `Device`
* If `ComboDevice` inherits from both, **which version of `processDoc()` should it use?**

Java’s dynamic class loading makes it unclear which method to choose, so it **disallows multiple inheritance entirely**.

#### Example — Multiple Inheritance Not Allowed

```java
// Device class
public class Device {
  void showMsg() {
    System.out.println("I'm a Device!");
  }
}

// Scanner class
public class Scanner extends Device {
  public String scanDoc(String docType) {
    return docType;
  }
}

// Copier class
public class Copier extends Device {
  public String copyDoc(String docType) {
    return docType;
  }
}

// Invalid: won't compile!
public class ComboDevice extends Scanner, Copier {
}
```

This code results in a **compilation error** because Java only allows a class to **extend one other class**. The compiler will not understand how to handle two parent classes.

#### Simulating Multiple Inheritance with Interfaces

To achieve similar functionality, Java uses **interfaces**.

An **interface** is like a class, but it contains only **method signatures** and **constants** — no implementation. A class can implement **multiple interfaces**, providing a clean solution to the multiple inheritance issue.

#### Example — Using Interfaces

```java
// Interfaces
interface Scan {
  public String scanDoc(String doc);
}

interface Copy {
  public String copyDoc(String doc);
}

// One class implements both interfaces
public class MultiExample implements Scan, Copy {
  @Override
  public String scanDoc(String doc) {
    System.out.println("Scanning the Document = " + doc);
    return doc;
  }

  @Override
  public String copyDoc(String doc) {
    System.out.println("Copying the Document = " + doc);
    return doc;
  }

  public static void main(String[] args) {
    MultiExample multi = new MultiExample();
    multi.scanDoc("Rates.doc");
    multi.copyDoc("Rates.doc");
  }
}
```

**Output:**

```
Scanning the Document = Rates.doc  
Copying the Document = Rates.doc
```

This way, `MultiExample` is able to **combine behavior from both interfaces** without inheritance conflicts.

The `@Override` annotation ensures that you are correctly overriding interface methods. Modern IDEs like NetBeans even suggest adding it for clarity and accuracy.

#### Lesson Summary

* **Multiple inheritance** allows a class to inherit from more than one parent — supported in C++, **not in Java**.
* Java avoids multiple inheritance to prevent **ambiguities** (like the diamond problem).
* Java **only allows single inheritance**, but supports **multiple interface implementation**.
* **Interfaces** provide a flexible alternative, allowing classes to implement methods from **multiple sources**.
* This is **not true multiple inheritance**, but it achieves a similar effect with **less complexity and better maintainability**.

### Section 12: Object-Oriented Principles

#### Objects and Classes

Java is an **object-oriented programming language**, which means **everything is an object**. An object is simply an **instance of a class**.

For example:

* The class `Sandwich` defines general features of all sandwiches (bread, filling, lettuce).
* A **specific sandwich** like *tuna on rye* is an **instance** of that class.

To create or manipulate an object, Java uses **methods**, such as:

```java
assembleSandwich()
getIngredients()
```

#### Inheritance

**Inheritance** allows one class to **inherit properties and methods** from another.

Example:

```java
public class HotSandwich extends Sandwich {
  // Inherits from Sandwich
}

public class PhillyCheese extends HotSandwich {
  // Inherits from HotSandwich
}
```

Here:

* `HotSandwich` inherits from `Sandwich`
* `PhillyCheese` inherits from `HotSandwich`

This builds a **family tree** of related classes. But Java does **not** allow a class to inherit from **multiple parents** (no multiple inheritance). A `PhillyCheese` sandwich can inherit from `HotSandwich`, **not both** `HotSandwich` and `ColdSandwich`.

#### Polymorphism

**Polymorphism** means “many forms.” It refers to the ability of different objects to **respond to the same method name** in different ways.

There are **three main types** of polymorphism in Java:

---

#### 1. **Polymorphism via Object Assignment**

You can assign a subclass object to a superclass reference:

```java
Sandwich mySandwich;
mySandwich = new HotSandwich();
mySandwich = new PhillyCheese();
mySandwich = new IceCreamSandwich();
```

Java recognizes the correct object type during **runtime** and calls the appropriate method.

---

#### 2. **Method Overloading**

**Overloading** means having **multiple methods with the same name** but **different parameters**.

Example:

```java
public class ColdSandwich extends Sandwich {
  public double assembleSandwich(int cheeseSlices) {
    return cheeseSlices;
  }
}

public class HotSandwich extends Sandwich {
  public double assembleSandwich(int cheeseSlices, double toastTime) {
    return toastTime;
  }
}
```

Java determines which method to call based on the number and types of arguments.

---

#### 3. **Method Overriding**

**Overriding** means a **child class redefines a method** from the parent class using the **same method name and parameters**.

Example:

```java
public class HotSandwich extends Sandwich {
  public void assembleSandwich() {
    System.out.println("Build hot");
  }
}

public class PhillyCheese extends HotSandwich {
  public void assembleSandwich() {
    System.out.println("Build Philly");
  }
}
```

Now let’s test it with a `main()` method:

```java
public class TestSandwich {
  public static void main(String[] args) {
    Sandwich hot = new HotSandwich();
    Sandwich philly = new PhillyCheese();
    hot.assembleSandwich();    // Outputs: Build hot
    philly.assembleSandwich(); // Outputs: Build Philly
  }
}
```

Even though both variables are of type `Sandwich`, Java uses the actual object type (`HotSandwich` or `PhillyCheese`) to determine which method to run.

---

#### Full Code Example

```java
// Base class
public class Sandwich {
  public void assembleSandwich() {
    System.out.println("Assemble Sandwich");
  }
}

// Inherits from Sandwich
public class HotSandwich extends Sandwich {
  public void assembleSandwich() {
    System.out.println("Build hot");
  }
}

// Inherits from HotSandwich
public class PhillyCheese extends HotSandwich {
  public void assembleSandwich() {
    System.out.println("Build Philly");
  }
}

// Test class
public class TestSandwich {
  public static void main(String[] args) {
    Sandwich hot = new HotSandwich();
    Sandwich philly = new PhillyCheese();
    hot.assembleSandwich();    // Build hot
    philly.assembleSandwich(); // Build Philly
  }
}
```

To run:

```bash
javac Sandwich.java HotSandwich.java PhillyCheese.java TestSandwich.java
java TestSandwich
```

**Output:**

```
Build hot  
Build Philly
```

---

#### Inheritance vs. Polymorphism

| Feature      | Inheritance                                  | Polymorphism                                                           |
| ------------ | -------------------------------------------- | ---------------------------------------------------------------------- |
| What it does | Allows one class to **inherit** from another | Allows different classes to **respond differently** to the same method |
| Code example | `extends` keyword in subclass                | Method `assembleSandwich()` behaves differently per class              |
| Types        | Single inheritance only (no multiple)        | Overloading, overriding, object-type polymorphism                      |

---

#### Lesson Summary

* Java is object-oriented: **everything is an object**, and **every object is an instance of a class**.
* **Inheritance** allows a class to reuse code from another class. For example, `PhillyCheese` inherits from `HotSandwich`, which inherits from `Sandwich`.
* **Polymorphism** enables different behaviors using the **same method name**.

  * **Overloading**: Same method name, **different parameters**
  * **Overriding**: Same method name and parameters, but **redefined in subclass**
  * **Dynamic assignment**: One variable can refer to different subclass objects
* Java is smart enough to determine which method to call based on **parameters** and **object types**.

### Section 13: Interfaces and Abstract Classes

#### Interfaces

An **interface** in Java defines **method signatures** without providing implementation. It's like a **contract** — a class that uses an interface must implement all the methods declared in it.

> Think of an interface like a **card game icon on your phone**:
> You click it, and something happens, but you don’t need to know how it works. The interface simply **triggers** functionality.

##### Example — Simple Interface

```java
interface CardGame {
  public void shuffle();
  public void deal();
}
```

In this example:

* `CardGame` is an interface with **no implementation details**
* It declares two methods: `shuffle()` and `deal()`
* Any class that implements this interface must define these methods

---

#### Multiple Inheritance with Interfaces

Java does **not support multiple inheritance** through classes, but it allows **a class to implement multiple interfaces**. This helps avoid the **diamond problem**.

> A class cannot inherit from both `CardGame` and `SolitaireCardGame`,
> but an interface can **extend** multiple interfaces, and a class can **implement** multiple interfaces.

##### Example — Interface Extending Multiple Interfaces

```java
public interface SolitaireDoubleDeck extends CardGame, Solitaire {
  public CardGame doubleShuffle();
}
```

Here:

* `SolitaireDoubleDeck` **inherits** from both `CardGame` and `Solitaire`
* It adds a new method `doubleShuffle()`
* This setup mimics **multiple inheritance** safely

---

#### Using Interfaces in Classes

To **use an interface in a class**, apply the `implements` keyword:

```java
public class DoubleDiamond implements CardGame {
  public void shuffle() {
    // logic for shuffling
  }

  public void deal() {
    // logic for dealing cards
  }
}
```

* The class `DoubleDiamond` must implement **all methods** declared in `CardGame`
* Interfaces ensure **consistent method behavior** across different implementations

---

#### Extend vs. Implement

| Use Case                    | Keyword      | Description                                         |
| --------------------------- | ------------ | --------------------------------------------------- |
| Interface extends interface | `extends`    | Interface inherits from one or more interfaces      |
| Class implements interface  | `implements` | Class commits to implementing all interface methods |

---

#### Abstract Classes

An **abstract class** is a class that **cannot be instantiated**. It's used as a **base class** that defines **common behavior** for its subclasses.

> Example: A generic `Game` class shouldn't be used to create objects — it’s too vague. But `CardGame` or `Solitaire` can inherit from it.

##### Abstract Class Example

```java
public abstract class CardGame {
  public abstract long getCards(); // must be overridden
}
```

You **cannot** create an instance of `CardGame` directly. However, a child class **can inherit** from it and provide the actual implementation.

##### Subclass Example

```java
public class DoubleDiamond extends CardGame {
  public long getCards() {
    return 104;
  }
}
```

Here:

* `DoubleDiamond` inherits from `CardGame`
* It **overrides** the abstract method `getCards()` to return the number of cards used

---

#### Key Differences: Interface vs. Abstract Class

| Feature               | Interface                               | Abstract Class                            |
| --------------------- | --------------------------------------- | ----------------------------------------- |
| Instantiation         | Cannot be instantiated                  | Cannot be instantiated                    |
| Method Implementation | No method body (Java 8+ allows default) | Can have implemented methods              |
| Multiple Inheritance  | Yes (multiple interfaces allowed)       | No (only one abstract class per class)    |
| Use Case              | Defining contracts (e.g., behaviors)    | Defining core base behavior and structure |

---

#### Lesson Summary

* An **interface** defines method signatures and acts as a **contract** for implementing classes.
* Interfaces **support multiple inheritance**, allowing a class to access methods from multiple sources.
* Use `implements` to add an interface to a class.
* Use `extends` to let an interface inherit from **multiple interfaces**.
* An **abstract class** provides a base for other classes but **cannot be instantiated**.
* Abstract classes can define **abstract methods** that **must** be implemented in subclasses.
* Use interfaces for **behavior templates**, and abstract classes for **shared implementation and structure**.

### Section 14: Error! Error!

#### What Is an Exception?

In Java, an **exception** is an **unexpected event** that disrupts the normal flow of a program. Think of it as a surprise glitch — something the program **did not plan for**.

When an exception occurs, **Java throws it** — but **not away**. Instead, it sends the error to the **runtime system**, which will try to handle it. If no one "catches" the error, the program crashes. This is called an **unhandled exception**.

---

#### Common Exception Types

Java includes many **built-in exceptions**, all organized in a class hierarchy under `Throwable`.

| Exception Name                   | Description                                      |
| -------------------------------- | ------------------------------------------------ |
| `ArithmeticException`            | Division by zero                                 |
| `ArrayIndexOutOfBoundsException` | Accessing an invalid index in an array           |
| `ClassCastException`             | Trying to cast an object to an incompatible type |
| `NullPointerException`           | Accessing a method or field on a null object     |

Examples of runtime errors:

* Divide by zero
* File not found
* Array index out of bounds

These errors may be **known by Java**, but they still cause the program to **terminate** if not properly handled.

---

#### Exception Classes in Java

All exceptions derive from the **`Throwable` class**, which has two main subclasses:

* **`Error`** – Used for serious problems (e.g., out-of-memory errors)
* **`Exception`** – Used for regular program-level exceptions

Custom exceptions can also be created by extending the `Exception` class.

---

#### Example — Divide by Zero

```java
double fees = 50;
double modifier = 0;
double total;
total = fees / modifier;  // Causes ArithmeticException
```

If `modifier` is `0`, this results in a divide-by-zero error. Although it seems simple here, these bugs often hide in real applications.

---

#### Example — Array Index Out of Bounds

```java
int[] numbers = new int[5];
for(int i = 0; i < 15; i++) {
  System.out.println(numbers[i]);  // IndexOutOfBoundsException
}
```

The program compiles successfully, but throws an exception when run — **because index 5 to 14 do not exist**.

---

#### Handling Exceptions

Java provides two keywords for handling exceptions:

* `try` – contains the code that might throw an exception
* `catch` – defines how to handle the exception

##### Example — Basic Try-Catch

```java
int[] numbers = new int[5];
try {
  for (int i = 0; i < 15; i++) {
    System.out.println(numbers[i]);
  }
} catch (ArrayIndexOutOfBoundsException e) {
  System.out.println("Oops!");
}
```

If an exception is thrown inside the `try` block, the **`catch` block** intercepts it and **prevents the program from crashing**.

---

#### Exception Flow

* Java throws the exception
* If a `catch` block is defined for that type, it handles the error
* If not, the program **terminates**

---

#### Lesson Summary

* An **exception** is an **unexpected event** that interrupts normal program flow.
* If an exception is not handled, it leads to a **program crash**.
* Java provides a set of **built-in exceptions** and an exception **class hierarchy** under `Throwable`.
* To **catch and handle** exceptions, use the `try` and `catch` keywords.
* Use exception handling to keep your programs **stable** and **user-friendly**.
