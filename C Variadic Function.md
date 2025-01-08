For example, `printf` can have a variable amount of arguments. 
* Must have at least one argument in the call and prototype, and they must be of the same type

> [!Example]
> A function that prints a variable amount of arguments. 
> Va expressions are macros
> In this example, we print until we hit a negative int (this is an arbitrary choice)
> ```
> void printargs (int arg1, ...) {
> 	va_list ap
> 	int i;
> 	va_start(ap, arg1);
> 	for (i = arg1; i >= 0; i = va_arg(ap, int)) {
> 		printf("%d ", i);
> 	}
> 	v_end(ap);
> }
> ```