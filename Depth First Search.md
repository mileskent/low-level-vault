A [[Traversal Algorithm]] whose goal is to visit all vertices in a [[Graph]] that are reachable from a given start vertex. 
* Explores a branch as far down as possible until exhaustion before it moves back up to explore other branches
	* This makes it highly suited for [[Recursion|recursive]] and [[Stack|stack]] implementations (these are secretly the same thing anyway)
* [[Inorder Traversal]], [[Preorder Traversal]], [[Inorder Traversal]] are all [[Depth First Search]]

### Efficiency
For all cases of both implementations
$$
O(|V| + |E|)
\quad\text{where V is the set of vertices and E is the set of edges}
$$
### Implementation
$T_\text{iter} \not = T_\text{rec}$
##### Iterative
$T \not = VS$
$\text{Pushes to } S = VS$
$\text{Pops from } S = T$
```
G: Graph
T: traversal

DFS (start: Vertex) {
	visitedSet VS(start), Stack S(start)
	while S { 
		T.add(S.peek)
		(VS, S).add(for S.pop.adj !in VS) 
	}
}
```
##### Recursive
$T = VS = \text{Pushes to Call Stack}$
```
DFS (start: Vertex) {
  T: Traversal, VS: Set
  DFShelper(start, T, VS)
  return T
}
DFShelper (vertex, T, VS) {
  (VS, T).add(vertex)
  for v in vertex.adj !in VS { DFShelper(v) }
}

// note T = VS = pushes to call stack
```

### Applications
- DFS can be used to detect if a graph is connected; moreover, if the graph is connected, then DFS can find if there exists a path from one vertex to another.
- DFS can be used for cycle detection. Mixed with the first application, it can be used to detect whether or not the graph is a tree.
- DFS can be used to obtain a spanning tree of the graph. As discussed earlier, a tree can be thought of as a graph with the minimal number of edges without disconnecting the graph. A spanning tree is a subgraph of the original graph for which all vertices are connected with the smallest number of edges.
- DFS can be used to detect if a graph is bipartite. A graph is bipartite if we can partition the vertices into two sets where there are no edges between vertices in the same set. This is equivalent to finding if the graph contains an odd cycle.
- DFS can be used to simulate decisions for an artificial intelligence (AI), particularly in games with structure. For example, you can have an AI simulate what will happen if it makes a move in Checkers or Chess, and cap it off once it gets to a certain depth. Usually, the algorithm will be a more involved variation of DFS because we'd want our search to be motivated by heuristics or cost/performance functions to help our AI make its choices.
- DFS can be used to do topological sorting on directed acyclic graphs (DAGs). In a DAG, the entire graph can be thought of as oriented based on the orientations of the edges (for theory students, you can think of this as a poset). DFS can be used to obtain from the graph an ordering of the vertices in sorted order based on the edge orientations.
- DFS can be used to obtain a meta-graph of strongly connected components in a digraph. In a digraph, it is not generally the case that a weakly-connected graph will be strongly-connected. However, we can find clusters of components in the graph that are strongly connected. Treating each of these strongly-connected components as a single vertex of a new meta-graph, we obtain a new graph all together.
### BFS vs DFS
* If we want a particular vertex and have prior knowledge of its location relative to the starting vertex
	* Choose BFS if the vertex is relatively close to the starting vertex, compared to the size of the graph
* Graph depth; if the graph is very deep or infinitely deep, we may want to use BFS or a modified DFS in order to avoid going down one path for too long
* Graph width; if each node has many neighbors, BFS may blow up in space due to storing all neighbors in a queue, so DFS is probably better

### See also
[[Graph]]
[[Breadth First Search]]
[[Traversal Algorithm]]