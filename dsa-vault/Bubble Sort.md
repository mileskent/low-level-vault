Bubbles larges element to end of array for each iteration
Total shit algorithm. Every single other algorithm is better than this, for any use case.
![[Pasted image 20250310205458.png|500]]
### Evaluation

|             | Best Case | Average Case | Worst Case | [[Stable]] | [[Adaptive]] | [[In-place]] |
| ----------- | --------- | ------------ | ---------- | ---------- | ------------ | ------------ |
| Bubble Sort | $O(n)$    | $O(n^2)$     | $O(n^2)$   | Yes        | Yes          | Yes          |
### Pseudocode
```
stopIndex := array.length - 1
while stopIndex not zero {
	i := 0
	lastSwappedIndex
	while i < stopIndex {
		if array[i] > array[i + 1]
			swap elements at i, i + 1
			lastSwappedIndex := i
		i++
	}
	stopIndex := lastSwappedIndex
}
```

### See Also
[[Sorting Algorithms]]