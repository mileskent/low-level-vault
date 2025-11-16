Iterative selects the maximum element in the unsorted subarray, and swaps it with the last element in the subarray.
*Iterative Sorts are generally **bad** unless the data set is relatively small*
![[Pasted image 20250310205611.png|500]]
* Minimal data movement
* No optimization possible
### Evaluation

|                | Best Case | Average Case | Worst Case | [[Stable]] | [[Adaptive]] | [[In-place]] |
| -------------- | --------- | ------------ | ---------- | ---------- | ------------ | ------------ |
| Selection Sort | $O(n^2)$  | $O(n^2)$     | $O(n^2)$   | No         | No           | Yes          |

### Pseudocode
```
loop n from end to start {
	maxIndex
	loop i from 0 to n {
		if array[i] > array[maxIndex]
			maxIndex := i
	}	
	swap elements at n and maxIndex
}
```

### See Also
[[Sorting Algorithms]]
