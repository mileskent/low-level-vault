* How do you organize the data ([[File|Files]]) that you put on a [[Storage]] medium?
	* We have to worry about both kinds of [[Fragmentation]]
* All this filesystem talk is the [[UNIX]] style.
* A file name corresponds [[Disk Block|Disk Blocks]]
	* Same virtual-physical [[Map|mapping]] idea as [[Paging]]
* Most [[Operating System]]s support more than one filesystem
* A good filesystem has
	* Fast sequential access
	* Fast random access
	* Ability to resize files
	* Ability to easily allocate [[Space]]
	* Efficient space utilization on the disk
# Filing Scheme
## Contiguous Allocation
If you want $N$ contiguous blocks, we will give you $N$ contiguous blocks.
* Variable size allocation leads to [[Fragmentation#External Fragmentation]] issues

Uses a [[Freelist]] that is stored on [[Storage|Disk]] but [[Caching|Cached]] in [[Memory]]
* Growth: ❌
* Allocation speed: ❌
	* Slow
* Space: ❌
	* Get both internal and external fragmentation
* Sequential Access: ✅
* Random Access: ✅
### Contiguous Allocation with Overflow
Helps the growth problem by adding extents.
An extent is simply a contiguous block of disk space that is separate from the file's initial, primary allocation.
When the file's primary contiguous space becomes full, a new, separate extent (another contiguous block) is allocated to hold the overflow data.
This new extent is linked to the primary allocation, usually through a pointer or record in the file's metadata.
## Linked Allocation
Uses linked list per file. Has free list.
Each file has a linked list of disk blocks. The blocks do not have to be contiguous in memory. This method eliminates external fragmentation.
* Growth: ✅
* Allocation speed: ✅
* Space: ✅
	* No external, minimal internal
* Sequential Access: ☑️
* Random Access: ❌
## File Allocation Table
Encode linked list in a table instead of in the disk blocks themselves.
Files are filenames and starting block indices. FAT has the block index, busy bit, and next block index. Sentinel -1 indicates the end of the list.
FAT stored on disk, cached in memory.
* Growth: ✅
* Allocation speed: ✅
* Space: ✅
	* No external, minimal internal, similar to linked
* Sequential Access: ✅
	* Much better than linked, contiguous is better
* Random Access: ☑️
## Indexed Allocation
This one is basically the [[UNIX]] filesystem.
The idea is that you store the metadata of the file separately from the data itself.
This is implemented using [[inode|inodes]]
* Growth: ❌
	* You can grow files up to the point that you run out of room for disk block address data in your inode, after which you are maxed out for that inode
* Allocation speed: ✅
* Space: ✅
	* No external, minimal internal, similar to linked
* Sequential Access: ✅
	* Same as FAT
* Random Access: ☑️
	* Same as FAT
### Multilevel Indexed Allocation
The basic idea of inodes, but you have the "Location on disk" part of the inode point to index blocks, instead of logical blocks. 
Index blocks are just blocks that have logical block entries. They could also have index block entries.
You can have as many levels of indirection, such that you have a sufficient ability to grow files.
The issue is that there is a lot of overhead going on. By having a system that enables you to have really big files, when you use normal size files, you have a bunch of [[Fragmentation#Internal Fragmentation]] going on.
![[Pasted image 20251128111344.png|400]]
### Hybrid Indexed Allocation
Multilevel Indexed Allocation, but there are multiple indirection levels that all coexist. The bigger the file, the bigger the indirection you use.
The bigger the file, the slower the access.
* Growth: ✅
	* The multilevel hybrid model fixes the growth issues associated with the basic indexed allocation
* Allocation speed: ✅
* Space: ✅
	* No external, minimal internal, similar to linked
* Sequential Access: ✅
	* Same as FAT
* Random Access: ☑️
	* Same as FAT
![[Pasted image 20251128111725.png|400]]



# Filesystem Integrity
![[Journaling]]

![[Copy-on-Write#Filesystem Copy-on-Write]]