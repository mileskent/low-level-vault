# UNIX Filesystem
See [[Filesystem#Indexed Allocation]]
## UNIX Filesystem Commands

| Command                     | Semantics                                                             |
| --------------------------- | --------------------------------------------------------------------- |
| `touch <filename>`          | Create a zero byte file with the provided filename, and current date. |
| `mkdir <dirname>`           | Create an empty directory with the provide dirname                    |
| `rm <filename>`             | Remove the file of the given filename                                 |
| `rmdir <dirname>`           | Remove the directory of the given dirname                             |
| `ln <orig> <new>`           | [[Hard Link]] the original to the new                                 |
| `ln -s <orig> <new>`        | [[Symlink]] the original to the new                                   |
| `chmod <rights> <filename>` | Change the permissions/access rights for the file                     |
| `chgrp <group> <filename>`  | Change the file of the given filename to be of the specified group    |
| `chown <user> <filename>`   | Change the owner of the file to the provided user                     |
| `cp <orig> <new>`           | Copy the original file to the new file                                |
| `mv <orig> <new>`           | Move the original file to the new file                                |
