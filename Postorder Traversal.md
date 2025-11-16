* At first traverse left [[Subtree]] then visit the root and then traverse the right [[Subtree]]
* Unique per tree; like [[Preorder Traversal]], the tree can be reconstructed from this order
	* If we remove in this order, we will only remove leaves
See [[Binary Search Tree]]

### Shortcuts
##### Implementation
Inorder traversal -> LRC
L -> left (traverse the left subtree of the current node)
R -> right (traverse the right subtree of the current node)
C -> process node ("count" for a tree sum, could also be something like print, for example)
```
postorderTraversal() {LRC(root)}
LRC (curr: Node) {
	if (curr is null) return
	LRC(left)	
	LRC(right)	
	process(curr)
}
```
##### Tracing
Trace counterclockwise around the perimeter of the tree. The order of processing corresponds to when a peg gets crossed, where every node has a peg.
![[Pasted image 20250401132738.png|300]]