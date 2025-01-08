### Declaration
* A declaration introduces an identifier and describes its type to the compiler so that it can process the identifier, accepting references to it for type checking. Comes in 2 parts:
	* Base Type
		* Type and optionally storage class and/or type qualifier
		* Applies to all names up until the semicolon
	* List of **Declarators**, seperated by commas
		* Each of  these declares a type for each idenitifier
		* Each is based on the base type but stands alone
		* Type-qualifers may optionally be prepended to the declarator phrases
	* example: `static volatile long int i, *j, k[10]`
		* Base type is `static volatile long int`
		* List of Declarators are `i, *j, k[10]`
	* Consider `int* x, y, z`
		* \*x is a pointer
		* y and z are not, we should really write it like `int* x, y, z`; this is why you see this syntax; the pointer notation and array brack notation go on the variable not the type
	* Read declarations inside out
		* `int *const p` vs `const int *p`
		* constant pointer to int vs pointer to constant integer
		* `char *db[10][20]`
			* `db` -> variable
			* `db[10]` -> variable: 10 array
			* `db[10][20]` -> variable: 10 array of 20 arrays
			* `*db[10][20]` -> variable: 10 array of 20 arrays of pointers to...
			* `char *db[10][20]` -> variable: 10 array of 20 arrays of pointers to chars
##### Declarator
* Rule 1: Remember the precedence of the declarators
	* () and \[\] declarators get processed first
	* \* gets processed last
	* Parentheses change the precendence order (just as in expressions)
* Rule 2: Read or form the declarations from the inside out
	* Remember to use "Pointer to", "Array\[\] of", and "Function returning"
	* The base type is always the **last** part of the type
* In short: ***from inside, go right if you can, left if you must***
* Example `double **m[][]`
	* Go right
		* Array of
		* Array of array of
	* Left if you must
		* Array of array of pointers
		* Array of array of pointers to pointers to
		* Array of array of pointers to pointers to doubles
* Example `int *(**f)()`
	* f is a pointer to a pointer to a function return a pointer to an int
	* start at f `f`
	* `*f` -> pointer to
	* `**f` -> pointer to pointer to
	* `(**f)()` -> pointer to pointer to function returning
	* `*(**f)()` -> pointer to pointer to function returning pointer to
	* `int *(**f)()` -> pointer to pointer to function returning pointer to int
##### Unwinding
* Example `int *(**f)()`
	* How do we unwind `f` to get the int?
	* `*(**f)()` -> it is totally symmetrical, put it together and take it apart with exact same syntax
* Example `int *(*c)[]`
	* `c` pointer to array of pointers to int
	* `*c` array of pointers to int
	* `(*c)[index]` pointers to int
	* `*(*c)[index]` int
### Definition
* A definition instantiates the idenitifer