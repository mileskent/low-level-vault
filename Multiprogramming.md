Multiprogramming involves running multiple [[Program]]s on a single [[CPU]] to maximize CPU utilization

# Goldilocks Multiprogramming
![[Pasted image 20251018150408.png|400]]
More multiprogramming does not equal more better. 
Too many [[Process]]es will result in [[Scheduler#Thrashing]] and constant [[Page Fault]]s
* *Overcommitment* of memory (Thrashing)
* Bigger [[Virtual Memory#Working Set]] than physical memory can hold
* System becomes I/O bound, with thrashing's [[Swap Space]] spamming and page fault constant [[Discontinuities#Trap]]s

# Memory Pressure
![[Memory Pressure]]
# See Also
[[Multitasking]]