# Pattern 13 — Graphs

# 13.0 — Graph Fundamentals

> **Goal:** Build the foundation required for every graph interview problem by understanding graph terminology, representations, traversal techniques, and how to recognize graph patterns.

---

# What is a Graph?

A **Graph** is a collection of:

* **Vertices (Nodes)**
* **Edges (Connections)**

Unlike trees:

* A graph may contain **cycles**.
* A graph may be **disconnected**.
* A graph does **not** require a root node.
* There can be **multiple paths** between two nodes.

Example:

```text
      A -------- B
      |          |
      |          |
      D -------- C
```

Vertices

```text
A B C D
```

Edges

```text
A-B

B-C

C-D

D-A
```

---

# Tree vs Graph

| Tree                | Graph                   |
| ------------------- | ----------------------- |
| Has a root          | No root required        |
| No cycles           | Cycles allowed          |
| Always connected    | May be disconnected     |
| N nodes → N−1 edges | Any number of edges     |
| Unique path         | Multiple paths possible |

---

# Graph Terminology

## Vertex (Node)

A single point in the graph.

```text
A
```

---

## Edge

Connection between two vertices.

```text
A ----- B
```

---

## Degree

Number of edges connected to a node.

Example

```text
A ---- B ---- C
       |
       D
```

Degree

```text
A = 1

B = 3

C = 1

D = 1
```

---

## Path

A sequence of connected vertices.

```text
A → B → C
```

---

## Cycle

A path that starts and ends at the same node.

```text
A

↓

B

↓

C

↓

A
```

---

## Connected Component

A group of vertices where every node is reachable from every other node.

Example

```text
A ---- B


C ---- D
```

There are **2 connected components**.

---

# Types of Graphs

## 1. Undirected Graph

Edges work in both directions.

```text
A ----- B
```

Equivalent to

```text
A ↔ B
```

Examples

* Friendships
* Roads
* Computer Networks

---

## 2. Directed Graph

Edges have direction.

```text
A → B
```

Moving from **B → A** is not allowed unless another edge exists.

Examples

* Course Prerequisites
* Twitter Follow
* Task Dependencies

---

## 3. Weighted Graph

Each edge has an associated cost.

```text
A --5--> B
```

Meaning

```text
Cost = 5
```

Examples

* GPS Navigation
* Flight Costs
* Network Latency

---

## 4. Unweighted Graph

Every edge has equal cost.

```text
A ----- B
```

Each edge contributes

```text
1
```

---

# Graph Representation

There are two common representations.

---

# 1. Adjacency Matrix

Example

```text
A ---- B
|
|
C
```

Matrix

```text
      A B C

A     0 1 1

B     1 0 0

C     1 0 0
```

Meaning

```text
matrix[A][B] = 1
```

An edge exists.

### Complexity

| Operation          | Complexity |
| ------------------ | ---------- |
| Space              | O(V²)      |
| Check Edge         | O(1)       |
| Traverse Neighbors | O(V)       |

### Best For

* Dense Graphs
* Small Graphs

---

# 2. Adjacency List ⭐⭐⭐⭐⭐

Most common interview representation.

Example

```text
A ---- B
|
|
C
```

Store

```text
A → B,C

B → A

C → A
```

Java

```java
List<List<Integer>> graph = new ArrayList<>();
```

or

```java
Map<Integer, List<Integer>> graph = new HashMap<>();
```

### Complexity

| Operation          | Complexity |
| ------------------ | ---------- |
| Space              | O(V + E)   |
| Check Edge         | O(Degree)  |
| Traverse Neighbors | O(Degree)  |

### Best For

* Sparse Graphs
* Competitive Programming
* Coding Interviews

---

# Which Representation Should You Use?

| Situation               | Representation   |
| ----------------------- | ---------------- |
| Sparse Graph            | Adjacency List   |
| Dense Graph             | Adjacency Matrix |
| Competitive Programming | Adjacency List   |
| Interviews              | Adjacency List   |

> **90% of graph interview problems use an adjacency list.**

---

# Building an Adjacency List

Edges

```text
0-1

0-2

1-3

2-3
```

Graph

```text
      0
     / \
    1   2
     \ /
      3
```

Java

```java
List<List<Integer>> graph = new ArrayList<>();

for (int i = 0; i < n; i++)
    graph.add(new ArrayList<>());

graph.get(0).add(1);
graph.get(1).add(0);

graph.get(0).add(2);
graph.get(2).add(0);

graph.get(1).add(3);
graph.get(3).add(1);

graph.get(2).add(3);
graph.get(3).add(2);
```

Result

```text
0 → [1,2]

1 → [0,3]

2 → [0,3]

3 → [1,2]
```

---

# Graph Traversal

Two primary traversal techniques.

---

## DFS (Depth First Search)

Uses

* Recursion
* Stack

Explores one path completely before backtracking.

Visualization

```text
A

↓

B

↓

C

↓

D
```

Recognition Signals

* Explore entire graph
* Connected Components
* Cycle Detection
* Backtracking
* Enumerating Paths

---

## BFS (Breadth First Search)

Uses

* Queue

Visits nodes level by level.

Visualization

```text
A

↓

B   C

↓

D   E   F
```

Recognition Signals

* Shortest Path (Unweighted Graph)
* Minimum Steps
* Multi-Source Expansion
* Level Order Traversal
* Spread Simulation

---

# DFS vs BFS

| DFS                 | BFS                     |
| ------------------- | ----------------------- |
| Stack / Recursion   | Queue                   |
| Goes Deep First     | Goes Level by Level     |
| Good for Components | Good for Shortest Paths |
| Backtracking        | Layer Expansion         |

---

# Complexity

For both DFS and BFS:

```text
Time = O(V + E)

Space = O(V)
```

Where

* **V** = Number of Vertices
* **E** = Number of Edges

Reason

* Every vertex is visited once.
* Every edge is processed once.

---

# Mental Model

Think of a graph as a **city map**.

* Vertices → Cities
* Edges → Roads

DFS

> Pick one road and keep driving until you can't go further, then backtrack.

BFS

> Visit every city one road away, then two roads away, then three roads away.

---

# Recognition Cheat Sheet

| Problem Statement | Think                  |
| ----------------- | ---------------------- |
| Friend Network    | Graph                  |
| Roads             | Graph                  |
| Flights           | Weighted Graph         |
| Dependencies      | Directed Graph         |
| Social Network    | Graph                  |
| Course Schedule   | Directed Graph         |
| Islands           | Grid Graph             |
| Shortest Route    | BFS / Dijkstra         |
| Connected Groups  | DFS / BFS / Union-Find |

---

# Common Interview Patterns

| Pattern               | Typical Problems               |
| --------------------- | ------------------------------ |
| DFS                   | Islands, Provinces, Components |
| BFS                   | Rotting Oranges, Open Lock     |
| Multi-Source BFS      | 01 Matrix, Walls and Gates     |
| Topological Sort      | Course Schedule                |
| Union-Find            | Redundant Connection           |
| Dijkstra              | Network Delay Time             |
| Minimum Spanning Tree | Connect All Points             |

---

# Graph Pattern Roadmap

```text
Graph Fundamentals
        │
        ▼
DFS
        │
        ▼
BFS
        │
        ▼
Connected Components
        │
        ▼
Multi-Source BFS
        │
        ▼
Topological Sort
        │
        ▼
Union-Find (DSU)
        │
        ▼
Shortest Path (Dijkstra)
        │
        ▼
Minimum Spanning Tree
        │
        ▼
Advanced Graph Algorithms
```

---

# Key Takeaways

* Graphs generalize trees by allowing cycles and multiple paths.
* The **Adjacency List** is the preferred representation in interviews.
* **DFS** explores deeply and is ideal for components and path exploration.
* **BFS** explores level by level and is ideal for shortest-path problems in unweighted graphs.
* Most graph interview questions are built on a handful of reusable traversal patterns.

---

# One-Line Revision

> **A graph is a collection of vertices connected by edges. Most interview problems represent graphs using an adjacency list and solve them using DFS, BFS, Union-Find, Topological Sort, or shortest-path algorithms depending on the problem.**
