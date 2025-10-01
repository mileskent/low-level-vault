Find the longest common subsequence between 2 strings. 
* A subsequence must be in their original order, but are not neccessarily contiguous.
* [[Dynamic Programming]] because the previous max lengths are stored in a matrix, and the new max common lengths are determined from these stored values, reducing total computation

![[subsequence_grid-2270750513.gif|250]]

### Efficiency
$$
O(mn)
$$
where m and n are the lengths of each string, respectively
### Implementation
Recursive solution for original reasoning. Suffers the same poor [[Time Complexity]] as the recursive solution from [[Dynamic Programming#Fibonacci Sequence Example]]
```
LCS(s1: Str, s2: Str) {
	return LCShelper(s1.length, s2.length);
}

LCShelper(int i, int j) {
	// Base Case
		return 0

	if s1[i] == s2[j]
		return LCShelper(i - 1, j - 1) + 1
	else
		return max(LCShelper(i - 1, j), LCShelper(i, j - 1))
}
```

[[Dynamic Programming]] solution
* The point is to eliminate redudant calls from the call stack that occur in the above solution. The [[Set]] of all recursive calls from the bad solution is the same as entries of the matrix used in the DP solution
	* A given i, j entry of the matrix 
		* is the LCS of 0-i rows and 0-j columns, i.e. `L[i][j] = LCShelper(i, j)`
		* where `LCShelper(i, j)` is from above
		* note how the recursive calls above exactly match with the assignment to the matrix below
	* The users only cares about LCS(s1.length, s2.length), which is the bottom right of the matrix
	* Note index 0 for the columns and rows is the empty string, and the subsequence of any string with "" is 0. This means that all of row 0 and all of column 0 are 0s
* When tracing, you trace the arrows from the bottom right, backwards. Whenever you go diagonally, note, the corresponding character, which is in the subsequence.
```
LCS (s1: Str, s2: Str) {
	L[][] = int[n + 1][m + 1]
	Fill all row, column 0 with 0s
	For j in [1, m] {
		For i in [1,n] {
			if s1[i] == s2[j] {
				L[i][j] = 1 + L[i - 1][j - 1] // aboveleft
			} else {
				L[i][j] = max(L[i][j - 1], L[i - 1][j]) // left, above
			}
		}
	}

	The number in the bottom right corner
	is the length of the subsequence 
	
	Traceback through the matrix starting
		from the bottom right corner {
		Every diagonal trace corresponds
		to a letter in the common subsequence
	}
}
```

### Example
ransack (7), abacus (6)
Recall: top left if match, max of left and top if mismatch

|     | ""  | r   | a   | n   | s   | a   | c   | k     |
| --- | --- | --- | --- | --- | --- | --- | --- | ----- |
| ""  | 0   | 0   | 0   | 0   | 0   | 0   | 0   | 0     |
| a   | 0   | 0   | 1   | 1   | 1   | 1   | 1   | 1     |
| b   | 0   | 0   | 1   | 1   | 1   | 1   | 1   | 1     |
| a   | 0   | 0   | 1   | 1   | 1   | 2   | 2   | 2     |
| c   | 0   | 0   | 1   | 1   | 1   | 2   | 3   | 3     |
| u   | 0   | 0   | 1   | 1   | 1   | 2   | 3   | 3     |
| s   | 0   | 0   | 1   | 1   | 2   | 2   | 3   | **3** |
