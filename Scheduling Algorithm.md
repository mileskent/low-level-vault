An [[Algorithm]] used by the [[Scheduler]]

| Name         | Property                                                                 | Scheduling criterion                                    | Pros                                                                                                                             | Cons                                                                                                   |
|---------------|--------------------------------------------------------------------------|----------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------|
| FCFS          | Intrinsically non-preemptive; could accommodate preemption at time of I/O completion events | Arrival time (intrinsic property)                        | Fair; no starvation                                                                         | High variance in response time; convoy effect                                                         |
| SJF           | Intrinsically non-preemptive; could accommodate preemption at time of new job arrival and/or I/O completion events | Expected execution time of jobs (intrinsic property)      | Preference for short jobs; provably optimal for response time; low variance in response times | Potential for starvation; bias against long running computations                                      |
| Priority      | Could be either non-preemptive or preemptive                             | Priority assigned to jobs (extrinsic property)            | Highly flexible since priority is not an intrinsic property; its assignment to jobs could be chosen commensurate with the needs of the scheduling environment | Potential for starvation (ameliorated by dynamically increasing priority in proportion to waiting time) |
| SRTF          | Similar to SJF but uses preemption                                       | Expected remaining execution time of jobs (intrinsic)     | Similar to SJF                                                                               | Similar to SJF                                                                                        |
| Round robin   | Preemptive allowing equal share of the processor for all jobs            | Time quantum (extrinsic)                                 | Equal opportunity for all jobs                                                              | Overhead for context switching among jobs                                                             |
# Preemptive
Algorithm that forcible takes the [[Processor]] away from the current scheduled [[Process]] in response to an external event (e.g. I/O completion [[Discontinuities#Interrupt]], timer interrupt)
## Shortest Remaining Time First
## Round Robin
## Priority
![[Round Robin]]
# Nonpreemptive
An algorithm that allows the current scheduled process on the [[CPU]] to voluntarily reliquish the processor (either by terminating or making an I/O system call)
### Intrinsic 
#### First Come First Serve
#### Shortest Job First
### Extrinsic
#### Priority


![[Linux#Linux Scheduler]]