Note that "Job" and "Task" are vague terms usually used synonymously with process.
A [[Program]] that is being executed; program + state
![[Pasted image 20250927150711.png|200]]

We can also split this view more finely as follows, into program + memory state + [[Processor]] state + [[Thread]] of control.
![[Pasted image 20250927150809.png|200]]

We can generalize this so that for every additional processor you have, you can just add another processor state and thread of control to the representation.
![[Pasted image 20250927151105.png|200]]