QuickSort has many variations and the one detail here is **randomized inplace quick sort** using the **hoare partition scheme**.
##### Quicksort Recursive Algorithm
1. Pick pivot randomly (worst case cannot be caused purposefully by the user)
2. Move pivot to index 0
3. Partition data into two groups: < pivot and > pivot; after this partitioning everything less than the pivot will be to the left of it and everything greater than the pivot will be to the right of it
	1. swap pivot with element at 0
	2. Two pointers i (starts at beginning of left of subarray, after pivot) and j (at the end of the right subarray), i and j go towards each other iff they encounter valid data, respectively
	3. i is looking for things that are bigger than pivot, j is looking for things that are smaller than the pivot
	4. if they find something that does not belong then swap elements at i and j (equal to pivot -> belongs, regardless of left of right)
	5. if i and j have crossed (j < i), then we know we are done with the current partitioning
4. Put pivot back where it belongs (swap it with the element at j)
##### Pivot selection
* Can use index 0 for pivot but it can result in abuse by the user
* Median of medians is an alternative to random pivot
	* Finding the media is $O(n \log n)$
* Random pivot is the method that gets used irl
	* Random pivot has fastest average time
* ***Note that the index of the pivot once it is put back into place is the final index for the pivot***
	* This is because the current pass of QuickSort puts all smaller elements to the left of the pivot and all greater elements to the right of the pivot. Because of this, even though the left and right subarrays are not neccessarily sorted, the pivot is.
### Evaluation
QuickSort degenerates into something similar to [[Selection Sort]] for its worst case.
Sorted input actually makes this algorithm worse. It is as antithetical to being adaptive as possible.

|           | Best Case     | Average Case  | Worst Case | [[Stable]] | [[Adaptive]] | [[In-place]] |
| --------- | ------------- | ------------- | ---------- | ---------- | ------------ | ------------ |
| QuickSort | $O(n \log n)$ | $O(n \log n)$ | $O(n^2)$   | No         | No           | Yes*         |
\*In-place classification is somewhat subjective because some data is copied to local variables within recursive stack frames, but not another data structure. Because the data is not copied to another data structure, we say that its in place.
### Pseudocode
```
quicksort(array, start, end) {
	if end - start <= 1 return

	// Choose pivot
	// put it out of the way for partitioning
	pivotIndex := rand([start, end])
	pivotVal := array[pivotIndex]
	swap elements at start, pivotIndex

	// Partitioning
	// Move elements larger than the pivot to the right side of the array
	// Move elements smaller than the pivot to the left side of the array
	i := start + 1
	j := end
	while i and j have not crossed {
		while i and j not crossed and array[i] <= pivotVal { i++ }
		while i and j not crossed and array[j] >= pivotVal { j-- }
		if i and j have not crossed {
			swap elements at i, j
			i++
			j--
		}
	}	

	// Elements are grouped over-under relative to pivot
	swap elements at start, j
	quicksort(array, start, j - 1) // left
	quicksort(array, j + 1, end) // right
}
```

### See also
[[Sorting Algorithms]]