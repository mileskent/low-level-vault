Note that "Job" and "Task" are vague terms usually used synonymously with process.
A [[Program]] that is being executed; program + state
![[Pasted image 20250927150711.png|200]]

We can also split this view more finely as follows, into program + memory state + [[Processor]] state + [[Thread]] of control.
![[Pasted image 20250927150809.png|200]]

We can generalize this so that for every additional processor you have, you can just add another processor state and thread of control to the representation.
![[Pasted image 20250927151105.png|200]]

# [[Operating System|OS]] Implementation
Each process gets its own representation as a [[Process Control Block]] in the [[Scheduler#Ready Queue]] or [[Scheduler#I/O Queue]] 
Each process gets its own user [[Stack]] accessible through a stack pointer
Each process gets its own [[Kernel]] stack, which holds [[Activation Record]]s, accessible through a stack pointer
![[Pasted image 20251005002821.png|400]]
Create a new process by:
* Getting a fresh PCB and address space
* Load the program into the address space
* Construct a sched() and interrupt frame on top of the new kernel stack that goes along with that PCB, that has a return address of user mode and address 0
* link PCB into Ready Queue
* Call [[Scheduler]]
* When our PCB reaches the head of the Ready Queue and is [[Dispatcher|Dispatched]], the scheduler will return and using the new process' state which means that sched() will "return" to the first instruction of the program

![[Scheduler#Context Switch]]