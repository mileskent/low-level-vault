*A* [[Shortest Path Algorithm]] designed to solve the single source shortest path problem in a [[Graph]]. 
* [[Greedy Algorithm]], due to [[Heap|minHeap]]
	* Not exactly purely greedy due to semi [[Queue]] behavior of minHeap and the requirement that we cannot create [[Cycle|cycles]], i.e. use the visited [[Set]]
	* Having break conditions is typical for greedy algorithms
* [[Dynamic Programming]] because we reduce redundant calls using [[Memoization]], through the visited set
* Note that the visitedset takes node distance-from-start pairs that it gets from the minHeap, each time it dequeues its root
* It operates on weighted graphs
* Begins by assuming the distance to all vertices is infinite
	* If a vertex distance remains infinity, then no path exists to the source vertex
* Cumulative weight stored in vertices
* Assumes -> The shortest path between a pair of vertices must be composed of the shortest path to a neighbor plus the incident edge
	* Dijkstra's algorithm only works when the non-negative weight assumption is made
		* Negative weight graphs still have solutions
			* [[Bellman-Ford Algorithm]]
			* [[Floyd-Warshall Algorithm]]
		* Dijstra's algorithm breaks when the graph has negative [[Cycle|cycles]]
			* When a graph contains a negative cycle, the shortest path problem does not make any real sense as the negative will make the weighted path shorter and shorter by continuing to loop around the cycle. Inherently this means, that if there is a negative edge weight, then the edge cannot be undirected as it will create the cycle.
* Requires [[Heap]], Visited Set, Map, Source Vertex
	* Visited Set to keep track of visited vertices, using it prevents [[Cycle|cycles]] and provides an exit condition
	* Heap instead of stack or queue (referring to [[Breadth First Search]] and [[Depth First Search]])
* Works with both directed/undirected and connected/disconnected graphs
### Efficiency
$$
O(|E| \log |E|)
$$
> [!info]- Assumptions
The efficiency of Dijkstra's algorithm is heavily dependent on the data structures that are used, as well as, the design of the methods in the implementation. We assume that the visited set and distance map implemented in the algorithm are backed by a HashSet and a HashMap, which we also assume to have $O(1)$ standard operations. The priority queue is backed by a binary heap that was presented in GTx course 2. Keeping these structure assumptions in mind, let's examine the pseudocode for Dijkstra's algorithm, and the main sources of inefficiency that come from the priority queue.
> - The priority queue could, potentially, contain $O(|E|)$ entries. Each time a new path is considered and added to the priority queue, it is considered a new edge as an extension from the vertex. No new paths are added to the priority queue, if the vertex is already visited. A visited vertex means we found a smaller distance earlier in the search, and it guarantees we do not reuse edges.
> - By the same reasoning given in the first bullet, if the priority queue has been added to, potentially, $O(|E|)$ times throughout the algorithm, then there could also be, potentially,    removals from the priority queue. Recall that the priority queue remove operation has worst case time complexity of

> [!warning]-
Mostly just make sure to note that other implementations have different [[Time Complexity|time complexities]]! 
> * [[Binary Heap]] method
> 	* $O((|V| + |E|) \log |V|)$
> 	* Connected [[Graph]] -> $O(|E| \log |V|)$
> * [[Adjacency Matrix]] method
> 	* $O(|V|^2)$ -> The cost of going through neighbors dominator the log factors
> * [[Fibonacci Heap]] method
> 	* $O(|E| + |V| \log |V|)$, with $\Theta(1)$ adding and updating

###### Optimizations
There are several optimizations which can be made to Dijkstra's algorithm without inherently changing the nature of the algorithm.
1. The first optimization takes its inspiration from the [[Breadth First Search]] algorithm. The BFS algorithm decouples "visited" vertices and vertices in its "frontier." What Dijkstra's algorithm can do is decouple the visited set from the updates to the distance map. Rather than only updating the distance map when we visit a vertex and achieve the optimal shortest path to that vertex, we can update the distance map as we find new paths and add them to the [[Heap]]. This way, we can use the distance map as a criteria for adding to the priority queue to shrink the number of paths we add to the priority queue. This can also let us do away with the visited set if needed, reducing the amount of space by a constant factor.
2. A second improvement that can be implemented is make the priority queue update entries with a different priority. If this optimization is done, then the priority queue's size will never exceed $O(|V|)$, which is a definite improvement over the previous optimization. This particular optimization was mentioned in a previous lesson.
### Implementation
```
Dijkstras(start: Vertex) {
	VS: visitedSet, DM<Vertex, Int>: distanceMap, H<VD>: minHeap
	DM.put(graph.vertices, Integer.MAX_VALUE)
	H.add(VD(start, 0))
	
	while H and VS < G {
		v: Vertex, d: Distance = H.poll()
		if v !in VS {
			VS.add(v)
			DM.put(v, d) 
			for (adjv,adjd) in v.adj !in VS
				H.add( VD(adjv, d + adjd) )
		}
	}
	return DM
}
```


# See Also
[[Link-State Algorithm]]