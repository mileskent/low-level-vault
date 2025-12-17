* The system call is the fundamental interface between a [[Program]] and the [[Linux Kernel]]
* Generally not invoked directly, but rather via [[glibc]] wrapper functions

# Linux Syscall Table

| Syscall | Function                                                                                                                           | Man Page                                                     |
| ------- | ---------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------ |
| open    | Request the kernel to open a file, and return its [[File Descriptor]]                                                              | [man](https://www.man7.org/linux/man-pages/man2/open.2.html) |
| read    | Request the kernel to read data from a [[File Descriptor]] and place that data into a buffer supplied by the caller                | [man](https://man7.org/linux/man-pages/man2/read.2.html)     |
| write   | Request the kernel to write data from a caller specified buffer to the file (or output device) identified by a [[File Descriptor]] | [man](https://man7.org/linux/man-pages/man2/write.2.html)    |
| fork    | Request the kernel to duplicate (fork) the provided [[Process]], including it s open [[File Descriptor]]s                          | [man](https://man7.org/linux/man-pages/man2/fork.2.html)     |
| exit    | Request the kernel to terminate a process                                                                                          | [man](https://man7.org/linux/man-pages/man3/exit.3.html)     |
