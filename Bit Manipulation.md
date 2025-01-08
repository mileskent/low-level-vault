#### Change sign
```
~x++
-x
```
#### 0x1000 -> 0x0111
```
~(-x)
x - 1
```

#### Set at i
```
x | (1 << i)
```

#### Clear at i
```
x & ~(1 << i)
```
#### Toggle at i
```
x ^ (1 << i)
```

#### XOR
```
(x & ~y) & (~x & y)
x ^ y
```
