You can have an number as your base system. However, binary, i.e. base 2, is extremely advantageous in the case of computing, as a given bit (binary digit), can be represented by a signal being on or off. Basic binary decimal representation is what we call an unsigned integer.
e.g. $1011_2$ is the following is decimal
$$1 \cdot 2^3 + 0 \cdot 2^2 + 1 \cdot 2^1 + 1 \cdot 2^0$$

### Unsigned Integer
Mathematical base 2.
### Signed Integer
Base 2, but the sign needs to be encoded.
##### [[Signed-Magnitude]] (Naive Approach)
Leading 1 encodes sign. Remaining bits encode magnitude. Very ugly for math.
##### [[2's Complement]]
Nonnegative integers represented the same way as unsigned integers.
Negative integers "wrap around", so 1 + the maximum positive integer wraps around to the smallest negative integer.
Avoids 0 having two representations.

## Decimal to Binary Conversion
##### Long way
1. Find largest power of 2 that fits into the number
2. Note that power of 2
3. Subtract from number
4. Repeat until all bits noted
##### Faster way
1. Note parity
2. Integer divide by 2
3. Repeat
4. Odd -> 1, Even -> 0
5. Bit produced in reverse order

> [!Example]- Examples
> 7. 563 is odd -> 1
> 8. 562 / 2 = 281 is odd -> 1
> 9. 140 is even -> 0
> 10. 70 is even -> 0
> 11. 35 is odd -> 1
> 12. 34 / 2 = 17 is odd -> 1
> 13. 16 / 2 = 8 -> 0
> 14. 8 / 4 = 2 -> 0
> 15. 2 / 2 = 1 -> 1
> The digits are produced in reverse order.
> 100110011
> 
> 43 -> binary
> 43 1
> 21 1
> 10 0
> 5 1
> 2 0
> 1 1
> 101011
> 14 -> binary
> 8 + 4 + 2
> 001110

### Addition and Subtraction
Use [[2's Complement]] signed representation
* When adding $a$ and $b$, just add them 😳
* When subtracting $b$ from $a$ just add $a$ and $-b$
