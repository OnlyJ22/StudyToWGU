### Section 1: Arrays in Java

#### What Is an Array?

* An **array** in Java is a **sequence of values**, each of the **same data type**.
* It is a **single object**, even though it's made up of **multiple elements**.
* Think of it like a **row of buckets** or **a one-sided table**.

#### Arrays in Action

* Arrays can be used to break down things like a **user name into characters**.
* Java still sees the whole as a **single block**, but you can access **individual parts**, like **cells in a table**.

#### Declaring a Basic Array

```java
int[] sequence;
sequence = new int[50];
```

* You can **declare** an array and then **fill it** later.
* Example with values:

```java
int[] series = new int[5];
series[0] = 22;
series[1] = 44;
series[2] = 96;
series[3] = 122;
series[4] = 999;
```

* Or in one line:

```java
int[] series = {22, 44, 96, 122, 999};
```

#### Java Array Bucket

* Each **position** in the array is called a **bucket**.
* **Indexing starts at 0**, so:

  * `series[0] = 22`
  * `series[1] = 44`
  * and so on...

#### Everything Starts at Zero!

* Java arrays are **zero-indexed**.

* This means the **first element** is at **index 0**:

  ```java
  myArray[0]; // First element
  myArray[1]; // Second element
  ```

* This is **standard** in Java and many other programming languages.

#### Length is Fixed

* Once created, the **size of the array cannot change**.
* But you can find the length using `.length`:

```java
int[] sequence = new int[50];
System.out.println(sequence.length); // Outputs 50
```

#### Looping Through an Array

* Use a **for loop** to **step through** and access array elements:

```java
for(int i = 0; i < myArray.length; i++) {
  System.out.println(myArray[i]);
}
```

* `i` is the **counter**, and it moves through each **bucket** in the array.

#### Multiple Dimensions!

* Java supports **multi-dimensional arrays**.
* A **2D array** is like a **table** with **rows and columns**:

```java
int[][] myMatrix = new int[10][3];
```

* Looping through requires **nested for loops**.
* Declaring:

  * 1D array: `[]`
  * 2D array: `[][]`
  * and so on...

#### Examples

##### Prefilling and Displaying the Array

```java
public class Main {
  public static void main(String[] args) {
    String[] retailer = new String[5];
    retailer[0] = "Amazon";
    retailer[1] = "Wal-Mart";
    retailer[2] = "Target";
    retailer[3] = "Trader Joes";

    String[] retailer2 = {
      "Amazon",
      "Wal-Mart",
      "Target",
      "Trader Joes",
    };

    int len = retailer2.length;
    for(int i = 0; i < len; i++) {
      System.out.println("Retailer " + i + ": " + retailer2[i]);
    }
  }
}
```

##### The User Name Example

* You can **convert a String to a char array** and check characters:

```java
public class Main {
  public static void main(String[] args) {
    String userName = "Jane Austin&";
    char[] checkUserName = userName.toCharArray();

    for(int i = 0; i < checkUserName.length; i++) {
      if(userName.charAt(i) != '&') {
        System.out.println("ERROR");
      } else {
        System.out.println("OK");
      }
    }
  }
}
```

* This checks if the **username contains '&'** anywhere.

#### Summary

* A **Java array** is a sequence of values of the **same type**.

* Arrays can be:

  * **One-dimensional** (simple list)
  * **Two-dimensional** (matrix/table)
  * Or even **multi-dimensional**

* Arrays are:

  * **Fixed-length**
  * Accessed using **indexes**
  * Stepped through with **loops**

* Common Java tools with arrays:

  * `.length` to get size
  * `for` loops to iterate
  * Character arrays for string manipulation

* Arrays are **powerful tools** in the Java programming toolbox.

### Section 2: Java Arrays

#### What Is a Java Array?

* A **Java array** is like a **table**.
* The simplest array has **one column** and **many rows**.
* All elements in the array must be of the **same data type** — e.g., `int`, `char`, `double`.

#### Declaring and Initializing an Array

* To store game **high scores**, we can use an array with **5 buckets**:

```java
int[] highScores; // Declare the array
highScores = new int[5]; // Set the size to 5
```

* A shorter way to declare and initialize:

```java
int[] highScores = new int[5];
```

* All buckets are initialized to **0** by default (for numeric arrays).

#### Accessing Array Values

* Java arrays start counting at **zero**.
* To access a specific bucket, use its **index**:

```java
System.out.println(highScores[3]);
```

* This prints the value in the **fourth bucket** (index 3).

#### More Initializing Options

* You can **populate the array directly** using curly brackets:

```java
int[] highScores = {100, 150, 276, 600, 1000};
```

* No need to specify size — Java **infers** the length from the number of values.

* Another way is to **assign values one-by-one**:

```java
int[] highScores = new int[5];
highScores[0] = 350;
highScores[1] = 525;
highScores[2] = 980;
highScores[3] = 1025;
highScores[4] = 157550;
```

* If you try to access a **bucket that doesn't exist**, you'll get an **ArrayIndexOutOfBoundsException**.

#### Real-World Usage

* In real programs, arrays are usually **initialized first**, then **filled with values later**.
* For example, in a game:

  * Track the top 5 scores.
  * Push new scores into the array as the game progresses.

#### Summary

* **Declaring** an array ≠ **Using** an array — it must also be **initialized**.

* Ways to initialize a Java array:

  * **Two-step method** (declare, then initialize).
  * **One-line initialization** with default values.
  * **Populate with curly brackets** for pre-filled arrays.
  * **Set values individually** using index references.

* Most often, arrays are **initialized first**, then **populated as data becomes available** in the program.

Here are your notes on **Multidimensional Arrays in Java**, structured precisely in the same format as your previous sections:

---

### Section 3: Multidimensional Arrays in Java

#### What Is a Multidimensional Array?

* A **multidimensional array** is simply an **array within an array**.
* A **1D array** is like a **list**; a **2D array** is like a **table** with **rows and columns**.
* All data must still be of the **same type** — e.g., `int`, `char`, `double`.

#### Creating Multidimensional Arrays

* To declare a **2D array**, use the following syntax:

```java
int[][] table;
```

* To **initialize** a 5x5 table:

```java
table = new int[5][5];
```

* Java starts counting at **zero**, so `table[0][0]` is the **top-left** cell.
* To set a value (e.g., row 3, column 4):

```java
table[3][4] = 245;
```

#### Populating Multidimensional Arrays

* You can fill a 2D array directly with values using curly brackets:

```java
int[][] table = {
  {395, 830, 137, 450, 949},
  {446, 610, 636, 818, 22},
  {807, 337, 187, 812, 236},
  {546, 772, 699, 867, 216},
  {340, 814, 815, 88, 483}
};
```

* To access a specific element:

```java
int value = table[2][3]; // Access value at row 2, column 3
```

#### Processing 2D Arrays

* Use **nested for loops** — one for **rows**, one for **columns**:

```java
for (int row = 0; row < table.length; row++) {
  for (int column = 0; column < table[row].length; column++) {
    System.out.println("Value: " + table[row][column]);
  }
}
```

* **Real-world example**: A **GPS system** finding the closest `(x, y)` coordinate to the user's location `(0, 0)`.

```java
public class Main {
  public static void main(String[] args) {
    int[][] gps = { {-2, 4}, {3, 2}, {-5, -5}, {4, -1} };
    int index = 0;
    double shortestDistance = Double.MAX_VALUE;

    for (int i = 0; i < gps.length; i++) {
      double distance = distance(0, 0, gps[i][0], gps[i][1]);
      if (distance < shortestDistance) {
        index = i;
        shortestDistance = distance;
      }
    }

    System.out.println("The nearest point is (" + gps[index][0] + ", " + gps[index][1] + ")");
  }

  public static double distance(double x1, double y1, double x2, double y2) {
    return Math.sqrt((x2 - x1) * (x2 - x1) + (y2 - y1) * (y2 - y1));
  }
}
```

* The **closest point** to `(0, 0)` is calculated using a **distance formula**.
* Nested loops allow traversal of **every coordinate pair**.

#### 3D Arrays

* A **3D array** is an **array of arrays of arrays**.
* The syntax includes **three brackets**: `[][][]`

```java
int[][][] table = new int[5][5][5];
```

* To process a 3D array, use **three nested loops**:

```java
for (int row = 0; row < table.length; row++) {
  for (int column = 0; column < table[row].length; column++) {
    for (int plane = 0; plane < table[row][column].length; plane++) {
      System.out.println("row = " + row + " column = " + column + " plane = " + plane);
    }
  }
}
```

* Each loop handles **one dimension**.
* 3D arrays can be **complex and impractical**, and are used mainly for teaching purposes.

#### Summary

* A **multidimensional array** is an array within an array.
* A **2D array** is commonly used to represent a **table or matrix**.
* Use **nested for loops** to access and process all elements.
* A **3D array** introduces a third dimension, requiring three loops.
* Example use: GPS tracking with `(x, y)` coordinates in a 2D array.
* Beyond 3D arrays, dimensionality becomes **difficult to manage and rarely useful** in real-world Java programs.

### Section 4: Dynamic Arrays in Java

#### What Is a Dynamic Array?

* A **dynamic array** can **grow or shrink** in size as needed.

* Java does **not support** true dynamic arrays natively.

* Reasons include:

  * **Performance concerns**
  * **Memory overhead**

* Instead, we use either:

  * A **custom class** that resizes arrays manually
  * The **ArrayList** class from Java’s standard library

---

#### Custom Dynamic Array Class

* Example: Track top game scores using a custom `DynamicArray` class.
* Declare and initialize an array with one bucket inside a constructor:

```java
public static class DynamicArray {
  int[] topScores;

  public DynamicArray() {
    topScores = new int[1];
  }

  int get(int bucket) {
    if(bucket >= topScores.length) {
      return 0;
    } else {
      return topScores[bucket];
    }
  }

  void put(int bucket, int value) {
    if(bucket >= topScores.length) {
      int updatedSize = 2 * bucket;
      int[] newScores = new int[updatedSize];
      System.arraycopy(topScores, 0, newScores, 0, topScores.length);
      topScores = newScores;
      System.out.println("Array increased to " + updatedSize);
    }
    topScores[bucket] = value;
  }
}
```

* Example usage:

```java
DynamicArray scores = new DynamicArray();
scores.put(15, 9000);
```

* This manually resizes the array when the index exceeds the current size.

---

#### Using ArrayList (Built-In Java Class)

* Java provides **ArrayList**, a built-in dynamic array class.

```java
ArrayList<Integer> topScores = new ArrayList<Integer>();
```

* Use `.add()` to insert values:

```java
int buckets = 15;
for(int i = 0; i < buckets; i++) {
  topScores.add(userScore); // Assume userScore is predefined
}
```

* Add more scores later:

```java
topScores.add(0, 1000);
topScores.add(1, 1100);
topScores.add(2, 1150);
topScores.add(3, 1220);
topScores.add(4, 1400);
```

* Print all values:

```java
for(int i = 0; i < topScores.size(); i++) {
  System.out.println(topScores.get(i));
}
```

* Get the current size:

```java
System.out.println(topScores.size()); // Output: 20
```

---

#### Full Code Example

```java
import java.util.*;

public class Main {
  public static void main(String[] args) {
    System.out.println("Hello - Welcome to Dynamic Arrays");

    // Custom Dynamic Array
    DynamicArray scores = new DynamicArray();
    scores.put(15, 9000);

    // Using ArrayList
    ArrayList<Integer> topScores = new ArrayList<Integer>();
    topScores.add(0, 1000);
    topScores.add(1, 1100);
    topScores.add(2, 1100);
    topScores.add(3, 1150);
    topScores.add(4, 1220);
    topScores.add(5, 1400);

    for(int i = 0; i < topScores.size(); i++) {
      System.out.println("Score = " + topScores.get(i));
    }

    System.out.println("Total scores = " + topScores.size());
  }

  public static class DynamicArray {
    int[] topScores;

    public DynamicArray() {
      topScores = new int[1];
    }

    int get(int bucket) {
      if(bucket >= topScores.length) {
        return 0;
      } else {
        return topScores[bucket];
      }
    }

    void put(int bucket, int value) {
      if(bucket >= topScores.length) {
        int updatedSize = 2 * bucket;
        int[] newScores = new int[updatedSize];
        System.arraycopy(topScores, 0, newScores, 0, topScores.length);
        topScores = newScores;
        System.out.println("Array increased to " + updatedSize);
      }
      topScores[bucket] = value;
    }
  }
}
```

---

#### Summary

* Java arrays are **fixed in size** — once declared, they cannot grow.

* **Workarounds for dynamic arrays**:

  * Create a **custom class** to resize manually
  * Use Java’s **ArrayList** class

* `ArrayList` provides methods like:

  * `.add()` — Add values to the end or at a specific index
  * `.get()` — Access values
  * `.size()` — Get current number of elements

### Section 5: Array Review

#### Array Basics

* A **Java array** is a fixed-size holder of **buckets**, all of the **same data type**.
* You determine the **size** using the `.length` property.

```java
int[] buckets = new int[5];
System.out.println(buckets.length); // Output: 5
```

---

#### Manual Add

* You can **manually assign values** to each bucket if the array is small:

```java
buckets[0] = 15;
buckets[1] = 32;
buckets[2] = 7;
buckets[3] = 105;
buckets[4] = 78;
```

* Java starts **counting at 0**, so `buckets[0]` is the **first element**.

---

#### One-Line Initialization

* You can declare and fill the array in **one statement**:

```java
int[] buckets = new int[] {5, 10, 15, 20, 25};
```

* For readability, values can also be split across lines:

```java
int[] buckets = new int[] {
  5,
  10,
  15,
  20,
  25
};
```

---

#### Filling Arrays with a Loop

* Use a **for loop** to fill or update array values:

```java
int[] buckets = new int[5];
int j = 0;

for (int i = 0; i < buckets.length; i++) {
  buckets[i] = j;
  j += 5;
  System.out.println(buckets[i]);
}
```

* This loop fills each bucket with a value increasing by **5**.
* Output:

```
0
5
10
15
20
```

* Remember: **First index is 0**, and the loop runs until `i < buckets.length`.

---

#### Fixed Size Limitation

* Once created, **you cannot add new elements** to the array.
* Example:

```java
double[] payRates = new double[15];
payRates[15] = 203.34; // Error: Index 15 is out of bounds (0–14 are valid)
```

* This will throw a **runtime error**: `ArrayIndexOutOfBoundsException`

* Java arrays are **not dynamic** — you can **fill** values but **not expand** the array's size.

---

#### Summary

* An array is a **fixed-length container** of **same-type elements**.

* Array size is determined using **`.length`**.

* You can:

  * Fill values **manually**
  * Use a **for loop** for automation
  * Initialize with **curly brackets**

* You **cannot add more buckets** once the array is created.

* Trying to access an index **outside the defined size** results in an **out of bounds error**.

* Java does **not support dynamic arrays** — consider other data structures (like **ArrayList**) for that purpose.

### Section 6: A Programmer’s Life – Java Arrays

#### What Is a Java Array?

* A **Java array** is an **ordered collection of elements**.
* Arrays are **homogeneous** — all elements must be of the **same data type**.
* Example declaration:

```java
int[] test = new int[5];
```

* This creates an array with **5 integer elements**.

* Each element is accessed via its **index**:

  * `test[0]`, `test[1]`, `test[2]`, `test[3]`, `test[4]`

* Remember: **Java starts counting at 0**

---

#### Length of a Java Array

* The **length** of an array is the **number of elements** it contains.
* Example:

```java
int[] test2 = new int[7];
int len = test2.length; // len = 7
```

* Array length is **fixed** — it cannot be changed once declared.

---

#### Example: Finding Array Length

```java
public class Main {
  public static void main(String[] args) {
    int[] test = new int[5];
    int[] test2 = new int[7];

    int len = test.length;
    int len2 = test2.length;

    System.out.println(len);  // Output: 5
    System.out.println(len2); // Output: 7
  }
}
```

* The output of this program will be:

```
5
7
```

---

#### Size vs. Length in Java

* **Java arrays do not have a `size`** — only **length** is supported:

  ```java
  int[] array = new int[5];
  System.out.println(array.length); // ✅ Valid
  System.out.println(array.size);   // ❌ Invalid
  ```

* This is a common mistake for beginners.

---

#### Length vs. Size

| Concept    | Applies To  | Resizable | Keyword Used |
| ---------- | ----------- | --------- | ------------ |
| **Length** | Java Arrays | ❌ No      | `.length`    |
| **Size**   | ArrayList   | ✅ Yes     | `.size()`    |

* Arrays are part of the **language**.
* ArrayLists are part of the **Java Collections Library** and allow **dynamic resizing**.

---

#### Summary

* A **Java array** is a **fixed-length collection** of **same-type elements**.
* Use `.length` to find the number of elements.
* Java arrays do **not** support `.size()` — that’s only for **ArrayLists**.
* **ArrayLists** are more flexible and commonly used when dynamic sizing is needed.
* Understanding the difference between **length (arrays)** and **size (ArrayLists)** is key for working with collections in Java.

### Section 8: Lesson Overview & Knowledge Required

#### Skills Required

* Ability to **create a source file** and **compile** a Java program (e.g., using **NetBeans** or **Replit**).
* Understanding of **Java variable types** and **how to declare them**.
* Familiarity with **arrays**, which are:

  * **Lists of items**
  * All items are of the **same data type**
  * Indexed starting at **0**

---

### Section 9: Program Code

#### Initial Code Setup

```java
public class Main {
  public static void main(String[] args) {
  }
}
```

* This is the **basic Java program structure**.
* The array will be added **inside** the `main` method.

---

#### Declaring and Creating an Array

* To hold four **double values**, use the following line:

```java
double[] salaries = new double[4];
```

* This creates an array named `salaries` with **4 elements** of type `double`.

---

#### Assigning Values to the Array

```java
salaries[0] = 6.25;
salaries[1] = 6.55;
salaries[2] = 10.25;
salaries[3] = 16.85;
```

* Use **square brackets** `[]` to reference each **element by index**.
* Java starts counting at **0**, so:

  * `salaries[0]` = first element
  * `salaries[3]` = fourth element

---

#### Printing Each Salary

```java
System.out.println("Salaries one by one are: ");
System.out.println(salaries[0]);
System.out.println(salaries[1]);
System.out.println(salaries[2]);
System.out.println(salaries[3]);
```

* This prints each salary **individually**, one line at a time.
* Helps **verify correctness** of the array content.

---

#### Note on Looping

* Although this lesson focuses on **array creation**, remember that arrays are often **processed using for loops** for efficiency.
* Example (not required here):

```java
for(int i = 0; i < salaries.length; i++) {
  System.out.println(salaries[i]);
}
```

---

#### Summary

* Arrays in Java are used to store **multiple values of the same type**.
* Use `[]` to declare and reference elements.
* Indexing starts at **0**.
* Elements can be **assigned manually** or **looped through** for automation.
* This lesson focused on **creating**, **filling**, and **verifying** a `double[]` array of salary values.

### Section 10: Matrices

#### A Matrix

* A **matrix** is a **table of numbers** arranged in **rows and columns**.
* Think of it like a table in Microsoft Word.
* A matrix is described as **rows × columns**.
* Example: A **3 × 3** matrix has **3 rows and 3 columns**.

#### Multiplying Matrices

* **Matrix multiplication is not commutative**.

* To multiply two matrices:

  * The number of **columns in the first matrix** must equal the number of **rows in the second matrix**.
  * The resulting matrix will have the **rows of the first** and the **columns of the second**.

* Example dot product calculation:

```
(3 * 1) + (5 * 7) + (7 * 13) = 129
```

* Repeat the dot product for each position in the result matrix.

#### Multiplying Matrices in Java

* Java uses **2D arrays** to represent matrices.
* Indexing starts at **0**.
* Declare and initialize matrices:

```java
public class Main {
public static void main(String[] args) {
int[][] myMatrixA = {
{3, 5, 7},
{9, 17, 12},
{32, 21, 5}
};
int[][] myMatrixB = {
{1, 3, 5},
{7, 9, 11},
{13, 15, 17}
};
}
}
```

* To multiply matrices, use **three nested loops**:

```java
public class Main {
public static void main(String[] args) {
//get dimensions for each matrix
int rowsA = myMatrixA.length;
int colsA = myMatrixA[0].length;
int rowsB = myMatrixB.length;
int colsB = myMatrixB[0].length;
//new matrix to hold result
int[][] myMatrixC = new int [rowsA][colsB];
//start multiplying
for (i = 0; i < rowsA; i++) {
for(j = 0; j < colsB; j++) {
for(k = 0; k < colsA; k++) {
myMatrixC[i][j] += myMatrixA[i][k] * myMatrixB[k][j];
}
}
}
```

* Display the result:

```java
System.out.println("Multiplying A and B equals: ");
for(m = 0; m < myMatrixC.length; m++) {
for(n = 0; n < myMatrixC[0].length; n++) {
System.out.print(myMatrixC[m][n] + " ");
}
System.out.println();
}
```

* Output will include the dot product calculations — the first value will be `129`.

#### Invalid Matrices

* Matrix multiplication is only possible if:

  * **columns of matrix A** == **rows of matrix B**

* Use an `if` statement to check for mismatched matrices:

```java
//get dimensions for each matrix
int rowsA = myMatrixA.length;
int colsA = myMatrixA[0].length;
int rowsB = myMatrixB.length;
int colsB = myMatrixB[0].length;
//test if matrices can be multiplied
if(colsA != rowsB) {
System.out.println("Mismatched Matrices!");
return;
}
```

#### Putting it All Together

```java
public class Main {
public static void main(String[] args) {
//define matricies
int[][] myMatrixA = {
{3, 5, 7},
{9, 17, 12},
{32, 21, 5}
};
int[][] myMatrixB = {
{1, 3, 5},
{7, 9, 11},
{13, 15, 17}
};
//get dimensions for each matrix
int rowsA = myMatrixA.length; // Now within the main method
int colsA = myMatrixA[0].length;
int rowsB = myMatrixB.length;
int colsB = myMatrixB[0].length;
//test if matrices can be multiplied
if (colsA != rowsB) {
System.out.println("Mismatched Matrices!");
return;
}
//new matrix to hold result
int[][] myMatrixC = new int[rowsA][colsB];
//start multiplying
for (int i = 0; i < rowsA; i++) {
for (int j = 0; j < colsB; j++) {
for (int k = 0; k < colsA; k++) {
myMatrixC[i][j] += myMatrixA[i][k] * myMatrixB[k][j];
}
}
}
//print the result
System.out.println("Multiplying A and B equals: ");
for (int m = 0; m < myMatrixC.length; m++) {
for (int n = 0; n < myMatrixC[0].length; n++) {
System.out.print(myMatrixC[m][n] + " ");
}
System.out.println();
}
}
}
```

* Output:

```
Multiplying A and B equals:
129 159 189
284 360 436
244 360 476
```

#### Lesson Summary

* A **matrix** is a **table of values** in **rows and columns**.

* Multiplying matrices in Java:

  * Uses **2D arrays**
  * Requires **three nested loops**
  * Matches rows from the first with columns from the second
  * Stores the result in a **third matrix**

* Matrix multiplication is only possible when:

  * **Columns in Matrix A = Rows in Matrix B**

* Always validate dimensions before multiplying.

### Section 11: ArrayList

#### What Is an ArrayList?

* A **standard array** is fixed in size and limited in flexibility.
* An **ArrayList** is a **dynamic array** — it can **grow** or **shrink** as needed.
* Before using it, import the utility package:

```java
import java.util.ArrayList;
```

---

#### Declaring an ArrayList

* You create an **instance of the ArrayList class**, specifying the **data type** (e.g., `String`, `Integer`, `Double`):

```java
ArrayList<String> employees = new ArrayList<String>(5);
```

* This creates an **ArrayList of Strings** with an initial capacity of 5.

---

#### Adding Items to the ArrayList

```java
employees.add("Jane Eyre");
employees.add("Sherlock Holmes");
employees.add("Edmond Dantes");
employees.add("Jean Valjean");
employees.add("Sam Spade");
```

* Items are inserted using the `.add()` method.
* Java appends new items to the end if no index is given.

---

#### Looping Through the ArrayList

```java
System.out.println("Size = " + employees.size());

for (String counter : employees) {
  System.out.println("Employee = " + counter);
}
```

* `.size()` returns the **number of items** in the list.
* The enhanced **for-each loop** works naturally with ArrayLists.

---

#### Inserting New Elements

* Use `.add(index, value)` to **insert an item at a specific position**:

```java
employees.add(1, "Anna Karenina");
```

* This inserts into **bucket 1** (second element), shifting all later items.

---

#### Full Code with Insert

```java
public class Main {
public static void main(String[] args) {
  //create an instance of ArrayList
  ArrayList<String> employees = new ArrayList<String>();

  employees.add("Jane Eyre");
  employees.add("Sherlock Holmes");
  employees.add("Edmond Dantes");
  employees.add("Jean Valjean");
  employees.add("Sam Spade");

  //show arraylist size
  System.out.println("Size = " + employees.size());

  //loop through list and display
  for (String counter : employees) {
    System.out.println("Employee = " + counter);
  }

  System.out.println();

  //add Anna Karenina at 2nd position
  //remember Java starts at 0
  System.out.println("Array after Add: ");
  employees.add(1, "Anna Karenina");

  for(String counter : employees) {
    System.out.println("Employee = " + counter);
  }

  System.out.println("Size = " + employees.size());
}
}
```

* When run, the size **increases** and the list updates **automatically**.

---

#### ArrayList of Classes

* You can store **objects** in an ArrayList too.
* Example with a custom `Artist` class:

```java
ArrayList<Artist> artist = new ArrayList<>();

artist.add(new Artist(1025, "REO Speedwagon"));
artist.add(new Artist(9067, "Meat Loaf"));
```

* The data type of the ArrayList is `Artist`, matching the object type stored.

---

#### Summary

* **ArrayList** is a class in Java used for **flexible, resizable arrays**.
* Use `.add()` to **insert or append** values.
* Use `.add(index, value)` to **insert at a position**.
* Use `.size()` to **get current number of items**.
* ArrayLists shift elements **automatically** and are more efficient than fixed arrays for dynamic data.
* ArrayLists can store **primitive types (boxed)** and **custom objects**.

