How many page references are there in physical memory?
$$
\text{Memory Pressure} = M_{p} = \sum^n_{i=1} \text{wss}(P_{i})
$$
where $\text{wss}(P_{i})$ gives the [[Virtual Memory#Working Set]] Size of an ith [[Process]]
where $n$ is the number of processes running
working set set is exactly the count of page references per process

If $M_{p} > \sum\text{page frames}$ then [[Swap Space|swap]] out some processes
If $M_{p} < \sum\text{page frames}$  then increase degree of [[Multiprogramming]]

This is a concern of the [[Scheduler#Medium Term Scheduler]]