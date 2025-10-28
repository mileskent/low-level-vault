A kind of [[Memory]] organization where memory is actually split up into multiple banks. This allows concurrent access of data blocks without requiring wider buses. All the banks recive an address in the same cycle. Interleaving ensures that while one bank is busy, the [[CPU]] can access another, reducing wait time. The memory accesses are interleaved. 

![[Pasted image 20251028160056.png|300]]
![[Pasted image 20251028155749.png]]