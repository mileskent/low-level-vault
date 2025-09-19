# Bill's Sandwich Shop Analogy
The figure is an analogy for a pipeline. As opposed to one worker making all sandwiches, tasks are delegated as one task per employee. Each employee hands off their current sandwich down the line, along with an order form. In this organization, all stations will fill up, and there will be one sandwich per cycle instead of per 5 cycles. Another analogy for what this is like is a hose. You turn on the faucet and after a brief while, you get a continous stream of water.
![[Pasted image 20250918224333.png|500]]
* Some stages don't do anything for some orders
* Each stage works on a different instruction, in parallel
* Each stage passes two things to the next
	* The order form
		* This is equivalent to the IR
	* A partially assembled sandwich
		* This is equivalent to intermediate results
* Unequal division of labor causes backups

Accordingly, you can imagine how you could implement this pipelining for the macrostates.
![[Pasted image 20250918225405.png|500]]
![[Pasted image 20250918225519.png|500]]

And this is how it would actually work.
![[Pasted image 20250918225900.png|500]]
IF - fetch instruction in IR and increment PC
ID/RR - decode and read register contents
EX - performan arithmetic/logic if needed, address computation if needed
MEM - fetch/store memory operand if needed
WB - write to register if needed

Each stage is separated by registers, which are called "buffers" in this context, because they buffer between stages
![[Pasted image 20250918230521.png|500]]

| Stage | Units in Use       |
| ----- | ------------------ |
| Fetch | ALU, PC, MEM       |
| ID/RR | RegF, Decode logic |
| EXEC  | ALU                |
| MEM   | MEM                |
| WB    | RegF               |
Conclusion: we need a deticated datapath for each stage.
![[Pasted image 20250918230822.png|500]]
# See also
[[Latency]] vs [[Throughput]]