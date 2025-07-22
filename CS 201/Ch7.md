Look at  109 -> Ch7.md for more content

### Section 1: Abstract Data Type (ADT) — Positional List in Java

#### What Is an Abstract Data Type (ADT)?

An **Abstract Data Type (ADT)** is a class or structure that defines a set of **values** and **operations** without specifying how the data is stored in memory.

> Think of an ADT as a **black box**:
> You interact with its features (methods), but you don’t need to know the internal logic.

A real-world example of an ADT is a **playlist** in apps like iTunes or Spotify. You can rearrange or play songs from the list without knowing how the data is structured behind the scenes.

---

#### The Positional List ADT in Java

In Java, a **positional list** is a dynamic list structure that lets you **add, remove, insert, or sort** elements — not limited to the beginning or end.

It combines behaviors from both **queues** (add at end) and **stacks** (add/remove from top). The list consists of **nodes**, each pointing to the **next** (and optionally previous) node.

> Figure 1 would show a visual of a linked list with `head`, `tail`, and `nodes`.

---

#### Structure of a Positional List

* Each element in the list is a **node**
* The list has a **head** (start) and a **tail** (end)
* Nodes connect via pointers (`next`, optionally `prev`)
* Unlike arrays, elements are not stored contiguously in memory

---

#### Creating a Positional List in Java

**Step 1 — Basic Class Structure**

```java
import java.util.*;

public class PositionalList {
    public int size = 0;
    public Node head = null;
    public Node tail = null;

    public static void main(String[] args) {
    }

    class Node {
        int data;
        Node next;

        public Node(int data){
            this.data = data;
        }
    }
}
```

---

**Step 2 — Add Node at the Start**

```java
public void addNodeAtStart(int data) {
    Node n = new Node(data);
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

This method:

* Adds a node at the **head**
* Updates the `tail.next` to point back to the new head (circular list)

---

**Step 3 — Print the List**

```java
public void print(){
    System.out.print("Positional List:");
    Node temp = head;
    if(size <= 0){
        System.out.print(" List is empty");
    } else {
        do {
            System.out.print(" " + temp.data);
            temp = temp.next;
        } while(temp != head);
    }
    System.out.println();
}
```

---

**Step 4 — Using the Positional List in `main()`**

```java
PositionalList pl = new PositionalList();
for(int i = 0; i < 25; i++) {
    pl.addNodeAtStart(i + 5);
}
pl.print();
```

**Output:**

```
Positional List: 29 28 27 26 25 24 23 22 21 20 19 18 17 16 15 14 13 12 11 10 9 8 7 6 5
```

---

#### Accessing Nodes in the List

To **access a specific node**, use the following method:

```java
public int elementAt(int index){
    if(index > size){
        return -1;
    }
    Node n = head;
    while(index - 1 != 0){
        n = n.next;
        index--;
    }
    return n.data;
}
```

**Explanation:**

* Checks if the index is in range
* Traverses the list until the target node is reached
* Returns the `data` of the node

**Call it in `main()`**:

```java
System.out.println("Element at 21st Index = " + pl.elementAt(21));
```

**Output:**

```
Element at 21st Index = 9
```

---

#### Lesson Summary

* A **positional list** in Java is an **abstract data type (ADT)** — it defines the interface, not the implementation.
* It supports:

  * **Access**
  * **Insertion**
  * **Removal**
  * **Traversal**
* Combines **queue** and **stack** behaviors.
* Elements are stored as **nodes**, linked via pointers.
* The **head** marks the start, and the **tail** marks the end of the list.
* With `elementAt()`, we can access specific nodes by index.

### Section 2: Introduction to the Java Collections Framework

#### What Is the Java Collections Framework?

The **Java Collections Framework** is a unified architecture for representing and manipulating **collections of objects**. It consists of:

* **Interfaces** (e.g., List, Set, Map)
* **Implementations** (e.g., ArrayList, HashSet)
* **Algorithms** (e.g., sorting, searching)

> The collections framework defines **common behaviors** across all collection types, promoting:
>
> * Efficient programming
> * High-performance code
> * Improved portability across Java applications

---

#### The List Interface

The **List interface** is part of the Java Collections Framework and also extends the **Iterable** interface, which allows iteration using enhanced for-loops.

> Figure: Java Collections Framework → List Interface Inheritance

The List interface provides:

* Over two dozen native methods
* Inherited capabilities from `Collection` and `Iterable`
* Full control over element positioning and order

---

#### Working with Lists

To demonstrate how to use the **List interface**, let’s use `ArrayList` — one of its most common implementations.

```java
List<String> myList = new ArrayList<>();
myList.add("This");
myList.add("makes");
myList.add("no");
myList.add("sense");
```

We can **retrieve** a specific element using the `get()` method:

```java
System.out.println(myList.get(1));
```

> Output:

```
makes
```

Now let’s **replace** an item and iterate through the list:

```java
myList.set(2, "perfect");
for (String theValue : myList) {
    System.out.print(theValue + " ");
}
```

> Output:

```
This makes perfect sense
```

---

#### Searching and Sorting Lists

Let’s create a new list of names:

```java
List<String> listOfNames = new ArrayList<>();
listOfNames.add("jimmy");
listOfNames.add("sally");
listOfNames.add("cindy");
listOfNames.add("rhona");
listOfNames.add("john");
listOfNames.add("brenda");
listOfNames.add("lona");
```

---

**Searching**:

```java
if (listOfNames.contains("brenda")) {
    System.out.println("Record found!");
} else {
    System.out.println("Record not found!");
}
```

> Output:

```
Record found!
```

---

**Sorting**:

```java
Collections.sort(listOfNames);
for (String theName : listOfNames) {
    System.out.println(theName);
}
```

---

**Capitalizing First Letters**:

```java
for (int i = 0; i < listOfNames.size(); i++) {
    String tempName = listOfNames.get(i);
    listOfNames.set(i, tempName.substring(0, 1).toUpperCase() + tempName.substring(1));
}
```

**Print the List**:

```java
for (String theName : listOfNames) {
    System.out.println(theName);
}
```

Or all at once:

```java
System.out.println(listOfNames);
```

> Output:

```
[Brenda, Cindy, Jimmy, John, Lona, Rhona, Sally]
```

---

#### Algorithms for Lists

Java provides several **built-in algorithms** to manipulate Lists using the `Collections` class.

| **Algorithm**  | **Description**                              |
| -------------- | -------------------------------------------- |
| `binarySearch` | Uses a binary search algorithm               |
| `copy`         | Duplicates one list into another             |
| `fill`         | Replaces all elements with a specified value |
| `replaceAll`   | Performs global find-and-replace             |
| `reverse`      | Reverses the order of elements               |
| `shuffle`      | Randomly reorders the elements               |
| `sort`         | Sorts the list in ascending order            |
| `swap`         | Swaps two elements in the list               |

---

#### Lesson Summary

* Java's **Collections Framework** includes **interfaces**, **implementations**, and **algorithms** that help you build efficient and reusable data structures.
* The **List interface** supports element operations like **add**, **update**, **search**, and **remove**.
* The **ArrayList** is a dynamic array that supports random access and is one of the most commonly used List implementations.
* With built-in methods and algorithms, **sorting, searching, and modifying** lists becomes fast and easy.

### Section 3: An Introduction to Positional Lists

#### What Are Positional Lists?

A **Positional List** is a data structure that stores elements where each element has a **specific position**. These positions are referenced numerically — starting from index `0` — to indicate where each element is located in the list.

> Example:
> Think of a **grocery list**, a **basketball team roster**, or a **list of dog names**.
> Each entry holds a position and can be accessed directly or sequentially.

---

#### Working with Positional Lists

The most common Java implementation of a positional list is the **ArrayList**. It is an **abstract data structure** because it stores references to elements, but the specific data types can vary.

---

#### Instantiating a Positional List

To begin working with a list, you first need to import the relevant Java packages:

```java
import java.util.ArrayList;
import java.util.List;
import java.util.Collections;

public class PositionalListExample {
    public static void main(String[] args) {
        List<String> dogNames = new ArrayList<>();
    }
}
```

---

#### Adding Data to a Positional List

Use the `add()` method to add items to the list. By default, this appends items to the **end**:

```java
dogNames.add("Fido");
dogNames.add("Java");
dogNames.add("Cuddles");
dogNames.add("Abby");
dogNames.add("Muzz");
dogNames.add("Brandy");

System.out.println(dogNames);
```

> Output:

```
[Fido, Java, Cuddles, Abby, Muzz, Brandy]
```

You can also insert at a **specific position** by passing an index:

```java
dogNames.add(1, "George");
System.out.println(dogNames);
```

> Output:

```
[Fido, George, Java, Cuddles, Abby, Muzz, Brandy]
```

---

#### Getting Data from the List

Use the `get()` method to retrieve an element at a specific position:

```java
String theDog = dogNames.get(2);
System.out.println("The dog at position number 2 (3rd dog) is " + theDog + ".");
```

> Output:

```
The dog at position number 2 (3rd dog) is Java.
```

Use the `size()` method to count the elements:

```java
int numberOfDogs = dogNames.size();
System.out.println("There are " + numberOfDogs + " dogs on the list.");
```

> Output:

```
There are 7 dogs on the list.
```

---

#### Iterating Through a List

The most common way to loop through a list is with a `for` loop:

```java
for (int thePosition = 0; thePosition < dogNames.size(); thePosition++) {
    System.out.println("The dog at Position " + thePosition + " is " + dogNames.get(thePosition));
}
```

> Output:

```
The dog at Position 0 is Fido  
The dog at Position 1 is George  
The dog at Position 2 is Java  
The dog at Position 3 is Cuddles  
The dog at Position 4 is Abby  
The dog at Position 5 is Muzz  
The dog at Position 6 is Brandy
```

---

#### Sorting a Positional List

Use the `sort()` method from the `Collections` class to sort elements:

```java
System.out.println(dogNames); // Before sorting
Collections.sort(dogNames);
System.out.println(dogNames); // After sorting
```

> Output:

```
[Fido, George, Java, Cuddles, Abby, Muzz, Brandy]  
[Abby, Brandy, Cuddles, Fido, George, Java, Muzz]
```

---

#### Full Code Example

```java
import java.util.ArrayList;
import java.util.List;
import java.util.Collections;

public class PositionalListExample {
    public static void main(String[] args) {
        List<String> dogNames = new ArrayList<>();

        dogNames.add("Fido");
        dogNames.add("Java");
        dogNames.add("Cuddles");
        dogNames.add("Abby");
        dogNames.add("Muzz");
        dogNames.add("Brandy");

        System.out.println(dogNames);

        dogNames.add(1, "George");
        System.out.println(dogNames);

        String theDog = dogNames.get(2);
        System.out.println("The dog at position number 2 (3rd dog) is " + theDog + ".");

        int numberOfDogs = dogNames.size();
        System.out.println("There are " + numberOfDogs + " dogs on the list.");

        for (int thePosition = 0; thePosition < dogNames.size(); thePosition++) {
            System.out.println("The dog at Position " + thePosition + " is " + dogNames.get(thePosition));
        }

        System.out.println(dogNames); // Before sorting
        Collections.sort(dogNames);
        System.out.println(dogNames); // After sorting
    }
}
```

---

#### Lesson Summary

* A **positional list** is an **abstract data structure** that stores a series of **related elements**, each referenced by a numeric **position**.
* Implemented via **ArrayList**, it allows for:

  * Adding elements (with or without position)
  * Accessing specific elements
  * Iterating through the list
  * Sorting elements using `Collections.sort()`
* Common methods include:

  * `add()`
  * `get()`
  * `size()`
  * `sort()`
* Positional lists are ideal for tasks where order matters and frequent access or updates are needed.
