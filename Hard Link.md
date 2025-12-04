* Points directly to the [[inode]]
* Shares the same inode number as the original [[File]]
* Can only link to files within the same [[Filesystem]]
* Deleting the original file does not delete the data for that file until the last hard link is deleted
* Can only link to files
* As opposed to [[Symlink]]
* Shows up the same as the original file in `ls -l`