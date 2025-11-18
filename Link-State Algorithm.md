A [[Routing Protocol]] that is based on the [[Dijkstra's Algorithm]]
Everybody knows the state of all of the links.
It inherits the properties of Dijkstra's Algorithm like being a [[Recursion|Recursive]] [[Greedy Algorithm]]
* Each [[Node]] shows its neighbor links and costs to every other node in the [[Network]]
* Each Node collects the entire [[Topology]] of the network from these advertisements
* Using [[Dijkstra's Algorithm]] with a table, each node calculates its own [[Routing Table]]
	* Initialize table of entries of costs to neighbors
		* Start node gets 0, neighbors get their link costs
	* Iterate $|V| - 1$ times
		* Mark the node with smallest cost so far  
			* Marking also means that the node is "visited" and doesn't need to be processed again later, because it is confirmed that this cost is the guaranteed minimum cost to reach that node from the starting point
		* For the node we just marked, see if the distance through the marked node to its neighbors is shorter than the existing minimum distance in the table to that node, updating the ones that minimize the distance

Once this is done, update the [[Routing Table]] of each node to show the best routes.