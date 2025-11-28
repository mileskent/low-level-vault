---
aliases:
  - SSD
---
The faster on order of 100x, but more expensive alternative to [[Hard Disk Drive]]s.
Directed connected to [[PCIe]]
No moving parts
Minimal seek time
Wears out over time, unlike HDD
Power loss can result in data loss without protective circuitry
You can store multiple bits per cell, but at the cost of faster wear and higher error. Higher bits per cell organizations are cheaper, because they wear out faster.
![[Pasted image 20251127235546.png|400]]
Data can be written to an individual page, but only blocks can be erased
* SSD Controller must relocate pages when they are rewritten
* Writing a page is faster than erasing a block
* SSD Controller must [[Garbage Collector|Garbage Collect]]

# Flash Translation Layer
![[Pasted image 20251128000421.png|300]]
The SSD presents a uniform view of blocks by maintaining a blocking index.
This is because it must pretend to be a HDD, and present itself as such to the [[Operating System|OS]]
Writes or reallocations change the mapping index to allow logical blocks to be consistently mapped
Corruption of the mapping index results in signficant data loss

# Weap Properties
Drive Writes Per Day (DWPD) = TBW / (warrantied days *  capacity in TB)
TBW (Terabytes written before death)