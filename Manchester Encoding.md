[[Ethernet]] coax signaling uses this, which is a scheme that guarantees at least one voltage transition during each clock tick.
![[Pasted image 20251118165341.png|500]]
$$
\text{Manchester} = \text{Data}\ \oplus\ \text{Clock}
$$
* The signal is an [[XOR]] between the inputs
* Bits are encoded as transitions between low and high voltage.
* The clock pulses twice for every bit to be encoded, at the beginning of the window, and in the middle of the time window for that bit.
* Since every bit must have a transition in the middle, the receiver can easily extract the timing from the data stream itself
	* The ethernet preeamble is used to sync the receiving devices to the cycle speed of the signal.