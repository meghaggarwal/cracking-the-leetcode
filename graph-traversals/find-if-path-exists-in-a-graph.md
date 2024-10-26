# Find if Path Exists in a Graph

There is a **bi-directional** graph with `n` vertices, where each vertex is labeled from `0` to `n - 1` (**inclusive**). The edges in the graph are represented as a 2D integer array `edges`, where each `edges[i] = [ui, vi]` denotes a bi-directional edge between vertex `ui` and vertex `vi`. Every vertex pair is connected by **at most one** edge, and no vertex has an edge to itself.

You want to determine if there is a **valid path** that exists from vertex `source` to vertex `destination`.

Given `edges` and the integers `n`, `source`, and `destination`, return `true` _if there is a **valid path** from_ `source` _to_ `destination`_, or_ `false` _otherwise\_\_._

**Example 1:**

![](https://assets.leetcode.com/uploads/2021/08/14/validpath-ex1.png)

**Input:** n = 3, edges = \[\[0,1],\[1,2],\[2,0]] source = 0, destination = 2\
**Output:** true\
**Explanation:** There are two paths from vertex 0 to vertex 2:

* 0 → 1 → 2
* 0 → 2

### <mark style="background-color:blue;">**Intution**</mark>

* We need a graph to represent the edges, since edges can be indirect connected & bi-directional.
* Use the traversals to find till source become the destination.

### <mark style="background-color:green;">**BFS Pseudo**</mark>

* push into the queue
* mark as visited
* pop element from queue, i.e current node
* if pop element == destination return true
* find all unvisited neighbour nodes of current node and push to queue, mark visited
* repeat until queue.is not empty

### <mark style="background-color:green;">**DFS Pseudo**</mark>

* make source node visited
* iterative through all unvisited neighbours
* make the neighbour as new source
* go recursively

### <mark style="background-color:red;">**Edge Cases**</mark>

* the node can be single with no edges
* each edge is connected atmost 1, so edges\[i].length == 2
* no self edge
* the node starts from 0 no to n -1 where n is no of length of nodes

> <mark style="color:blue;background-color:purple;">**When to mark nodes visited in graph traversal?**</mark>
>
> * **DFS - Make sure to mark node as visited always, before you find its all neighbours.**
> * **BFS - Make sure to mark node as visited once pushed to queue**.



1. <mark style="color:purple;">**Adj Matrix & BFS**</mark>

```cpp
// TC - O(V2) // traverse whole matrix + O(E) // creating adjMatrix
// SC - O(V2) + O(V) // Matrix + vis array + queue

// Memory Limit Exceeded
class Solution {
public:
    bool validPath(int n, vector<vector<int>>& edges, int source, int destination) {
        if(source == destination) return true;

        vector<vector<int>> graphMatrix(n, vector<int>(n, 0));        
        vector<bool> isVisited(n , false);
        queue<int> q;

        for(auto &edge: edges) {
            graphMatrix[edge[0]][edge[1]] = 1;
            graphMatrix[edge[1]][edge[0]] = 1;
        }

        isVisited[source] = true;
        q.push(source);

        while(!q.empty()) {
            int curr = q.front();
            q.pop();
            if(curr == destination)
                return true;
            for(int neighbour = 0; neighbour < n ; neighbour++) {
                if(graphMatrix[curr][neighbour] == 1 && !isVisited[neighbour]) {
                    q.push(neighbour);
                    isVisited[neighbour] = true;
                }
            }
            
        }
        return false;
        
    }
};
```



2. <mark style="color:purple;">**Adj List & DFS**</mark>

```cpp
// TC - O(2E + V) -> DFS + AdjLIst -> O(V + E) = O(V + E)
// SC - Visited -> O(V) + AdList -> O(V + E) = O(V) + O(V + E)

class Solution {

private:
    bool dfsTraversal(vector<vector<int>>& graphList,  vector<bool>& isVisited , int source, int destination) {
	    if(source == destination) return true;
        isVisited[source] = true;

        // find all the neighbours
        for(int neighbour: graphList[source]) {
                if(!isVisited[neighbour] && dfsTraversal(graphList, isVisited, neighbour, destination)) {
                    return true;         
            }
        }
        return false;
    }


public:
    bool validPath(int n, vector<vector<int>>& edges, int source, int destination) {

        // create adj list
        vector<vector<int>> graphList (n);
        vector<bool> isVisited (n, false);

        for(auto &edge: edges) { 
            int u = edge[0];
            int v = edge[1];

            graphList[u].push_back(v);
            graphList[v].push_back(u);
        }

        return dfsTraversal(graphList, isVisited, source, destination);
    }
};
```



3. <mark style="color:purple;">**Adj List & BFS**</mark>

```cpp
// TC - O(2E + V) -> DFS + AdjLIst -> O(V + E) = O(V + E)
// SC - Visited -> O(V) + AdList -> O(V + E) + Queue -> O(V) = O(V) + O(V + E) + O(V)

class Solution {
public:
    bool validPath(int n, vector<vector<int>>& edges, int source, int destination) {
        if(source == destination) return true;

        vector<vector<int>> graphList(n, vector<int>());        
        vector<bool> isVisited(n , false);
        queue<int> q;

        for(auto &edge: edges) {
            graphList[edge[0]].push_back(edge[1]);
            graphList[edge[1]].push_back(edge[0]);
        }

        isVisited[source] = true;
        q.push(source);

        while(!q.empty()) {
            int vertex = q.front();
            q.pop();
            if(vertex == destination)
                return true;
            for(int neighbour: graphList[vertex]) {
                if(!isVisited[neighbour]) {
                    q.push(neighbour);
                    isVisited[neighbour] = true;
                }
            }
            
        }
        return false;
        
    }
};
```



4. <mark style="color:purple;">**Adj Matrix & DFS**</mark>

```cpp

// Memory limit exceeded
class Solution {

private:
    bool dfsTraversal(vector<vector<int>>& adjMatrix, vector<bool>& isVisited,
                      int source, int destination) {
        if(source == destination) return true;
        isVisited[source] = true;

        for (int dest = 0; dest < adjMatrix[source].size(); dest++) {
            if (adjMatrix[source][dest] && !isVisited[dest]) {
				if(dfsTraversal(adjMatrix, isVisited, dest, destination))
					return true;
            }    
        }
        return false;
    }

public:
    bool validPath(int n, vector<vector<int>>& edges, int source,
                   int destination) {
        // create an adj matrix
        vector<vector<int>> adjMatrix(n, vector<int>(n, 0));
        vector<bool> isVisited(n, 0);
        for (auto& edge : edges) {
            int u = edge[0];
            int v = edge[1];
            adjMatrix[u][v] = 1;
            adjMatrix[v][u] = 1;
        }
        return dfsTraversal(adjMatrix, isVisited, source, destination);
    }
};
```
