GNU Compiler Collection. Includes [[C]] [[Compiler]].
![[Pasted image 20250324124711.png|500]]
![[Pasted image 20250324124742.png|500]]


# Optimization
*We should forget about small efficiencies, say about 97% of the time: premature optimization is the root of all evil. Yet we shuold not pass up our opportunities in that critical 3%* - Knuth
## Basic Optimization
### Constant Folding
Evaluates expressions at compile time and replace them with their constant values
### Constant Propagation
Replaces variables with their constant values wherever possible
### Common Subexpression Elimination
Identifies and elimminates redundant calculations by resuing the result of a previous calculation
### Dead Code Elimination
Removes code that has no effect on the program's output
## Loop Optimizations
### Loop Unrolling
Copies the loop body multiple times to reduce loop overhead and improve performance
### Loop Invariant Code Motion
Move calculations that are independent of the loop counter outside the loop
### Loop Fusion
combines adjacent loops that operate on the same data
### Loop Fission
Splits a loop into multiple loops to enable further optimizations

## Function Optimizations
### Function Inlining
See [[C Function#`inline`]]
### Tail Call Optimization
Optimizes tail recursive calls to avoid stack frame allocation
## Advanced Optimizations
### Instruction Scheduling
### Strength Reduction
Replaces rexpensive operations with cheaper equivalents
### Vectorization
Uses SIMD instructions to perform operations on multiple data elements simulatenously
### Profile Guided Optimization
Uses runtime profiling data to optimize code for real-world execution scenarios
### Interprocedural Optimization
Optimizes across functionboundaries such as [[C Function#`inline`|inlining]] across files or optimizing based on the call graph
# Flags
* `-O{level}` for optimization
	* Levels
		* 0 - Don't move code around
		* 1 - Quick optimizations that don't take much compilation time
		* 2 - all optimizations that don't involve speed/space tradeoff
		* 3 - As much as possible
	* Use 0 or 1 with a debugger