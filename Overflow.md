When you run out of places to keep the largest digit, the value overflows back to its smallest value.
e.g. 111 + 001 = 1000. However, if you only have 3 bits, then it goes to 0.

For [[2's Complement]], it's a bit more complicated.
e.g. 1100 + 1100 = 11000 -> 1000
1100 -> 1011 -> 0100 4
1000 -> 0111 -> 1000 8
so even though the bits do overflow in the basic binary sense, they are serving their [[2's Complement]] purpose as expected