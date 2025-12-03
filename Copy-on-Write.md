A strategy used to optimize the copying of resources.
Resources are [[Lazy|lazily]] copied. 
Only when a write is attempted is the resource copied. Up to that point, only reads have taken place, which do not effect the state of the resource.

# Filesystem Copy-on-Write 
A strategy for [[Filesystem#Filesystem Integrity]] where data blocks are never rewritten, but copied to free space
Blocks are rewritten in an order tyhat guarantees that the filesystem is always consistent
e.g. ZFS, BTRFS
