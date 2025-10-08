![[Pasted image 20251008143728.png|200]]
* Round Robin is a [[Scheduling Algorithm#Preemptive]] [[Scheduling Algorithm]]
* Requires a timer interrupt
* When a processes starts, it is given a **time quantum** (time slice) which limits the continuous CPU time it may use
* When a process is dispatched, the timer is set to interrupt at the end of the remaining time quantum
* If a processes uses up its remaining time quantum
	* The process is interrupted
	* The scheduler is called to put the process at the end of the ready list
	* The process' remaining time quantum is reset
* If an interrupt other that the timer occurs, the process' remaining time quantum is reduced by the amount of time it has used prior to the interrupt