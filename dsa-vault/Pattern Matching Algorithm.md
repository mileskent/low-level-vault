An algorithm that locates a pattern within a string. 
* Variations include finding the *first occurence* and *all occurences*.
* n = len(text)
* m = len(pattern)
* Algorithms
	- [[Brute Force Pattern Matching]]
		- Intuitive and simple
		- Not efficient
	- [[Boyer-Moore]]
		- Preprocesses the pattern
	- [[Knuth-Morris-Pratt]]
		- Preprocesses the pattern
	- [[Rabin-Karp]]
		- Reduces the problem to integer matching, going for a [[LSD Radix Sort]] kind of approach

|                 |                  | Best Case    | Worst Case |
| --------------- | ---------------- | ------------ | ---------- |
| **Brute Force** | No occurrences   | $O(n)$       | $O(mn)$    |
|                 | Single occurence | $O(m)$       | $O(mn)$    |
|                 | All Occurencess  | $O(n)$       | $O(mn)$    |
| **Boyer-Moore** | No occurrences   | $O(m + n/m)$ | $O(mn)$    |
|                 | Single occurence | $O(m)$       | $O(mn)$    |
|                 | All Occurencess  | $O(m + n/m)$ | $O(mn)$    |
| **KMP**         | No occurrences   | $O(m + n)$   | $O(m + n)$ |
|                 | Single occurence | $O(m)$       | $O(m + n)$ |
|                 | All Occurencess  | $O(m + n)$   | $O(m + n)$ |
| **Rabin-Karp**  | No occurrences   | $O(m + n)$   | $O(mn)$    |
|                 | Single occurence | $O(m)$       | $O(mn)$    |
|                 | All Occurencess  | $O(m + n)$   | $O(mn)$    |
