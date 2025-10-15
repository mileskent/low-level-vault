An exception(/trap/interrupt) that the [[Memory Management]] unit raises when a process tries to access a [[Paging|Page]] without proper preparations, in [[Paging#Demand Paging]]

* In a [[Pipeline]]
	* IF can cause page faults. After this we have to let the pipeline drain. This is slow
	* MEM can cause page faults, flush all previous stages including MEM

# Page Fault Handler
* Find free [[Paging#Page Frame]]
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