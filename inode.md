---
aliases:
  - index node
  - inodes
  - index nodes
---
* Inodes store metadata for every file on your system in a table-like structure usually located near the beginning of a partition. They store all the information except the file name and the data.
	- Size
	- Permission
	- Owner/Group
	- Location of the hard drive
	- Date/time
	- Other information
* Every file in a given directory is an entry with the filename and inode number. All other information about the file is retrieved from the inode table by referencing the inode number.
* Inodes numbers are unique at the partition level. Every partition has its own inode table.
* Every used inode has 1 file. Every file has 1 inode.
* List inodes with `ls -i`
* List inode usage with `df -hi`