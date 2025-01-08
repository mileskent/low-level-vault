"K Map"

|     | B'    | B     |
| --- | ----- | ----- |
| A'  | $X_0$ | $X_1$ |
| A   | $X_2$ | $X_3$ |

|     | B'  | B   |
| --- | --- | --- |
| A'  | 1   | 0   |
| A   | 1   | 0   |
$A'B' + AB'$

* In order to simplify, using a karnaugh map, you need to group a quantity of a power of 2 that is a rectangle (with wrapping).
* You don't want to group only wildcard values

|     | B'C'  | B'C   | BC    | BC'   |
| --- | ----- | ----- | ----- | ----- |
| A'  | $X_0$ | $X_1$ | $X_3$ | $X_2$ |
| A   | $X_4$ | $X_5$ | $X_7$ | $X_6$ |
* See [[Gray Code]] for this ordering
* Adjacency wraps around; the only input that doesnt change in a "square" is what the expression simplifies to