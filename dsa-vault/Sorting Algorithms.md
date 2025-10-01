An algorithm that puts elements of a list into an order. The most frequently used orders are numerical order and lexicographical order, and either ascending or descending. Efficient sorting is important for optimizing the efficiency of other algorithms that require input data to be in sorted lists. 
All examples will be ascending order.
![[014-sorting-algorithms-1853296222.gif|500]]

* Keywords for sorting algorithms are [[Stable]], [[In-place]], and [[Adaptive]]
* ***Comparison-based sorting algorithms are theoretically impossible to optimize beyond $\Omega(n \log n)$***
### Iterative Sorts
Solve the sorting problem by iteratively processing the entire dataset.
*Iterative Sorts are generally **bad** unless the data set is relatively small (we say generally bad because datasets are generally not small)*
*If the dataset **is** relatively small, they can even perform **better** than [[#Divide and Conquer Sort|Divide and Conquer Sorts]] due to being [[Adaptive]] (D&C are not) and having far better [[Auxiliary Space Complexity]] by all being [[In-place]] (D&C are not \[[[QuickSort]] is technically in place but not really and still has the overhead of recursive calls\])*

|                          | Best Case | Average Case | Worst Case | [[Stable]] | [[Adaptive]] | [[In-place]] |
| ------------------------ | --------- | ------------ | ---------- | ---------- | ------------ | ------------ |
| [[Bubble Sort]]          | $O(n)$    | $O(n^2)$     | $O(n^2)$   | Yes        | Yes          | Yes          |
| [[Cocktail Shaker Sort]] | $O(n)$    | $O(n^2)$     | $O(n^2)$   | Yes        | Yes          | Yes          |
| [[Insertion Sort]]       | $O(n)$    | $O(n^2)$     | $O(n^2)$   | Yes        | Yes          | Yes          |
| [[Selection Sort]]       | $O(n^2)$  | $O(n^2)$     | $O(n^2)$   | No         | No           | Yes          |
### Divide and Conquer Sort
Recursively break down the dataset into smaller subproblem, solve each subproblem independently, and then recombine the solutions to achieve a final sorted order.

|                | Best Case     | Average Case  | Worst Case    | [[Stable]] | [[Adaptive]] | [[In-place]] |
| -------------- | ------------- | ------------- | ------------- | ---------- | ------------ | ------------ |
| [[HeapSort]]   | $O(n \log n)$ | $O(n \log n)$ | $O(n \log n)$ | No         | No           | No           |
| [[Merge Sort]] | $O(n \log n)$ | $O(n \log n)$ | $O(n \log n)$ | Yes        | No           | No           |
| [[QuickSort]]  | $O(n \log n)$ | $O(n \log n)$ | $O(n^2)$      | No         | No           | In*          |
### Noncomparative

|                    | Best Case | Average Case | Worst Case | [[Stable]] | [[Adaptive]] | [[In-place]] |
| ------------------ | --------- | ------------ | ---------- | ---------- | ------------ | ------------ |
| [[LSD Radix Sort]] | $O(kn)$   | $O(kn)$      | $O(kn)$    | Yes        | No           | No           |

