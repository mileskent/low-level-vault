| Storage Class Specifiers |                                                                                                                                                        |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| \<no keyword\>           | Visible to everything else in the regular scope. As a global, possibly other files; **external definition** - visible to other files - defines storage |
| static                   | Visible no other files.                                                                                                                                |
| extern                   | **External reference** - visible to other files - declares reference to an external defiintion somewhere                                               |
| auto                     | Exists.                                                                                                                                                |
##### Example
An external definition
```file1.c
int a[10]; // external definition
```
An external reference; a reference to variable `a` from `file1.c`:
```file2.c
extern int a[10]; // external reference
```
If variable `a` was `static`, the `extern` in `file2.c` would fail.

### Storage Keyword Combinations

|          | Outside a function definition                          | Inside a function definition                                                                                                                        |
| -------- | ------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| None     | scope: external definition<br>storage: static address  | scope: within the function<br>storage: on the stack)<br>(same as auto)                                                                              |
| auto     | N/A                                                    | scope: within the function<br>storage: on the stack<br>(same as None)                                                                               |
| static   | scope: within the file only<br>storage: static address | scope: external reference<br>storage: static address; location determined by file containing the external definition (can't have intializer either) |
| register | N/A                                                    | scope: within the function<br>storage: register or stack (hint to compiler; use of & operator not allowed; seldom used)                             |
Most important takeaways:
* static has two meanings
	* inside a function: static changes the *storage location* to static memory (see [[C Memory Layout]]) instead of on the stack
	* outside a function: static changes the *scope* to be only visible with the file (the storage stays in static memory)
* extern
	* Compiler does *not* allocate sotrage
	* For type check of the idenitifer name only
	* another C file must allocate storage by defining that varible or function
	* Typical way to link global variables between C files
* volatile
	* tells the compiler not to optimize away the variable
	* use this for device registers
	* prevents compiler from optimizing (removing) dead code
### Type Qualifiers
* Can appear as part of the base type or within a declarator
* Not mutally exclusive with a storage class
* **const** - the value of this varibale is immutable after initialization
* **volatile** - the compiler may not optimize reference to this variable (e.g. it's a device register that may change value asynchronously)
	* e.g. [[GBA#Light Up a Pixel|REG_DISPCTL for GBA]]
* **restrict** - for the lifetime of a pointer, only the pointer itsel or a value directly derived from it may be used to access the object to which it points. This allows better optimizzation but isn't required.