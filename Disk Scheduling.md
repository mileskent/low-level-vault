* Do all requests in the same [[Hard Disk Drive#Cylinder]] before moving on
* Want to move between close cylinders
* Want to do requests that are closest to the [[Hard Disk Drive#Read/Write Head]] in the rotational time domain
* Disk scheduling used to be performed by the [[Operating System|OS]], now it is performed by the disk controller. All the OS does is enter the requests into a queue, which can be 31 length

# FCFS
"First Come First Serve"
Do the requests in the order that they arrive in.
![[Pasted image 20251127233120.png|300]]
# SSTF
"Shortest Seek Time First"
Perform the request that is closest to the head, i.e. has the shortest seek time.
![[Pasted image 20251127233301.png|300]]
# LOOK
Go in the same direction until no more requests in that direction.
Works like a real elevator.
![[Pasted image 20251127234514.png|300]]
# SCAN
LOOK, but always go to the top and bottom floors every trip.
So-called "elevator algorithm", but LOOK is more deserving of the title
![[Pasted image 20251127234206.png|300]]
# C-SCAN
SCAN, but you only service on the way up, then jump all the way to the bottom.
![[Pasted image 20251127234441.png|300]]
# C-LOOK
LOOK, but you only service requests in one direction, then jump all the way over in the other direction.
![[Pasted image 20251127234620.png|300]]
