Arrays of 1s and 0s that describe to the [[CPU]] how to direct the flow of information, per [[Clock]] cycle
Each memory address (in the main [[ROM]]) will hold an entry that represents a microstate. Such an entry holds two crucial pieces of information: what signals to assert on the datapath for a specific microstate and what the next state should be (what address to jump to next).
Lots of microcode culminates in a microprogram.
Input bits <-> current state, address
Each line <-> outputs, next state

![[Pasted image 20250209153845.png]]
> Microcode for [[LC3]]
