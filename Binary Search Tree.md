---
aliases:
  - BST
---

A [[Binary Tree]] where left nodes are less than the parent and right nodes are greater than the parent

##### contains()
* Best Case
	* Shortest Tree Possible with n nodes -> [[Complete]]
	* $O(\log(n))$
* Worst Case
	* Longest Tree Possible with n nodes -> [[Degenerate]]
	* $O(n)$

##### remove()
1. Recursively search tree for target
2. Find target
	1. [[Leaf]] -> Remove target
	2. 1 child -> Connect target child to target parent
	3. 2 children -> Replace target value with [[predeccesor]] or [[successor]]

### Traversal
![[Pasted image 20250204174442.png]]
* [[Inorder Traversal]]
* [[Preorder Traversal]]
* [[Postorder Traversal]]
* [[Levelorder Traversal]]


### Efficiencies

|              | Add      | Remove   | Access   | Height |
| ------------ | -------- | -------- | -------- | ------ |
| Average Case | O(log n) | O(log n) | O(log n) | O(n)   |
| Worst Case   | O(n)     | O(n)     | O(n)     | O(n)   |
