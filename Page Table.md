A [[Map]] from [[Virtual Address]] to [[Physical Address]] of Pages, used by the [[Memory Management#Memory Broker]]
$n$ [[Process]]es requires $n$ Page Tables
Where page tables live in memory:
![[Pasted image 20251012222556.png|200]]
Use a register PTBR to hold the base physical address of the page table for the currently running process. Put this value in the [[Process Control Block|PCB]]
## Demand Paging
![[Pasted image 20251014212152.png|400]]
If the [[Memory Management#Memory Broker|Broker]] tries to access a Page that is not valid, it will throw a [[Page Fault]]