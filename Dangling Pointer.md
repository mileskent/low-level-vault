A [[Pointer]] to memory that is no longer reserved.

```
...
int * ptr = (int*)malloc(sizeof(int));

// After below free call, ptr becomes a dangling pointer
free(ptr);

// removing Dangling Pointer
ptr = NULL;
...
```
