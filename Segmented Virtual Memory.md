- **Segmentation** is a system allowing a process's memory space to be subdivided into chunks of memory each associated with some aspect of the overall program
* Segments can be different sizes
- **Segmentation isn't transparent like [[Paging]]**, but it is much more aware of program and data structures
- Segmentation came before paging, but it is visible to the ISA, so it doesn't work as a retrofit to ISAs with contiguous memory models. IBM couldn't use it in the 1970s because they had already committed during the 1960s to upper/lower bound register memory management and a contiguous address space.
- Hence, we have **paging** that could be transparently slipped under existing memory management. Other manufacturers followed suit because **paging didn't require their applications to be aware of paging.**
- Typical Segments
	- Code segments
	- Global Data
	- Heap
	- Stack


Each segment has a number and a size
Each segment starts at its own address 0 and goes up to its size - 1
Segment addressing is almost like page addressing
![[Pasted image 20251018191118.png|300]]

Segmenation has no [[Fragmentation#Internal Fragmentation]] but has [[Fragmentation#External Fragmentation]]---opposite of [[Paging]]
![[Pasted image 20251018191203.png]]
This is basically [[Memory Management#Base + Limit]] but for segmented virtual memory
It is different because of the size in the segment table and the need to compare the bounds
![[Pasted image 20251018191219.png]]

