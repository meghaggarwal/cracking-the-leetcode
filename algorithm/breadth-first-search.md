---
description: This is the BFS algorithm
icon: sandwich
---

# breadth first search

* We traverse the nodes by breadth, level wise.

### **Tree traversal (Binary, Ternary, etc)**

```
PSEUDOCODE

- traverse the root node
- Put the root node in queue: q
- till not q.empty() loop:
	~ - Calculate the current queue size - curr_size
	~ till curr_size() loop: **// this inner loop is only needed in case we need level order manipulation, as soon as inner loop ends, that level finishes**
		~ pop curr node from queue: FIFO
		~ implement logic if that curr level element is needed, ex: Store that node val in the array
		~ get children of node using pointers.
		~ push the children of node in queue
```

### **Graph traversal (graph is also one special kind of tree)**

```
PSEUDOCODE

- traverse any source vertex, mark the vertex as visited
- Push the vertex in queue: q
- till not q.empty() loop:
	~ pop the curr vertice: FIFO
	~ Get all neighbours of vertex using graph representation
	~ for neighbour of neighbours is not visited; bool check:
		~ push all neightbours of the curr vertex in the queue
		~ mark all the neightbours vertices visited that are pushed

// NOTE:
In general we don't need level order manipulation in graph, but if needed, we need to find curr queue size, and add an inner loop.
```



> <mark style="background-color:green;">**Why Graphs nodes are marked as visited during BFS?**</mark>
>
> * **In graph, nodes are always marked visited** once they are pushed.\
>   This is important because if we don't mark visited for bidirectional/cyclic graph, we will encounter unlimited stack push, TLE.
> * **Also we mark visited while PUSH, not POP to prevent repetitive push of vertices in queue.** Try it out!

### **Time Complexity** ⏰

<mark style="color:blue;">**Tree**</mark>: Visit all nodes once: O(n), where n is total no of nodes in tree.

<mark style="color:blue;">**Graph:**</mark>\
<mark style="background-color:yellow;">**Adjacency matrix**</mark>\
\- O(v2): In matrix, Visit all neighbours of the node even if neighbours doesn't exist, since we use matrix.\
<mark style="background-color:yellow;">**Adjacency list:**</mark>\
\- O(V + E): visit all the vertices and the edges

### **Space Complexity**&#x20;

<mark style="color:blue;">**Tree**</mark>: Queue: O(V) At max we can keep V nodes in queue, where V is the no of nodes at deepest level

<mark style="color:blue;">**Graph:**</mark>\
<mark style="background-color:yellow;">**Adjacency matrix**</mark>\
\- O(V2) - matrix representation for graph\
\- O(V) - keep visited vertices in array + queue push\
\== O(V2)\
<mark style="background-color:yellow;">**Adjacency list**</mark> \
\- O(V + E) - graph representation\
\- O(V) - keep visited vertices in array + queue push

> <mark style="background-color:green;">**Why V + E complexity is accounted in graphs but not trees?**</mark>
>
> Since graph can have more no of edges than vertices, in cyclic or bidirectional graph, so we have to check neighbours connected via edge, and see if it's not already marked visited, etc. So in traversal of graphs, edge complexity is necessary since it accumulates weight to calculate neighbours of graph.
>
> But in tree, the no of edges are always V - 1, so edges doesnt add any weight. There are no cycles or bidirectional, a child can have only 1 parent.

### **Time & Space Complexity Summary ✅:**

| Operation                              | Adjacency List       | Adjacency Matrix | Tree                                      |
| -------------------------------------- | -------------------- | ---------------- | ----------------------------------------- |
| **Space Complexity**                   | O(V + E) + O(V)      | O(V²) + O(V)     | O(max\_nodes\_at\_deepest\_level)         |
| **BFS Time Complexity**                | O(V + E)             | O(V²)            | O(n)                                      |
| **Check if Two Vertices are Adjacent** | O(degree(v)) \~ O(V) | O(1)             | NA, we have parent and child concept O(1) |

_<mark style="color:purple;">degree of v: no of neighbour vertices connected to the the vertice, at max in a dense graph, every vertex can be connected to each other</mark>_

