* `[]` makes the array's contents get stored on the stack (think about how it works in [[LC3]]), directly where it was declared in memory, otherwise it would just be the pointer on the stack
* Its pretty much like [[blkw]], where it allocates the memory in-line, and the array name is like the LC3 label, which is why its a const pointer.
* Note that doing it this way allows the array to be written to
	* for a string, for example, if you just set a pointer to a string literal, it will cause issues if you try to write, because string literals are read only.o 
* If you pass an array to a function it decays into just a pointer
	* This means `sizeof` outside of the function on `arr` and inside of the function on `arr` will *not* yield the same result
### 1D
* `int arr[size]`
* `arr[i] = *(arr + i) = i[arr]`
* `i[arr]` works because the bracket notation will expand it to `*(i + arr)`
* Address of beginning of array -> `ia, &arr[0]` (different types but same data; just cast)
### Multidimensional
can be arbitrary dimension
* 2D
	* `int arr[rows][columns]`
	* Address of beginning of array -> `arr, &arr[0][0]`
	* Address of row r -> `ia[r], &ia[r][0]`
* 3D
	* `int a[slices][rows][columns]`
	* `offset = (i * rows * columns) + (j * columns) + k`, note that `slices` not included, because the array is really just a pointer to an array of `[rows][columns]`
	* `a[i][j][k] = *(*(*(a + i) + j) + k)`
### Marginally Indexed Arrays (Array of Pointers)
For example, an array of strings
```
static char *weekdays[] = {
	"Monday", "Tuesday", "Wednesday", "Thursday", "Friday"
};
```
It is an array with a pointer to the beginning of each string. The strings are probably stored in memory like so.
```
...Monday\0Tuesday\0Wednesday\0Thursday\0Friday\0...
```
This can be more memory efficient than having a static max buffer size for each string, unless the latter case happens to have a scenario where every single string is the same length. It doesn't really matter if the strings are actually contiguous in memory from the perspective of space efficiency, but they probably are.