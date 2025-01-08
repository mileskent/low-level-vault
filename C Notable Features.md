* Procedural (no objects or classes)
* C structs
* [[Pointer]] for raw memory access instead of arrays, references, or strings
	* never forget that strings don't exist. always remember you are handling character pointers!
	* don't use [[C Operators#sizeof|sizeof]] for string length! you will get the size of the character pointer to the head of the character array! Use strlen() instead!
	* Think about [[LEA]]
	* No runtime checking
* No function overloading
* Immutable vs Mutable function parameters, i.e. "Pass by value" vs "Pass by reference"
	* Recall [[LC3]] [[Stack Frame|Stack Frames]], when you just have normal types in your function signature, within the scope of the function, the parameters are just local variable copies of the actual variables, saved on the stack in the stack frame of the function. Accordingly, when you modify the local variable stack frame parameters, it doesn't mutate the original variable that was pushed onto the stack by the [[Caller]].
	* If you actually want to mutate your parameters, you have to pass a pointer to the variable (i.e. pass by reference), as even if the value of the pointer on the stack is a copy, it is still a pointer, and thus you can dereference and mutate the actual value of the variable that it points to.
* Does not have printing, I/O, or (dynamic/heap) memory management built in
* Function Prototypes and Function Definitions
* Compiled by [[GCC]]
* There are source code files and header files. Source code files are usually .c and header files are usually .h
	* Source code files
		* definitions (allocation of storage)
		* functions
	* Header files
		* Declarations (no storage allocation)
		* Macros
		* Function prototypes
	* All source code files that use functions from a source code file need to include the respective header file. 
* [[Heap Allocation]]
* [setjmp.h](https://en.cppreference.com/w/cpp/utility/program/setjmp)
	* NEVER USE THIS!
