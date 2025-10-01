Noncomparison sort that repeatedly sorts integers by the digit and position, starting at the least significant digit.
* Process
	* Sorts by least significant digit, then next digit, then next, etc.
	* Achieves sorting by putting elements into buckets
	* Pop from front from each Linked List, reinserting back into original array
* Doesn't rely on comparisons.
* Only works on integer or integer-like data types.
### Evaluation
$k$ from pseudocode

|                | Best Case | Average Case | Worst Case | [[Stable]] | [[Adaptive]] | [[In-place]] |
| -------------- | --------- | ------------ | ---------- | ---------- | ------------ | ------------ |
| LSD Radix Sort | $O(kn)$   | $O(kn)$      | $O(kn)$    | Yes        | No           | No           |
### Pseudocode
```
radix(array) {
	buckets := Array of LinkedLists[19] // for [-9, 9]
	for iteration [0, k) {
		for i [0, array.length) {
			buckets[digit(array[i]) + 9].addBack(array[i])
		}
		idx := 0
		for bucket in buckets {
			while bucket not empty {
				array[idx++] := bucket.popFront() 
			}
		}
	}
}
```
### See also
[[Sorting Algorithms]]
Most Significant Radix Sort. Same thing, different digit order.