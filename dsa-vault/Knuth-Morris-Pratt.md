A [[Pattern Matching Algorithm]] that preprocesses like [[Boyer-Moore]], but considers what has occured in the pattern and the text. 
* Main Idea: take advantage of matches and repetition in the text and pattern
* Creates Failure table, an integer array based on if the prefix and suffix of the substring match
	* What does the failure table mean?
		* If you have a pattern mask of length k, ending at the current character, you would need to just the pattern by k, in order to get the same pattern mask
		* The corresponding integer for each character of the pattern indicates "how much of your progress you get to keep".
		* k = FailTable\[index\] stores the length of the longest string that is both a prefix of the pattern and a proper suffix of pattern\[0...index)
		* The number shifts the pattern until it begins k characters before the mismatched location.
* KMP, unlike [[Boyer-Moore]], does not know if a mistmatching character from the text does not exist in the pattern at all, which means if it encounters a character not in the pattern, it will compare it against every character in the entire pattern in the worst case. However, this won't happen too often, as we are doing $O(1)^*$ work per character.
* Each shift is `(i, j) = (i is 0) ? (i + 1, 0) : (i + j - k, k)  
### Best Situation
Performs best for texts and patterns that have similar characters and repetition, e.g. DNA sequences.
### Analysis
For algorithm AND proprocessing 

|                  | Best Case  | Worst Case |
| ---------------- | ---------- | ---------- |
| No occurrences   | $O(m + n)$ | $O(m + n)$ |
| Single occurence | $O(m)$     | $O(m + n)$ |
| All Occurences   | $O(m + n)$ | $O(m + n)$ |
### Auxiliary Space Complexity
$\Omega(m)$
### Pseudocode
```
f: failureTable
matches = []
while i = 0 <= n - m  {
	while j = 0 < m {
		if mismatch {
			if index 0 { i++, j = 0 } // bc index -1 for failtable OOB
			else {
				// Skip checking first k characters of pattern against text
				k = failtable[index - 1]
				i += j - k
				j = k
			}
			break
		} else {
			j++
		}
	}

	// if there's a match, bc j got to the end of the pattern
	if (j == m) {
		matches.add(j)
		
		// Skip checking first k characters of pattern against text
		k = f[j - 1]
		i += j - k
		j = k
	}
}

failtable -> int[] {
	FailTable[j] stores the length of the longest string that is both a prefix
	of the pattern and an inclusive prefix to the current character
	e.g. abcdabcdabcaba -> 00001234567121
	int[] f = new int[m]
	if (m == 0) return f
	if (m == 1) f[0] = 0, return f

	int i = 0
	int j = 1

	while (j < m) {
		if (pattern[i] == pattern[j]) {
			f[j] = i + 1;
			i++;
			j++;
		} else {
			if (i == 0) {
				f[j] = i;
				j++;
			} else {
				i = f[i - 1];
			}
		}
	}

	return f;
}
```
