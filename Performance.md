# Metrics
* Space
	* [[#Instruction Frequency]]
		* [[#Instruction Frequency#Static]]
		* [[#Instruction Frequency#Dynamic]]
* [[#Execution Time|Time]]
* [[#Benchmarking]] (culmination of the above)

# Execution Time
$$
\text{Ideal:} \quad \text{Execution time} = \sum^{n-1}_{0}(\text{CPI}_{j}) \cdot \text{clock cycle time}
$$
$$
\text{Good enough:} \quad \text{Execution time} = n \cdot \text{CPI}_{\text{avg}} \cdot \text{clock cycle time}
$$
where $n$ is instruction count
where Cycles Per Instruction (CPI) is the number of clock cycles per instruction
where $\text{CPI}_\text{avg} = \frac{\text{inst X count}}{\text{total count}}$

## Total Execution Time
Cumulative total of the execution times of the individual programs
## Geometric Mean
This is generally the default
The metric removes the bias present in arithmetic mean
## Arithmetic Mean
This metric is biased towards time-consuming jobs
## Harmonic Mean
This metric is biased against time-consuming jobs
## Weighted Arithmetic Mean
This metric takes into account the relative frequency of the execution of the programs in the benchamrk mix
# Instruction Frequency
## Static 
Occurence of instruction X in compiled code
## Dynamic
Occurence of instruction X in executed code

# Benchmarking
The goal of a benchmark is to be representative of the expected workload for a processor.

---

# Improving Performance
Goal: minimize [[#Execution Time]]
Execution time = Instruction Count * CPI * Cycle Time
So just reduce one of the factors

## Measuring Improvement
$$
\text{speedup}_{\text{A over B}} = \frac{\text{Execution Time on Processor B}}{\text{Execution Time on Processor A}}
$$
$$
\text{speedup}_{\text{improved}} = \frac{\text{Execution Time Before Improvement}}{\text{Execution Time After Improvement}}
$$
$$
\text{improvement in execution time} = \frac{\text{old execution time}-\text{new execution time}}{\text{old execution time}}
$$
$$
\textbf{Amdahl's Law:}\quad\text{Time}_{\text{after}} = \frac{\text{Time}_{\text{affected}}}{\text{Amount of Improvement}} + \text{Time}_{\text{unaffected}}
$$
> [!Example]- Office Walk (Amdahl's Law)
I can walk from my office to campus in 12 minutes, and run there twice as fast as I can walk, and I walk half the distance and run the rest, how long will it take?
> $$
> \text{Time}_{\text{after}} = \frac{6}{2} + 6 = 9\text{ minutes}
> $$

> [!Example]- Processor Optimization (Amdahl + Speedup Improved)
A processor spends 15% of its time on ADD instructions. An engineer proposes to improved the speed of the ADD instruction threefold. What is the speedup achieved by this modification?
> $$
> \text{Time}_{\text{after}} = \frac{.15}{3} + .85 = .9
> $$
> $$
> \text{Speedup} = \frac{1}{.9} = 1.11
> $$
11% speedup

> [!example]- Architecture Change
We have a computer with three types of instructions that have the following CPIs:
>
> | Type | CPI |
> | --- | --- |
> | A    | 2   |
> | B    | 5   |
> | C    | 1   |
> An architect determines that he can reduce the CPI for B to 4, but will need to slow down the clock speed of the processor. What is the maximum permissible slowing of the clock that will make this change worthwhile? 
> Assume that all the workloads for this processor use 25% A, 15% B, and 60% C type instructions, respectively.
> 
> $$
> \begin{align}
> ET_{\text{old}}
> &= n (F_{A} CPI_{A} + F_{B\text{ old}}CPI_{B \text{ old}} + F_{C}CPI_{C}) \cdot C_{\text{old}}\\
> &= n (.25 \cdot 2 + .15 \cdot 5 + .6 \cdot 1) \cdot C_{\text{old}}\\
> &= 1.85 \cdot n \cdot C_{\text{old}}
> \end{align}
> $$
> $$
> \begin{align}
> ET_{\text{new}} &= n (F_{A} CPI_{A} + F_{B\text{ new}}CPI_{B \text{ new}} + F_{C}CPI_{C}) \cdot C_{\text{new}}\\
> &= n (.25 \cdot 2 + .15 \cdot 4 + .6 \cdot 1) \cdot C_{\text{new}}\\
> &= 1.7 \cdot n \cdot C_{\text{new}}
> \end{align}
> $$
> where $F_X$ and $CPI_X$ are the dynamic frequencies and CPIs of each type of instruction
> For the design to be viable: $ET_{\text{new}} < ET_{\text{old}}$
> $$
> \begin{align}
> ET_{\text{new}} &< ET_{\text{old}}\\ \\
>  1.7 \cdot n \cdot C_{\text{new}} &< 1.85 \cdot n \cdot C_{\text{old}}\\
>  C_{\text{new}} &< \frac{1.85}{1.7} \cdot C_{\text{old}}\\
>  C_{\text{new}} &< \frac{1.85}{1.7} \cdot C_{\text{old}}\\
>  C_{\text{new}} &< 1.09 \cdot C_{\text{old}}\\
> \end{align}
> $$
The maximum permissible slowdown is about 9%


# Performance with Caches
$$
\text{Execution Time} = n \cdot \text{CPI}_{\text{effective}} \cdot \text{cycle time}
$$
$$
\text{CPI}_{\text{effective}} = \text{CPI}_{\text{avg}} + \text{Memory Stalls}_{\text{avg}}
$$
$$
\text{Memory Stalls}_{\text{avg}} = \text{misses per instr}_{\text{avg}} \cdot \text{miss penalty}_{\text{avg}}
$$
$$
\text{Total Memory Stalls} = N \cdot \text{Memory Stalls}_{\text{avg}}
$$
