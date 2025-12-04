---
aliases:
  - HDD
  - Disk Drive
---
A storage device with many physically spinning magnetic disks that store information.
Connected to [[PCIe]] via [[SATA]] or [[SAS]] controllers

![[Pasted image 20251127220607.png|400]]
# Platter
A platter is like a floor of storage. A disk drive is made up of many floors of platters. The spin of the platter is faster than the movement of the [[#Read/Write Head]]s
# Surface
Each platter has two surfaces: the top and bottom face. Both faces can be used for data storage. Each surface has a [[#Read/Write Head]]
# Track
Each [[#Surface]] has a track, which is a path that the [[#Read/Write Head]] can follow. It is like a ridge in a record. 
# Sector
[[#Track]]s are subdivided into sectors. Sectors are the smallest physical unit of storage.
# Block
![[Disk Block]]
# Cylinder
A conceptual grouping of [[#Track]]s that are all the same distance from the center of the [[#Platter]]. There are as many cylinders as there are tracks.
![[Pasted image 20251127221626.png|200]]
# Read/Write Head
The instrument that accesses the data on a platter. The one circles in the figure is the one that reads the top [[#Surface]]. Each surface has a head. All heads general move in unison, but whether they do or not depends on the implementation.
![[Pasted image 20251127221102.png|200]]

# Capacity
$$
\text{Capacity} = bstnp\quad\text{bytes}
$$
* where $b=$ bytes per sector
* where $s=$ sectors per track
* where $t=$tracks per surface
* where $n=$surfaces per platter (1 or 2)
* where $p=$platters

Mnemonic: "[[Binary Search Tree|BST]]? No problem"

## ZBR Capacity
For ZBR, the $st$ term from the above equation, which equals \# sectors, becomes:
$$
\sum_{z_{0}}^{z^n} s_{i} \cdot t_{i}
$$
This summation just says that we calculate $st$ for each zone, and then add them up to get the overall \# sectors
# Transfer Metrics
* Time for one revolution (read one track) = $60/\text{RPM}\quad\text{seconds per revolution}$
* Time to read a sector $60 /(\text{RPM} \cdot s)\quad\text{seconds per sector}$
* Average Rotational Latency = $\frac{60 /\text{RPM}}{2}\quad\text{seconds}$
* Amount of data read in one revolution = $s \cdot b\quad\text{bytes}$
* Transfer rate = $(s \cdot b) /(60/\text{RPM}) = (s \cdot b \cdot\text{RPM}) /60\quad\text{bytes per revolution}$
* Time to find a random block = Seek Time + Average Rotational Latency + Time to read a sector

# Zoned Bit Recording
Maintain somewhat constant bit density per sector.
The further out a [[#Track]] is, the greater its circumference.
Outer zones have more [[#Sector]]s than inner zones.
![[Pasted image 20251127223556.png|200]]

![[Disk Scheduling]]