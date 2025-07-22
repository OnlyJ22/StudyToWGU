Look at  109 -> Ch3.md for more content

### Section 1: The Linked List Data Structure

#### What Is a Linked List?

A **linked list** is a linear data structure where each element is a **node**, and each node contains:

* A **data field**
* A **reference** (pointer) to the next node in the sequence

> Think of it like your **browsing history**:
> Clicking "Back" or "Forward" steps through web pages like a linked list navigates nodes.

The **first node** is the **head**, and the **last node** is the **tail**. In a basic singly linked list, the tail node points to **`null`**, indicating the end.

---

#### Singly Linked List

A **singly linked list** connects each node to the **next** one only. It allows **one-way traversal** — from head to tail.

> Analogy: A **train** where each car is connected only to the one in front of it.

**Use Cases:**

* Undo/Redo functionality
* Building other structures like **hash tables**
* Graphs and adjacency matrices

---

#### Doubly Linked List

A **doubly linked list** allows **two-way traversal** — each node stores:

* A pointer to the **next** node
* A pointer to the **previous** node

> Analogy: **Web browser history** — you can go **backward** and **forward** between pages.

**Advantages:**

* Easier to reverse and traverse in both directions
* Insertions and deletions are more flexible

---

#### Circular Linked List

A **circular linked list** is a variation of the singly linked list, except the **tail points back to the head**.

> There’s **no end** — you can **loop infinitely** through the list.

Only **forward traversal** is allowed unless implemented as a **circular doubly linked list**.

**Used in:**

* Memory storage
* Operating system task scheduling
* Circular buffers

---

#### Linked List vs. Array

| **Feature**            | **Linked List**                        | **Array**                           |
| ---------------------- | -------------------------------------- | ----------------------------------- |
| **Memory layout**      | Non-contiguous                         | Contiguous                          |
| **Size**               | Dynamic (can grow/shrink)              | Fixed-length (unless reallocated)   |
| **Insertion/Deletion** | Easy, constant time (if pointer known) | Costly (requires shifting elements) |
| **Random Access**      | Not supported                          | Supported (access via index)        |
| **Traversal**          | Sequential (must follow links)         | Direct via index                    |
| **Search**             | Linear search only                     | Binary search possible (if sorted)  |

> Linked lists provide **flexibility**, but require traversal — you **can’t jump** to an element like with an array.

---

#### Linked List Methods (Common Operations)

| **Method**                       | **Description**                    |
| -------------------------------- | ---------------------------------- |
| `add()`                          | Adds a node to the end of the list |
| `addFirst()`                     | Adds a node to the beginning       |
| `getFirst()` / `getLast()`       | Returns the first or last node     |
| `removeFirst()` / `removeLast()` | Removes the first or last node     |
| `print()`                        | Displays the list contents         |

---

#### Lesson Summary

* A **linked list** is a sequence of connected **nodes**, where each node points to the **next** (and optionally the previous).
* The **head** is the first node; the **tail** is the last.
* Types of linked lists:

  * **Singly Linked List** – One-directional
  * **Doubly Linked List** – Two-directional (forward/backward)
  * **Circular Linked List** – Tail connects back to head
* Linked lists differ from arrays by:

  * Using **non-contiguous memory**
  * Requiring **linear traversal**
  * Being **dynamically resizable**
* Common in:

  * **Memory management**
  * **Operating system task scheduling**
  * **Graph structures**, **buffers**, and **hash collisions**

### Section 2: Array Comparison in Java

#### Why Array Comparison Is Tricky

At first glance, comparing two Java arrays should be easy. After all, arrays seem like any other variable. However, using `==` or `.equals()` doesn't behave as you might expect.

> Arrays are **objects** in Java — comparing them with `==` or `.equals()` checks **references**, not contents.

---

#### What Doesn’t Work

##### **Test 1 — Using `==`**

```java
import java.util.*;

public class Main {
    public static void main(String[] a) {
        int var1[] = {1, 2, 3};  // First array
        int var2[] = {1, 2, 3};  // Second array

        if (var1 == var2) {
            System.out.println("Equivalent");
        } else {
            System.out.println("Not Equivalent");
        }
    }
}
```

> Output:
> `Not Equivalent`

**Explanation:**
The `==` operator compares memory **addresses**, not the actual values in the arrays.

---

##### **Test 2 — Using `.equals()`**

```java
import java.util.*;

public class Main {
    public static void main(String[] a) {
        int var1[] = {1, 2, 3};
        int var2[] = {1, 2, 3};

        if (var1.equals(var2)) {
            System.out.println("Equivalent");
        } else {
            System.out.println("Not Equivalent");
        }
    }
}
```

> Output:
> `Not Equivalent`

**Explanation:**
`.equals()` still checks for **object identity** unless overridden — which Java arrays do **not** do.

---

#### What Does Work

##### **Using `Arrays.equals()`**

```java
import java.util.*;

public class Main {
    public static void main(String[] a) {
        int arr1[] = {1, 2, 3};
        int arr2[] = {1, 2, 3};

        if (Arrays.equals(arr1, arr2)) {
            System.out.println("Equivalent");
        } else {
            System.out.println("Not Equivalent");
        }
    }
}
```

> Output:
> `Equivalent`

**Explanation:**
`Arrays.equals()` checks **each element by index** — if all match, it returns `true`.

---

#### Comparing Arrays with Different Data Types

```java
import java.util.*;

public class Main {
    public static void main(String[] a) {
        Object[] studentPositions = {1, 2, 3};
        String[] studentClassPositions = {"1", "2", "3"};

        if (Arrays.equals(studentPositions, studentClassPositions)) {
            System.out.println("Same Students Position List");
        } else {
            System.out.println("Different Students Position List");
        }
    }
}
```

> Output:
> `Different Students Position List`

**Explanation:**
Even if values seem similar, **different data types** (e.g., `Integer` vs `String`) cause the comparison to fail.

---

#### Equivalency in Object-Oriented Design

Comparing **custom objects** brings in additional challenges. Even if two objects look identical, the comparison can fail if:

* They are not the **same instance**
* They differ by **fields**, **methods**, or **inheritance behavior**

---

#### Effects on Object Comparison

##### **Type Casting**

* Casting fields to different types can cause unequal behavior
* Example: `feeBalance` as `int` vs `String`

##### **Overloading**

* Two objects may have the same method name but different parameters
* Overloading differences will make them **not equal**

##### **Overriding**

* Overridden methods in subclasses change the behavior
* Comparing objects with different implementations yields `false`

##### **Custom Instance Methods**

* One object might have additional methods
* These differences break equality

---

#### Lesson Summary

* Using `==` or `.equals()` on arrays only checks **object reference**, not **content**
* Use `Arrays.equals()` from `java.util.Arrays` for element-by-element comparison
* For **object comparison**:

  * Ensure you compare **fields**, not references
  * Be careful of **type casting**, **overloading**, **overriding**, and **custom methods**
* **Equivalency testing** in OOP requires thoughtful, consistent object design

### Section 3: Cloning an Array

#### Clone vs Copy?

In Java, cloning and copying arrays serve similar purposes — **duplicating array data** — but they’re **not the same**.

* **Copying**: Uses `System.arraycopy()` to copy array elements
* **Cloning**: Uses the `.clone()` method to create a mirror image of the entire array

> Think of copying like **Ctrl + C and Ctrl + V** for selective data,
> while cloning is like creating a **full duplicate** of the original file.

---

#### Shallow Copy Using `System.arraycopy()`

```java
public static void main(String[] args) {
    int scores[] = {250, 275, 300, 525, 705};
    int[] newScores = new int[5];
    System.arraycopy(scores, 0, newScores, 0, 5);

    System.out.println("Scores contents:");
    for (int i = 0; i < scores.length; i++) {
        System.out.print(scores[i] + " ");
    }

    System.out.println("\nNew Scores:");
    for (int i = 0; i < newScores.length; i++) {
        System.out.print(newScores[i] + " ");
    }
}
```

> Output shows both arrays have the **same values**, but they are **different objects** in memory.

---

#### Limitations: Shallow Copy with Objects

If your array contains **objects**, copying only copies the **references**, not the objects themselves.

```java
public class Scores {
    int scores;

    public Scores(int scores) {
        this.scores = scores;
    }
}
```

```java
public static void main(String[] args) {
    Scores[] scoresArray = new Scores[5];
    scoresArray[0] = new Scores(100);
    scoresArray[1] = new Scores(500);

    Scores[] newScoresArray = new Scores[5];
    System.arraycopy(scoresArray, 0, newScoresArray, 0, 2);
}
```

> This will result in a **NullPointerException** if you try to access other elements not initialized.
> **No deep copy** occurs — only references are copied.

---

#### Cloning an Array

The `.clone()` method is used to **create a new array object** with the same contents.

```java
public class CloneArray {
    public static void main(String[] args) {
        int[] highScores = {100, 150, 275, 300, 525};
        int[] cloneMe = highScores.clone();

        for (int i = 0; i < highScores.length; i++) {
            System.out.println("Original: " + highScores[i] + " Cloned: " + cloneMe[i]);
        }
    }
}
```

> `.clone()` works well for **primitive type arrays**, but still only performs a **shallow copy** for arrays of objects.

---

#### Multi-Dimensional Arrays

Java does **not** support multi-dimensional arrays in the same way as C.

* A "2D" array in Java is really an **array of arrays**
* Cloning or copying only duplicates the **outer array**, not the inner ones

```java
int[][] matrix = {
    {1, 2},
    {3, 4}
};

int[][] matrixClone = matrix.clone();
```

> `matrixClone[0]` and `matrix[0]` still **point to the same inner array**

---

#### Lesson Summary

* `System.arraycopy()` performs a **shallow copy** — element-by-element transfer
* `.clone()` duplicates the entire array — creating a **new instance**
* Both methods **do not perform a deep copy** for arrays of objects
* For object arrays, a **manual deep copy** is needed to create new instances of each element
* Java treats **multi-dimensional arrays** as arrays of arrays — cloning only affects the outer layer
