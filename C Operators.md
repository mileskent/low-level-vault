| Arithmetic Operators     | Symbol | Operator                 | Description                                                                                      | Syntax  |
| ------------------------ | ------ | ------------------------ | ------------------------------------------------------------------------------------------------ | ------- |
|                          | +      | Plus                     | Adds two numeric values.                                                                         | a + b   |
|                          | –      | Minus                    | Subtracts right operand from left operand.                                                       | a – b   |
|                          | *      | Multiply                 | Multiply two numeric values.                                                                     | a * b   |
|                          | /      | Divide                   | Divide two numeric values.                                                                       | a / b   |
|                          | %      | Modulus                  | Returns the remainder after diving the left operand with the right operand.                      | a % b   |
|                          | +      | Unary Plus               | Used to specify the positive values.                                                             | +a      |
|                          | –      | Unary Minus              | Flips the sign of the value.                                                                     | -a      |
|                          | ++     | Increment                | Increases the value of the operand by 1.                                                         | a++     |
|                          | `--`   | Decrement                | Decreases the value of the operand by 1.                                                         | `a--`   |
| **Relational Operators** |        |                          |                                                                                                  |         |
|                          | <      | Less than                | Returns true if the left operand is less than the right operand. Else false                      | a < b   |
|                          | >      | Greater than             | Returns true if the left operand is greater than the right operand. Else false                   | a > b   |
|                          | <=     | Less than or equal to    | Returns true if the left operand is less than or equal to the right operand. Else false          | a <= b  |
|                          | >=     | Greater than or equal to | Returns true if the left operand is greater than or equal to right operand. Else false           | a >= b  |
|                          | ==     | Equal to                 | Returns true if both the operands are equal.                                                     | a == b  |
|                          | !=     | Not equal to             | Returns true if both the operands are NOT equal.                                                 | a != b  |
| **Logical Operators**    |        |                          |                                                                                                  |         |
|                          | &&     | Logical AND              | Returns true if both the operands are true.                                                      | a && b  |
|                          | \|     | Logical OR               | Returns true if both or any of the operand is true.                                              | a \| b  |
|                          | !      | Logical NOT              | Returns true if the operand is false.                                                            | !a      |
| **Bitwise Operators**    | Symbol | Operator                 | Description                                                                                      | Syntax  |
|                          | &      | Bitwise AND              | Performs bit-by-bit AND operation and returns the result.                                        | a & b   |
|                          | \|     | Bitwise OR               | Performs bit-by-bit OR operation and returns the result.                                         | a \| b  |
|                          | ^      | Bitwise XOR              | Performs bit-by-bit XOR operation and returns the result.                                        | a ^ b   |
|                          | ~      | Bitwise First Complement | Flips all the set and unset bits on the number.                                                  | ~a      |
|                          | <<     | Bitwise Leftshift        | Shifts the number in binary form by one place in the operation and returns the result.           | a << b  |
|                          | >>     | Bitwise Rightshilft      | Shifts the number in binary form by one place in the operation and returns the result.           | a >> b  |
| **Assignment Operators** |        |                          |                                                                                                  |         |
|                          | =      | Simple Assignment        | Assign the value of the right operand to the left operand.                                       | a = b   |
|                          | +=     | Plus and assign          | Add the right operand and left operand and assign this value to the left operand.                | a += b  |
|                          | -=     | Minus and assign         | Subtract the right operand and left operand and assign this value to the left operand.           | a -= b  |
|                          | *=     | Multiply and assign      | Multiply the right operand and left operand and assign this value to the left operand.           | a *= b  |
|                          | /=     | Divide and assign        | Divide the left operand with the right operand and assign this value to the left operand.        | a /= b  |
|                          | %=     | Modulus and assign       | Assign the remainder in the division of left operand with the right operand to the left operand. | a %= b  |
|                          | &=     | AND and assign           | Performs bitwise AND and assigns this value to the left operand.                                 | a &= b  |
|                          | \|=    | OR and assign            | Performs bitwise OR and assigns this value to the left operand.                                  | a \|= b |
|                          | ^=     | XOR and assign           | Performs bitwise XOR and assigns this value to the left operand.                                 | a ^= b  |
|                          | >>=    | Rightshift and assign    | Performs bitwise Rightshift and assign this value to the left operand.                           | a >>= b |
|                          | <<=    | Leftshift and assign     | Performs bitwise Leftshift and assign this value to the left operand.                            | a <<= b |
### Miscellaneous Operators
Apart from the above operators, there are some other operators available in C used to perform some specific tasks. Some of them are discussed here: 

###### sizeof
```
sizeof (operand)
```
- A **compile-time** unary operator which can be used to compute the size of its operand.
- The result of sizeof is of the unsigned integral type which is usually denoted by size_t.
- Basically, the sizeof the operator is used to compute the size of the variable or datatype.

###### comma
```
operand1 , operand2
```
- The comma operator (represented by the token) is a binary operator that evaluates its first operand and discards the result, it then evaluates the second operand and returns this value (and type).
- The comma operator has the lowest precedence of any C operator.
- Comma acts as both operator and separator. 

###### ternary/conditional
```
operand1 ? operand2 : operand3;
```
- The conditional operator is the only ternary operator in C++.
- Here, Expression1 is the condition to be evaluated. If the condition(Expression1) is __True__ then we will execute and return the result of Expression2 otherwise if the condition(Expression1) is __false__ then we will execute and return the result of Expression3.
- We may replace the use of if..else statements with conditional operators.

###### member operators
```
structure_variable . member;
```
and
```
structure_pointer -> member // same as (*structure_pointer).member
```

- Member operators are used to reference individual members of classes, structures, and unions.
- The dot operator is applied to the actual object. 
- The arrow operator is used with a pointer to an object.

##### cast
```
(new_type) operand;
```

- Casting operators convert one data type to another. For example, int(2.2000) would return 2.
- A cast is a special operator that forces one data type to be converted into another. 
###### pointer address of and dereference
```
&variable
```
and
```
*address
```
- Pointer operator & returns the address of a variable. For example &a; will give the actual address of the variable.
- The dereference operator * has the opposite effect. For example \*p will give the value that the pointer p points to. In a [[C Variable Management#Declaration|declaration]], it indicates that a variable is a pointer.
