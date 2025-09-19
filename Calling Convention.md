# LC3 Calling Convention
The callee does most of the work, while the callee really only needs to push arguments (in reverse order) before the function call, and pop arguments and save the return value after the function call.
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


# LC2200 Calling Convention
If we split the assingment of the registers, then most of the time, the caller ancd calle can each save fewer registers based on what they actually need to use

s0-s2 registers are reservable by the callee
t0-t2 registers are reservable by the caller
v0 return value
a0-a2 parameters

This splitting saves memory accesses, because memory access is slow
If we run out of registers, we have to use the stack

## Procedure
We have a pointer to the current position on the stack **sp**. If we need to add anything to the stack, we will decrement **sp** to allocate space, and then write to `mem[sp]`
**Step 1**
Caller saves any of the **t0-2** on the stack if it needs them postcall
**Step 2**
Caller places the parameters in **a0-2** and optionally on the stack if it needs more than 3
**Step 3**
Caller allocates space for return values on the stack if **v0** is insufficient
**Step 4**
Caller saves the previous return address in **ra**
**Step 5**
Caller executes `JALR at, ra`
Control is transferred to the stack construction code in the callee
**Step 6**
Callee stores previous frame pointer then copies the contents of the stack pointer into the frame pointer
**Step 7**
Callee saves any **s0-2** that it plans to use during it execution on the stack 
**Step 8**
Callee allocates space for any local variables on the stack
**Step 9**
The body of the callee runs and finally leaves the return result in **v0** and on the stack if needed.
Frame is torndown.
**Step 10**
Callee restores relevant **s0-2** from stack
**Step 11**
Callee replaces **sp** with the frame pointer, popping the local variables and s registers off of the stack.
**Step 12**
Caller restores the previous return address to **ra** and pops it off of the stack
**Step 13**
Callee executes `JALR $ra, $zero` to return back to the caller.
**Step 14**
Caller retrives any additional return values as desired and pops them off the stack
**Step 15**
Caller pops additional parameters off of the stack if any
**Step 16**
Caller restores any saved **t0-2** from the stack and also pops them off of the stack
The caller moves on to the next instruction after the function call and the stack is back to its state before the function call was executed.