---
description: This is the DFS algorithm
icon: sandwich
---

# depth first search

* Visit nodes at depth

### Tree Traversal 🌲

```
ITERATIVE PSEUDOCODE
- traverse the root node
- push the node in stack
- while not stack.isEmpty() loop:
	~ pop the curr node: LIFO
	~ get children of the curr node
	~ push the children in right to left order, so we get INORDER traversal


RECURSIVE PSEUDOCODE
- visit the root node.
- vist left subtree
- visit right subtree
- Try with different DFS tree order traversals
```

### Graph Traversal 👩‍💻

```
PSEUDOCODE: EQUIVALENT TO BFS, JUST USE STACK
- traverse any source vertex, mark visited
- push to stack
- while not stack.empty() loop:
	~ pop the curr vertex: LIFO
	~ find all neighbours of that curr vertex, using graph representation
	~ if not neighbour visted bool check:
		~ push the neighbour vertices to stack
		~ mark them visited
```

> BFS and DFS are very similar in terms of time complexities, bfs uses queue, dfs uses stack.

### **Space Complexity**

<mark style="color:blue;">**Tree**</mark><mark style="color:blue;">:</mark> Recursive stack space O(V) for skewed tree, same for actual stack for iterative approach O(V)

<mark style="color:blue;">**Graph**</mark>\
<mark style="background-color:yellow;">**Adjacency List**</mark><mark style="background-color:yellow;">:</mark>

* O(V): We use stack to store + visited array , where v is total no of vertices
* O(V + E): stores vertices and store adjacent edges connected to it

<mark style="background-color:yellow;">**Adjacency Matrix**</mark>

* O(V2): store graph
* O(V): stack + array to keep visited vertex

### **Time & Space Complexity Summary ✅:**

| Operation                              | Adjacency List       | Adjacency Matrix | Tree                                      |
| -------------------------------------- | -------------------- | ---------------- | ----------------------------------------- |
| **DFS Space Complexity**               | O(V + E) + O(V)      | O(V²) + O(V)     | O(n) for skewed tree, stack trace         |
| **DFS/BFS Time Complexity**            | O(V + E)             | O(V²)            | O(n)                                      |
| **Check if Two Vertices are Adjacent** | O(degree(v)) \~ O(V) | O(1)             | NA, we have parent and child concept O(1) |
