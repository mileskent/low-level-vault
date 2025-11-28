---
aliases:
  - Soft Link
  - Symbolic Link
---
* Points to the path name of a [[File]] or [[Directory]]
* Has its own unique [[inode]] number, i.e. it occupies an inode, unlike [[Hard Link]]
* Can link to files or directories across [[Filesystem]]s
* Deleting the original file results in a dangling link, similar to a [[Dangling Pointer]]