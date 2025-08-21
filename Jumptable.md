How a switch statement can be faster than "equivalent" if else chaining, but it of course depends upon the implementation of the [[Compiler]].
Get [[PC]] addresses to the locations of each case. Then jump the PC to the address of the given case very quickly. if else chaining, on the other hand, potentially has to evaluate every single boolean expression in the chain.

(Sometimes the compiler will convert if else chaining into a switch)