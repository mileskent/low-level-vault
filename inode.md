---
aliases:
  - index node
  - inodes
  - index nodes
---
* Inodes store metadata for every [[File]] on your system
* Stored in a table-like structure usually located near the beginning of a partition. 
* They store all the information except the filename and the file data:
	- Size in bytes
	- Location on [[Storage|disk]]
	- Permissions
	- Owner/Group
	- Date/time
	- Reference Count  (How many [[Hard Link]]s lead to this file?)
* Every file in a given directory is an entry with the filename and inode number. All other information about the file is retrieved from the inode table by referencing the inode number.
* Inodes numbers are unique at the partition level. Every partition has its own inode table.
* Every used inode has 1 file. Every file has 1 inode.
* List inodes with `ls -i`
* List inode usage with `df -hi`
* See `stat <file>`
* Inode tables can get full before the disk space is actually full
* Inode table size is tied to the disk size, and is created when the [[Filesystem]] is created (for [[EXT Filesystem|EXT]])