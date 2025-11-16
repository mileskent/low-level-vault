Performs [[Bubble Sort]] twice to bubble the largest element to the top of the array and the smallest element to the bottom of the array.
*Iterative Sorts are generally **bad** unless the data set is relatively small*
![[Pasted image 20250310205444.png|500]]
### Evaluation
Same evaluation as [[Bubble Sort]], but is slightly more optimal. Because Bubble Sort is so bad, this one isn't much better.

|                      | Best Case | Average Case | Worst Case | [[Stable]] | [[Adaptive]] | [[In-place]] |
| -------------------- | --------- | ------------ | ---------- | ---------- | ------------ | ------------ |
| Cocktail Shaker Sort | $O(n)$    | $O(n^2)$     | $O(n^2)$   | Yes        | Yes          | Yes          |
### Code
```
boolean swapMade = true;
int startIndex = 0;
int endIndex = arr.length - 1;
int lastBubbleUpIndex = endIndex;
int lastBubbleDownIndex = startIndex;
while (swapMade) {
	swapMade = false;
	endIndex = lastBubbleUpIndex;
	startIndex = lastBubbleDownIndex;
	// Bubble Up
	for (int i = lastBubbleDownIndex; i < endIndex; ++i) {
		if (comparator.compare(arr[i], arr[i + 1]) > 0) {
			swap(arr, i, i + 1);
			swapMade = true;
			lastBubbleUpIndex = i;
		}
	}
	// Bubble Down
	if (swapMade) {
		for (int i = lastBubbleUpIndex; i > startIndex; --i) {
			if (comparator.compare(arr[i - 1], arr[i]) > 0) {
				swap(arr, i - 1, i);
				swapMade = true;
				lastBubbleDownIndex = i;
			}
		}
	}
}
```
### See Also
[[Sorting Algorithms]]