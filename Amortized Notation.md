Concerning [[Big O, Ω, Θ Notation]], the classic example is resizing an [[ArrayList]].
Let's say that every time you resize the array list, you double the size. This means that the number of insertions between each insertion increases exponentially. Functionally, the [[Time Complexity]] of insertion is constant, even though the worst case when resizing is linear, because the fact that the time complexity is constant the vast majority of the time makes up for the fact that sometimes it is worse when resizing.
In the case of this example, if you are asked the time complexity of insertion it could mean
* $O(n)$ (Worst Case)
* $O(1)^*$ *Amortized* (Worst Case)
