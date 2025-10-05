[[Memory]]
![[Pasted image 20251005012333.png|400]]
# Fence Register
Compare requested address to value of the fence register. 
* Only allows one process at a time
![[Pasted image 20251005012359.png|400]]
# Multifence
Example with P1
Has an upper and lower bound that is including in the [[Process Control Block|PCB]]
* At [[Loader|Load Time]]:
	* Find an available block of memory
	* Copy P1 into memory
	* Set LB and UB in the PCB
* At [[Dispatcher|Context Switch Time]]
	* Load LB, UB into registers
![[Pasted image 20251005013233.png|400]]

# Base + Limit
[[Relocatibility#Dynamically Relocatable]] because all addresses the CPU tries to access can be manipulated (offset) by the broker. Note that the CPU requests the [[Virtual Address]] and ultimately accesses the [[Physical Address]]
![[Pasted image 20251005014310.png|400]]

