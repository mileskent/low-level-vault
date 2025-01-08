### Getting Started
```
gcc -g main.c
gdb a.out
```
### Basic Commands
* b file\:line
	* set a breakpoint at file, line
* b function
* run (args)
	* run the program
* p expr
	* print the value of an expression
* n
	* execute the next statement
* l \[file\:line\]
	* list program at file, line
* bt
	* "backtrace"
	* show the runtime stack
* c
	* continue execution
* s
	* step into a function call
* d breakpointnumber
	* delete a breakpoint
* Ctrl-C
	* suspend the program and reenter gdb
