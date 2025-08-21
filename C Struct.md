Compositive data type that has only public member variables. In C, (unlike C++) this is its only functionality.

### Syntax
```
struct <optional name> {
	<type declaration>;
	<type declaration>;
	...
} <optional variable list>
```
The struct tag names the type, e.g.
```
struct car {
	char model[100];
	int year;
}
```
Names following the struct tag *define* instances of the struct, i.e. allocate memory for the instances:
```
struct car car1, car2;
```
or all in one block
```
struct car {
	char model[100];
	int year;
} car1, car2;
```
or like the following where the struct car and instance car are in difference namespaces
```
struct car {
	char model[100];
	int year;
} car;
```
Note that this is invalid; we are assigning an array to another array, which will cause a compiler error because the character array is a const character pointer, which is thus immutable.  
```
car.model = "Ford"; // problem line
car.year = 1972;
```
But this is valid, because the compiler recognizes what is happening.
```
car = {"Ford", 1972};
```

### Storage
![[Pasted image 20250403162407.png|500]]
* Rule 1: Members are stored in the same order as they are initialized in source code
	* Even if it is not optimal, like in this example
* Rule 2: Datatypes must be aligned on a multiple of their size. 
	* Think about how pointer arithmetic works. You want data to be aligned on natural boundaries. If you don't do this you need hardware to handle it.
	* If the character array came first, we would not waste bytes on filler for maintaining natural alignment
	* We align it in this way, sacrificing space for time
* Rule 3: The struct is filled out to the end to meet the most strict alignment of its members. 
	* In this case of `int` which is 4 bytes. This is because: imagine what happens if we need to make an array of this struct. 
	* The size of this struct is 4 x 7
Note: [[Compiler]] maintains a list of the members, their types, and an offset from the beginning of the struct

> [!Example] Another Example
What is the size of struct a?
> ```
> struct a {
> 	char x, y;// sizeof char = 1 byte
> 	int a, b; // sizeof int = 4 bytes
> 	double d; // sizeof double = 8 bytes
> 	char z;   // sizeof char = 1 byte
> }
> ```
>
>> [!Solution]-
>> * x and y each take 1 byte
>> 	* allocated 2 bytes so far
>> * a and b must be aligned on 4 byte multiple so we need 2 bytes of filler before we start a
>> 	* allocated 2 + 2 = 4 bytes so far
>> * a and b each take 4 bytes
>> 	* allocated 4 + 8 = 12 bytes so far
>> * d must be aligned on a multiple of 4 bytes, and we have allocated 12 so far, so we need 4 bytes of filler
>> 	* allocated 12 + 4 = 16 bytes so far
>> * d takes 8 bytes
>> 	* allocated 16 + 8 = 24 bytes so far
>> * z takes 1 byte
>> 	* allocated 24 + 1 = 25 bytes so far
>> * Per Rule 3: allocate 7 bytes to get to a multiple of the strictest size, which is double, 8 bytes
>> 	* allocated 25 + 8 = 32 bytes
>> * Answer is 32 bytes