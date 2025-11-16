A [[Pattern Matching Algorithm]] that improves upon the [[Brute Force Pattern Matching]] algorithm by changing how the pattern mask is shifted when it doesn't match. 
* Main Idea: Shift by more than one if we know we can safely; taking advantage of the mismatched characters
* We use *Simplified Boyer-Moore*. We only use bad character rule[^1].
	* A bad character is a character that does not appear in the pattern.

### Ideal Use Case
* It performs best when there are many characters in the text that do not occur in the pattern. 
* Note $\Omega(m)$ means 
### Analysis
n = len(text)
m = len(pattern)

|                  | Best Case    | Worst Case |
| ---------------- | ------------ | ---------- |
| No occurrences   | $O(m + n/m)$ | $O(mn)$    |
| Single occurence | $O(m)$       | $O(mn)$    |
| All Occurencess  | $O(m + n/m)$ | $O(mn)$    |
* The table takes $O(m)$
* The ideal scenario of the text having no common characters with the pattern is $O(n/m)$ as the pattern shifts entirely past each character (from the back of the pattern)
* The worst case could be if the pattern is "aa" and text is "aaaaaa", every text mask ($O(n)$) must be checked for each character in the pattern ($O(m)$), thus $O(mn)$

### Auxiliary Space Complexity
$\Omega(m)$
### Pseudocode
* Preprocesses the **pattern** to create a last occurence table, a hashmap of the last occurence of each letter
* Right to left in pattern
* When processing the text left to right
	* Mismatch
		* Case 1: Pattern can be shifted to align with the last occurence of the mismatching text character
		* Case 2: case 1 would result in a negative shift, so shift by one
		* Case 3: Character is not in pattern so shift the entire pattern past the mismatching text character
```
n = len(text)
m = len(pattern)

bm(text, pattern) {
	lot = lot(pattern)
	i = 0
	while i <= n - m {
		// Going backwards in the pattern, check if pattern match
		j = m - 1
		while j >= 0 && text[i + j] == pattern[j] { j-- }
		
		// Check if pattern found
		if j == -1 { i++ } 
		
		// text and pattern don't match, shift pattern all the way past
		else { 
			shift = last[text[i + j]]
			if shift < j { i = i + j - shift }
			else { i++ }
		}
	}
	return pattern not found
}

lot(pattern)-> hashmap { // O(m) - all cases
	for i [0, m - 1] { hashmap.put(pattern[i], i) }
	return hashmap
}
```


[^1]: but there are other things like good suffix and [[Galil Rule]]
