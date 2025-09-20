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
Hardware limitations
## Data Hazard
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
Program limitations, dealing with branches

# Busy Bit
* Each [[Register]] in the [[Register File]] gets a bit called the "Busy Bit". 
* A register's busy bit is set when it is not yet ready to be accessed. 
* Any instruction that is not yet executing whose registers have a least one busy bit must wait for the currently executing instruction to finish before proceeding down the pipeline.
* ID/RR sets the busy bit, WB resets it
# Register Forwarding
* logic in ID/RR: RP ? use forwarded value : read entry from DPRF
* The forwarded value is passed back from the currently executing instruction to the one in ID/RR if applicable
* Eliminates [[#Bubble|Bubbles]] caused by [[#Read After Write]] hazards for all instructions that get their result in EXEC (so LW has bubbles)
* Faster than [[#Busy Bit]] because you avoid [[#Pipeline Stall|stalling]], but more complicated
# See also
[[Latency]] vs [[Throughput]]