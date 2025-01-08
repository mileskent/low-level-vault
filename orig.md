Where to start placing the instructions in memory. Instructionss within the block are placed within the [[LC3]]'s [[Memory]] contiguously, in the order they appear, starting at the argument for .orig, e.g. x3000, x4000.

```
.orig x3000
...
.end

.orig x4000
...
.end
```