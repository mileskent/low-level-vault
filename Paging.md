The idea of paging is to eliminate [[Fragmentation#External|External Fragmentation]] by storing the memory footprint of a process in discontinuous memory locations called Pages.
Then the [[Memory Management#Memory Broker]] can handle maintaining semantics, while enforcing this scheme.
![[Pasted image 20251012220055.png|400]] 
# Page
Memory block used in paging.
Bigger pages yield more [[Fragmentation#Internal|Internal Fragmentation]]
Smaller pages get us a bigger page table and take more CPU time to manage
All [[Memory]] is divided into pages
![[Pasted image 20251012222921.png|200]]
## Page Size
Page size is always a power of 2 for ease of computation.
* Power of 2 allows us to split the virtual address into a *Virtual Page Number* and *Offset* within the page at a bit boundary (without using division)
* If the page size is $2^n$, the lower $n$ bits are the offset and bit $n$ and up are the virtual page number
 e.g. with a 4 kilobyte ($2^{12}$ bit) page size and a 32 bit virtual address space
 ![[Pasted image 20251012222146.png|300]]

* Page frames = $2^{\text{PFN}}$
* Table entries = $2^{\text{VPN}}$
e.g. 4 KB page size, 32 bit virtual addresses, 24 bit physical addresses
$\text{PFN} = 24 - 12= 12 \implies 2^{12}\text{ page frames}$
$\text{VPN} = 32 - 12 = 20 \implies 2^{20}\text{ table entries}$

e.g.
You have a memory system with **16-bit virtual and physical addresses** and a **1K page size**. The entries in the current page table are **0x14**, **0x18**, **0x08**, **0x01**. What is the physical address that virtual address **0x4ED** maps to?

Remember: 6 VPN, 10 offset bits 
Virtual addr = 0x4ED 
(000001 | 0011101101) 
VPN=0x01, Offset=0x0ED 
PFN=0x18, Offset=0x0ED 
(011000 | 0011101101) 
(0110 0000 1110 1101) 
Physical addr = 0x60ED

# Page Table
A table mapping [[Virtual Address]] to [[Physical Address]] of Pages, used by the memory broker.
$n$ [[Process]]es requires $n$ Page Tables
Where page tables live in memory:
![[Pasted image 20251012222556.png|200]]

# Broker
![[Pasted image 20251012223049.png|400]]
