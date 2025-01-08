A region of memory that operates like a stack data structure. The stack grows up in the negative direction towards the [[Heap]] which grows down towards the positive direction.
Function calls create [[Stack Frame|Stack Frames]] which is like a struct that has all the relevant information for a function call. 
Stack frames must be constructed and deconstructed. Both the [[Caller]] and [[Callee]] contribute to this effort, but the callee does most of the work, while the callee really only needs to push arguments (in reverse order) before the function call, and pop arguments and save the return value after the function call.

### See also
[[Stack Frame]]