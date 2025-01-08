A freelist is a data structure used in a scheme for [[Heap Allocation]]. 
* It operates by connecting unallocated blocks of memory together in a linked list, using metadata at the beginning of the block to encode the pointer to the next block for example, maybe the size of the block, as well
	* If a block of memory is in the free list it is unallocated and ready to be used
* Free lists make the allocation and deallocation operations very simple. 
	* To free a region, one would just link it to the free list
	* To allocate a region, one would simply remove a single region from the end of the free list and use it

> [!Example] Freelist Diagram
![[Pasted image 20250409140321.png]]
This diagram represents five contiguous memory regions which each hold a pointer and a data block. The List Head points to the 2nd element, which points to the 5th, which points to the 4th, thereby forming a linked list of available memory regions.

# See also
[[C Memory Layout]]
[[malloc]], [[realloc]], [[calloc]], [[free]]
[[Heap]], [[Heap Allocation]]