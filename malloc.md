Malloc allocates memory on the [[Heap]] and keeps track of that memory in large blocks of storage called [[Arena|Arenas]]. You must [[free]] the memory you allocated when you are done with it, ideally setting the [[Pointer]] to null when you are done. Malloc usually rounds up the [[Heap Allocation]], including metadata, to the system alignment. This is not visible to the user.
```
void *malloc( size_t size );
```

*malloc* (Memory Allocation) allocates `size` contiguous, uninitialized bytes of memory on the heap at runtime. 
* On success, returns the pointer (`void*`) to the beginning of newly allocated memory. To avoid a memory leak, the returned pointer must be deallocated with [[free]] or [[realloc]]
* On failure, returns a null pointer.
### Handling Failed Malloc
```
type *rp;
if ((rp = (type *)malloc(sizeof r)) == NULL) {
	// Handle Error Here
}
```

### Allocating Memory
#todo

### See also
[[sbrk]]
[[calloc]]
[[realloc]]
[[strdup]]
[[regcmp]]
[[Freelist]]
[[Canary]]
[[Arena]]