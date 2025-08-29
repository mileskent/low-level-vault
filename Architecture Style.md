# Accumulator
* Uses a single accumulator register for most operations. Simple but memory-heavy.
* Early Digital Computers
# Stack Oriented
* Operands come from the stack; results pushed back. Simplifies code but limits random access.
* Burroughs
# Register-Memory 
* Ops can mix registers and memory directly. Flexible but complex
* Intel x86, IBM s/360, DEC VAX, PDP-11
# Register-Register
* All ops use registers; memory only via loads/stores. Fast, simple, pipeline-friendly.
* MIPS, ARM, Alpha, PowerPC, CDC 6600, [[LC 2200]]