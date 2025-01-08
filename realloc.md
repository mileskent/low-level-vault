```
type *currptr = realloc(oldptr, num_bytes)
```
* Resizes a previous allocation, recalling [[malloc]] for your new specified size
* Find space for new allocation
* Copy original data into new space
	* Truncating if allocating less than original
* Free old [[malloc]] space
* If successful
	* Return pointer to new space
	* `oldptr` has been freed by realloc and should never be used again
* If fails
	* Return null
	* `oldptr` has not been freed and still maintains its reference to the original [[malloc]] block

> [!tip]
> ```
> malloc(n) = realloc(NULL, n)
> ```
### Template
```
type *cp = malloc(...);
{
	void *tmp;
	if ((tmp = realloc(cp, ...)) == NULL) {
		/* realloc error */
		free(cp);
		// probably crash program here
	} else {
		cp = tmp;
	}
}
```

### See also
[[Heap Allocation]]