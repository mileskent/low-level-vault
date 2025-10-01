# Implementation
Depends on whether you have a [[Control Unit#3 ROM Control Unit|Multiple ROMs]] or a [[Control Unit#Flat ROM]] in your [[Control Unit]].
## Multiple ROMs
![[Control Unit#3 ROM Control Unit#Conditional ROM]]
## Flat ROM
![[Control Unit#Flat ROM]]
# Pipelined Branching
## Conservative
Conservative is the same as stalling the pipeline
* Wait until branch outcome is known.
	* Stall the pipeline, send NOOPs from IF state
* Resume normal execution when branch outcome is known
	* e.g. Result of comparison A-B is known
	* IF there is need to branchh, PC gets the target address of the branch and IF stage is flushed
* Two Cases
	* Branch TAKEN
	* Branch NOT TAKEN
## Branch Prediction
(Modern Technique)
Assume branch not taken
Continue in pipeline
Prediction may be wrong, flush the instructions at IF and ID/RR, adjust PC if needed
The term for this is speculative execution
If prediction is correct, then we get pipelining benefit, and it is as if no branch took place
![[Pasted image 20250923194132.png|400]]
![[Pasted image 20250923194511.png|400]]
![[Pasted image 20250923194531.png|400]]
It is impossible to always guess whether we branch. See [[Halting Problem]].
### Heuristics
* Compare target with current PC
	* Loops generally branch backwards (target < PC)
		* Guess branch will be taken
	* Conditionals generally branch forward (target > PC)
		* Guess branch won't be taken
* Some ISAs have 2 different families of branch instructions so that the [[Compiler]] can signal whether it thinks the branch will be taken or not
* Keep a history of branch target addresses, e.g. Branch Target Buffer where there are 3 columns of PC of branch instruction, Taken?, PC of branch target address
	* "If we took it last time, we will probably take it this time"

## Delaying Branch
(Not super important)
* Ignore the problem in hardware (i.e. don't automatically generate NOOPs in fetch stage)
* Give the NOOP instructions to the compiler
	* e.g. the instruction after a branch is always executed
* Let the compiler worry about it
	* Compile in a NOOP instruction after every branch instruction
* Therefore the compile has the abillity to optimize the branching itself, e.g. by choosing whether or not the semantics of the program change when a NOOP is removed. If not, then they can be removed
