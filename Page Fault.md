An exception (/trap/interrupt) that the [[Memory Broker]] raises when a process tries to access a [[Virtual Address]] whose [[Paging#Page Frame]] is not currently resident in [[Physical Memory]], in [[Paging#Demand Paging]].

Invokes [[Replacement Algorithm]] to get space for the page it tried to access.
* Many many page faults per second don't neccessarily indicate [[Scheduler#Thrashing]]; thrashing implies too many page faults, but too many page faults don't always imply thrashing. Applications can be changing the page in use without changing their [[Virtual Memory#Working Set]] size for instance. Rather you'd look for [[Memory Pressure]] being greater than the number of available page frames, high paging rate, low CPU utilization, unresponsive paging I/O

* Page faults are very disruptive, and should therefore be limited as much as possible
	* From a [[Process]] point of view
		* implicit I/O
	* From a [[Scheduler#CPU Utilization]] perspective
		* Overhead that doesn't contribute to work


# Pipeline
* IF can cause page faults. After this we have to let the [[Pipeline]] drain. This is slow
* MEM can cause page faults, flush all previous stages including MEM

# Page Fault Handler
* Find free [[Paging#Page Frame]]
	* See [[Replacement Algorithm]]
* Load the faulting [[Paging#Virtual Page]] from [[Storage|disk]] into the page frame (slow)
	* Done through [[Disk Map]]
* Give up the [[CPU]] while waiting for the paging I/O to complete
* Update the [[Paging#Page Table]] entry of the faulting page
* Link the [[Process Control Block|PCB]] of the [[Process]] back in the [[Scheduler#Ready Queue]] of the [[Scheduler]]
* Call the Scheduler

A [[Freelist]] can be used to link free [[Frame Table]] entries together
![[Pasted image 20251014215653.png|400]]
Possible metadata in [[C]] for a frame
```
union pframe {
    struct {
        char state;
        address PFN;
        PCB *PID;
    } filled;
    struct {
        char state;
        union pframe *next;
    } empty;
};
```