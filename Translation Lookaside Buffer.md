---
aliases:
  - TLB
---
* [[Caching|Cache]]s VPN to PFN address translations, i.e. [[Page Table]] entries
	* The TLB does not automatically know which process an entry belongs to
* It is an *associative* memory, which means it can search on a match on the first two columns and output the corresponding last two columns in one cycle
* [[RAM#SRAM]]
![[Pasted image 20251018141533.png|400]]
# Usage
Use a [[Translation Lookaside Buffer|TLB]] to reduce bubbles. If the TLB hits, we have a fast path and no bubbles.
* TLB can only hit if
	* Entry exists
	* Process has access (user proc can't use kernel entry)
	* Entry is valid
If the TLB misses, we have a slow path, bubbles, and the TLB is updated.
The point of a TLB is anticipating [[Locality]] in [[Program]]s; if a program has poor [[Locality]], then we have poor performance, because the TLB will constantly miss, and we will degenerate into the performance of the naive approach.
![[Pasted image 20251018141804.png|400]]



# Context Switching
* Kernels can have page maps, but the kernel page map doesn't change when we do a [[Context Switch]]. Hence the user/kernel flag.
* When we do a Context Switch, the [[Page Table#PTBR]] changes, and consequently the page table we have access to changes to that of the new proccess. 
	* Each process owns its own user space. Therefore, we must purge all of the cached user entries in the TLB after a Context Switch because they still point to the memory space of the previous process. Whatever user entries the old process cached in the TLB are useless to the new process, because the two process don't share their memory.
	- Cached kernel entries do not need to be purged because the kernel space is shared by all processes. 
- The [[Dispatcher]] is responsible for performing this purge





