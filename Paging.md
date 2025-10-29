The idea of paging is to eliminate [[Fragmentation#External Fragmentation]] by storing the memory footprint of a process in discontinuous memory locations called Pages.
However, it has [[Fragmentation#Internal Fragmentation]] because a process will almost always not utilize 100% of its allocated page.
Then the [[Memory Management#Memory Broker]] can handle maintaining semantics, while enforcing this scheme.
![[Pasted image 20251012220055.png|400]] 
# Page
Memory block used in paging.
All [[Memory]] is divided into pages
![[Pasted image 20251012222921.png|200]]
![[Pasted image 20251014211700.png|400]]
## Virtual Page
Virtual page is a fixed-length block of [[Virtual Memory]] that is mapped to [[Physical Address]]es
## Page Frame
A page frame refers to a contiguous block of memory that corresponds to actual storage locations in [[Memory]]
## Page Size
Bigger pages yield more [[Fragmentation#Internal Fragmentation]]
Smaller pages get us a bigger page table and take more CPU time to manage

* Using a power of 2 allows us to split the virtual address into a *Virtual Page Number* and *Offset* within the page at a bit boundary, without using extra logic
* If the page size is $2^n$, the lower $n$ bits are the offset and bit $n$ and up are the virtual page number
 e.g. with a 4 kilobyte ($2^{12}$ bit) page size and a 32 bit virtual address space
 ![[Pasted image 20251012222146.png|300]]

* Page frames = $2^{\text{PFN}}$
* Table entries = $2^{\text{VPN}}$
e.g. 4 KB page size, 32 bit virtual addresses, 24 bit physical addresses
$\text{PFN} = 24 - 12= 12 \implies 2^{12}\text{ page frames}$
$\text{VPN} = 32 - 12 = 20 \implies 2^{20}\text{ page table entries}$

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
### PFN
Page Frame Number. Indexes [[#Page Frame]]s.
### VPN
Virtual Page Number. Indexes [[#Virtual Page]]s

# Page Coloring
![[Page Coloring]]
# Page Table
![[Page Table]]
# Broker
![[Pasted image 20251012223049.png|400]]

# Page Fault
![[Page Fault]]

# Paging Optimization
![[kswapd]]