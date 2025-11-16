Binary Heap has 2 definining properties:  
1. Shape Property: must be complete.  Each level of tree is as "full" as possible, bottom level is filled left to right 
2. Order Property: each node must be higher priority than its kids

It is a [[Binary Tree]] Data Structure.

Implement Heap in an array, in the order of a [[Levelorder Traversal]]
Always leave index 0 as null for easier math

## Methods
#### Add
```
add(value) {
	resize (if needed)
	add at next open array slot
	call upheap at index of node you just added
	increase size
}
```
#### Remove
```
remove() -> value {
	move last value in array to root
	downHeap at root
	return oldroot
}
```
#### BuildHeap
```
buildHeap() {
	// reverse level order of inner nodes is i = [size / 2 ... 1]
	downheap at index for node at index in reverse levelorder of inner nodes
}
```
## Helper Methods
#### Upheap
```
upheap(int nodeIndex) {
	base case: if root return          // isRoot -> nodeIndex == 1
	if node is higher priority than parent, swap with parent and upheap at parent index
}
```
#### Downheap
```
downheap(int nodeIndex) {
	basecase: if leaf, return          // isLeaf -> nodeIndex > size / 2
	if node is lower priority than highest priority child {
		swap and then downheap at relevant child index
	}
}
```

## Big O
#### Add
| TIME COMPLEXITY     |           |                                                                                                               |
| ------------------- | --------- | ------------------------------------------------------------------------------------------------------------- |
| Worst               | O(log n)* | When adding a new element, in the worst case, it bubbles up to the root through logn levels.                  |
| Worst (unamortized) | O(n)      | In the resize case, we must copy all the data to a new larger array.                                          |
| Average             | O(log n)  | New elements typically bubble up through some of the heap's levels, logarithmically proportional to the size. |
| Best                | O(1)      | In the best case, the newly added data belongs in the leaf level and does not have to be bubbled up.          |es not have to be bubbled up.          |
#### Remove
| TIME COMPLEXITY |          |                                                                                                                           |
| --------------- | -------- | ------------------------------------------------------------------------------------------------------------------------- |
| Worst           | O(log n) | After removing the root, the last element is put at the room and in the worst case must bubble down logn levels.          |
| Average         | O(log n) | The new root typically needs to bubble down through some of the heap's levels, logarithmically proportional to the size.  |
| Best            | O(1)     | In the best case, we only have to downheap one level after swapping the last element to the root. This case is very rare. |
#### BuildHeap
| TIME COMPLEXITY |      |                                                                                                                                                                                      |
| --------------- | ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| All cases       | O(n) | Most nodes are near the bottom and require minimal adjustments. More specifically, about half of all data are on the leaf layer, and a quarter are on the second-to-last level, etc. |
