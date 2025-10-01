### Analysis

|                  | Best Case | Worst Case |
| ---------------- | --------- | ---------- |
| No occurrences   | $O(n)$    | $O(mn)$    |
| Single occurence | $O(m)$    | $O(mn)$    |
| All Occurencess  | $O(n)$    | $O(mn)$    |
### Pseudocode
```
bruteforce(text, pattern) {
	n = len(text)
	m = len(pattern)
	for n length substring in text from left to right {
		if current substring matches pattern { return current index } 
	}
	return pattern not found
}
```
