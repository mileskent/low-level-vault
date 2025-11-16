* Solving a large problem that is composed of smaller, overlapping, predictably ordered subproblems
	* The hard part of creating a DP solutions is identifying and applying [[Memoization]] to the subproblem(s) 
	* where the storing of solutions to subproblems is called [[Memoization]]
* In DP, we always look for an **optimal substructure**, where if we compute the optimal solution to the subproblems then we can compute the optimal solution of the larger more complex problem.
* A drawback to DP is that the [[Auxiliary Space Complexity]] will be larger than normal, but this is usually okay because space is almost always cheaper than time
* DP often involves [[Recursion]], though this recursion might just be in the reasoning for the implementation, while the implementation may be iterative, e.g. for the [[#Fibonacci Sequence Example]], the reasoning is recursive still but the implementation is iterative.
### Components of Dynamic Programming
* Identify the optimal structure of subproblems
* Establish an order of solving
* Solve subproblems to solve the large problem

### Fibonacci Sequence Example
> [!Example]-
> A typical fibonacci function might look like the below. 
> ```
> fib(n):
> 	if (n is 0 or 1) return n 
> 	else return fib(n - 1) + fib(n - 2)
> ```
> The function calls for `fib(5)` look like this. There are many redundant calls being performed, and this redundant amount will increase exponentially with n, i.e. $O(2^n)$, which is bad.
> ![[Pasted image 20250414201626.png|250]]
> 
>
> A dynamic programming solution to the same problem looks like this
> ```
> fib(n):
> 	num: int[]
> 	num[0] = 0
> 	num[1] = 1
> 	for n-2 num[n] = num[n - 1] + num[n - 2]
> 	return num[n]
> ```
> So at the cost of storing previous subproblem solutions, we can calculate the same thing with fewer function calls, because we eliminate all redundant function calls. The resultant [[Time Complexity]] is $O(n)$ which is far better than that of the classic [[Recursion|recursive]] solution.
> ![[Pasted image 20250414202127.png|100]]
> * The DP solution is usually based off of the intuitive solution, but then identifies redundancy and eliminates it through [[Memoization]]
> * Note that the non-DP solution isn't always going to be recursive, and may have no [[Auxiliary Space Complexity]], but in this case it is so the memory tradeoff is not as much of a consideration. 

### Dynamic Programming Problems
[[Dijkstra's Algorithm]]
[[Longest Common Subsequence]]
[[Bellman-Ford Algorithm]]
[[Floyd-Warshall Algorithm]]