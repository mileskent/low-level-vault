^
$\oplus$
True when the inputs are different.

# Usage
a\^b\^b = a
* If there is an array with a single duplicate value, you can accumulate xor over the array to find the duplicate
* `dupe = accumulate(nums, xor)`

Swapping
```
a, b = b, a

EQUIV

a ^= b
b ^= a
a ^= b
```
