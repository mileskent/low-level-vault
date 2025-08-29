Instructions and data stored in the same place
Relies of both [[Combinational Logic]] and [[Sequential Logic]]
Controlled by [[Finite State Machine]]

# Datapath
> [!Example]- Full Datapath
![[Pasted image 20250330145206.png|700]]

> [!Example]- Simplified Datapath
![[Pasted image 20250330143501.png|600]]
## Components
* 8 registers in the [[Register File Circuit]]
* [[ALU]]
	* ***ADD***
	* ***AND***
	* ***NOT***
	* ***PASS***
		* Passes SR1 to bus
		* Only accessable through [[Microcode]]
* [[ROM]]
* [[RAM]]
* [[Finite State Machine]]
* [[PC]]
* etc... #todo



# Instructions
See [[Instruction Cycle]]
## ALU Instructions
### ADD
### AND
## Load Instructions
### LD
### LDR
### LDI
### LEA
## Store Instructions
## Control Instructions
### BR
### JMP
### JSR
### RET
### RTI
### TRAP




# 3 Macrostates of LC3
## [[Fetch]]
3 Clock Cycles
Gets the next instruction from [[Memory]] and puts it in the [[Instruction Register]]
## [[Decode]]
Is like a dictionary for how to do an [[Instruction]]
The [[Opcode]] actually goes into a [[Decoder]], which chooses the relevant instruction to be performed.
## [[Execute]] Runs the instruction.
# [[Memory]]
* $2^{16}$ memory locations from 0x0000 to 0xFFFF
* $16$ bits per [[Word]]
* Instructions start at 0x3000,
	* Recall typical [[orig]] in [[LC3 Instructions]]