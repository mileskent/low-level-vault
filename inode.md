---
aliases:
  - index node
  - inodes
  - index nodes
---
![[Pasted image 20251128110338.png]]
* inodes store metadata for every [[File]] on your system
* inodes are fixed size, meaning that their location section is fixed, and therefore they have a max file data size
* inodes are stored as a list of inodes
	* The [[Storage|Disk]] location of an inode can be calculated from its [[#inumber]], which is an index into the list of inodes
* They store all the information except the filename and the file data:
	- Size in bytes
	- Location on [[Storage|disk]]
		- The ordered list of [[Disk Block#Disk Block Address]]es
		- Kind of like having one [[Filesystem#File Allocation Table]] per file
	- Permissions
		- User, Group, Other
		- Bits go: Read, Write, Execute
		- e.g. `-rw-r--r--` means user can read and write, and everyone else can read
	- User id
	- Group id
	- Modification date
	- Reference Count  (How many [[Hard Link]]s lead to this file?)
- inodes can be [[Caching|Cached]] by the [[Operating System|OS]] in [[Memory]] when a file is in use
* Every file in a given directory is an entry with the filename and inode number. All other information about the file is retrieved from the inode table by referencing the inode number.
* Inodes numbers are unique at the partition level. Every partition has its own inode table.
* Every used inode has 1 file. Every file has 1 inode.
* List inodes with `ls -i`
* List inode usage with `df -hi`
* See `stat <file>`
* Inode tables can get full before the disk space is actually full
* Inode table size is tied to the disk size, and is created when the [[Filesystem]] is created (for [[EXT Filesystem|EXT]])

# inumber
inode index number; the index of the inode in the inode [[Array]]

![[Filesystem#Indexed Allocation]]