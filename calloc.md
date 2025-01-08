```
void *calloc(size_t num, size_t size)
```
* Calls in [[malloc]] to find space for `num * size` bytes
* Initializes the allocated space to 0s
* Otherwise same as [[malloc]]