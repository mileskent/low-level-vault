---
aliases:
  - PC
---
Keeps track of the *address* of the *next* execution to be executed
* Really the address of the word after the current instruction being executed. This matters because of changes in control flow, i.e. with JMP, RET calls and is not the same as the above definition. 
* The above definition is there because it is usually functionally correct, as usually there is not change in control flow.
([[Instruction Register]] holds the current instruction)

# LC3
Control Signals
* GatePC
	* Assert the PC on the [[Bus]]
	* [[Tri State Buffer]]
* LD.PC
	* Update the PC
* PC Mux
	* 2 bit [[Multiplexor]] for the output


