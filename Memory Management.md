---
aliases:
  - Memory Brokerage
  - Virtual Memory Management
  - Virtual Memory Brokerage
---

When there are multiple programs in [[Memory]], we must ensure processwise memory segregation, resource sharing, and abstraction of resource limitations (through [[Virtual Memory]])

# Memory Broker
![[Memory Broker]]
# Fence Register
* *Hardware Separation* of user and kernel space
* Compare requested address to value of the fence register. 
* Only allows one process at a time in the user space
* Stuck using one location in memory per process
* In kernel mode, the fence does nothing
![[Pasted image 20251005012359.png|400]]
# Multifence
Also: "Static Relocation Memory Management", so [[Relocatibility#Statically Relocatable]]
Have [[Process Control Block|PCB]]s to handle multiple processes
Example with P1
Has an upper and lower bound that is including in the [[Process Control Block|PCB]]
* At [[Loader|Load Time]]:
	* Find an available block of memory
	* Copy P1 into memory
	* Set LB and UB in the PCB
* At [[Dispatcher|Context Switch Time]]
	* Load LB, UB into registers
Poor memory utilization because cannot expand memory space of a process in real time if needed.
![[Pasted image 20251005013233.png|400]]

# Base + Limit
[[Relocatibility#Dynamically Relocatable]] because all addresses the CPU tries to access can be manipulated (offset) by the broker. Note that the CPU requests the [[Virtual Address]] and ultimately accesses the [[Physical Address]]
A [[Process]] running with Base + Limit believes that it is running at [[Address]] zero, but this is really just the virtual address, not the physical address.
![[Pasted image 20251005014310.png|400]]
When a process is allocated memory, the base register is set to the address of the memory region.

# Paging
![[Paging]]