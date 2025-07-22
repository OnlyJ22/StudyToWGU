Look at  109 -> Ch8.md for more content

### Section 1: Binary Trees

A **tree** is an abstract data structure used to manage data **hierarchically**, allowing for faster and more efficient searching, inserting, and organizing than linear structures. It is composed of **nodes** connected in a non-cyclic, directed graph.

---

#### Tree Terminology

* **Root** – The first node in the tree where all operations begin.
* **Node** – A single unit in the tree containing data (usually in a key-value structure).
* **Child** – A node directly connected and descending from another node.
* **Parent** – The node that has one or more children.

---

#### Types of Trees

* **Binary Tree** – Each node has at most two children.
* **Other Trees** – May have more than two children per node.

**Binary trees** are widely used due to their performance advantages in insertion and searching operations.

---

#### Common Operations

**1. Insertion**

Insertions compare each new data point with the current node and place it to the **left** if smaller or **right** if larger.

```java
public Node insertNode(Node node, int data){
  if (node == null){
    node = new Node(data);
    return node;
  }
  if (data <= node.data){
    node.leftChild = insertNode(node.leftChild, data);
  } else if (data > node.data){
    node.rightChild = insertNode(node.rightChild, data);
  }
  return node;
}
```

Example input array: `(5, 3, 7, 6, 2, 1, 8, 4)`
The resulting tree grows recursively with decisions made at each node level.

---

**2. Search**

Searching a binary tree follows the same logic as insertion:
Compare the value to the current node → move left or right accordingly.

```java
public Node findNode(Node node, int data){
  if (node == null) return null;
  if (data == node.data){
    return node;
  }
  if (data <= node.data){
    return findNode(node.leftChild, data);
  } else {
    return findNode(node.rightChild, data);
  }
}
```

The function returns the **Node** if found, or **null** if the value is not in the tree.

---

#### Lesson Summary

A **tree** is a hierarchical data structure composed of nodes, beginning at the **root**, and connected by **parent-child** relationships. Binary trees are the most common and efficient form, especially for **insertion** and **search** operations. Each decision to go left or right cuts the problem space in half, enhancing performance.

Key elements:

* Root
* Node
* Child
* Parent

Binary trees are especially efficient for **dynamic datasets** where ordering is crucial and quick retrieval is necessary.

### Section 2: Types of Binary Trees

A **binary tree** is a specialized form of a tree in which each **node can have at most two children** — a left and a right child. Unlike a general tree with unrestricted children, binary trees enforce this two-child rule. The top node is called the **root**, and nodes with no children are called **leaf nodes**.

---

#### Types of Binary Trees

| Type                     | Description                                                                               |
| ------------------------ | ----------------------------------------------------------------------------------------- |
| **Full Binary Tree**     | Every node other than leaf nodes has exactly two children.                                |
| **Complete Binary Tree** | All levels are fully filled except possibly the last, which is filled from left to right. |
| **Perfect Binary Tree**  | All internal nodes have two children and all leaf nodes are at the same level.            |

---

#### Binary Tree Structure (Java Example)

Each node holds a key and references to its left and right children:

```java
public static class Node {
  int key;
  Node left, right;

  public Node(int item) {
    key = item;
    left = right = null;
  }
}
```

To build a binary tree:

```java
BinaryTree tree = new BinaryTree();
tree.root = new Node(1);
tree.root.left = new Node(2);
tree.root.right = new Node(3);
tree.root.left.left = new Node(4);
```

Resulting structure:

```
    1
   / \
  2   3
 / 
4
```

---

#### Tree Traversal Methods

Traversal is the process of visiting every node. Three primary methods:

| Traversal Type | Order Description                                                                        |
| -------------- | ---------------------------------------------------------------------------------------- |
| **Preorder**   | Visit root ➝ left subtree ➝ right subtree<br>*Example*: 7, 1, 0, 3, 2, 5, 4, 6, 9, 8, 10 |
| **Inorder**    | Visit left ➝ root ➝ right<br>*Example*: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10                 |
| **Postorder**  | Visit left ➝ right ➝ root<br>*Example*: 0, 2, 4, 6, 5, 3, 1, 8, 10, 9, 7                 |

In **binary search trees**, the **inorder traversal** is used to print all node values in ascending order.

---

#### Binary Search Tree (BST)

A **binary search tree** is a binary tree where:

* All values in the **left subtree** are **less** than the parent node.
* All values in the **right subtree** are **greater** than the parent node.

This ordering makes **searching** and **insertion** more efficient than regular binary trees.

---

#### Applications of Binary Trees

| Implementation             | Application Area                                                   |
| -------------------------- | ------------------------------------------------------------------ |
| **Binary Search Tree**     | Used in search algorithms with dynamic data                        |
| **Binary Space Partition** | Graphics rendering and collision detection in 3D games             |
| **Binary Trees**           | Routing tables in high-bandwidth routers                           |
| **Hash Trees**             | File verification in peer-to-peer sharing, image-similarity checks |
| **Heaps**                  | Used in OS priority queues and AI pathfinding                      |
| **Huffman Coding Tree**    | Image and audio compression (.jpeg, .mp3)                          |
| **GGM Trees**              | Pseudorandom number generation in cryptography                     |
| **Syntax Trees**           | Parsing code in compilers and calculators                          |

---

#### Complete Java Code Example

```java
public class Main {
  public static class Node {
    int key;
    Node left, right;
    public Node(int item) {
      key = item;
      left = right = null;
    }
  }

  public static class BinaryTree {
    Node root;
    BinaryTree(int key) { root = new Node(key); }
    BinaryTree() { root = null; }
  }

  public static void main(String[] args) {
    BinaryTree tree = new BinaryTree();
    tree.root = new Node(1);
    tree.root.left = new Node(2);
    tree.root.right = new Node(3);
    tree.root.left.left = new Node(4);
  }
}
```

---

#### Lesson Summary

A **binary tree** is a hierarchical data structure with a restriction of **0, 1, or 2 children per node**. Key types include **full**, **complete**, and **perfect** binary trees. **Traversal** methods (inorder, preorder, postorder) are used to visit nodes in different orders. Binary search trees enhance efficiency by enforcing ordering rules. Binary trees have broad real-world applications — from compilers to cryptography, from network routing to game engines.

### Tree Data Structures

In computer science, a **Tree** is a hierarchical data structure composed of nodes arranged in a parent/child relationship. The **root node** is the topmost node of the tree and serves as the parent for all other nodes. Nodes directly connected to the root are known as **child nodes**.

---

#### Common Tree Types

| Tree Type       | Description                                                                                                                                                                   |
| --------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Binary Tree** | A structure where each node has at most **two children**. Traversal moves left for smaller values and right for greater or equal. Time complexity for search: **O(log n)**.   |
| **B-Tree**      | Nodes can have **more than two children**. Commonly used in databases and file systems. B-Trees are **self-balancing** to maintain performance.                               |
| **Heap**        | A **special binary tree** where parent nodes are either always greater than (max-heap) or always less than (min-heap) their children. Root holds the highest or lowest value. |

---

#### Visual Examples

**Binary Tree**

```
    5
   / \
  3   7
 / \   \
2   4   8
```

**B-Tree**

```
[10 | 20]
 /   |   \
[5] [15] [25]
```

**Heap (Max)**

```
    90
   /  \
  85   70
 / \   /
40 60 65
```

---

#### Strengths and Weaknesses

| Feature      | **Binary Tree**                                     | **B-Tree**                                                   | **Heap**                                                           |
| ------------ | --------------------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------------ |
| **Strength** | Quickly filters out unnecessary data in operations. | Efficient for large data; used in database frameworks.       | Ideal for retrieving highest/lowest priority elements efficiently. |
| **Weakness** | Becomes inefficient if unbalanced.                  | Leaf and non-leaf node size disparity makes storage complex. | Slower insertion and comparison operations due to structure.       |

---

#### Applications

| Tree Type       | Real-World Usage                                                                                     |
| --------------- | ---------------------------------------------------------------------------------------------------- |
| **Binary Tree** | - Expression evaluators and parsers<br>- Storing routing tables in high-bandwidth routers            |
| **B-Tree**      | - Widely used in **database indexing**<br>- Used in **Ruby on Rails** for managing databases         |
| **Heap**        | - Used for building **priority queues**<br>- Core structure in **heapsort algorithm** implementation |

---

#### Lesson Summary

A **tree** is a fundamental hierarchical data structure in computer science. Each tree begins with a root node and branches into child nodes. The **binary tree**, **B-tree**, and **heap** are three of the most widely used types. Binary trees offer fast filtering but require balance. B-trees are essential in databases due to their scalable structure. Heaps provide optimal access to priority elements and are used in scheduling and sorting.
