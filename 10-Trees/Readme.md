# 🌳 Tree Pattern Notebook

> **Goal:** Master Binary Trees through **pattern recognition**, not problem memorization.
>
> Learn trees in the same order used by top interviewers (Amazon, Microsoft, Google, Atlassian, Adobe, Walmart, JPMC, etc.).

---

# 📚 Tree Learning Roadmap

```
12-Tree
│
├── 01-Tree Fundamentals
│      ├── TreeNode
│      ├── DFS vs BFS
│      ├── Recursive Thinking
│      ├── Traversals
│      ├── Height & Depth
│      └── Binary Tree vs BST
│
├── 02-Tree DFS
│      ├── Basic DFS
│      ├── Root-to-Leaf
│      ├── Bottom-Up DFS
│      ├── Global Answer DFS
│      ├── Tree DP
│      └── Lowest Common Ancestor
│
├── 03-Tree BFS
│      ├── Level Order
│      ├── Zigzag
│      ├── Right View
│      ├── Left View
│      ├── Average of Levels
│      └── Vertical Traversal
│
├── 04-BST
│      ├── Search
│      ├── Insert
│      ├── Delete
│      ├── Validate BST
│      ├── Kth Smallest
│      ├── Iterator
│      └── Recover BST
│
├── 05-Tree Construction
│      ├── Build from Traversals
│      ├── Sorted Array → BST
│      ├── Sorted List → BST
│      └── Serialize / Deserialize
│
└── 06-Advanced Trees
       ├── Flatten Tree
       ├── Morris Traversal
       ├── Euler Tour
       ├── Binary Lifting
       └── Advanced Tree DP
```

---

# ⭐ Interview Priority

| Pattern | Importance |
|----------|------------|
| Tree DFS | ⭐⭐⭐⭐⭐ |
| Tree BFS | ⭐⭐⭐⭐⭐ |
| BST | ⭐⭐⭐⭐⭐ |
| Lowest Common Ancestor | ⭐⭐⭐⭐⭐ |
| Diameter | ⭐⭐⭐⭐⭐ |
| Maximum Path Sum | ⭐⭐⭐⭐⭐ |
| Balanced Tree | ⭐⭐⭐⭐⭐ |
| Tree Construction | ⭐⭐⭐⭐ |
| Serialization | ⭐⭐⭐⭐ |
| Vertical Traversal | ⭐⭐⭐⭐ |
| Morris Traversal | ⭐⭐⭐ |

---

# Pattern Recognition

| Question asks... | Pattern |
|------------------|---------|
| Height | DFS |
| Count Nodes | DFS |
| Root to Leaf Path | DFS |
| Diameter | Bottom-Up DFS |
| Maximum Path Sum | Global DFS |
| Balanced Tree | Bottom-Up DFS |
| Lowest Common Ancestor | LCA |
| Level Order | BFS |
| Zigzag | BFS |
| Right View | BFS |
| Vertical Traversal | BFS + Coordinates |
| Kth Smallest | BST Inorder |
| Build Tree | Tree Construction |
| Serialize | DFS/BFS |

---

# Learning Order

```
Fundamentals

↓

Basic DFS

↓

Root-to-Leaf DFS

↓

Bottom-Up DFS

↓

Global DFS

↓

Tree DP

↓

Lowest Common Ancestor

↓

BFS

↓

BST

↓

Construction

↓

Serialization

↓

Advanced Trees
```

---

# Problems We'll Solve

## Fundamentals

- LC104 Maximum Depth
- LC100 Same Tree
- LC101 Symmetric Tree
- LC111 Minimum Depth
- LC222 Count Complete Tree Nodes

---

## Root-to-Leaf DFS

- LC112 Path Sum
- LC113 Path Sum II
- LC257 Binary Tree Paths

---

## Bottom-Up DFS

- LC110 Balanced Binary Tree
- LC543 Diameter of Binary Tree
- LC687 Longest Univalue Path

---

## Global DFS

- LC124 Binary Tree Maximum Path Sum
- LC1372 Longest ZigZag Path
- LC549 Binary Tree Longest Consecutive Sequence II

---

## Tree DP

- LC337 House Robber III
- LC968 Binary Tree Cameras
- LC979 Distribute Coins

---

## Lowest Common Ancestor

- LC236 LCA
- LC1644 LCA II
- LC1676 LCA IV

---

## BFS

- LC102 Level Order
- LC103 Zigzag
- LC199 Right Side View
- LC515 Largest Value
- LC637 Average of Levels
- LC987 Vertical Traversal

---

## BST

- LC700 Search BST
- LC701 Insert BST
- LC450 Delete BST
- LC98 Validate BST
- LC230 Kth Smallest
- LC173 BST Iterator
- LC99 Recover BST

---

## Construction

- LC105 Build Tree
- LC106 Build Tree II
- LC108 Sorted Array to BST
- LC109 Sorted List to BST

---

## Serialization

- LC297 Serialize & Deserialize

---

## Advanced

- LC114 Flatten Binary Tree
- LC426 BST to Doubly Linked List
- LC94 Morris Traversal

---
# 🌳 Tree Fundamentals

> **Goal:** Build the recursive thinking needed for every Tree interview problem.

---

# What is a Tree?

A **Tree** is a collection of nodes connected without cycles.

Unless specified otherwise,

**Tree = Binary Tree**

```
        1
      /   \
     2     3
    / \     \
   4   5     6
```

Each node has at most **two children**.

---

# TreeNode

Almost every interview uses this structure.

```java
class TreeNode {

    int val;
    TreeNode left;
    TreeNode right;

    TreeNode() {}

    TreeNode(int val) {
        this.val = val;
    }

    TreeNode(int val, TreeNode left, TreeNode right) {
        this.val = val;
        this.left = left;
        this.right = right;
    }
}
```

---

# Tree Terminology

```
        A
      /   \
     B     C
    / \
   D   E
```

| Term | Meaning |
|------|----------|
| Root | First node |
| Parent | Node having children |
| Child | Connected below parent |
| Leaf | Node with no children |
| Height | Longest path from node to leaf |
| Depth | Distance from root |
| Subtree | Tree rooted at any node |

---

# The Most Important Mindset

Unlike Arrays,

You **cannot jump** to any node.

At every node, you only know:

```
Current Node

↓

Left Child

↓

Right Child
```

Almost every Tree problem follows this idea.

---

# Recursive Thinking

Every recursive Tree problem answers three questions.

## 1. What should I do at the current node?

Examples

- Compare values
- Update answer
- Build path
- Count node

---

## 2. What should the left subtree return?

---

## 3. What should the right subtree return?

Most Tree problems become easy once these three questions are answered.

---

# Universal DFS Template

```java
void dfs(TreeNode root){

    if(root == null)
        return;

    dfs(root.left);

    dfs(root.right);
}
```

Every DFS solution is this template with additional logic.

---

# DFS Traversals

## Preorder

```
Root

↓

Left

↓

Right
```

Template

```java
void dfs(TreeNode root){

    if(root==null)
        return;

    visit(root);

    dfs(root.left);

    dfs(root.right);
}
```

Used when

- Build Tree
- Serialize
- Copy Tree
- Flatten Tree

---

## Inorder

```
Left

↓

Root

↓

Right
```

Template

```java
void dfs(TreeNode root){

    if(root==null)
        return;

    dfs(root.left);

    visit(root);

    dfs(root.right);
}
```

Used when

- BST
- Sorted Order
- Kth Smallest
- Validate BST

---

## Postorder ⭐⭐⭐⭐⭐

```
Left

↓

Right

↓

Root
```

Template

```java
void dfs(TreeNode root){

    if(root==null)
        return;

    dfs(root.left);

    dfs(root.right);

    visit(root);
}
```

Used when

- Height
- Diameter
- Balanced Tree
- Maximum Path Sum
- Tree DP

This is the **most important traversal** for interviews.

---

# BFS Template

```
        1
      /   \
     2     3
    / \   / \
   4  5  6  7
```

Traversal

```
1

2 3

4 5 6 7
```

Template

```java
Queue<TreeNode> q = new LinkedList<>();

q.offer(root);

while(!q.isEmpty()){

    int size = q.size();

    for(int i=0;i<size;i++){

        TreeNode node = q.poll();

        if(node.left!=null)
            q.offer(node.left);

        if(node.right!=null)
            q.offer(node.right);
    }
}
```

Used for

- Level Order
- Zigzag
- Right View
- Left View
- Vertical Traversal

---

# DFS vs BFS

| DFS | BFS |
|------|-----|
| Stack / Recursion | Queue |
| Goes Deep | Goes Level by Level |
| Height | Level Order |
| Diameter | Zigzag |
| LCA | Right View |

---

# Four Return Types

## Return Nothing

```java
void dfs(TreeNode root)
```

Examples

- Flatten Tree
- Binary Tree Paths

---

## Return Integer ⭐⭐⭐⭐⭐

```java
int dfs(TreeNode root)
```

Examples

- Height
- Count
- Maximum
- Sum

---

## Return Boolean

```java
boolean dfs(TreeNode root)
```

Examples

- Same Tree
- Symmetric Tree
- Validate BST

---

## Return TreeNode

```java
TreeNode dfs(TreeNode root)
```

Examples

- Lowest Common Ancestor
- Search BST
- Delete Node

---

# Recognition Cheat Sheet

| If the question says... | Think... |
|-------------------------|----------|
| Height | Postorder DFS |
| Diameter | Postorder DFS |
| Balanced | Postorder DFS |
| Path | DFS |
| Root to Leaf | DFS |
| Level | BFS |
| Zigzag | BFS |
| Right View | BFS |
| Kth Smallest | Inorder |
| Validate BST | Inorder |
| LCA | DFS |
| Build Tree | Recursion |
| Serialize | DFS / BFS |

---

# Tree Decision Flow

```
Tree Problem

        │
        ▼

Need levels?

YES → BFS

NO

↓

Need information from children?

YES

↓

Postorder DFS

↓

Need parent before children?

↓

Preorder

↓

BST?

↓

Inorder
```

---

# One-Page Revision

✅ Trees are solved using Recursion or BFS.

✅ Every recursive problem asks:
- What do I do now?
- What does left return?
- What does right return?

✅ Traversals

- Preorder → Root Left Right
- Inorder → Left Root Right
- Postorder → Left Right Root

✅ Postorder is the most important traversal.

✅ BFS is used whenever the problem mentions **levels**.

✅ Inorder is almost always used in **BST** problems.

If you can recognize these patterns, you've already solved half of the interview problem before writing any code.