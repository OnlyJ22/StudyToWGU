### Section 1: Defining Graphs

#### Definition

A **graph** \$G\$ is defined as a triplet consisting of:

* \$V(G)\$: a set of **vertices**
* \$E(G)\$: a set of **edges**
* A **relation** that assigns distinct points (vertices) to each edge

Graphs are essential for modeling and solving real-world problems like:

* Finding the shortest distance between two cities
* Optimizing travel routes (e.g., flights)
* Circuit design
* Efficient algorithm implementation (e.g., pathfinding, network flow)

---

#### Example

Let:

* \$V(G) = {1, 2, 3, 4}\$
* \$E(G) = {e\_1, e\_3, e\_5}\$
* Edge definitions:

  * \$e\_1 \rightarrow {1, 2}\$
  * \$e\_3 \rightarrow {3, 4}\$
  * \$e\_5 \rightarrow {2, 4}\$

These define edges between the given vertices.

---

#### Loop

A **loop** is an edge where both endpoints (vertices) are **identical**.

**Example:**
Graph \$G(V, E)\$

* \$V(G) = {1, 2, 3}\$
* \$E(G) = {e\_1, e\_2, e\_3}\$
* Edge definitions:

  * \$e\_1 \rightarrow {1, 2}\$
  * \$e\_2 \rightarrow {1, 3}\$
  * \$e\_3 \rightarrow {1, 1}\$ → a **loop**

Here, \$e\_3\$ forms a loop since it connects a vertex to itself.

---

#### Multi-Edges

**Multi-edges** (also known as parallel edges) are **multiple edges** between the same pair of vertices.

**Example:**
Graph \$G(V, E)\$

* \$V(G) = {1, 2, 3}\$
* \$E(G) = {e\_1, e\_2, e\_3}\$
* Edge definitions:

  * \$e\_1 \rightarrow {1, 2}\$
  * \$e\_2 \rightarrow {2, 3}\$
  * \$e\_3 \rightarrow {2, 3}\$

Here, \$e\_2\$ and \$e\_3\$ are **multi-edges** between vertices 2 and 3.

---

#### Simple Graph

A **simple graph** is a graph that contains **no loops or multi-edges**.

---

#### Isomorphism

Two graphs \$G\$ and \$H\$ are **isomorphic** if there exists a **bijection** \$f: V(G) \rightarrow V(H)\$ such that:

* \$|V(G)| = |V(H)|\$
* \$|E(G)| = |E(H)|\$
* The **degree** of corresponding vertices is the same
* Edge connections are preserved:

  * \${u, v} \in E(G) \iff {f(u), f(v)} \in E(H)\$

---

#### Example of Isomorphism

Let \$f: V(G) \rightarrow V(H)\$ be defined as:

* \$w \rightarrow c\$
* \$x \rightarrow b\$
* \$y \rightarrow d\$
* \$z \rightarrow a\$

If all conditions are met, then **G ≅ H** (G is isomorphic to H).

---

#### Properties of Isomorphism

1. \$G \cong H\$ **only if** both are **simple graphs**.
2. \$G \cong H\$ if their **adjacency matrices** are identical (after vertex relabeling).
3. Subgraphs of \$G\$ and \$H\$ must also be **isomorphic** when corresponding vertices are deleted.

---

#### Homomorphism

Graphs \$G\_1\$ and \$G\_2\$ are **homomorphic** if they can be obtained from the **same original graph** \$G\$ by **dividing edges** with new intermediate vertices.

A **homomorphism** from \$G\_1\$ to \$G\_2\$ is a mapping:

$$
f: V(G_1) \rightarrow V(G_2)
$$

such that:

$$
\{u, v\} \in E(G_1) \Rightarrow \{f(u), f(v)\} \in E(G_2)
$$

**Important:**

* Edges in \$G\_1\$ map to edges in \$G\_2\$.
* **Non-edges** may map to edges, non-edges, or even a single vertex.
* **Adjacency** must be preserved.

---

#### Example of Homomorphism

If graph \$G\_1\$ contains an edge \$rs\$, and we divide it by introducing a new vertex \$t\$, then we get a modified graph \$G\_2\$. If all mappings preserve edge connectivity, then:

$$
G_1 \text{ is homomorphic to } G_2
$$

---

#### Summary

* A **graph** is composed of a **set of vertices** and **set of edges**.
* A **loop** is an edge connecting a vertex to itself.
* **Multi-edges** are multiple edges between the same pair of vertices.
* A **simple graph** contains neither loops nor multi-edges.
* Two graphs are **isomorphic** if there's a bijection between their vertices preserving edge connections and vertex degrees.
* **Homomorphism** allows graph simplification or extension while maintaining adjacency structure.
---

### Section 2: Euler Paths and Circuits

#### Euler Path

An **Euler path** is a path in a graph that **traverses every edge exactly once** without retracing any edge. You are allowed to visit vertices multiple times, but **no edge** can be crossed more than once.

A graph that contains at least one Euler path is called **semi-Eulerian**.

**Example:**
Imagine a figure that can be drawn without lifting your pencil and without retracing any edge. Suppose you follow this sequence:

```
1 → 3 → 2 → 4 → 3
```

Each edge is used **once**, and you **end at a different vertex**. This is a valid **Euler path**.

---

#### Characteristics of a Semi-Eulerian Graph

A graph has an **Euler path** if and only if:

* Exactly **two vertices** have **odd degree** (number of edges incident to them)
* All other vertices have **even degree**

In the example above:

* Vertex 1: odd
* Vertex 3: odd
  → Thus, the graph is **semi-Eulerian**

---

#### Example 1: Euler Path

Try the sequence:

```
2 → 1 → 4 → 2 → 3 → 4
```

This uses each edge once and ends at a different point than it started, forming an **Euler path**.

Another valid Euler path is:

```
4 → 3 → 2 → 4 → 1 → 2
```

There are **6 total Euler paths** in this graph. What distinguishes them is the **order** in which edges are used.

---

#### Euler Circuit

An **Euler circuit** is a circuit in a graph that:

* **Starts and ends at the same vertex**
* **Traverses every edge exactly once**

A graph that contains an Euler circuit is called **Eulerian**.

**Example:**
Try the path:

```
2 → 3 → 4 → 1 → 2
```

Or:

```
1 → 2 → 3 → 4 → 1
```

Both are **Euler circuits** because they:

* Start and end at the same vertex
* Use each edge exactly once

---

#### Characteristics of an Eulerian Graph

A graph has an **Euler circuit** if and only if:

* **All vertices** have an **even degree**

---

#### Example 2: Complex Euler Circuit

In some graphs, **edges are labeled** instead of vertices. Even in these, an Euler circuit can be identified by:

* Following all edges **exactly once**
* Returning to your **starting point**

**Hint:** Try tracing the edges in **alphabetical order**. If all conditions are met, the graph is **Eulerian**.

Multiple Euler circuits may exist, just with different traversal orders.

---

#### Summary

* An **Euler path**:

  * Traverses every edge once
  * Starts and ends at **different vertices**
  * Exists if **exactly two vertices** have **odd degree**

* An **Euler circuit**:

  * Traverses every edge once
  * **Starts and ends at the same vertex**
  * Exists if **all vertices** have **even degree**

* A **semi-Eulerian graph** contains an Euler path

* An **Eulerian graph** contains an Euler circuit


### Section 3: Euler Paths and Circuits in Real Life

#### Review of Concepts

* An **Euler path** traverses **every edge exactly once**.

  * Start and end points can be **different**.
  * A graph can have an Euler path if it has **0 or 2 vertices of odd degree**; the rest must be **even**.

* An **Euler circuit** is an Euler path that **starts and ends at the same vertex**.

  * A graph has an Euler circuit if **all vertices have even degree**.

---

#### Application 1: Delivering the Mail

A postman needs to deliver mail across **five streets**. He simplifies the neighborhood map by marking intersections as **vertices** and roads as **edges**.

To minimize effort, he wants to:

* Walk each road **only once**
* **Return** to his starting point (to his parked car)

**Euler circuit solution:**

```
1 → 2 → 3 → 4 → 5 → 1
```

This is an **Euler circuit** because:

* All edges are traversed once
* The start and end points are the same
* All vertices have **even degrees**

There are **10 different Euler circuits** for this graph, depending on:

* Starting vertex
* Direction of travel

With **5 vertices** and **2 directions**, the total is:

$$
5 \times 2 = 10
$$

---

#### Application 2: The Traveling Salesman

The salesman needs to travel **each road once**, but does **not** need to return to the starting point.

He draws a simplified graph of **five roads**.

**Euler path solution:**

```
3 → 2 → 1 → 5 → 4 → 1
```

This is a **valid Euler path** because:

* All edges are used once
* The start and end points are **different**
* The graph has **exactly two vertices of odd degree**

There are multiple Euler paths possible, depending on the **starting point** and **order** of edge traversal.

---

#### Application 3: The Seven Bridges of Königsberg

A famous historical problem:
**Can a person walk through all seven bridges of Königsberg exactly once without repeating any?**

**Approach:**

1. Simplify the map by creating a **graph**:

   * Each **land mass** becomes a **vertex**
   * Each **bridge** becomes an **edge**

2. Analyze the degrees of vertices:

   * All **four vertices** have **odd degrees** (3 or 5)

**Conclusion:**

* An **Euler path** requires **at most two odd-degree vertices**
* An **Euler circuit** requires **all vertices to be even**
* Since this graph has **four odd vertices**, **no Euler path or circuit** is possible

This unsolvable problem led **Leonhard Euler** to formalize **graph theory** in the 18th century — the foundation of today’s topic.

---

#### Summary

* **Euler Path**:

  * Crosses each edge once
  * Start and end points are **different**
  * Graph must have **0 or 2** odd-degree vertices

* **Euler Circuit**:

  * Crosses each edge once
  * **Starts and ends** at the same vertex
  * Graph must have **only even-degree vertices**

* **Real-World Applications**:

  * Mail delivery
  * Sales route planning
  * Network routing


### Section 4: Finding an Euler Circuit – Fleury's Algorithm

#### Scenario

Your friend is studying graph theory and encounters a problem:
He knows his graph contains an **Euler circuit** (a path that starts and ends at the same vertex and uses **each edge exactly once**), but he doesn’t know **how** to find it.

This is where **Fleury’s Algorithm** comes in.

---

#### What is Fleury's Algorithm?

**Fleury’s Algorithm** is a step-by-step method for finding an **Euler path** or an **Euler circuit** in a graph.

---

#### Step-by-Step Rules

1. **Check the Graph’s Degree Conditions**

   * If the graph has **0 odd-degree vertices**, it has an **Euler circuit**
   * If the graph has **2 odd-degree vertices**, it has an **Euler path**
   * Any more than 2 odd vertices → **No Euler path or circuit**

2. **Choose a Starting Vertex**

   * If 0 odd vertices → **Start anywhere**
   * If 2 odd vertices → **Start at one of the odd-degree vertices**

3. **Traverse the Graph by Choosing Safe Edges**

   * At each step, **prefer an edge that is *not* a bridge**
   * Only take a **bridge** if it’s the **only option left**

4. **Remove Each Edge After Using It**

   * Once you travel an edge, consider it **removed** from the graph
   * Repeat until all edges are used exactly once

---

#### What is a Bridge?

In graph theory, a **bridge** is an edge whose removal would **disconnect** the graph.

**Fleury's rule:**

> “Don’t burn your bridges — unless you must.”

That is, avoid bridges unless there are no alternative edges at your current vertex.

---

#### Example Walkthrough

Suppose your graph has **0 odd vertices**, so it contains an **Euler circuit**. You can **start at any vertex**. Let's say you start at the **bottom-most vertex**.

**Choices:**

* First move: choose between edge **A** and **K**

  * Neither is a bridge → pick either (e.g., **A**)
* After crossing **A**, you are at the **leftmost vertex**

  * Next choices: **B**, **D**, or **E**
  * Again, none are bridges → choose **B**
* From there: options are **C**, **F**, or **G**

  * Continue the process...

At each step:

* Choose a **non-bridge** if possible
* Cross the edge
* **Remove it** from the graph
* Continue until all edges are used

This will give you an **Euler circuit**.

Try starting at a **different vertex** to find another valid Euler circuit!

---

#### Summary

* **Fleury’s Algorithm** helps find **Euler paths and circuits** by:

  1. Checking for **0 or 2 odd vertices**
  2. Starting at a valid vertex (odd if path, any if circuit)
  3. Avoiding **bridges** until necessary
  4. Removing used edges as you go

* **Euler Path:** start ≠ end, exactly **2 odd-degree vertices**

* **Euler Circuit:** start = end, **0 odd-degree vertices**

By following Fleury's rules, you can **systematically construct** a valid Euler path or circuit in any qualifying graph.
 

### Section 5: Euler’s Theorems in Graph Theory

#### Why Euler’s Theorems Matter

Graphs are powerful tools for modeling **real-world networks** such as:

* Neighborhoods (intersections = **vertices**, roads = **edges**)
* Delivery routes
* Circuit designs
* Routing problems

**Euler’s theorems** allow us to determine whether it's possible to find a path or circuit that visits every edge **exactly once**, saving time and effort in planning.

---

#### 1. Euler’s Circuit Theorem

**Theorem:**

> *If a graph’s vertices are all of even degree, then the graph has an Euler circuit. Otherwise, it does not.*

**Explanation:**
An **Euler circuit** is a path that:

* **Uses every edge exactly once**
* **Starts and ends at the same vertex**

**Application:**
This is especially helpful for someone like a **mailman** who needs to return to their starting point without repeating any roads.

**Example:**

Let’s say we have the following graph:

* Bottom vertex: degree = 2
* All others: degree = 4

Since **all vertices have even degree**, the graph **has an Euler circuit**.

---

#### 2. Euler’s Path Theorem

**Theorem:**

> *If a graph has exactly two vertices of odd degree, then it has an Euler path that starts and ends at the odd-degree vertices. Otherwise, it does not.*

**Explanation:**
An **Euler path**:

* **Uses every edge exactly once**
* **Starts and ends at different vertices**

This is useful for scenarios like the **traveling salesman**, who doesn’t need to return to the starting point.

**Important Note:**
If the graph has **0** or **2 odd-degree vertices**, it may have an Euler path. If it has **more than 2**, no such path exists.

**Example:**
In our graph, **all vertices are even**, so:

* Euler **circuit** exists ✅
* Euler **path** exists ❌ (no odd-degree vertices to start/end on)

---

#### 3. Euler’s Sum of Degrees Theorem

**Theorem:**

> *The sum of the degrees of the vertices in a graph is equal to **twice** the number of edges.*

**Formula:**

$$
\sum \text{deg}(v) = 2 \times \text{number of edges}
$$

**Why this matters:**
This confirms whether a graph is **mathematically valid**.

**Example:**

* Total edges: 11
* Expected degree sum: \$2 \times 11 = 22\$

Now count the degrees:

* Bottom vertex: degree = 2
* Five other vertices: each with degree = 4
* Total: \$2 + (5 \times 4) = 2 + 20 = 22\$ ✅

This confirms the theorem.

---

#### Summary

We explored **three of Euler’s theorems** and their applications:

1. **Euler’s Circuit Theorem**:
   → All vertices even → Euler **circuit** exists

2. **Euler’s Path Theorem**:
   → Exactly two odd vertices → Euler **path** exists

3. **Euler’s Sum of Degrees Theorem**:
   → \$\sum \text{deg}(v) = 2 \times\$ number of edges

These theorems help determine whether it’s even possible to plan an **efficient route** through a network, which is useful for solving practical problems in navigation, logistics, and engineering.


### Section 6: Eulerizing and Semi-Eulerizing a Graph

#### Real-World Scenario

You are the **chief engineer** of the town of **Harrisville**. Your task:
Design the **road system** so that mail carriers can deliver efficiently — **crossing each street only once** and ideally **ending where they began**.

To achieve this, you apply **graph theory**.

* **Vertices** = intersections
* **Edges** = roads

---

#### Mailman-Friendly Graphs

A graph is **mailman-friendly** if:

* It has an **Euler circuit** (best case):

  * Mailman traverses each street **once**
  * Starts and ends at the **same** intersection

* It has an **Euler path** (acceptable):

  * Traverses each street **once**
  * Starts and ends at **different** intersections

You use **Fleury’s Algorithm** to analyze the graph.

---

#### Eulerizing a Graph

**Eulerizing** means adding edges (roads) to the graph to make it contain an **Euler circuit**.

#### Key Rule (Fleury’s Algorithm):

> A graph has an Euler **circuit** ⇨ **All vertices must have even degree**

---

#### Original Problem

You analyze the existing town graph and find **4 odd-degree vertices** (say, vertices 2, 3, 4, and 5).
This means:

* ❌ No Euler circuit
* ❌ No Euler path
* ➡ You must modify the graph

---

#### Step-by-Step Eulerizing

1. **Pair up odd vertices to make them even**
   Example:

   * Connect **vertex 2 to 3** → both become even
   * Connect **vertex 4 to 5** → both become even

2. Now **all vertices are even**
   ✅ The graph has an **Euler circuit**

You’ve now **Eulerized** the graph with **two new roads**.

---

#### Semi-Eulerizing a Graph

If you're short on funds, you can **semi-Eulerize** instead.

**Semi-Eulerizing** means changing the graph so that it contains an **Euler path**.

#### Key Rule (Fleury’s Algorithm):

> A graph has an Euler **path** ⇨ Exactly **two** vertices of **odd degree**

---

#### Step-by-Step Semi-Eulerizing

1. **Reduce odd vertices from 4 to 2**

   * Only **one** new road needed
   * Example: connect **vertex 2 to 3**

2. Now, only **vertices 4 and 5** remain odd
   ✅ The graph has an **Euler path**

This is a more **budget-friendly** solution, though the mailman won’t return to the starting point.

---

#### Comparison

| Feature              | Eulerizing         | Semi-Eulerizing |
| -------------------- | ------------------ | --------------- |
| Endpoints            | Same (start = end) | Different       |
| Graph Result         | Euler Circuit      | Euler Path      |
| Odd Vertices Allowed | 0                  | 2               |
| Efficiency           | Optimal            | Moderate        |
| Edge Additions       | More (e.g., 2)     | Fewer (e.g., 1) |
| Budget Impact        | Higher             | Lower           |

---

#### Summary

* **Eulerizing** a graph:
  → Add edges until **all vertices** are even
  → Creates an **Euler circuit**

* **Semi-Eulerizing** a graph:
  → Add edges until **exactly two** vertices are odd
  → Creates an **Euler path**

* Use **Fleury’s Algorithm** to determine how many vertices are odd and what modifications are needed.

Depending on your goals and **budget**, you can choose to **Eulerize** or **semi-Eulerize** your graph to make your city’s mail routes more efficient.

### Section 7: A Graph

#### Hamilton Circuit

Meet Larry. Larry is on a mission to visit **every house** in a neighborhood to promote a **free breakfast and shoe program** for children. He needs to visit each house **once** to spread the word and collect donations. To plan efficiently, Larry uses **graph theory**.

Larry models the neighborhood as a **graph**:

* **Vertices** = houses (dots)
* **Edges** = roads (lines connecting houses)

Larry wants to find a **route** that:

* Visits **each house exactly once**
* **Ends where he began**

This is known as a **Hamilton circuit**.

**Example route (Hamilton circuit):**

Start at house **A**, then:

$$
A \rightarrow B \rightarrow C \rightarrow D \rightarrow E \rightarrow F \rightarrow J \rightarrow I \rightarrow H \rightarrow G \rightarrow A
$$

This is a valid **Hamilton circuit**: every vertex is visited once, and the path returns to the start.

---

#### Hamilton Path

If Larry didn’t need to return to where he started, he could take a **Hamilton path** instead:

* Visits **each vertex once**
* **Ends at a different vertex**

**Example route (Hamilton path):**

$$
A \rightarrow B \rightarrow C \rightarrow D \rightarrow E \rightarrow F \rightarrow G \rightarrow H \rightarrow I \rightarrow J
$$

This is a valid **Hamilton path**, as all houses are visited once and Larry ends at house **J**.

---

#### More Circuits and Paths

There are **multiple** Hamilton circuits and paths possible.

**Another Hamilton circuit:**

$$
E \rightarrow J \rightarrow D \rightarrow I \rightarrow C \rightarrow H \rightarrow B \rightarrow G \rightarrow A \rightarrow F \rightarrow E
$$

**Another Hamilton path:**

$$
C \rightarrow H \rightarrow I \rightarrow D \rightarrow J \rightarrow E \rightarrow F \rightarrow G \rightarrow B \rightarrow A
$$

Finding all Hamilton circuits and paths is **not trivial** and becomes more complex with larger graphs. This is part of what makes problems like the **traveling salesman problem** computationally challenging.

---

#### Summary

* A **Hamilton circuit** visits **every vertex exactly once** and **returns to the starting point**.
* A **Hamilton path** visits **every vertex exactly once**, but **ends at a different vertex**.
* Many different Hamilton circuits and paths may exist for the same graph.
* These concepts are applicable in **real-world route planning**, especially when efficiency is needed across multiple locations.

### Section 8: A Hamilton Circuit

#### Hamilton Circuit

Imagine you're a **salesman** who wants to visit each house in a neighborhood **exactly once** and return to the starting point. You draw a **graph** to represent this neighborhood:

* **Vertices** = houses
* **Edges** = roads

In graph theory, such a route is called a **Hamilton circuit** — a path that:

* Visits each **vertex once**
* Ends at the **starting vertex**

**Example Hamilton circuit:**
Start at **B**, then:

$$
B \rightarrow C \rightarrow D \rightarrow E \rightarrow A \rightarrow G \rightarrow F \rightarrow J \rightarrow I \rightarrow H \rightarrow B
$$

This is a valid **Hamilton circuit** because it:

* Visits all vertices once
* Ends where it started

---

#### A Weighted Graph

Now suppose each road has a **cost** (e.g., gas or distance). This is called a **weighted graph**, where each **edge has an associated weight**.

Your goal now changes:

> Find the **Hamilton circuit with the least total cost**

**Example minimum-cost Hamilton circuit:**
Start at **B**, then:

$$
B \rightarrow H \rightarrow C \rightarrow I \rightarrow D \rightarrow J \rightarrow E \rightarrow F \rightarrow A \rightarrow G \rightarrow B
$$

**Total cost:** 20
This is the **cheapest** Hamilton circuit in the graph.
You could start at **any vertex** and follow the same order (cyclically) — the total cost remains 20.

Try other routes and add up the edge weights to verify that **none are cheaper**.

---

#### Complete Graph

A **complete graph** is one where **every vertex is connected to every other vertex**.

In a complete graph:

* You can **travel directly** from any vertex to any other
* There are **many Hamilton circuits**

To calculate the number of Hamilton circuits in a complete graph:

* Let \$N\$ = number of vertices
* Use the formula:

$$
(N - 1)!
$$

---

#### Example: 5 Vertices

If \$N = 5\$:

$$
(5 - 1)! = 4! = 4 \times 3 \times 2 \times 1 = 24
$$

There are **24 Hamilton circuits**.

---

#### Example: 4 Vertices

If \$N = 4\$:

$$
(4 - 1)! = 3! = 3 \times 2 \times 1 = 6
$$

There are **6 Hamilton circuits**.
**Example circuit:**

$$
A \rightarrow B \rightarrow C \rightarrow D \rightarrow A
$$

---

#### Summary

* A **Hamilton circuit** visits each vertex **once** and returns to the **starting point**
* A **weighted graph** assigns a **cost** to each edge
* The **best** Hamilton circuit in a weighted graph is the one with the **lowest total cost**
* A **complete graph** has all possible connections between vertices
* The number of Hamilton circuits in a complete graph is:
  $(N - 1)!$
  where \$N\$ is the number of vertices

### Section 9: Graph Representations in Discrete Mathematics

#### Introduction

You’re craving french fries, so you type in a recipe search. Within seconds, your search engine delivers a list of perfect recipes.

But behind the scenes, what actually happens?

That **search engine** is built on **graph theory**. Each webpage is a **vertex**, and hyperlinks between them are **edges**. In fact, **the entire World Wide Web is a graph**.

Let’s now explore how these graphs are represented in **discrete math**.

---

#### What Is a Graph?

A **graph** is a collection of:

* **Vertices** (dots)
* **Edges** (lines connecting the dots)

Graphs come in two forms:

* **Directed Graph** (digraph):
  Edges have a direction. You can only travel **from** one vertex **to** another in the direction indicated.

* **Undirected Graph**:
  Edges have **no direction**. You can travel both ways between any two connected vertices.

---

#### Graph Representations

Graphs can be represented in **two main ways**:

1. **Adjacency Matrix**
2. **Adjacency List**

---

#### 1. Adjacency Matrix

An **adjacency matrix** is a **V × V** two-dimensional array, where **V** is the number of vertices.

* In a **directed graph**:

  * If there is an edge from vertex **i** to vertex **j**, then the entry at row **i**, column **j** is `1`
  * If no such edge exists, the entry is `0`

**Example:**

If a graph has the edges `PQ`, `PT`, `RP`, `RS`, `TR`, `TS`, the matrix will reflect a `1` in those positions and `0` elsewhere.

* In an **undirected graph**:

  * If there is an edge between **i** and **j**, both entries `i → j` and `j → i` are `1`

**Observation:**
The matrix of an undirected graph is **symmetric** across its diagonal.

---

#### 2. Adjacency List

An **adjacency list** records all neighbors of each vertex. It is implemented as an array of **linked lists**, where:

* Each index in the array represents a vertex
* Each linked list contains **all vertices** connected to that vertex

---

#### Adjacency List – Directed Graph

If vertex **P** connects to **Q** and **T**, and **R** connects to **P** and **S**, then the adjacency list looks like:

```
P → Q → T  
R → P → S  
T → R → S  
```

---

#### Adjacency List – Undirected Graph

If **P** connects to **Q**, **R**, and **T**, and so on, the adjacency list would be:

```
P → Q → R → T  
Q → P  
R → P → T → S  
S → R → T  
T → P → R → S  
```

---

#### Summary

* A **graph** is a set of vertices connected by edges.

* Graphs may be:

  * **Directed** (one-way edges)
  * **Undirected** (two-way edges)

* Graphs can be represented as:

  * **Adjacency Matrix** (a 2D array of `1`s and `0`s)
  * **Adjacency List** (linked lists of neighboring vertices)

* Adjacency matrices are ideal for **dense graphs**

* Adjacency lists are more efficient for **sparse graphs**

These representations are foundational to computer science, web searches, social networks, logistics, and more.