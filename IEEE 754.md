System for representing [[Floating Point]] values; kind of scientific notation with extra steps
#### What it looks like
For a 32 bit floating point.

| 32   | 31 - 23  | 22 - 0                 |
| ---- | -------- | ---------------------- |
| 0    | 00000000 | 0000000000000000000000 |
| Sign | Exponent | [[Mantissa]]           |
| $S$  | $E$      | $M$                    |
$$\left(\ (-1)^S \cdot 1.M ) << (E - 127_{10})\ \right)_2 $$
#### Special Cases

|        | E == 0                             | 0 < E < 255      | E == 255           |
| ------ | ---------------------------------- | ---------------- | ------------------ |
| M == 0 | 0                                  | Powers of 2      | $\infty$           |
| M != 0 | non-normalized, typically overflow | Ordinary numbers | Not a number (NaN) |
