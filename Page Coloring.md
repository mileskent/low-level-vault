---
aliases:
  - Cache Coloring
---

The OS guarantees that some bit of the VPN will remain unchanged through address translation, i.e. the low bits of the VPN and PFN are identical
The low bits are like a color. The color of the virtual address must match the color of the physical address.
This means that a virtual page can only occupy a subset of page frames in which the low bits of the VPN match the low bits of the PFN.
![[Pasted image 20251029123702.png|400]]
[[Replacement Algorithm|Page Replacement Algorithms]] has to keep track of this.
It could be harded to fit a working set into physical memmory, but it's often fine because processes tend to use continguous pages, so the VPNs of the pages are spread evenly amoung the colors.
![[Pasted image 20251028155055.png|600]]
![[Pasted image 20251029122225.png|400]]

# Example
> [!Question]- size(Colored Bits)
> - 64-bit virtual address
> - 32-bit physical address
> - Virtually-indexed, physically-tagged, 4-way set associative cache
> - Page size of 4 KB
> - Memory is byte-addressable
> - Total cache size of 512 KB
> - Cache block size of 64 bytes
> 
> How many of the least significant bits of the VPN must remain unchanged in the VPN-PFN translation?
> 
> If you look at the above figures,
> $$
> \text{size}(\text{colored}) = \text{size}(\text{cacheIndex}) + \text{size}(\text{blockOffset}) - \text{size}(\text{pageOffset})
> $$
> $\text{size}(\text{pageOffset}) = \log_{2}(\text{pageSize}) = \log_{2}(2^{12}) = 12$
> $\text{size}(\text{blockOffset}) = \log_{2}(\text{blockSize}) = \log_{2}(2^{6}) = 6$
> $\#\text{ ways} = 4$
> $\#\text{ entries} =\frac{\text{cacheSize}}{\text{entrySize}} = \frac{2^{19}}{2^6} = 2^{13}$
> $\#\text{ sets} = \frac{\#\text{ entries}}{\#\text{ ways}} = \frac{2^{13}}{4} = 2^{11}$
> $\text{size}(\text{cacheIndex}) =\log_{2}(\#\ \text{sets}) = \log_{2}(2^{11}) = 11$
> $$
> \text{size}(\text{colored}) = 11 + 6 - 12 = 5
> $$
