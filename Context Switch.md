* Grab attention of processor
	* Preemptive: external interrupt, like timer
	* Nonpreemptive: system call (trap), I/O request, process exit
* Save the state of current process
	* Dump PC and registers of current process (at the start of the ready queue) into PCB
* Select new process to run
	* [[#Short Term Scheduler]] scheduling algorithm result -> select a PCB to "dispatch"
* Dispatch the selected process
	* Call [[Dispatcher]] for the closest [[Process Control Block|PCB]] in the Ready Queue, load state of the selected PCB into processor registers (PC, [[Register File]])

![[Pasted image 20250927154154.png|400]]
The scheduler does not call any process to run. Instead it rearranges the PCB queues and then returns to the first out of the queue.

# TLB
![[Translation Lookaside Buffer#Context Switching]]