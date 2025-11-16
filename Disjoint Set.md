A kind of [[Set]] [[Data Structure]]. Called *Union-Find* data structure. Two sets are disjoint if they have no common elements. A disjoint set data structure is used to store such sets. A disjoint set has a representative vertex called a root, kind of like how the root of a [[Binary Search Tree]] serves as a representive for the entire BST.
* Union -> Merge two disjoint sets
* Find -> Find the root of a given element
	* Elements are in the same disjoint set if they all have the same root

### Efficiency
All methods:
$$
O(\alpha(|V|))^* \approx O(1)
$$
See [[Inverse Ackermann Function]]

### See also
Used in [[Kruskal's Algorithm]]