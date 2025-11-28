A container of information.
Assuming [[Filesystem#Indexed Allocation]]
It is a filename and an [[inode]] number. You can see this with `ls -i`
When you create a file, initialize an inode, and create a directory entry. This sets the reference count of the inode to 1.
There is no way to "remove" a file. You can only unlink a directory entry.
A file is deleted when its inode's reference count reaches zero.
Accessing a file counts as a reference, so, for example. If you try to remove a log file, it might not go away, because there is probably a [[daemon|service]] that is writing it.