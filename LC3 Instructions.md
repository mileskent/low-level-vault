[[Instruction|Instructions]] of the [[LC3]]
Note that DR, SR -> Destination, Source Register

# [[ADD]]
# [[AND]] 
# [[NOT]]

# LD
Load
**0010 | DR | PCoffset9**
```
DR <- mem[PC* + PCoffset9]
```
PCoffset9 -> PCoffsetN
Note that [[PC]] points to next instruction
> [!example]- LD Trace
3 Clock Cycles: 
> * Red
> 	* Very similar to LEA
> * Yellow
> * Purple
![[Pasted image 20250210173801.png]]

# LDI
Load Indirect
**1010 | DR | PCoffset9**
```
DR <- mem[mem[PC* + PCoffset9]]
```

# LDR
Load
*Similar to LD except address is using an offset provided register instead of an offset PC*
**0110 | DR | BaseR | offset6**
```
DR <- mem[BaseR + offset6]
```

# LEA
Load Effective Address
**1110 | DR | PCoffset9**
```
DR <- PC* + SEXT(PCoffset9)
```

# STI
Store Indirect
**1011 | SR | PCoffset9**
```
mem[mem[PC* + SEXT(PCoffset9)]] <- SR
```
5 Cycles

# ST
# STR
# JMP
# BR
Conditional Branch
**0000 | n | z | p | PCoffset9**
n z p are instruction bits, N Z P are circuit bits from the CC
```
if ((n AND N) OR (z AND Z) OR (p AND P)) PC = PC* + SEX(PCoffset9)
```

# JSR
# JSRR
# RET
Return.
# RTI
# TRAP
Interrupt for errors or whatever other reason. 
For "Program discontinuities"
**1111 | 0000 | trapvect8**