See [[LC3]]
When the [[CPU]] wakes up the [[Finite State Machine|FSM]] syarts running a loop that is called the [[Instruction Cycle]]

We can divide that loop in to six phases, each phase taking zero or more clock cycles. Only fetch and decode are mandatory.
* **FETCH**
* **DECODE**
* *EVALUATE ADDRESS*
* *FETCH OPERATORADS*
* *EXECUTE* 
* *STORE RESULT*

FETCH
* Cycle 1
	* MAR <- PC
	* GatePC, LD.MAR
* Cycle 2
	* MDR <- MEM\[MAR\]
	* MEM.EN, LD.MDR
* Cycle 3
	* IR <- MDR
	* GateMDR, LD.IR
Every other signal is low.