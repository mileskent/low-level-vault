In a C environment there are 3 files opened for you on predefined "streams", typically connected to your keyboard/display
* stdin -> Standard input
* stdout -> Standard output
* stderr -> Standard error output
	* Never buffered

Any other files must be opened and closed by calling a standard io routine
* flags for which can be either r, w, or a, each of which can also have + simulatanenously

Can write/read raw bytes if you want with `fread` and `fwrite`

`fclose` files

`fflush` to force output buffer to be flushed

`setvbuf` family of functions to set the buffering on a stream

If the program crashes, buffer contents may be lost
