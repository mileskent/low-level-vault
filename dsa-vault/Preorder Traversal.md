A [[Traversal Algorithm]]
For [[Tree]]s
* Start at the node and trace counterclockwise around the tree, processing nodes as they appear
* Unique per tree; the nodes need to be added in that order to reproduce that tree

### Shortcuts
##### Implementation
Preorder traversal -> CLR
C -> process node ("count" for a tree sum, could also be something like print, for example)
L -> left (traverse the left subtree of the current node)
R -> right (traverse the right subtree of the current node)
```
preorderTraversal() {CLR(root)}
CLR (curr: Node) {
	if (curr is null) return
	process(curr)
	CLR(left)	
	CLR(right)	
}
```
##### Tracing
Trace counterclockwise around the perimeter of the tree. The order of processing corresponds to when a peg gets crossed, where every node has a peg.
![[Pasted image 20250401132738.png|300]]
