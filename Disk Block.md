---
aliases:
  - Block
  - Storage Block
---
A conceptual [[#Sector]] set of natural cardinality; the smallest logical unit of [[Storage]].

# Disk Block Address
In the past, an ordered triple of (cylinder, head, block) was used for disk block addressing.
Nowadays, we have smart disk controllers that do the scheduling for us, as well as [[Hard Disk Drive#Zoned Bit Recording]]
This means that we don't use that triple anymore, because we don't need to know about the geometry of the disk, especially because it's variable. This basically makes it uncalculatable from the [[Operating System|OS]] perspective.
We just do logical block addressing nowadays, addressing it as an [[Array]] of disk blocks