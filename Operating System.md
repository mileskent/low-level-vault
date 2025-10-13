---
aliases:
  - OS
---

Operating Systems are about sharing resources and protecting users from themeselves and others. Performing certain operations require *specialized knowledge* and *protection* which not every programmer knows or wants to know, so we abstract them in an Operating System Machine Layer. We transparently provide service to I/O devices and we notify user programs of unexpected situations. We provide *service routines* or *system calls* as part of the Operating System to safely and convieniently perform low-level, priviledged operations.
A partial abstraction on the [[Instruction Set Architecture|ISA]]. It rides on top of the ISA, but lets alot of it show through. You can run machine instructions from the OS, but not all machine instructions.
Subroutine library.
Does [[Scheduler|Scheduling]] and [[Discontinuities|Interrupt]] handling
The OS provides a number of abstractions:
* Multiple [[Process]]es (how can one physical processor run multiple programs at the same time?)
	* [[Scheduler|Scheduling]]
	* [[Scheduling Algorithm]]
	* [[Context Switch]]
	* [[Dispatcher]]
	* [[Loader]]
	* [[Memory Management|Memory Brokerage]]
* [[Memory]] permissions, to make sure you can't "step on other people's stuff"
* Shared access to I/O devices, e.g. networks, [[Filesystem]]s
* Resource sharing ([[Processor]]s, memory, I/O)
* Additional instructions (read, write, exit, [[sbrk]], change permissions) implemented through [[Discontinuities#Trap]]s