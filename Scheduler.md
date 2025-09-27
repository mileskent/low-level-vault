---
aliases:
  - Scheduling
---
Scheduler is responsible for scheduling many [[Process|processes]]. This is called scheduling. 
![[Pasted image 20250927150123.png|400]]
Who gets to use the Processor at any given moment? Different processes will have different priorities. There are also properties enforced by system policies that affect the decision.

![[Pasted image 20250927151728.png|400]]
# Context Switch
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
# Loader
![[Loader]]
# Dispatcher
![[Dispatcher]]
# Long Term Scheduler
Determine whether a [[Program]] should be turned into a [[Process]].
"Do I have the resources to finish you?"
# Medium Term Scheduler
Deals with processes that already exist.
"Can I let you run efficiently? Should I put you on the backburner to let other more efficient processes finish first?"
# Short Term Scheduler
We already know we have enough resources to go around.
"Who gets to run next?"
The scheduler's job is to order the ready queue.

# CPU Burst
Continuous CPU Activity by a process before requiring an I/O operation
# I/O Burst 
Activity initiated by the CPU on an I/O device
# Ready Queue
Queue of PCBs that represent the set of memory resident processes that are ready to run on the CPU
# I/O Queue
Queue of PCBs that represent the set of memory resident processes that are waiting for some I/O operation either to be initiated or completed
# Thrashing
A phenomenon wherin the dynamic memory usage of the processes current in the [[#Ready Queue]] exceed the total memory capacity of the system. The system's resources have been overcommitted. The [[#Medium Term Scheduler]] would get involved and evict some [[Process Control Block|PCB]]s out of the Ready Queue. 

# Nonpreemptive Scheduling Algorithm
![[Nonpreemptive Scheduling Algorithm]]

# Preemptive Scheduling Algorithm
![[Preemptive Scheduling Algorithm]]

# Metrics
![[Pasted image 20250927155958.png]]
where $w_{i}, e_{i}, t_{i}$ are respectively the [[#Wait Time]], [[Performance#Execution Time]], and [[#Turnaround Time]] (elapsed time) for a job $j_{i}$
## Throughput
Jobs per second
## Turnaround Time
How long did this job take to complete after being requested?
### Average Turnaround Time
Average the turnaround times
## Wait Time
How long did this job take to start?
### Average Wait Time
Average the wait times
## Response Time
The turnaround time, but from a user centric perspective.
## CPU Utilization
Percentage of time the CPU is busy
## Starvation
User-centric metric that signfies denial of service to a particular process or set of processes due to some intrinsic property of the scheduler.
E.g. I put in a long job, and all my friends are spamming short jobs; [[#Shortest Job First]]
## Convoy Effect
User-centric metric that results in a detrimental effect to some set of processes due to some intrinc property of the scheduler.
E.g. I put in a long job, and all of my friends with short jobs have to wait; [[#First Come First Serve]]
