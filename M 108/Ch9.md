### Section 1: Trees in Discrete Mathematics

#### Definition and Structure

A **tree** in discrete mathematics is a type of **graph**: a collection of **nodes (vertices)** connected by **edges (lines)**. A tree has the following defining characteristics:

* **Connected**: Every node can be reached from any other node.
* **Acyclic**: No loops or cycles exist.
* **Hierarchical**: Often has a root and branches downward like a family or decision tree.

Example: Directions to Albert's house can be modeled as a tree starting from "School" (the **root**) with each **corner** or **intersection** representing a **decision point**, branching into different path choices (e.g., left, right, straight).

---

#### Decision Trees

A **decision tree** represents a sequence of decisions.

* Each **node** represents a choice point.
* Each **branch** represents a possible action or outcome.
* The **depth** of the tree represents the number of decisions made.

**Example**:
If at every intersection Albert gives 3 options (left, right, straight), then for 3 blocks of instructions, the number of possible paths is:

```
3^3 = 27 total routes
```

Only **one path** leads to Albert's house, and the rest represent alternate routes.

---

#### Binary Trees and Probability

A **binary tree** is a type of decision tree where each node has **two options**, typically labeled "yes/no", "true/false", or "heads/tails".

**Example**: Ada flips 3 coins.
Each flip has two outcomes: H or T.
Using a binary tree:

* Level 1: First flip → H or T
* Level 2: Second flip → H or T
* Level 3: Third flip → H or T
  This results in:

```
2^3 = 8 possible outcomes:  
HHH, HHT, HTH, HTT, THH, THT, TTH, TTT
```

To find outcomes with **exactly two heads**:

* HHT, HTH, THH → **3 out of 8** favorable outcomes

---

#### Spanning Trees

A **spanning tree** connects all nodes in a graph using the **minimum number of edges** without creating a cycle.

**Properties**:

* Has **n – 1** edges for **n** nodes
* Provides a **minimal network** to connect all elements

Used in:

* Network design
* Routing algorithms
* Electrical grid planning

---

#### Centers in Trees

When a tree has **no distinct root**, we can identify its **center(s)**:

* A **center** is a node with the **least total distance** (in hops or edges) to all other nodes.
* A tree may have **one or two centers** in the case of a tie.

Example:
In a labeled tree, nodes **B** and **D** both have **8 total hops** to reach all other nodes — hence, they are **both centers**.

---

#### Applications of Trees in Discrete Math

* **Programming Logic**: Control flow diagrams and function call trees
* **Artificial Intelligence**: Game trees (e.g., chess move planning)
* **Decision-Making**: Modeling choices and their outcomes
* **Network Routing**: Finding minimal paths using spanning trees
* **Probability**: Calculating outcomes via binary trees
* **Social Networks**: Graphing relationships and message paths

---

#### Summary

* Trees are foundational structures in discrete math used to model **hierarchical, logical, and decision-based systems**.
* A **decision tree** maps out possible outcomes of a sequence of choices.
* A **binary decision tree** represents two possible outcomes at each decision point.
* A **spanning tree** connects all nodes in a graph with no cycles.
* **Centers** of a tree are nodes with minimal connection distance to all others.
* Trees are essential for solving real-world problems in **computer science, networking, game theory**, and **probability**.

### Section 2: Spanning Trees

#### Definition and Characteristics

A **spanning tree** is a type of subgraph derived from a **connected, undirected graph** that:

* **Includes all nodes (vertices)** from the original graph.
* **Connects every node with no cycles or loops**.
* **Uses the minimum number of edges** necessary to maintain connectivity.

If a graph has **n nodes**, then any spanning tree of that graph will always contain exactly **n – 1 edges**. Adding more than that would introduce a cycle, violating the properties of a tree.

---

#### Example: Albert’s Calling Tree

Albert, the secretary of the **Fungus Appreciation Society (FAS)**, must notify 12 other members (13 people in total) if a meeting is cancelled. He wants to minimize his workload and avoid redundant calls.

Each **strategy** Albert considers is an example of a **spanning tree** (except for the last two):

* **Strategy One**: Albert calls all 12 members directly

  * One level, 12 edges
  * High burden on Albert

* **Strategy Two**: Albert calls 3 people, and they each call 3 others

  * Total edges = 1 (Albert → 3) + 3 (Each of the 3 → 3 members) = 12
  * Balanced and efficient

* **Strategy Three**: Albert calls 4 people, and each calls 2 others

  * Also uses 12 edges
  * Efficient with a different structure

* **Strategy Four**: Chain call; Albert calls one person, who calls the next, and so on

  * Linear spanning tree
  * Long delay in reaching final member

* **Strategy Five**: Contains extra edges that create **cycles (loops)**

  * **Not a spanning tree**

* **Strategy Six**: Some members are not contacted (**missing nodes**)

  * **Not a spanning tree**

**Conclusion**: All valid strategies (One through Four) are spanning trees with **13 nodes and 12 edges**.

---

#### Applications in Network Design

Spanning trees are fundamental in **network optimization**, especially when:

* Designing **cycle-free topologies** in Ethernet networks using **Spanning Tree Protocol (STP)**
* Building **organizational charts** with one clear reporting path
* Planning **communication trees** to spread messages efficiently

In computer networks:

* Redundant connections (not part of the active spanning tree) are kept on standby
* If an active connection fails, a new spanning tree can be recalculated
* This provides **fault tolerance** while maintaining efficiency

---

#### Organizational Charts as Spanning Trees

* Every **employee (node)** reports to **one boss (parent node)**
* No cycles exist—employees don’t report back upward in a loop
* The **“span of control”** defines how many direct reports a manager supervises
* The chart is optimized for clarity, efficiency, and communication flow

---

#### Summary

* A **spanning tree** is a cycle-free, connected subgraph covering all nodes of a graph using exactly **n – 1** edges.
* Multiple spanning trees may exist for the same graph, and choosing the right one depends on the problem (e.g., fairness, speed, fault-tolerance).
* **Valid spanning trees** are:

  * Fully connected
  * Contain no loops
  * Include every node
* Applications include:

  * Phone trees
  * Network routing (e.g., Ethernet)
  * Organizational management
  * Program and project planning in software engineering

Spanning trees are practical, efficient, and essential tools in discrete math and real-world problem solving.

### Section 3: Minimum Spanning Trees

#### Overview

A **minimum spanning tree (MST)** is a specific type of **spanning tree** that not only connects all the nodes of a graph without forming cycles, but also **minimizes the total edge weight**. This weight could represent cost, time delay, or error rate, depending on the problem at hand.

In summary:

* A **spanning tree** connects all nodes with the **minimum number of edges** (exactly *n – 1* for *n* nodes), but does **not consider edge weight**.
* A **minimum spanning tree** ensures that the **total weight of all edges is the smallest possible** among all spanning trees.

---

#### Ada’s Problem

Ada must ensure that every computer in a university network is connected either directly to the Internet or indirectly through other connected computers. This requires:

1. A **spanning tree** to guarantee full connectivity.
2. A **minimum spanning tree** to **minimize network delay** and **maximize efficiency**.

---

#### Brute Force: Explicit Enumeration

In a small network, it's possible to:

* List **all possible spanning trees**.
* Calculate the **total weight** of each tree.
* Choose the tree with the **lowest total weight**.

For example, in a network of four nodes with known edge weights, Ada enumerates four different spanning trees. The total weights for each tree are calculated, and the one with the **smallest total** is selected as the MST.

---

#### Algorithms for Large Networks

In larger networks, explicit enumeration is **not feasible** due to exponential growth in the number of spanning trees. Two well-known algorithms can be used instead:

---

#### Kruskal’s Algorithm

**Procedure**:

1. **List all edges** and **sort them** in order of **ascending weight**.
2. Start with an empty graph and **add edges one by one** from the sorted list.
3. **Skip any edge** that would form a **cycle**.
4. Continue until **n – 1 edges** have been added.

**Example Execution**:

* Sorted Edges:
  `EdgeAB(1), EdgeBE(1), EdgeAC(2), EdgeAE(3), EdgeBD(3), EdgeCD(4), EdgeDE(7), EdgeCE(9)`
* Insert:

  * EdgeAB (1)
  * EdgeBE (1)
  * EdgeAC (2)
  * EdgeAE (3) → **rejected** (creates cycle)
  * EdgeBD (3)
* All further edges produce cycles and are discarded.
* **Resulting MST edges**: AB, BE, AC, BD

---

#### Prim’s Algorithm

**Procedure**:

1. **Start from any node**.
2. Add the **lowest-weight edge** that connects a **new (unconnected) node** to the tree.
3. Repeat until all nodes are connected.

**Example Execution (starting at Node D)**:

* EdgeBD (3)
* EdgeBE (1)
* EdgeBA (1)
* EdgeAC (2)
* **Resulting MST edges**: BD, BE, BA, AC

Both algorithms yield the same MST in this example.

---

#### Applications

* **Computer networks**: Efficient Internet routing with protocols like **Spanning Tree Protocol (STP)** in Ethernet.
* **Telecommunications**: Laying cables or lines with minimum cost.
* **Transportation planning**: Building roads or pipelines minimizing total distance.
* **Clustering in Machine Learning**: Grouping data with minimum intra-cluster distance.

---

#### Lesson Summary

* A **spanning tree** connects all nodes using **n – 1 edges**, avoiding loops.
* A **minimum spanning tree** additionally ensures that **total edge weight is minimized**.
* In small graphs, MSTs can be found by **explicit enumeration**.
* In large graphs, use:

  * **Kruskal’s Algorithm**: Add edges by lowest weight, avoid cycles.
  * **Prim’s Algorithm**: Expand the tree from a start node, always choosing the lowest-cost connection to a new node.
* MSTs are widely applicable in **networks, infrastructure planning, and optimization problems**.
