Literally just a compile-time text substitution. Often used for constants.
* `gcc -E` will show you the preprocessed input file with all the include and macros expanded

Can also be used in more complex (and confusing/hard to trace/easy to mess up) ways:
```
#define MULT(a, b) = ((a)*(b))
// 3 * ((2+3)*(3)) = 45
// Problems without partheses
int main(void) {
	printf("%d\n", 3 * MULT(2 + 3, 3))
}
```

Another example of bad behavior
```
#define MAX(x,y)     (x > y ? x : y)
```
```
int highest = MAX (v1++, v2++); // int highest = (v1++ > v2++ ? v1++ : v2++); // clearly not intended
```
### See also
[[C]]