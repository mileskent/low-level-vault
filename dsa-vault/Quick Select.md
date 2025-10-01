A [[Selection Algorithms|Selection Algorithm]] that uses a similar technique to [[QuickSort]] in finding the $k$th smallest/largest value of an array, performing something similar to binary search.
The goal of this algorithm is to be better than $\Omega(n \log n)$, i.e. better than just sorting the dataset and then grabbing the $k$th element
The idea is that you can do the same first two steps as quicksort (pick a pivot and partition), but then for the last step you only recursively continue to sort the data that the $k$th element could be in, while ignoring everything else because it doesn't have the $k$th element. You can determine where the $k$th element is because the current pivot is already in its correct location. Because of this, you can compare k to the index of the pivot to determine which way to recurse.
### Evaluation
Runtime comes from same [[Time Complexity]] justification as [[Binary Heap#BuildHeap|BuildHeap]]

|              | Best Case | Average Case | Worst Case | [[Stable]] | [[In-place]] |
| ------------ | --------- | ------------ | ---------- | ---------- | ------------ |
| Quick Select | $O(n)$    | $O(n)$       | $O(n^2)$   | No         | Yes*         |
\*For the same reason as [[QuickSort]]
### Pseudocode
See [[QuickSort]] for explanation of [[QuickSort#Quicksort Recursive Algorithm|choose pivot and paritioning steps]].
```
quickselect(array, start, end, k) {
	if end - start <= 1 return

	// Choose pivot
	// put it out of the way for partitioning
	pivotIndex := rand([start, end])
	pivotVal := array[pivotIndex]
	swap elements at start, pivotIndex

	// Partitioning
	// Move elements larger than the pivot to the right side of the array
	// Move elements smaller than the pivot to the left side of the array
	// Not crossed -> i <= j
	i := start + 1
	j := end
	while i and j have not crossed position {
		while i and j in not crossed position and array[i] <= pivotVal { i++ }
		while i and j in not crossed position and array[j] >= pivotVal { j-- }
		if i and j have not crossed position {
			swap elements at i, j
			i++
			j--
		}
	}	

	// quickselect special behavior vs quick sort
	swap elements at start, j
	if j == k - 1 { return array[j] } // kth value has been found
	if j > k - 1 { quickselect(array, start, j - 1, k) } // recurse left
	else { quickselect(array, j + 1, end, k) } // recurse right
}
```