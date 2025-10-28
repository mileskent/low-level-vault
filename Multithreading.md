Using multiple [[Thread|threads]] for one [[Process]]
![[Pasted image 20250927151239.png|200]]


# Thread Synchronization
Synchronization is the war against [[Race Condition]]s
[[Mutex]]
[[Condition Variable]]

# Thread Communication
Accomplish through software by keeping all threads in the same address space by the OS
Accomplish through hardware with hardware shared memory and coherent caches 
# Producer-Consumer Problem
![[Pasted image 20251028164139.png]]
The producer-consumer problem is a multithread synchronization problem where there are two threads: the producer and the conusmer, which share a fixed size buffer that acts as a queue.
The producer's job is to put the data it produces into the buffer.
The consumer job is to consume that data by removing it from the buffer, one datum at a time.
1. The producer shall not add data into the buffer when it is full.
2. The consumer shall not remove data from an empty buffer.
3. The producer and consumer shall not access the buffer simultaneously.
## Circular Buffer
We implement this queue with a circular buffer that has a head and tail pointer. 
Head points to the first filled frame in the buffer.
Tail points to the first empty spot in the buffer.
Insert elements at tail and then increment the pointer mod base size.
Remove elements at head and then increment the pointer mod base size.
Only the consumer touches head.
Only the producer touches tail.
You can track if the buffer is full or not EITHER with a current size variable, or with a buffer entry, i.e. not allowing tail to overlap with tail (check if tail is immediately before head to see if the buffer is full)
![[Pasted image 20251028164541.png|400]]

# See Also
[[C++ Multithreading]]