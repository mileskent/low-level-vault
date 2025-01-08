# Memory Mapped I/O
![[Pasted image 20250330142101.png|600]]
### Keyboard
![[Pasted image 20250330140551.png|400]]
##### KBSR
xFE00
Keyboard status register
* Only uses 1 bit
* Bit 15 is set when a character is available
##### KBDR
xFE02
Keyboard display register
* Only uses 8 bits
* Read only
* Reading clears [[#KBSR]]

##### Read Characters from Keyboard
```
.orig x3000
ld r4, term
lea r2, buffer ; init buffer pointer
start ldi r1, kbsrA; see if char is there
	BRzp start ; "are we there yet" until character is present
	ldi r0, kbdrA ; get the character typed
	str r0, r2, 0 ; store it in buffer
	; terminate if they typed ctrl-z
		not r0, r0
		add r0, r0, 1
		add r0, r0, r4
		BRz quit
	add r2, r2, 1 ; inc buffer pointer
	BR start ; do it again
quit halt

term .fill x001A ; ctrl-z
kbsrA .fill xfe00
kbdrB .fill xfe02
buffer .blkw x0100
.end
```
### Display
##### DSR
xFE04
Display status register
* Transferring a character to DDR clears DSR
* When monitor is finished processing a character it sets DSR bit 15
* "Please sir, may I have another?"
##### DDR
xFE06
Display display register
* Transfer character to this address to print it on the monitor
##### Write string to display
```
.orig x3000
lea r2, buffer ; init buffer pointer

start ldr r0, r2, 0 ; r0 <- char
	brZ quit ; terminate on null
wait ldi r3, dsrA ; are we ready?
	brZP wait
	sti r0, ddrA ; send R0 to monitor
	add r2, r2, 1 ; inc buffer pointer
	br start ; loop
	
quit halt
dsrA .fill xfe04
ddrA .fill xfe06
buffer .stringz "Hello, World!"
.end
```
# Program Discontinuities
Handled by
* Save CPU state (Processor Status Register - PSR)
* Last 3 bits of PSR are NZP
* Raise CPU priviledge level
* Call [[Operating System]] routine
* Restore CPU State
* Restore Priviledge level
* Resume execution
### Interrupts
![[Pasted image 20250330143812.png|500]]
* An I/O device is reporting a completion or an error
* An *unscripted subroutine call*, triggered by an external event
* *Supervisor stack*, unique call stack for interrupts, different from user stack
* Every [[Fetch]], [[LC3]] polls for an interrupt
* Modifications to the hardware of the datapath and I/O, and additional software to allow an external device to cause the CPU to stop current execution of the original program
* Can be signficantly more efficient than polling
	* Useful in an environment where there are numerous devices and concurrent activities
	* Polling is better when there is a high likelihood of the CPU having nothing better to do
* The [[RTI]] is a priviliedged instruction that undoes what an interrupt or trap does, i.e. what the microcode does for an interrupt service routine or trap
	* Can only be executed in supervisor mode
### TRAPs
* A program-initiated interrupt
* The program is calling a priviledged [[Operating System]] subroutine, e.g. Read a line from a file
* Call trap with a argument that specifies which operation it should execute
##### Trap Vector Table

| Vector | Symbol | Routine                                                        |
| ------ | ------ | -------------------------------------------------------------- |
| x20    | GETC   | read a single character (no echo)                              |
| x21    | OUT    | output a character to the monitor                              |
| x22    | PUTS   | write a string to the console                                  |
| x23    | IN     | print prompt to console, read and echo character from keyboard |
| x25    | HALT   | halt the program                                               |
### Exceptions
* Something unanticipated has happened
	* Hardware error in the CPU or memory
	* Program error (illegal opcode, division by zero)


# LC3 Assembly
#todo