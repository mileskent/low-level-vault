ROM stands for Read-only Memory and as its name suggests it is a piece of memory that can only be read.Each memory address will hold an entry that represents a micro-state. This entry holds two crucial pieces ofinformation: 1) what signals to assert on the datapath for a specific micro-state and 2) what the next stateshould be. Now we have a way to encode the output bits (the datapath signals) and next state (the nextmicro-state) for each micro-state in a binary string. As long as we know the appropriate memory address,we can now read from the ROM to obtain the binary string for a specific micro-state.

![[Pasted image 20250209153845.png]]

Holy Dancing Crab!
