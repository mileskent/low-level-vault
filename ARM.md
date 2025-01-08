A family of [[RISC]] [[ISA]]s.

# ARM vs [[LC3]]
* Both are Load/Store architectures
* Both have Fixed-Format instruction encodings
	* All instructions are the same size
* Register-Register address
	* Most instructions take two source registers and store their results in a destination register
* Addresses
	* LC3
		* [[Address Space]] is $2^{16}$ words, where each word is 2 bytes
		* [[Word Addressable]]
		* [[Addressability]] is 32 bites
	* ARM
		* [[Address Space]] is $2^{32}$ bytes
		* [[Byte Addressable]]
		* [[Addressability]] is 32 bits
* Processor Modes
	* LC3
		* User
		* System
	* ARM
		* User
			* Normal
		* System
			* Priviledged [[Operating System|OS]] tasks
		* FIQ
			* High priority interrupt request
		* IRQ
			* General purpose interrupts
		* Supervisor
			* Protected mode for OS
		* Abort
			* Memory Access Violations
		* Undefined
			* Undefined Instructions
* [[ALU]] and [[Register|Registers]]
	* ARM
		* 16 registers
		* PC is itself a register -> R15
		* All registers are 32 bits wide
		* Storing to PC can have unpredictable results on older ISAs 1-5
		* R11 -> Frame Pointer
			* Like R5 in LC3
		* R13 -> Stack Pointer
			* Like R6 in LC3
		* R14 -> Link Register
			* Like R7 in LC3
* [[Condition Code]]
	* LC3
		* N
			* Negative result from ALU
		* Z
			* Zero result from ALU
		* P
			* Postivie Result from ALU
	* ARM
		* N
			* Negative result from ALU
		* Z
			* Zero result from ALU
		* C
			* Carry out bit from ALU
		* V
			* [[2's Complement]]

