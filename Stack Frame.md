Stack frames must be constructed and deconstructed. Both the [[Caller]] and [[Callee]] contribute to this effort, but the callee does most of the work, while the callee really only needs to push arguments (in reverse order) before the function call, and pop arguments and save the return value after the function call.
### Caller Precall
```
for arg in reverse order of args {
	stack pointer -= 1
	mem[stack pointer] = arg
}
```
### Callee Stack Construction
```
ADD R6, R6, -4 ; Allocate 4 words for rv, old ra, old fp, lv  
STR R7, R6, 2 ; Save old ra (R7) into frame  
STR R5, R6, 1 ; Save old fp (R6) into frame  
ADD R5, R6, 0 ; FP = SP  
; allocate addition local variables here if applicable
ADD R6, R6, -5 ; Allocate 5 words for R0-R5  
STR R0, R5, -1 ; save R0 into frame  
STR R1, R5, -2 ; save R1 into frame  
STR R2, R5, -3 ; save R2 into frame  
STR R3, R5, -4 ; save R3 into frame  
STR R4, R5, -5 ; save R4 into frame
```
### Callee Stack Frame Teardown
```
STR R0, R5, 3 ; Save return value on stack
LDR R4, R6, 0   ; restore R4
ADD R6, R6, 1   ; pop R4 off stack
LDR R3, R6, 0   ; restore R3
ADD R6, R6, 1   ; pop R3 off stack
LDR R2, R6, 0   ; restore R2
ADD R6, R6, 1   ; pop R2 off stack
LDR R1, R6, 0   ; restore R1
ADD R6, R6, 1   ; pop R1 off stack
LDR R0, R6, 0   ; restore R0
ADD R6, R6, 1   ; pop R0 off stack
ADD R6, R5, 1   ; pop all local variables (mem[R5] has one guaranteed)
LDR R5, R6, 0   ; restore R5 (old FP)
ADD R6, R6, 1   ; pop R5 off stack
LDR R7, R6, 0   ; restore R7 (return address)
ADD R6, R6, 1   ; pop R7 off stack
```
### Caller Postcall
```
return value = mem[stack pointer] // save return value
stack pointer += (1 + argcount) // pop return value and func args
```
