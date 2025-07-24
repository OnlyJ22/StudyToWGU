Look at  109 -> Ch9.md for more content

### Section 1: Understanding Priority Queues

#### What Is a Priority Queue?

Imagine you've been waiting in the **emergency room** for two hours. Suddenly, a new patient walks in and is seen **before you**. This may seem unfair — until the nurse explains that patients are treated based on **medical severity**, not order of arrival.

This is a **priority queue** in action.

> A **priority queue** is a queue where elements are processed based on **priority**, not just order.

Unlike a regular queue (which follows **First-In-First-Out**), a **priority queue** removes elements with the **highest priority** first.

---

#### Characteristics of a Priority Queue

* It is an **abstract data type** (ADT) — the data type it stores isn't specified at the start
* Elements are **not retrieved in insertion order**
* **Highest-priority items are removed first**
* Commonly used in **real-world systems** like emergency rooms, CPU scheduling, etc.

In Java, this structure is implemented using the `PriorityQueue` class.

---

#### Creating Order in a Priority Queue

By default, Java uses **natural ordering**:

* **Numbers** are sorted numerically
* **Strings** are alphabetized

You can also create **custom orderings**, such as:

* Medical severity
* Task urgency
* Customer importance

This makes priority queues highly **versatile**.

---

#### Example: Emergency Room Priority Queue

Let’s simulate a **hospital triage system** using a custom `Patient` class.

---

#### Creating the Patient Class

We define a class with these **instance variables**:

* `severityID` — numeric severity level
* `patientName`
* `conditionName`

```java
public class Patient implements Comparable<Patient> {
    private int severityID;
    private String patientName;
    private String conditionName;

    public Patient(int severity, String name, String condition) {
        severityID = severity;
        patientName = name;
        conditionName = condition;
    }
```

---

#### Adding Accessor Methods

These **getter methods** return the patient data:

```java
    public int getSeverityID() { return severityID; }
    public String getPatientName() { return patientName; }
    public String getConditionName() { return conditionName; }
```

---

#### Adding Comparison Logic

To determine priority, we implement `equals()` and `compareTo()`:

```java
    public boolean equals(Patient theOtherPatient) {
        return this.getSeverityID() == theOtherPatient.getSeverityID();
    }

    @Override
    public int compareTo(Patient theOtherPatient) {
        if (this.equals(theOtherPatient))
            return 0;
        else if (getSeverityID() > theOtherPatient.getSeverityID())
            return 1;
        else
            return -1;
    }
```

---

#### Adding Output Formatting

We override `toString()` for easy printing:

```java
    public String toString() {
        return "Next Patient (" + getSeverityID() + "): " +
               getPatientName() + "\tCondition: " +
               getConditionName();
    }
}
```

---

#### Creating the Implementing Class

Now we create a Java class that uses our `Patient` class in a **priority queue**:

```java
import java.util.PriorityQueue;

public class PatientExample {
    public static void main(String[] args) {
```

---

#### Adding Patients to the Queue

We simulate patients entering the ER:

```java
        Patient er1 = new Patient(4, "Vinnie Pinatino", "Broken Nose");
        Patient er2 = new Patient(1, "Gabe Scholamachia", "Chest Pain");
        Patient er3 = new Patient(3, "Margaret Sinpliny", "Broken Leg");
        Patient er4 = new Patient(5, "Walter Comettenin", "Broken Finger");
        Patient er5 = new Patient(2, "Cynthia Bittonnia", "Shortness of Breath");
```

---

#### Instantiating the Priority Queue

```java
        PriorityQueue<Patient> theER = new PriorityQueue<>();
        theER.add(er1);
        theER.add(er2);
        theER.add(er3);
        theER.add(er4);
        theER.add(er5);
```

---

#### Displaying Queue Contents

```java
        for (Patient iterate : theER) {
            System.out.println(iterate);
        }
```

**Sample Output:**

```
Next Patient (1): Gabe Scholamachia    Condition: Chest Pain  
Next Patient (2): Cynthia Bittonnia    Condition: Shortness of Breath  
Next Patient (3): Margaret Sinpliny    Condition: Broken Leg  
Next Patient (5): Walter Comettenin    Condition: Broken Finger  
Next Patient (4): Vinnie Pinatino      Condition: Broken Nose  
```

---

#### Removing a Patient from the Queue

Use `remove()` to dequeue the highest-priority patient:

```java
        System.out.println(theER.remove());
        System.out.println("There are " + theER.size() + " patients in queue.");
```

**Output:**

```
Next Patient (1): Gabe Scholamachia    Condition: Chest Pain  
There are 4 patients in queue.
```

---

#### Additional PriorityQueue Methods

| Method         | Description                               |
| -------------- | ----------------------------------------- |
| `add()`        | Adds an element                           |
| `clear()`      | Empties the queue                         |
| `comparator()` | Returns the comparator used               |
| `iterator()`   | Iterates over the queue                   |
| `offer()`      | Inserts an element                        |
| `peek()`       | Returns the highest-priority item         |
| `poll()`       | Returns and removes highest-priority item |
| `remove()`     | Removes the highest-priority item         |
| `size()`       | Returns number of elements                |
| `toArray()`    | Returns an array of the queue's items     |

---

#### Lesson Summary

* **Priority queues** retrieve elements based on **priority**, not insertion order
* They use **natural or custom ordering**
* In Java, the `PriorityQueue` class handles this structure
* A priority queue is more flexible than a regular queue
* Essential for scenarios like **emergency triage, scheduling, and task prioritization**
* Priority queues provide useful methods beyond those of regular queues

> In software and real life, **urgency often matters more than timing** — and priority queues help us manage that reality.

### Section 2: Heap and Binary Tree

#### What Is a Heap?

A **heap** is a specialized **binary tree-based data structure** that maintains a specific order among its elements. In a binary tree, each **parent node** can have **at most two children**.

What makes a heap different? A **heap is stored in an array**, and it allows efficient insertion, deletion, and access to the **minimum or maximum element**, depending on the heap type.

> Think of an **airport boarding process**:
> Passengers form a queue at the gate (array). But they board in a **hierarchy** — first priority groups, then business class, and finally economy. This mirrors a **heap structure**.

---

#### Key Properties of a Heap

1. **Ordering Property**

   A heap must follow **either** of these properties:

   * **Min-Heap**: Each child node has a **greater or equal value** than its parent.
     → The **minimum** element is always at the root.

     ```
     Min-Heap Example:
           1
         /   \
        3     5
     ```

   * **Max-Heap**: Each child node has a **lesser or equal value** than its parent.
     → The **maximum** element is at the root.

     ```
     Max-Heap Example:
           9
         /   \
        6     4
     ```

2. **Structural Property**

   * A heap is a **complete binary tree**.

   * All levels must be **completely filled**, except possibly the last.

   * Nodes on the last level are added **from left to right**.

   > Unlike a binary search tree (BST), a heap **does not** require elements in left/right subtrees to follow ordering rules.

---

#### Heap vs. Binary Tree

| Property   | Binary Tree         | Heap                           |
| ---------- | ------------------- | ------------------------------ |
| Shape      | Any                 | Complete binary tree           |
| Order Rule | Based on left/right | Based on parent-child priority |
| Use Case   | Search, Structure   | Priority queues, sorting       |

---

#### Heap Operations

A heap supports the following operations:

* **find** — Search for an element
* **insert** — Add a new item while maintaining heap order
* **delete** — Remove a specified item
* **extract** — Remove and return the root (min or max)
* **replace** — Remove the root and insert a new item (in one step)

Additional operations:

| Method       | Purpose                                              |
| ------------ | ---------------------------------------------------- |
| `size()`     | Returns number of elements in heap                   |
| `is-empty()` | Checks whether the heap is empty                     |
| `merge()`    | Combines two heaps; **original heaps are preserved** |
| `meld()`     | Combines two heaps; **original heaps are destroyed** |

---

#### Heap Implementation

Heaps are typically implemented using **arrays**. This allows for:

* Efficient parent-child indexing:

  * Parent at index `i`
  * Left child at `2i + 1`
  * Right child at `2i + 2`
* Faster access and manipulation than pointer-based trees

After every **insertion** or **deletion**, the heap must be **rebalanced** to restore heap properties.

---

#### Application: Priority Queue

A **priority queue** is an abstract data type where each item has a **priority**. Items with **higher priority** are removed **before** those with lower priority.

**Difference from Regular Queue:**

| Feature           | Regular Queue        | Priority Queue                      |
| ----------------- | -------------------- | ----------------------------------- |
| Removal Order     | FIFO                 | Based on priority                   |
| Structure Used    | Linked List or Array | Heap                                |
| Priority Handling | Not considered       | Numeric or logical priority applied |

**Example Use Case:**

* Network routers using priority queues to manage bandwidth
* Emergency room triage systems
* Task scheduling in operating systems

---

#### Lesson Summary

* A **heap** is a complete binary tree stored as an array and used to implement **priority-based access**.
* It follows the **min-heap** or **max-heap** property:

  * Min-Heap → smallest value at root
  * Max-Heap → largest value at root
* It is **not** a binary search tree and doesn't compare left/right node values.
* The most common use of a heap is in the **priority queue**, where the highest-priority item is served first.
* **Operations** like insert, delete, and extract must maintain the heap property.
* **Heaps are highly efficient** for managing dynamic data where ordering by priority is essential.

### Section 3: The Need for Priority Queues

#### Why Do We Need a Priority Queue?

Imagine you're collecting **tickets** at the entrance to a national sports event. Your job?
*Organize them in **alphabetical order by city*** and tell the event coordinator which city comes **first**.

Simple enough — until you realize you're dealing with over **20,000** tickets!

> This is where a **priority queue** shines:
> It maintains elements in **natural order** and retrieves the **highest-priority item first**, regardless of insertion order.

---

#### What Is Natural Order?

In Java, natural order refers to:

* **Strings** → Alphabetical order
* **Numbers** → Numeric order (ascending)

So in our ticket example, city names are sorted **alphabetically**.
The **first city alphabetically** is the highest-priority item.

---

#### Implementing a Priority Queue for Tickets

Let’s build a custom `Ticket` class with:

* `city`
* `ticketHolder`

The class implements the `Comparable<Ticket>` interface to define sorting behavior.

```java
public class Ticket implements Comparable<Ticket> {
    private String city;
    private String ticketHolder;

    public Ticket(String theCity, String theName) {
        city = theCity;
        ticketHolder = theName;
    }

    public String getCity() { return city; }
    public String getTicketHolder() { return ticketHolder; }

    public String toString() {
        return "Next on our list is " + getTicketHolder() + " from " + getCity();
    }

    @Override
    public int compareTo(Ticket theOtherTicket) {
        int theResult = this.city.compareTo(theOtherTicket.city);
        return theResult;
    }
}
```

---

#### Creating the Driver Class

```java
import java.util.PriorityQueue;

public class TicketExample {
    public static void main(String[] args) {
        PriorityQueue<Ticket> ticketList = new PriorityQueue<>();
```

Create and add five ticket instances in **random order**:

```java
        Ticket ticket1 = new Ticket("Winsted", "Orrzo, Bobby");
        Ticket ticket2 = new Ticket("Manchester", "Windmill, Sandy");
        Ticket ticket3 = new Ticket("Honolulu", "Pine, Rhona");
        Ticket ticket4 = new Ticket("Nashville", "Orbitz, Nate");
        Ticket ticket5 = new Ticket("Ashville", "Prink, Katelin");

        ticketList.add(ticket1);
        ticketList.add(ticket2);
        ticketList.add(ticket3);
        ticketList.add(ticket4);
        ticketList.add(ticket5);
```

---

#### Displaying Ticket Order Using Poll

```java
        while (!ticketList.isEmpty()) {
            Ticket i = ticketList.poll();
            System.out.println(i);
        }
    }
}
```

**Output:**

```
Next on our list is Prink, Katelin from Ashville  
Next on our list is Pine, Rhona from Honolulu  
Next on our list is Windmill, Sandy from Manchester  
Next on our list is Orbitz, Nate from Nashville  
Next on our list is Orrzo, Bobby from Winsted
```

Notice how the cities are sorted **alphabetically**, even though they were added in random order.

---

#### Sorting by Multiple Elements

Now let’s test what happens if we have **two ticket holders from the same city**:

```java
Ticket ticket6 = new Ticket("Honolulu", "Betty Clearly");
ticketList.add(ticket6);
```

**Previous compareTo only sorted by city**, so the two Honolulu entries appear together but not ordered by name.

To fix that, modify `compareTo` for **secondary sorting**:

```java
@Override
public int compareTo(Ticket theOtherTicket) {
    int theResult = this.city.compareTo(theOtherTicket.city);
    if (theResult == 0) {
        theResult = this.ticketHolder.compareTo(theOtherTicket.ticketHolder);
    }
    return theResult;
}
```

**New Output:**

```
Next on our list is Prink, Katelin from Ashville  
Next on our list is Betty Clearly from Honolulu  
Next on our list is Pine, Rhona from Honolulu  
Next on our list is Windmill, Sandy from Manchester  
Next on our list is Orbitz, Nate from Nashville  
Next on our list is Orrzo, Bobby from Winsted
```

Now the ticket holders from the **same city** are ordered by **name** as a secondary condition.

---

#### Lesson Summary

* A **priority queue** is a powerful data structure that allows for **automatic ordering** of items.
* In Java, the `PriorityQueue` class implements natural ordering using the `Comparable` interface.
* You can **customize sorting logic** using the `compareTo` method.
* Priority queues are great when:

  * You need the **next best item** fast
  * You don’t want to **sort manually** every time
  * You want to support **dynamic ordering** based on multiple fields

Use priority queues to keep your data sorted, smartly and efficiently — no matter how many items you're working with.
