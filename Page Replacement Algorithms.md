An [[Algorithm]] to decide which [[Paging#Page]] to replace in [[Memory]]


| ALGORITHM                     | HARDWARE ASSIST        | COMMENTS                                                                                                |
| :---------------------------- | :--------------------- | :------------------------------------------------------------------------------------------------------ |
| **FIFO**                      | None                   | Could lead to performance anomalies                                                                     |
| **Belady's MIN**              | An oracle              | Provably optimal; not realizable in hardware; useful as a standard                                      |
| **True LRU**                  | Push down stack        | Expected performance close to optimal; infeasible                                                       |
| **Approximate LRU #1**        | A small hardware stack | Expected performance close to optimal; worst-case performance may be similar to FIFO                    |
| **Approximate LRU #2**        | Reference bit per page | Expected performance close to optimal; moderate hardware complexity                                     |
| **Second chance replacement** | Reference bit per page | Expected performance better than FIFO; memory manager implementation simplified compared to LRU schemes |
# Belady's Min
![[Belady's Min]]
# Random Algorithm
The baseline algorithm

# FIFO
* Similar behavior to [[Belady's Min]]
* Go circularly through [[Frame Table]] with a head [[Pointer]] to create FIFO behavior: Clock Algorithm
# Least Recently Used (LRU)
* Use past performance as a predictor of the future
* Use a [[Stack]] where you have a reference to the top and bottom of the stack. Replace the bottom of the stack because it is least recently used.
 - **Memory references** are known to the **hardware**, but [[Memory Management]] (i.e. victim selection) is in **software**, which is an issue
	 - Approximation #1
		 - Small hardware stack
	 - Approximation #2
		 - Reference bit per [[Paging#Page Frame]] inside the [[Page Table]]
			 - Set bit when page is referenced (hardware)
			 - Paging daemon
				 - Flush reference bits periodically
				 - Clear reference bits
			 - Victim is the page with the counter that has the lowest value

# Second Chance
1. Clear all ref bits
2. Hardware sets reference bits when a page is referenced
3. If a page has to be evicted, the memory manager selects a page frame in a FIFO manner
4. If the chosen victim's reference bit is set, the manager clears it and moves to the next page frame
5. The victim is the first page that doesn't have the reference bit set
6. Start the next search with the page frame after the victim