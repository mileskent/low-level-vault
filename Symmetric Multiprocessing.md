Multiple [[CPU]]s are connected to a single, shared main [[Memory]], have full access to all input and output devices, and are controlled by a single [[Operating System]] that treats all processors equally, reserving none for special purposes.
Symmetric multiprocessing is a [[Uniform Memory Architecture]]
![[Pasted image 20251113101058.png|400]]

Such a system must guarantee:
* [[Thread]]s of the same [[Process]] share the same [[Page Table]]
* Threads have [[Multithreading#Atomic Read-Modify-Write Instruction|Synchronization Atomicity]]
* Threads have identical views of memory

# Context Switch Handling
As in the [[Translation Lookaside Buffer#Context Switching|single CPU case]], the [[Translation Lookaside Buffer|TLB]] of the particular CPU must be flushed of userspace entries upon [[Context Switch]] in Multiprocessing.

# Page Replacement Handling
* Evict TLB entry for that process
* Tell other CPUs to evict their corresponding TLB entry through OS, "TLB shootdown"
## TLB Shootdown
Performed by the [[Replacement Algorithm|Page Replacement Algorithm]]
A CPU that has evicted a page table entry from its TLB tells other CPUs to evict their corresponding TLB entry through OS/software interrupts, because that PTE is invalid
![[Pasted image 20251113105436.png|400]]

# Thread Synchronization
Bypass the [[Caching|Cache]] for [[Multithreading#TEST-AND-SET]], because the caches will be wrong due to the atomicity of the test-and-set instruction.
![[Pasted image 20251113105800.png|400]]

# Cache Coherency
The requirement of threads needing to have identical views of memory implies that all caches have to be in sync.
This guarantee is complicated and slow. This is the bottleneck to [[Core]] count on a [[CPU]].

Cache snoops the bus; if a memory value changes (e.g. from $X \rightarrow X'$), it must account for this within itself.
## Write-Invalidate Protocol
If the cache sees you write to memory, it invalidates that entry within itself.
![[Pasted image 20251113110651.png|400]]
## Write-Update Protocol
If the caches sees you write to memory, it updates its own corresponding cache entry to be correct.
![[Pasted image 20251113110753.png|400]]