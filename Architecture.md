Architecture defines what a computer system will do. As opposed to [[Organization]]
The abstract design and structure of a computer system. It includes the set of rules and methods that describe the functionality, organization, and implementation of computer systems. Architecture is concerned with the higher-level aspects like the instruction set (how a machine understands and processes instructions), addressing modes, data types, and the hardware abstraction (e.g., the interaction between the CPU and memory). It is more about the "what" the system does.
The abstraction involving programmer-visible details of a computer system such as [[Instruction Set Architecture|ISA]].

# Style
## Accumulator
* Uses a single accumulator register for most operations. Simple but memory-heavy.
* Early Digital Computers
## Stack Oriented
* Operands come from the stack; results pushed back. Simplifies code but limits random access.
* Burroughs
## Register-Memory 
* Ops can mix registers and memory directly. Flexible but complex
* Intel x86, IBM s/360, DEC VAX, PDP-11
## Register-Register
* All ops use registers; memory only via loads/stores. Fast, simple, pipeline-friendly.
* MIPS, ARM, Alpha, PowerPC, CDC 6600, [[LC 2200]]