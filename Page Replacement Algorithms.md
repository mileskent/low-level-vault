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
* True LRU
	* Use a push down [[Stack]] where you have a reference to the top and bottom of the stack. 
	* If you are trying to add an already existing page number to the stack, move its entry from its existing location to the top of the stack
	* Replace the bottom of the stack because it is least recently used.
 - **Memory references** are known to the **hardware**, but [[Memory Management]] (i.e. victim selection) is in **software**, which is an issue
	 - Approximation #1
		 - Small hardware stack
	- Approximatation #2 (Reference Counter Method)
	    - Uses a multi-bit Reference Counter (history register) per frame to estimate the LRU page.
	    - **Components & Location:**
	        - Reference Bit: A single bit located in the page table entry.
	            - Set to 1 by hardware (MMU) upon page access.
	        - Reference Counter: A multi-bit register located in the [[Frame Table]] (managed by OS software).
	    - **The Paging Daemon's Periodic Update:**
	        - Age History: The Reference Counter is **right-shifted by one bit** (`>>= 1`), clearing the MSB and aging the history.
	        - Record Use: The value of the PTE's Reference Bit is inserted into the counter's **MSB**.
	        - Reset Hardware: The PTE's Reference Bit is then **cleared (set to 0)** for the next time quantum.
	    - Victim Selection
	        - Rule: The frame whose Reference Counter has the **lowest numerical value** is chosen as the victim.
	        - Rationale: A low count indicates a page has **not been referenced** in the most recent time quanta.
	        - Exception: Frames marked as protected must be ignored.
# Second Chance
1. Clear all ref bits
2. Hardware sets reference bits when a page is referenced
3. If a page has to be evicted, the memory manager selects a page frame in a FIFO manner
4. If the chosen victim's reference bit is set, the manager clears it and moves to the next page frame
5. The victim is the first page that doesn't have the reference bit set
6. Start the next search with the page frame after the victim


# Victim Selection
## Global 
## Local
