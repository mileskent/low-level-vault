---
aliases:
  - Recursive
---

Recursive calls go onto the Call [[Stack]] and are popped off when the base case is reached.

Code before recusive call: before recursive stack, while going through
Code after recursive call: after recursive stack, while backtracking

### See Also
###### [[Binary Search Tree]]
A recursive structure, therefore use recursion.
When recursing on a tree, need to handle 3 cases, where the order might change
1. Handle curr node
2. Handle left [[Subtree]]
3. Handle right [[Subtree]]

> [!example] Example: Print tree in [[Preorder Traversal]]
> ```
> def preOrder():
> 	preOrderH(root)
> def preOrderH(Node curr):
> 	if curr == null:
> 		return
> 	print(curr.data)
> 	preOrderH(curr.left)
> 	preOrderH(curr.right)
