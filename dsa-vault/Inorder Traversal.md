A [[Traversal Algorithm]]
* Traverse nodes in ascending order 
* Not unique to particular trees
	* Same order causes same traversal
See [[Binary Search Tree]], [[Tree]]

### Shortcuts
##### Implementation
Inorder traversal -> LCR
L -> left (traverse the left subtree of the current node)
C -> process node ("count" for a tree sum, could also be something like print, for example)
R -> right (traverse the right subtree of the current node)
```
inorderTraversal() {LCR(root)}
LCR (curr: Node) {
	if (curr is null) return
	LCR(left)	
	process(curr)
	LCR(right)	
}
```
##### Tracing
Trace counterclockwise around the perimeter of the tree. The order of processing corresponds to when a peg gets crossed, where every node has a peg.
![[Pasted image 20250401132738.png|300]]