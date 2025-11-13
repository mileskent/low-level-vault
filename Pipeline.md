Specifically [Instruction Pipelining](https://en.wikipedia.org/wiki/Instruction_pipelining). Pipelines are just an abstract technique.

5 Stages of a Pipeline
 1. IF (Instruction Fetch)
 2. ID/RR (Instruction Decode / Reset Register)
 3. EX (Execute)
 4. MEM (Memory Access)
 5. WB (Write Back)
 
 Responsibilities of Each Stage
 1. IF - fetch instruction in IR and increment PC
 2. ID/RR - decode and read register contents
 3. EX - performan arithmetic/logic if needed, address computation if needed
 4. MEM - fetch/store memory operand if needed
 5. WB - write to register if needed

The opcode is passed through ALL buffers because it encodes what the appropriate datapath actions are for next stage
It is stored at the beginning of ALL buffers
![[Pasted image 20251007165740.png|400]]

| Buffer | Who's Output? | Contents                                                                                                                              |
| ------ | ------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| FBUF   | IF            | Essentially contains the IR                                                                                                           |
| DBUF   | ID/RR         | Decoded IR and values read from<br>register file                                                                                      |
| EBUF   | EX            | Primarily contains result of ALU<br>operation plus other parts of the<br>instruction depending on the<br>instruction specifics        |
| MBUF   | MEM           | Same as EBUF if instruction is not<br>LW or SW; If instruction is LW,<br>then buffer contains the contents<br>of memory location read |
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

## Pipeline Stall
This example is a [[#Structual Hazard]] because there are not enough resources in the pipeline to avoid serialization at station III. There is partial serialization in this pipeline due to the hazard. A stall can be caused by any hazard.
![[Pasted image 20250920134433.png|500]]
![[Pasted image 20250920134507.png|500]]
This results in a [[NOOP]] [[#Bubble]] propogating down the pipeline. You can also solve this by adding more hardware.
### Bubble
* [[NOOP]] "Bubbles" propogate through the buffers of pipeline stages downstream of the one taking more than more cycle, during a [[#Pipeline Stall]].
* A [[Compiler]] will try to optimize the order of expressions to minimize bubbles in the pipeline

# Hazard
* Hazards result in serialization, aka slowing down
* The longer the pipeline, the larger the potential maximum hazard slowdown
## Structual Hazard
Structual hazards are caused by hardware limitations.
For example, if BEQ branches, we have to use the ALU twice! If we only have one ALU in the datapath for EX, then all the insructions behind the BEQ in the pipeline have to wait for it, as it cycles twice in EX.

## Data Hazard
When pipelining destroys the serial semantics of a program. 
* Program limitations, mismatch between pipelining and serial external appearance of program
* When pipelined (i.e. out of serial order) execution leads to semantic violations. The next instruction may clobber the information needed for intermediate calculations of the current instruction.
### Read After Write
(RAW)
True dependency
$I_{1}: R_{\color{red}\mathbf{1}} =R_{2}+R_{3}$
$I_{2}: R_{4} =R_{\color{red}\mathbf{1}}+R_{5}$
![[Pasted image 20250920140006.png|400]]
### Write after Read
(WAR)
Antidependency
$I_{1}: R_{4} =R_{\color{red}\mathbf{1}}+R_{5}$
$I_{1}: R_{\color{red}\mathbf{1}} =R_{2}+R_{3}$
### Write after Write
(WAW)
Output dependency
$I_{1}: R_{\color{red}\mathbf{1}} =R_{2}+R_{3}$
$I_{2}: R_{\color{red}\mathbf{1}} =R_{4}+R_{5}$
## Control Hazard
Changes to the control flow of a process, e.g. branching.

"Branches cause disruption to the normal flow of control and are detrimental to pipelined processor performance"

# Busy Bit
* Each [[Register]] in the [[Register File]] gets a bit called the "Busy Bit". 
* A register's busy bit is set when it is not yet ready to be accessed. 
* Any instruction that is not yet executing whose registers have a least one busy bit must wait for the currently executing instruction to finish before proceeding down the pipeline.
* ID/RR sets the busy bit, WB resets it
# Register Forwarding
* RP (read-pending) signal associated with each register to indicate an instruction is stalled in ID/RR for this register value
* if RP { use forwarded value } else { read entry from DPRF }
* The forwarded value is passed back from the deeper, associated instruction to the one in ID/RR if applicable
* Eliminates all [[#Bubble|Bubbles]] caused by [[#Read After Write]] hazards for all instructions that get their result in EXEC
	* for LW, you have to wait for it to get its result from MEM, so you get an EXEC bubble
* Faster than [[#Busy Bit]] because you avoid [[#Pipeline Stall|stalling]], but more complicated

![[Branching#Pipelined Branching]]
# Discontinuities
See [[Discontinuities]].
An interrupt can occur at any time.
Any one of the instructions in the pipeline can cause a discontinuity.
* When do we take the interrupt?
	* We could stop, drain the pipeline, then go to the interrupt state
		* Slow
	* Look for external INT in a specific stage (e.g. EX state)
		* DRAIN preceding stages
		* FLUSH subsequent instructions


# Virtual Memory
A pipelined processor with [[Virtual Memory]] will experience major inefficiencies in its naive implementation; Every memory access requires two memory accesses: accessing the page table entry, followed by the actual memory word. This is awful for our pipeline because all memory accesses introduce bubbles. Additionally, there is one bubble for every instruction because we have to access page table entries in our fetch stage.
![[Paging#Broker]]
The entire page table is not going to fit in registers. And even if they did, we would have to reload all of them every [[Context Switch]]
However, we definitely can fit a subset of those entries in registers.
Putting some entries in a subset register file actually works well due to [[Locality]]. 
![[Locality]]

Use a [[Translation Lookaside Buffer]] for this subset of the [[Page Table]]
![[Translation Lookaside Buffer#Usage]]

# Pipeline with Caches
Instructions and data have separate caches.
![[Pasted image 20251026005457.png]]

# See also
[[Latency]] vs [[Throughput]]

