Instructions and data stored in the same place
Relies of both [[Combinational Logic]] and [[Sequential Logic]]
Controlled by [[Finite State Machine]]

# Datapath
> [!Example]- Full Datapath
![[Pasted image 20250330145206.png|700]]

> [!Example]- Simplified Datapath
![[Pasted image 20250330143501.png|600]]
## Datapath Components
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
* 4 bit [[Opcode]]
* Instructions
	*  Operate (ALU)
		* [[ADD]] ([[2's Complement]])
			* Register Mode
				* 5th bit 0, with a source register after
				* [[Opcode]] | R2 | R1 | 000 | R3
			* Immediate (Literal) Mode
				* 5th bit 1, uses literal for source
				* [[Opcode]] | R2 | R1 | 1 | literal
			* Bit number 5 goes into a [[Multiplexor]] to choose whether to use the register value or the literal value
		* [[AND]]
		* [[NOT]]
	* Load
		* [[LD]] [[LDR]] [[LDI]] [[LEA]]
	* Write
		* [[ST]] [[STR]] [[STI]]
	* Control
		* [[BR]] [[JMP]] [[JSR]] [[JSRR]] [[RET]] [[RTI]] [[Traps & Interrupts#TRAPs|TRAP]]

See [[Instruction Cycle]]
# 3 Macrostates of LC3
## [[Fetch]]
3 Clock Cycles
Gets the next instruction from [[Memory]] and puts it in the [[Instruction Register]]
## [[Decode]]
Is like a dictionary for how to do an [[Instruction]]
The [[Opcode]] actually goes into a [[Decoder]], which chooses the relevant instruction to be performed.
## [[Execute]]
Runs the instruction.
# [[Memory]]
* $2^{16}$ memory locations from 0x0000 to 0xFFFF
* $16$ bits per [[Word]]
* Instructions start at 0x3000,
	* Recall typical [[orig]] in [[LC3 Instructions]]