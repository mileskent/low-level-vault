* Bare Metal Programming
* No Operating System
* Makes [[C]] more obvious
* [GBA Reference](http://www.coranac.com/tonc/text)
* Simple Hardware
* Understand performance tradeoffs
* [[Von Neumann Model]]
	* I/O
		* DMA
		* Button Controller
		* Video Controller
		* Audio Controller
	* Memory
	* Processor
* RISC
* Datatypes
	* 8 bit char
	* 16 bit short
	* 32 int
* 32 bit address space


Memory Map
![[Pasted image 20250324161331.png|500]]
![[Pasted image 20250325143100.png|500]]
* 6 Display Modes
	* Bit Mapped
	* Tiled

### Light Up a Pixel
Talk to device registers
Screen is 240 columns, 160 rows
REG_DISPCTL at 0x04000000
`#define REG_DISPCTL *(volatile unsigned short int *) 0x04000000`
![[Pasted image 20250324161813.png|500]]
Video Memory starts at 0x60000000
Turn on the pixel at row 5, column 8
```
offset = 5 * 240 + 8*
pixel5_8 = *(unsigned short *) 0X6000000 + offset)
```
##### Color
Type of unsigned short
![[Pasted image 20250324162216.png|500]]
Note: BGR instead of RGB
### Button Input
10 buttons, 1 bit per button, contained in button register(s).
0 -> button down, 1 -> button up

### Graphics
###### HBlank and VBlank
![[Pasted image 20250325143434.png|400]]
If you are trying to change video memory while the system is rendering in vdraw, you get tearing. This is because you are changing the original instructions for what to draw (possibly) before they have actually finished executing.
Instead, wait for vdraw, then wait for it to end, in order to wait for vblank. Then change video memory during vblank.
![[Pasted image 20250325143832.png|500]]

###### Graphics Loop
```
init
loop {
	prevState = currentState
	checkButtons()
	currentState = calculateCurrentState()
	waitForVBlank()
	undraw(prevState)
	draw(currentState)
}
```
### Direct Memory Access
When drawing, for example, we have to copy from a source in memory to a buffer register and then into some destination location in memory.
Therefore we have **direct memory access** (DMA) which allows us to directly move data in memory. It is a hardware feature that allows for faster moving of memory.

### Font
2D arrays mapped to a table according to [[ASCII]] value.