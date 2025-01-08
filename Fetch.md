[[LC3]] [[Macrostate]]
3 Clock Cycles
Gets the next instruction from [[Memory]] and puts it in the [[Instruction Register]]

### Fetch 1 (MAR <- PC, ++PC)
* GatePC = 1
* LD.MAR = 1
* PCMux = 00 (inc)
* LD.PC = 1
### Fetch 2 (MDR <- mem\[MAR\])
* MEM.EN = 1
* LD.MDR = 1
### Fetch 3 (IR <- MDR)
* GateMDR = 1
* LD.IR = 1

### See also
[[LC3#Datapath]]
