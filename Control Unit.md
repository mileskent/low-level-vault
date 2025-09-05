We only care about **microprogrammed control units** which are a type of CPU [control unit](https://en.wikipedia.org/wiki/Control_unit) that generate the control signals needed to execute machine instructions by reading [[Microcode]] from the main [[ROM]]. This control unit, controls the [[Finite State Machine]] that keeps track of the states of all of the gates and mux signals and such, directing the control flow of the [[ISA]] and [[Macrostate]]s. Not all control units use microcode.

> [!note]+ Georgia Tech
> Georgia Tech seems to uniquely call microprogrammed control units microcontrollers and microcontrol unit

# 3 ROM Control Unit
3 ROM Control Unit from LC 4200 architecture.
![[Pasted image 20250901193653.png]]
## Main Rom
Contains the [[Microcode]]
## Sequencer ROM
Converts [[Opcode]] to address in [[#Main Rom]]
## Conditional ROM
#todo