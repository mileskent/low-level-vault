initializes the location of the command with a provided value

For example
```
(x3001) ~~~~~~~~ LABEL1 .fill 30
(x3002) ~~~~~~~~ LABEL2 .fill 31
```
x3001 in memory is filled with the value 30, x3002 is filled with 31. We put [[Label|labels]] for later access if needed, and .fill lines will usually look like this, but the use of labels isn't strictly neccessary.