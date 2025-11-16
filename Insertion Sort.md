Assume the elements before the current index are sorted. Insert the next element in the remaining dataset into the correct place in the sorted data.
*Iterative Sorts are generally **bad** unless the data set is relatively small*
![[Pasted image 20250310205601.png|500]]
### Evaluation

|                | Best Case | Average Case | Worst Case | [[Stable]] | [[Adaptive]] | [[In-place]] |
| -------------- | --------- | ------------ | ---------- | ---------- | ------------ | ------------ |
| Insertion Sort | $O(n)$    | $O(n^2)$     | $O(n^2)$   | Yes        | Yes          | Yes          |

### Pseudocode
```
for n in [1, arr.length) {
	for i = n; i > 0 and arr[i] < arr[i - 1]; i-- {
		swapAt(i, i - 1)
	}
}
```

### See Also
[[Sorting Algorithms]]