A [[Map]] from [[Virtual Address]] to [[Physical Address]] of Pages, used by the [[Memory Management#Memory Broker]]
$n$ [[Process]]es requires $n$ Page Tables
Where page tables live in memory:
![[Pasted image 20251012222556.png|200]]
![[Pasted image 20251016211140.png]]
# PTBR
PTBR holds the base [[Physical Address]] of the current proccess' page table
* Put this value in the [[Process Control Block|PCB]]

## Demand Paging
![[Pasted image 20251014212152.png|400]]
If the [[Memory Management#Memory Broker|Broker]] tries to access a Page that is not valid, it will throw a [[Page Fault]]