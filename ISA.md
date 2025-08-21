"Instruction Set Architecture". See Patt 1.7.4
The ISA is responsible for defining the set of instructions to be supported by the processor. It is the assembly language for that processor. It is a level of abstraction above the [[Microarchitecture]] of the processor.
* Examples include
	* [[LC3]]
	* [[LC 2200]]
	* [[ARM]]
	* [[MIPS]]
	* [[RISC]]
* [[Memory]] Organization
* [[Register|Register Set]]
	* [[Address Space|How many]]?
	* [[Addressability|What size]]?
	* How are they used?
* Instruction Set
	* Opcodes 
	* Data Types
		* [[IEEE 754]], [[IEEE 754 Double]]
		* ISA may need special functionality for multiple word data types
	* [[Addressing Mode]]s

> An ISA describes  the interface to the computer  from the perspective  of the 0s and 1s of  the program.  For example,  it describes the operations,  data types,  and addressing modes a programmer can use on that particular computer. It doesn’t specify the actual physical implementation. The microarchitecture does that. Using the car analogy, the ISA is what the driver sees, and the microarchitecture is what goes on under the hood.
> - Patt

Used by Machine language programmers, Assembly language progrmammers, compiler writers, etc.

### Philosophies

> [!tldr]
Minimal size instruction sets are superior, i.e. RISC. 

* Many Instruction ISAs
	* RISC (Reduced Instruction Set Computer)
	* ARM, PowerPC, MIPS, [[LC3]]
	* Expose as much as you can to the compiler so that it can optimized
	* Hard to write efficient machine code by hand
* Few Instruction ISAs
	* CISC (Complex INstruction Set Computer)
	* Intel x86, DEC VAX, IBN Z-Series
	* Do as much as you can per instruction
	* Relatively easy to write efficent machine code by hand