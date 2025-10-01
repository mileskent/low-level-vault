We only care about **microprogrammed control units** which are a type of CPU [control unit](https://en.wikipedia.org/wiki/Control_unit) that generate the control signals needed to execute machine instructions by reading [[Microcode]] from the main [[ROM]]. This control unit, controls the [[Finite State Machine]] that keeps track of the states of all of the gates and mux signals and such, directing the control flow of the [[Instruction Set Architecture|ISA]] and [[Macrostate]]s. Not all control units use microcode.

> [!note]+ Georgia Tech
> Georgia Tech seems to uniquely call microprogrammed control units microcontrollers and microcontrol unit

# 3 ROM Control Unit
3 ROM Control Unit from LC 4200 architecture.
![[Pasted image 20250907153336.png]]
## Main Rom
Contains the [[Microcode]]
## Sequencer ROM
Maps [[Opcode]] to address in [[#Main Rom]]
Only is used after fetch3
## Conditional ROM
Maps CmpTarget to address in [[#Main Rom]]
When doing a conditional branch, CC ROM's current selected address or the next state bits will be used.
The CC ROM contains addresses of the beginning of different microstates needed for branching.
It would probably look something like this

| CmpTarget (Input) | CC ROM Content (Output Address)     | Corresponding "True" Condition          |
| ----------------- | ----------------------------------- | --------------------------------------- |
| 00                | Address of BEQ_Branch_Microstate    | For a BEQ instruction, when SR1 == SR2. |
| 01                | Address of BGT_Branch_Microstate    | For a BGT instruction, when SR1 > SR2.  |
| 10                | Address of CLMP_LessThan_Microstate | For a CLMP instruction, when DR < SR1.  |
| 11                | Address of CLMP_MoreThan_Microstate | For a CLMP instruction, when DR > SR2.  |

# Flat ROM
* More space
* Faster since only one ROM access in each microinstruction
* Add a T bit to the ROM
	* AND the T bit and the Z reg become the 6th address bit
	* This will result in branching behavior
* Add an M bit to the ROM 
	* AND the M bit and the OP to become the 7-10 address bits
	* This will result in branching behavior
* Clone fetch in microcode

# Hardwired
* More expensive
* Doesn't have to wait on any ROMs