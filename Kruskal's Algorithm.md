 A [[Minimum Spanning Tree Algorithm]]
* Computing [[Minimum Spanning Tree]] for [[Directed|Undirected]], [[Connected]] [[Graph]]
	 * If a graph is not connected, what is generated is a *Minimum Spanning Forest*
	 * Works with both [[Connected]] and disconnected graphs
* [[Greedy Algorithm]]
	* Motivation: be even greedier than [[Prim's Algorithm]]
	* We are greedier because when we add, it is only the minimum of the remainder of the minHeap
 * Focuses on [[Disjoint Set]] (clusters) of [[Vertex|vertices]] at a time, as opposed to a [[Path]] like [[Prim's Algorithm]]. 
 * Main Idea
	 * We add all edges into a heap, for the purpose of [[HeapSort]]
		 * You can sort it in other ways. It doesn't matter
		 * If you can use [[LSD Radix Sort]] that will be even better
	 * We check if we can add each edge so long as it doesnt make a [[Cycle]]
		 * *A cycle is not created if the vertices it connects are in different disjoint sets*
		 * It is easy to tell if two vertices are in the same disjoint set or not, as they have the same root
		 * The Visited Set idea from other [[Graph]] [[Traversal Algorithm]] fails, which is why use [[Disjoint Set]]s
	 * Do this until we have a [[Minimum Spanning Tree]]
	* This is trivial to trace as a human, but it is hard to tell a computer how to do it. The main problem is telling the computer how to determine if adding an edge creates a cycle.
### Efficiency
$$
O(|E| \log |E|)
$$
* If the graph is [[Simple]], then $|E| = O(|V|^2) \implies O(|E| \log |V|)$
* If the graph is [[Dense]], then $O(|E| \log |E|)$
* If the graph is [[Sparse]], then $O(|E| \log |E|)$
* Edges presorted, then $O(|E|)$
### Implementation
On a high level, we do the following.
1. Add every [[Edge]] of the graph into a [[Heap]].
2. While the heap is not empty and the MST size is not reached, dequeue an edge from the heap. If the dequeued edge does not form a [[Cycle]], then add the edge to the MST.
```
kruskals() {
	MST: EdgeSet, DS: DisjointSet, h(G.edges): minHeap
	DS.find(graph.vertices)
	
	while (h and MST < 2(V - 1)) {
		e: Edge = h.poll()
		u: Vertex, v: Vertex = e.vertices

		// do both vertices have different roots/clusters?
		bool noCycles = DS.find(u) != DS.find(v)
		if (noCycles) {
			MST.add(e.uv), MST.add(e.vu)
			DS.union(u, v)	
		}
	}
	
	return MST < 2*(V - 1) ? null : MST
}
```