A [[Routing Protocol]] that is based on the [[Bellman-Ford Algorithm]]
* Each [[Node]] only sees its neighbors, the cost to each neighbor, and the "rumor" (Routing Table) from each neighbor, which has the cost from the neighbor to all of its neighbors.
* Each node keeps track of the minimum distance it has seen so far to each other node in a [[Routing Table]].
* This algorithms runs simultaneously on every node, quickly converging to the correct answer for the shortest path from any arbitrary node A to any other arbitrary node B in the [[Network]]

The problem with this algorithm is that because it runs on all nodes simulatneously, it employs trust in every [[Host]], which is not advisable in the modern day.