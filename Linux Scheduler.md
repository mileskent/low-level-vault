* Market
	* Interactive Desktop, Server
* Goals
	* Efficiency, interactivity, real-time, no [[Scheduler#Starvation]]
* 3 Classes of [[Process|tasks]]
	* Real-time [[Scheduling Algorithm#First Come First Serve]], Real-time [[Scheduling Algorithm#Round Robin]], Timeshared
	* 140 Priority; basically has 140 [[Scheduler#Ready Queue]]s
		* 0-99 for real-time; remaining for timeshared
		* Carrot and Stick approach
			* Reward Good behavior
			* Punish bad behavior
			* Reward interactive I/O by increasing priority
			* Punish compute bound tasks by decreisng priority
		* Starvation Threshold
			* Set a time interval (starvation goal) for the threshold waiting time that determines a process is being starved by higher priority processes
			- When starvation occurs, give the process a time slice at the highest interactive priority
* Winner is the first task in the highest priority list in the active array
* If the task blocks (due to I/O) put it aside and pick the next highest one to run
* If the time quantum runs out (doesn't apply to real time tasks) for the current task, place it in the expired array
* On I/O completion, place the relevant task in the active array at the right priority level, having adjusted its remaining time quantum
* When the active array is empty, flip the active and expired array pointers and continue with the scheduling algorithm (i.e. the expired array becomes the active array and vice versa).
* This scheduler is O(1)
![[Pasted image 20251005011119.png]]