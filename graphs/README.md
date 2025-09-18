
---

```markdown
# Graphs in Data Structures

This document provides a clear explanation of **graphs**, their basic components, common types, representation methods in C, and traversal techniques like **DFS (Depth-First Search)** and **BFS (Breadth-First Search)**.

---

## 📌 What is a Graph?

A **graph** is a non-linear data structure consisting of a finite set of **nodes (or vertices)** and a set of **connections (or edges)** between them.  
Graphs are widely used to model relationships between objects, such as social networks, road maps, communication systems, and computer networks.

Formally, a graph is represented as:  
**G = (V, E)**  
- **V** = Set of vertices (nodes)  
- **E** = Set of edges (connections between vertices)

---

## 📌 Vertices and Edges

- **Vertices (Nodes):**  
  These are the fundamental units or points in a graph. For example, in a social network, each person can be represented as a vertex.

- **Edges (Links):**  
  These are the connections between vertices. An edge may represent relationships (friendship, road connection, etc.) between two vertices.

Example:  
```

Vertices: {A, B, C, D}
Edges: {(A, B), (B, C), (C, D), (A, D)}

```

---

## 📌 Types of Graphs

Graphs can be categorized in multiple ways depending on their characteristics:

1. **Undirected Graph**  
   - Edges have no direction.  
   - If an edge exists between `A` and `B`, then traversal is possible both ways (`A → B` and `B → A`).

2. **Directed Graph (Digraph)**  
   - Edges have a direction.  
   - If an edge exists from `A` to `B`, you can only traverse `A → B`, not necessarily `B → A`.

3. **Weighted Graph**  
   - Each edge is assigned a weight (or cost).  
   - Useful in shortest path algorithms like Dijkstra’s.  
   - Example: Road networks where edges represent distance or time.

4. **Unweighted Graph**  
   - All edges are considered equal (no weights).

5. **Cyclic Graph**  
   - Contains at least one cycle (a path that starts and ends at the same vertex).

6. **Acyclic Graph**  
   - Contains no cycles.  
   - Example: Trees are a special case of acyclic graphs.

7. **Connected Graph**  
   - There is a path between every pair of vertices.

8. **Disconnected Graph**  
   - Some vertices are not reachable from others.

---

## 📌 Representation of Graphs in C

In C programming, graphs are commonly represented using:

### 1. **Adjacency Matrix**
- A 2D array `graph[V][V]` where `graph[i][j] = 1` (or weight) if an edge exists between vertex `i` and `j`, else `0`.
- Easy to implement but requires **O(V²)** space.

Example (Undirected Graph):  
```

```
A B C
```

A \[ 0 1 0 ]
B \[ 1 0 1 ]
C \[ 0 1 0 ]

```

### 2. **Adjacency List**
- An array of linked lists where each index represents a vertex, and each node in the linked list represents the connected vertices.
- More space-efficient for sparse graphs.
- Space complexity: **O(V + E)**.

Example:  
```

A → B
B → A → C
C → B

````

---

## 📌 Graph Traversal

Traversal means visiting all the vertices of a graph in a systematic manner. Two common methods are:

### 1. **Depth-First Search (DFS)**
- Explores as far as possible along a branch before backtracking.
- Uses **recursion** or a **stack**.
- Suitable for detecting cycles, pathfinding, and topological sorting.

**Pseudocode (DFS using recursion):**
```c
void DFS(int v, bool visited[], int graph[V][V]) {
    visited[v] = true;
    printf("%d ", v);

    for (int i = 0; i < V; i++) {
        if (graph[v][i] == 1 && !visited[i]) {
            DFS(i, visited, graph);
        }
    }
}
````

---

### 2. **Breadth-First Search (BFS)**

* Explores all neighbors of a vertex before moving to the next level.
* Uses a **queue**.
* Suitable for finding the shortest path in unweighted graphs.

**Pseudocode (BFS using queue):**

```c
void BFS(int start, int graph[V][V]) {
    bool visited[V] = {false};
    int queue[V], front = 0, rear = 0;

    visited[start] = true;
    queue[rear++] = start;

    while (front < rear) {
        int v = queue[front++];
        printf("%d ", v);

        for (int i = 0; i < V; i++) {
            if (graph[v][i] == 1 && !visited[i]) {
                visited[i] = true;
                queue[rear++] = i;
            }
        }
    }
}
```

---

## ✅ Summary

* A **graph** is a collection of **vertices** connected by **edges**.
* Graphs can be **directed, undirected, weighted, unweighted, cyclic, acyclic, connected,** or **disconnected**.
* Graphs in C are typically represented using **adjacency matrices** or **adjacency lists**.
* Common traversal algorithms are:

  * **DFS (Depth-First Search)** → Stack/Recursion
  * **BFS (Breadth-First Search)** → Queue

---
