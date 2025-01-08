* [[Pointer]] for raw memory access instead of arrays, references, or strings
	* never forget that strings don't exist. always remember you are handling character pointers!
	* don't use [[C Operators#sizeof|sizeof]] for string length! you will get the size of the character pointer to the head of the character array! Use strlen() instead!
	* Think about [[LEA]]
	* No runtime checking
* Null Pointers!!!
	* Just because you declare a pointer doesn't mean that it actually points to anything.
	* Null Pointer Dereferences cause unexpected behavior.
	* For example: `char *foo(void) { char ca[10]; ...; return ca; }`
		* Since `ca` was allocated locally, i.e. on the stack inside of the function call, the pointer returned is now pointing to essentially [[free|freed]], who-knows-what memory
		* Bad!!!