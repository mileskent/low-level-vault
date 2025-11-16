A [[Traversal Algorithm]] whose goal is to visit all vertices in a [[Graph]] that are reachable from a given start vertex.
* Visited all vertices 1 edge away from starting vertex, then all vertices 2 edges away, etc, etc, until the entire graph has been traversed
* Gives the path with the least number of edges if you are traversing in order to perform a [[Shortest Path Algorithm]]
* [[Levelorder Traversal]] is [[Breadth First Search]]

### Efficiency
For all cases
$$
O(|V| + |E|)
\quad\text{where V is the set of vertices and E is the set of edges}
$$
### Implementation
$T = VS = \text{Polls from } Q$
```
BFS (start: Vertex) {
  T: Traversal, VS: Set, Q: Queue(start)
  while Q {
     temp = Q.poll
     (VS, T).add(temp)
     Q.add(temp.adj !in VS)
  } 
}
```

### BFS vs DFS
* If we want a particular vertex and have prior knowledge of its location relative to the starting vertex
	* Choose BFS if the vertex is relatively close to the starting vertex, compared to the size of the graph
* Like [[Levelorder Traversal]] visits nodes in order of their distance from the starting node, making it ideal for finding the shortest path in unweighted graph
* Graph depth; if the graph is very deep or infinitely deep, we may want to use BFS or a modified DFS in order to avoid going down one path for too long
* Graph width; if each node has many neighbors, BFS may blow up in space due to storing all neighbors in a queue, so DFS is probably better

### See also
[[Graph]]
[[Depth First Search]]
[[Traversal Algorithm]]