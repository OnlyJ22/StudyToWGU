### Section 1: Creating a Data Type and Using Abstraction in Java

---

#### What Is a Data Type?

In programming, a **data type** defines:

* The kind of **data** a variable can hold (e.g., `int`, `String`)
* The **operations** that can be performed on it (e.g., `+`, `-`, method calls)

Custom data types are usually created using **classes**, which allow you to define **characteristics (fields)** and **behaviors (methods)** of that type.

---

#### Example: Custom `Time` Data Type

Suppose you're developing an application that logs server activity. You need a way to represent **precise times** — hours, minutes, and seconds. This is a good use case for a **custom class**:

```java
import java.time.*;

public class Time {
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
        System.out.println("Hour logged: " + time_logged.getHour());
    }
}
```

> ✅ This class uses Java’s `LocalDateTime` class to retrieve and display current time data.

---

#### Why Abstraction?

You may need to use your `Time` type in different **contexts**:

* One that uses a **company time server**
* One that uses the **public system clock**

Each version **should behave the same**, even if they get time differently. This is where **abstraction** helps.

---

#### Abstraction with Interfaces

An **abstract data type** only defines **what** the class does — not **how** it does it.

In Java, this is done using an **interface**:

```java
interface Time {
    int getHour();
    int getMinute();
    int getSecond();
}
```

* No method bodies — only **signatures**
* Acts like a **blueprint**

---

#### Implementing the Interface

Here’s how a concrete class like `PublicTime` can implement the interface:

```java
import java.time.*;

interface Time {
    int getHour();
    int getMinute();
    int getSecond();
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
        System.out.println("Hour (from interface): " + time_logged.getHour());
    }
}
```

> 🔁 Now, you can make other versions like `CompanyTime` that also implement `Time`, but use different internal logic.

---

#### Benefits of Abstraction

* **Modularity**: You can change how time is retrieved without changing how it is used.
* **Consistency**: Any class that implements `Time` must offer `getHour()`, `getMinute()`, and `getSecond()`.
* **Flexibility**: Works great for large systems with multiple environments or services.

---

#### Lesson Summary

* **Custom data types** in Java are often created using **classes**.
* To create **abstract data types**, use **interfaces**.
* An interface describes **what** a class can do (method names), not **how** (method bodies).
* A class **implements** an interface using the `implements` keyword.
* Interfaces ensure that all classes provide the same behavior, which is essential for **abstraction** and **polymorphism**.

---

#### Key Terms

| Term              | Definition                                                          |
| ----------------- | ------------------------------------------------------------------- |
| **Data Type**     | Defines kind of data and operations allowed                         |
| **Class**         | A blueprint for creating custom objects                             |
| **Interface**     | Abstract type that defines method signatures without implementation |
| **Implements**    | Keyword used by a class to implement an interface                   |
| **Abstraction**   | Separates behavior from implementation; focuses on what not how     |
| **LocalDateTime** | Java class that retrieves date and time                             |

### Section 2: Stacks in Java – Abstract Data Type Implementation

---

#### What Is a Stack?

A **stack** is a linear data structure that follows the **LIFO** (Last-In, First-Out) principle:

* Think of a **stack of plates** in a cafeteria — the last one placed on top is the first one removed.
* Similar concepts are used in computers — for example, the **Undo** operation in text editors and **method call stacks** in Java.

---

#### Stack Operations

| Operation   | Description                           |
| ----------- | ------------------------------------- |
| `push(n)`   | Adds item `n` to the top of the stack |
| `pop()`     | Removes and returns the top item      |
| `peek()`    | Returns top item without removing     |
| `isEmpty()` | Returns `true` if stack is empty      |
| `size()`    | Returns total number of elements      |

---

#### Creating the Stack Interface

We first define the **Stack** interface, which outlines the structure of our stack’s behavior:

```java
// Stack interface
public interface Stack {
    void push(int plate);
    int pop();
    int peek();
    int size();
    boolean isEmpty();
}
```

This interface abstracts what a stack can do, without defining how it does it.

---

#### Implementing the Stack with a Linked List

Now, let’s implement the `LinkedStack` class using a **singly linked list**:

```java
import java.util.NoSuchElementException;

public class LinkedStack implements Stack {
    private class Node {
        int plate;
        Node next;
        public Node(int current) {
            plate = current;
        }
    }

    private Node top;

    public LinkedStack() {
        top = null;
    }

    public void push(int current) {
        Node c = new Node(current);
        c.next = top;
        top = c;
    }

    public int pop() {
        if (top == null) throw new NoSuchElementException("Stack is empty");
        int returnPlate = top.plate;
        top = top.next;
        return returnPlate;
    }

    public boolean isEmpty() {
        return top == null;
    }

    public int size() {
        int counter = 0;
        for (Node node = top; node != null; node = node.next) {
            counter++;
        }
        return counter;
    }

    public int peek() {
        if (top == null) throw new NoSuchElementException("Stack is empty");
        return top.plate;
    }
}
```

> 🔄 We use the `top` variable to always track the top of the stack. This allows `push` and `pop` to operate in constant time.

---

#### Using the Stack in the Main Program

Now let’s use the stack in a program through the `StackOperations` class:

```java
public class StackOperations {
    public static void main(String[] args) {
        int plate;
        LinkedStack lottaPlates = new LinkedStack();

        // Push 125 plates onto the stack
        for (plate = 25; plate < 150; plate++) {
            lottaPlates.push(plate + 5);
        }

        // Basic stack operations
        if (lottaPlates.isEmpty()) {
            System.out.println("Empty Stack");
        } else {
            System.out.println("Peeking at the top = " + lottaPlates.peek());
            System.out.println("Size of the stack = " + lottaPlates.size());
            System.out.println("Popping the top = " + lottaPlates.pop());
        }

        // Accessing the 50th plate (by removing elements)
        for (int j = lottaPlates.size(); j >= 50; j--) {
            System.out.println("Removing plate at position: " + lottaPlates.size());
            lottaPlates.pop();
        }
    }
}
```

---

#### Output Example

```text
Peeking at the top = 154
Size of the stack = 125
Popping the top = 154
...
Removing plate at position: 124
Removing plate at position: 123
...
Removing plate at position: 50
```

> ⚠️ Remember: In a stack, you **can only access** the top item. To reach deeper items, you must **pop off** those above.

---

#### Lesson Summary

* A **stack** is a Last-In, First-Out (LIFO) data structure.
* Common operations include `push`, `pop`, `peek`, `size`, and `isEmpty`.
* You can implement a stack **from scratch** using a **singly linked list**.
* The **top** of the stack is where all operations take place — adding or removing elements.
* Accessing an item inside the stack (not on top) requires **popping items off** until you reach it.
* While Java has a built-in `Stack` class, building one manually reinforces understanding of **abstract data types**.

### Section 3: Linked Lists vs. Arrays in Java

---

#### Arrays – Fixed Structures

An **array** is a linear data structure that holds a **fixed number** of elements of the same type. Once created, its **size cannot change**.

> 🛤️ **Analogy**: Think of an array as a rigid train with a fixed number of cars. To add or remove a car, you must build a new train.

##### Characteristics of Arrays:

* Fixed size upon initialization
* Fast random access: `O(1)`
* Inefficient insertion/deletion (except at the end)
* Stored in contiguous memory

```java
String[] arr = new String[6];  // Array of size 6
arr[0] = "L";                  // Add element
```

---

#### Linked Lists – Dynamic Data Structures

A **linked list** is a **dynamic structure** consisting of individual **nodes**, where each node contains:

* **Data**
* A reference (or link) to the **next node**

> 🚂 **Analogy**: Like a train where each car is connected to the next. Cars (nodes) can be added or removed easily.

##### Key Features:

* Grows/shrinks dynamically
* Efficient insertions/deletions at the head/tail
* Slower access: Must traverse from the head
* No fixed size limit

---

#### Java LinkedList Implementation

Java provides a `LinkedList` class from the `java.util` package.

```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        LinkedList<String> myList = new LinkedList<>();
        myList.add("I");
        myList.add("S");
        myList.add("T");
        System.out.println("Linked List = " + myList);
    }
}
```

**Output:**

```
Linked List = [I, S, T]
```

---

#### Inserting at Head and Tail

Adding elements at the beginning or end is easy with `addFirst()` and `addLast()`:

```java
myList.addFirst("L");  // Add to head
myList.addLast("9");   // Add to tail
System.out.println("Try Again! " + myList);
```

**Output:**

```
Try Again! [L, I, S, T, 9]
```

---

#### Removing and Modifying Elements

```java
myList.remove("9");  // Remove an element
System.out.println("After removal: " + myList);

Object item = myList.get(2);                // Access element at index
myList.set(2, (String) item + " Changed");  // Modify it
System.out.println("After the change: " + myList);
```

---

#### Useful LinkedList Methods

| Method                         | Description                 | Example                    |
| ------------------------------ | --------------------------- | -------------------------- |
| `add(Object o)`                | Appends item at the end     | `myList.add("T")`          |
| `add(int index, Object value)` | Inserts at a specific index | `myList.add(2, "H")`       |
| `remove(Object o)`             | Removes first occurrence    | `myList.remove("T")`       |
| `addFirst(Object o)`           | Inserts at the beginning    | `myList.addFirst("L")`     |
| `addLast(Object o)`            | Appends to the end          | `myList.addLast("9")`      |
| `size()`                       | Returns number of elements  | `myList.size()`            |
| `contains(Object o)`           | Checks if an element exists | `myList.contains("L")`     |
| `getFirst()` / `getLast()`     | Gets first or last element  | `myList.getFirst()`        |
| `set(int index, Object value)` | Updates element at index    | `myList.set(2, "Changed")` |

---

#### Full Java Code

```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        LinkedList<String> myList = new LinkedList<>();
        myList.add("I");
        myList.add("S");
        myList.add("T");
        System.out.println("Linked List = " + myList);

        myList.addFirst("L");
        myList.addLast("9");
        System.out.println("Try Again! " + myList);

        myList.remove("9");
        System.out.println("After removal: " + myList);

        Object item = myList.get(2);
        myList.set(2, (String) item + " Changed");
        System.out.println("After the change: " + myList);
    }
}
```

**Final Output:**

```
Linked List = [I, S, T]
Try Again! [L, I, S, T, 9]
After removal: [L, I, S, T]
After the change: [L, I, S Changed, T]
```

---

#### Lesson Summary

* **Arrays** are static, fixed-size containers for data. They allow fast access but are rigid when it comes to insertion and deletion.
* **Linked Lists** are dynamic structures that allow flexibility in adding and removing elements.
* Each node in a singly linked list points to the next. The head is the start, and the tail is the end.
* Java's `LinkedList` class supports all basic operations such as `add`, `remove`, `get`, `set`, and more.
* Linked lists are ideal when the number of elements may change frequently.

### Section 4: Circularly Linked Lists

#### What Is a Circularly Linked List?

* Unlike a single- or double-linked list, a **circularly linked list** connects back to itself.
* Think of a **child’s toy train** where the engine is connected to the caboose.
* The last node connects to the **first node**, forming a continuous loop.

#### Circularly Linked Lists vs Linked Lists

* Used when you need to **loop through elements repeatedly**.
* Ideal for systems like **round-robin scheduling** in operating systems.
* After allocating CPU time, the first node moves to the end, giving each process a fair chance.

#### Practical Applications

* **GPS/Navigation tools**: Vehicles using circular routes (buses, trains) can represent stops as nodes, looping from end to start.
* **Hash tables**: Helps prevent **collisions** — colliding keys can be stored in a circular list.
* **Media players**: Playlists using circular lists can **loop continuously**.
* **Queues**: Elements are **added to the back** and **removed from the front** — perfect for circular implementation.
* **Memory management**: Circular lists track free/used memory, and loop back after reclaiming space.

#### Implementing in Java

* We will build a **circular linked list** and simulate **round-robin rotation**.

#### Create the Java File

* Use Java 11 (e.g., on Replit).
* Begin by updating `Main.java`:

```java
import java.util.*;
class Main {
  public static void main(String[] args) {
  }
}
```

* Create two more files:

  * `CircularLinkedList.java`
  * `Node.java`

#### Update CircularLinkedList.java

```java
import java.util.*;
public class CircularLinkedList {
  public int size = 0;
  public Node head = null;
  public Node tail = null;
}
```

#### Update the Node Class

```java
class Node {
  int element;
  Node next;
  public Node(int element){
    this.element = element;
  }
}
```

#### Print Function

* Loops through and displays elements.
* Use a `do-while` loop to prevent infinite looping:

```java
public void print(){
  System.out.print("The List So Far:");
  Node temp = head;
  do {
    System.out.print(" " + temp.element);
    temp = temp.next;
  } while(temp != head);
  System.out.println();
}
```

#### Add Node to Head

```java
public void addNodeToHead(int element){
  Node n = new Node(element);
  if(size == 0){
    head = n;
    tail = n;
    n.next = head;
  } else {
    Node temp = head;
    n.next = temp;
    head = n;
    tail.next = head;
  }
  size++;
}
```

#### Update Main.java

```java
import java.util.*;
class Main {
  public static void main(String[] args) {
    CircularLinkedList myList = new CircularLinkedList();
    myList.addNodeToHead(75);
    myList.addNodeToHead(50);
    myList.addNodeToHead(25);
    myList.print();
  }
}
```

* **Output:**

  * `The List So Far: 25 50 75`

#### Add Node to Tail

```java
public void addNodeToTail(int element){
  if(size == 0){
    addNodeToHead(element);
  } else {
    Node n = new Node(element);
    tail.next = n;
    tail = n;
    tail.next = head;
    size++;
  }
}
```

* Add to `main()`:

```java
myList.addNodeToTail(100);
myList.print();
```

#### Round Robin Rotation

```java
public void rotateElement() {
  System.out.println("Rotating!");
  tail = head;
  head = head.next;
}
```

* Add to `main()`:

```java
myList.rotateElement();
myList.print();
```

#### Delete Node from Tail

```java
public void deleteNodeFromTail() {
  System.out.println("\nDeleting Node " + tail.element + " from Tail");
  if(tail.next == tail) {
    tail = null;
  }
  Node newTail = tail;
  while(newTail.next != tail) {
    newTail = newTail.next;
  }
  newTail.next = tail.next;
  tail = newTail;
}
```

* Add to `main()`:

```java
myList.deleteNodeFromTail();
myList.print();
```

#### Delete Node from Head

```java
public void deleteNodeFromHead(){
  head = head.next;
  tail.next = head;
  size--;
}
```

* Add to `main()`:

```java
myList.deleteNodeFromHead();
myList.print();
```

#### Lesson Summary

* A **circularly linked list** connects tail-to-head.
* Used in **round-robin scheduling**, **media players**, and **queues**.
* Java implementation requires a `Node` class and a `CircularLinkedList` class.
* You can **rotate**, **add**, **delete**, and **traverse** using custom methods.

### Section 5: Doubly Linked Lists

#### What Is a Doubly Linked List?

* When you **browse the Internet** and click **Back** or **Forward**, you're using a **doubly linked list**.
* Your browser strings together your **viewing history**, tracking where you've been and where you can go.
* A doubly linked list node tracks both the **previous** and the **next** item.
* If a node has no previous, it's the **head**; if no next, it's the **tail**.

#### Real-World Example

* If you're at the **end of your browsing session**, there's no forward page — you're at the **tail**.
* The list enables easy traversal **both directions**, like navigating browser history.

#### Node Class

* In Java, each page or item is a **Node**, which can move **forward and backward**.
* Each node must track:

  * The **next node**
  * The **previous node**

```java
class Node {
  int data;
  Node next;
  Node prev;

  public Node(int data) {
    this.data = data;
  }
}
```

#### Uses for a Doubly Linked List

* **Operating systems**: Scheduling running processes.
* **Card games**: Like a deck of cards that can be shuffled or reversed.
* **Undo/Redo**: Step forward or backward in changes.
* **Media players**: Next/Previous track navigation.
* **Web navigation**: Back and forward between visited pages.

#### DoubleLists Class

```java
import java.util.*;
public class DoubleLists {
  Node head;
}
```

All further methods are added inside the `DoubleLists` class.

#### Add to Head

```java
public void addToHead(int element) {
  Node n = new Node(element);
  n.next = head;
  n.prev = null;
  if(head != null) {
    head.prev = n;
  }
  head = n;
}
```

#### Add to Tail

```java
public void addToTail(int element) {
  Node n = new Node(element);
  Node end = head;
  n.next = null;

  if(head == null) {
    n.prev = null;
    head = n;
    return;
  }

  while(end.next != null) {
    end = end.next;
  }

  end.next = n;
  n.prev = end;
}
```

#### Insert at a Given Position

```java
public void insertNode(Node prev, int element) {
  if(prev == null) {
    System.out.println("Cannot have previous node of null");
    return;
  }

  Node n = new Node(element);
  n.next = prev.next;
  prev.next = n;
  n.prev = prev;

  if(n.next != null) {
    n.next.prev = n;
  }
}
```

#### Print List (Forward and Backward)

```java
public void printList(Node node) {
  System.out.println("Going forward --> ");
  Node end = null;
  while(node != null) {
    System.out.print(node.data + " ");
    end = node;
    node = node.next;
  }

  System.out.println();
  System.out.println("<-- Going backward ");
  while(end != null) {
    System.out.print(end.data + " ");
    end = end.prev;
  }
}
```

#### Main Class

```java
import java.util.*;
public class Main {
  public static void main(String[] args) {
    DoubleLists dll = new DoubleLists();
    dll.addToHead(50);
    dll.addToTail(100);
    dll.addToHead(25);
    dll.insertNode(dll.head.next, 75);
    dll.printList(dll.head);
  }
}
```

* **Output should be:**

  * `Going forward --> 25 50 75 100`
  * `<-- Going backward 100 75 50 25`

#### Complete Code

```java
import java.io.*;
import java.math.*;

public class Main {
  public static class Node {
    int data;
    Node next;
    Node prev;
    public Node(int data) {
      this.data = data;
    }
  }

  public static class DoubleLists {
    Node head;

    public void addToHead(int element) {
      Node n = new Node(element);
      n.next = head;
      n.prev = null;
      if(head != null) {
        head.prev = n;
      }
      head = n;
    }

    public void addToTail(int element) {
      Node n = new Node(element);
      Node end = head;
      n.next = null;

      if(head == null) {
        n.prev = null;
        head = n;
        return;
      }

      while(end.next != null) {
        end = end.next;
      }

      end.next = n;
      n.prev = end;
    }

    public void insertNode(Node prev, int element) {
      if(prev == null) {
        System.out.println("Cannot have previous node of null");
        return;
      }

      Node n = new Node(element);
      n.next = prev.next;
      prev.next = n;
      n.prev = prev;

      if(n.next != null) {
        n.next.prev = n;
      }
    }

    public void printList(Node node) {
      System.out.println("Going forward --> ");
      Node end = null;
      while(node != null) {
        System.out.print(node.data + " ");
        end = node;
        node = node.next;
      }

      System.out.println();
      System.out.println("<-- Going backward ");
      while(end != null) {
        System.out.print(end.data + " ");
        end = end.prev;
      }
    }
  }

  public static void main(String args[]) {
    DoubleLists dll = new DoubleLists();
    dll.addToHead(50);
    dll.addToTail(100);
    dll.addToHead(25);
    dll.insertNode(dll.head.next, 75);
    dll.printList(dll.head);
  }
}
```

#### Lesson Summary

* A **doubly linked list** connects nodes **both forward and backward**.
* The **head** has no previous node; the **tail** has no next node.
* Used in **Undo/Redo**, **navigation**, **task schedulers**, and more.
* You need a **Node** class with `next` and `prev`, and a **list class** to manage operations.
* Key operations:

  * **Add to head**
  * **Add to tail**
  * **Insert at position**
  * **Print both ways**


### Section 6: Introduction to Queues

#### Real-World Analogy

* Imagine standing in line at a **busy coffee shop**.
* You wait your turn — no one **cuts** the line, and everyone gets served in order.
* This is how a **queue** works in Java: **first-in, first-out (FIFO)**.
* Anything can be stored in a queue: **numbers, strings, objects**, and more.

#### What Is a Queue?

* A **queue** is an **abstract data type** — it’s **defined by behavior**, not by structure.
* Unlike `int x = 5`, you don't define a queue directly.
* Instead, you use methods to interact with the queue: **add, peek, remove**, etc.
* Java provides the **Queue Interface** to define and manage queues.

#### First-In, First-Out (FIFO)

* **New elements** are added at the **end** of the queue.
* **Removal** happens from the **front** of the queue.
* There is **no cutting** in line — queue discipline is enforced by the interface.

#### The Queue Interface in Java

Java’s Queue Interface has **6 methods**, grouped into **3 pairs**:

| Method      | Purpose                              | Result                                               |
| ----------- | ------------------------------------ | ---------------------------------------------------- |
| `add()`     | Adds new item to end of queue        | Adds item; throws exception if no room               |
| `offer()`   | Adds new item to end of queue        | Adds item; **no exception** if no room               |
| `element()` | Retrieves front item (no removal)    | Retrieves; throws exception if queue is empty        |
| `peek()`    | Retrieves front item (no removal)    | Retrieves; returns `null` if queue is empty          |
| `remove()`  | Retrieves **and removes** front item | Removes item; **throws exception** if queue is empty |
| `poll()`    | Retrieves **and removes** front item | Removes item; **returns null** if queue is empty     |

* `add` and `offer`: for **inserting**
* `element` and `peek`: for **looking**
* `remove` and `poll`: for **removing**
* One method in each pair **throws an exception**; the other is **safe**.

#### Implementing a Queue in Java

```java
import java.util.LinkedList;
import java.util.Queue;

public class Main {
  public static void main(String[] args) {
    Queue<String> coffeeShop = new LinkedList<String>();
    coffeeShop.add("Sally");
    coffeeShop.add("Debra");
    coffeeShop.add("Jimmy");
    coffeeShop.add("Cindy");

    System.out.println(coffeeShop.peek()); // Output: Sally
  }
}
```

#### Removing Customers from the Queue

```java
coffeeShop.remove(); // removes Sally
coffeeShop.remove(); // removes Debra
System.out.println(coffeeShop.element()); // Output: Jimmy
```

* `remove()` deletes the first two; `element()` shows the next.

#### Alternating Remove and Poll

```java
coffeeShop.remove(); // removes Jimmy
coffeeShop.poll();   // removes Cindy
coffeeShop.remove(); // throws exception (queue is now empty)
```

* Use `poll()` to avoid exceptions, or wrap `remove()` in a try-catch block.

#### Try-Catch for Empty Queue

```java
import java.util.*;

public class Main {
  public static void main(String[] args) {
    Queue<String> coffeeShop = new LinkedList<String>();
    coffeeShop.add("Sally");
    coffeeShop.add("Debra");
    coffeeShop.add("Jimmy");
    coffeeShop.add("Cindy");

    System.out.println(coffeeShop.peek());

    coffeeShop.remove();
    coffeeShop.remove();

    System.out.println(coffeeShop.element());

    coffeeShop.remove();
    coffeeShop.poll();

    try {
      coffeeShop.remove();
    } catch(NoSuchElementException e) {
      System.out.println("Oops! It doesn't exist!");
    }
  }
}
```

* Output will show each customer as they are served.
* Final `remove()` throws an exception, caught by the `catch` block.

#### Advanced Considerations

* **Arrays** and **ArrayLists** can also be used to implement queues.

  * Arrays require **fixed size**.
  * ArrayLists are **dynamic** in size.
* Choose **arrays** for efficiency when size is known.
* Choose **ArrayLists** when the size is **unpredictable or always changing**.

#### Lesson Summary

* Queues are **first-in, first-out** abstract data types.
* Java’s **Queue Interface** offers 6 key methods for queue interaction.
* Three method pairs:

  * **Add**: `add()` (throws) and `offer()` (safe)
  * **View**: `element()` (throws) and `peek()` (safe)
  * **Remove**: `remove()` (throws) and `poll()` (safe)
* Use **try-catch** blocks or `poll()` to handle empty queue scenarios safely.
* Queues can be implemented using **arrays** or **ArrayLists**, depending on size constraints.

### Section 7: Double-Ended Queues

#### What Is a Double-Ended Queue?

* A **double-ended queue** (or **deque**) can act as both a **queue** (first-in, first-out) and a **stack** (last-in, first-out).
* Regular queues have a **head** and **tail** — elements are added to the back and removed from the front.
* Stacks add and remove elements from the **top** only.
* A **deque allows operations at both ends** — elements can be added or removed from the **front or back**.
* Deques in Java are implemented using the **Deque Interface**.

#### Deques as Abstract Data Types

* Like stacks and queues, **deques are abstract data types**.
* You don't directly define what goes in — instead, you use **methods** to work with the data.
* Deques can store any type of object: **numbers, strings, or custom objects**.

#### Practical Application: Work Queue

* Deques are useful in specific scenarios, such as **manufacturing workflows**.
* Example: Widgets wait in a **work queue** for inspection.
* Based on inspection results:

  * Passed? → Remove from front of queue.
  * Minor fix? → Keep at the **head**.
  * Major fix? → Move to the **tail**.
* This process allows **dynamic prioritization** from both ends.

#### Creating a Deque in Java

```java
Deque workQueue = new LinkedList<>();
```

* The **LinkedList class** implements the **Deque interface**.

#### Add Elements to Deque

```java
workQueue.add("widget 001");
workQueue.add("widget 002");
workQueue.add("widget 003");
workQueue.add("widget 004");
workQueue.add("widget 005");
System.out.println(workQueue);
```

* Adds widgets to the **tail** of the deque.
* Output:
  `widget 001, widget 002, widget 003, widget 004, widget 005`

#### Inspect and Process a Widget

```java
System.out.println("Inspecting " + workQueue.peek());

int status = 1;

if (status == 1) {
  workQueue.removeFirst();
  System.out.println("Widget passed inspection; removed from deque.");
} else if (status == 0) {
  System.out.println("Widget left at head of deque for minor work.");
} else if (status == -1) {
  Object inspectionItem = workQueue.pollFirst();
  workQueue.addLast(inspectionItem);
  System.out.println("Widget moved to tail of deque for major work.");
}

System.out.println(workQueue);
```

* `peek()` → Views the item at the front.
* `removeFirst()` → Removes from front.
* `pollFirst()` → Retrieves and removes safely.
* `addLast()` → Adds to the back of the deque.

#### Scenario 1: Status = 1

* Widget **passed inspection** and is **removed** from the deque.

```
Inspecting widget 001  
Widget passed inspection; removed from deque.  
widget 002, widget 003, widget 004, widget 005
```

#### Scenario 2: Status = 0

* Widget needs **minor work** and stays at the front.

```
Inspecting widget 001  
Widget left at head of deque for minor work.  
widget 001, widget 002, widget 003, widget 004, widget 005
```

#### Scenario 3: Status = -1

* Widget needs **major work**, removed from front and moved to the end.

```
Inspecting widget 001  
Widget moved to tail of deque for major work.  
widget 002, widget 003, widget 004, widget 005, widget 001
```

#### Add a Priority Widget to the Front

```java
workQueue.addFirst("Priority Widget 319");
System.out.println(workQueue);
```

* Output:
  `Priority Widget 319, widget 001, widget 002, widget 003, widget 004, widget 005`

#### Full Code

```java
import java.util.*;
public class Main {
  public static void main(String[] args) {
    Deque workQueue = new LinkedList<>();
    workQueue.add("widget 001");
    workQueue.add("widget 002");
    workQueue.add("widget 003");
    workQueue.add("widget 004");
    workQueue.add("widget 005");

    System.out.println(workQueue);

    System.out.println("Inspecting " + workQueue.peek());

    int status = 1;
    if (status == 1) {
      workQueue.removeFirst();
      System.out.println("Widget passed inspection; removed from deque.");
    } else if (status == 0) {
      System.out.println("Widget left at head of deque for minor work.");
    } else if (status == -1) {
      Object inspectionItem = workQueue.pollFirst();
      workQueue.addLast(inspectionItem);
      System.out.println("Widget moved to tail of deque for major work.");
    }

    System.out.println(workQueue);

    workQueue.addFirst("Priority Widget 319");
    System.out.println(workQueue);
  }
}
```

#### Lesson Summary

* A **double-ended queue (deque)** can function as a **queue or a stack**.
* Java uses the **Deque Interface**, implemented by `LinkedList`.
* Methods include:

  * `addFirst()` – Add to the head
  * `addLast()` – Add to the tail
  * `peek()` – View head item
  * `removeFirst()` – Remove head
  * `pollFirst()` – Safely retrieve and remove head
* Deques are flexible for **inspection processes**, **priority handling**, and **real-world scheduling**.

### Section 8: Priority Queues

#### What Is a Priority Queue?

* A **priority queue** is a special kind of queue where elements are **removed based on priority**, not order of insertion.
* Java provides this with the **`PriorityQueue`** class, which extends `AbstractQueue` and implements `Serializable`.
* While normal queues follow **first-in, first-out**, priority queues remove the **highest priority item** first.

#### Priority Criteria

* By default, Java uses **natural order**:

  * **Alphabetical** for strings
  * **Numerical** for numbers
* You can define **custom priorities** using classes that implement the `Comparable` interface.
* Priority queues work well in systems where **task priority overrides order**.

---

#### Priority Queue with an Unsorted List

#### Creating and Populating a Priority Queue

```java
import java.util.PriorityQueue;

public class Main {
  public static void main(String[] args) {
    PriorityQueue<String> myPriorityQueue = new PriorityQueue<String>();
    myPriorityQueue.add("Augustus");
    myPriorityQueue.add("Tiberius");
    myPriorityQueue.add("Caligula");
    myPriorityQueue.add("Claudius");
    myPriorityQueue.add("Nero");
    myPriorityQueue.add("Galba");
    myPriorityQueue.add("Otho");
    myPriorityQueue.add("Aulus Vitellius");
    myPriorityQueue.add("Vespasian");
    myPriorityQueue.add("Titus");
    myPriorityQueue.add("Domitian");
    myPriorityQueue.add("Nerva");
  }
}
```

#### Natural Ordering Example

* Java alphabetizes the list automatically using **natural order**.
* When calling `remove()`, the **alphabetically first** item is removed — **not** the first one added.

```java
myPriorityQueue.remove();
System.out.println(myPriorityQueue);
```

* **Result**: `"Augustus"` is removed because it is alphabetically first, not because it was added first.

---

#### Priority Queue with a Custom Sorted List

#### Define Custom Priority with a New Class

```java
import java.util.*;

public class RomanRulers implements Comparable<RomanRulers> {
  private int rulerID;
  private String rulerName;

  public RomanRulers(int id, String name) {
    rulerID = id;
    rulerName = name;
  }

  public int getRulerID() {
    return rulerID;
  }

  public String getRulerName() {
    return rulerName;
  }

  @Override
  public boolean equals(Object obj) {
    if (this == obj) return true;
    if (!(obj instanceof RomanRulers)) return false;
    RomanRulers theOther = (RomanRulers) obj;
    return this.getRulerID() == theOther.getRulerID();
  }

  public int compareTo(RomanRulers theOther) {
    return Integer.compare(this.rulerID, theOther.rulerID);
  }

  @Override
  public String toString() {
    return "Ruler Succession # " + getRulerID() + "\tRuler Name: " + getRulerName();
  }
}
```

---

#### Custom PriorityQueue in Main Class

```java
import java.util.PriorityQueue;

public class Main {
  public static void main(String[] args) {
    PriorityQueue<RomanRulers> theRulers = new PriorityQueue<RomanRulers>();

    theRulers.add(new RomanRulers(1, "Augustus"));
    theRulers.add(new RomanRulers(2, "Tiberius"));
    theRulers.add(new RomanRulers(3, "Caligula"));
    theRulers.add(new RomanRulers(4, "Claudius"));
    theRulers.add(new RomanRulers(5, "Nero"));
    theRulers.add(new RomanRulers(6, "Galba"));
    theRulers.add(new RomanRulers(7, "Otho"));
    theRulers.add(new RomanRulers(8, "Aulus Vitellius"));
    theRulers.add(new RomanRulers(9, "Vespasian"));
    theRulers.add(new RomanRulers(10, "Titus"));
    theRulers.add(new RomanRulers(11, "Domitian"));
    theRulers.add(new RomanRulers(12, "Nerva"));

    while (!theRulers.isEmpty()) {
      System.out.println(theRulers.poll());
    }
  }
}
```

#### Sample Output

```
Ruler Succession # 1	Ruler Name: Augustus  
Ruler Succession # 2	Ruler Name: Tiberius  
Ruler Succession # 3	Ruler Name: Caligula  
...  
Ruler Succession # 12	Ruler Name: Nerva
```

* Items are removed based on **succession order**, not natural alphabetical order.

---

#### Comparing Implementations

#### Unsorted List

* **Fast add** operations.
* **Slow remove** – entire list must be searched for the highest priority.

#### Sorted List

* **Fast remove** operations – highest priority is always at the front.
* **Slower add** – items must be inserted at the correct position.

---

#### Lesson Summary

* **Priority queues** remove elements based on **priority**, not insertion order.
* Java uses **natural ordering** by default (alphabetical or numerical).
* You can define **custom priorities** using the `Comparable` interface.
* Use priority queues when task execution should depend on importance.
* Two ways to implement:

  * **Unsorted list** – fast insert, slow delete
  * **Sorted list** – slow insert, fast delete
