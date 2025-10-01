Takes advantage of the [[Binary Heap#Big O#BuildHeap|O(n) time complexity]] of [[Binary Heap#Methods#BuildHeap|BuildHeap]] function of [[Binary Heap|Heaps]], by buildheaping the array and then removing from the heap until its empty. Removing is logarithmic so the result is O(n log n)
### Evaluation

|          | Best Case     | Average Case  | Worst Case    | [[Stable]] | [[Adaptive]] | [[In-place]] |
| -------- | ------------- | ------------- | ------------- | ---------- | ------------ | ------------ |
| HeapSort | $O(n \log n)$ | $O(n \log n)$ | $O(n \log n)$ | No         | No           | No           |
### Pseudocode
```
h = heap(dataset)
array = []
for dataset.length {
	array.add(h.remove())
}
```

### See also
[[Sorting Algorithms]]