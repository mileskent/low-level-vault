---
aliases:
  - Cache
---
Ephermeral holding of data for the purpose of expediting future accesses. In this entry, the cache exists as hardware. For more algorithmic notions of caching, look at [[Memoization]].

When a CPU needs to access a physical address, the access to main memory is preceeded by an access to some cache. If there is a cache hit (the memory address and its contents are cached), then we save time by not needing to perform a [[RAM#Performance|slow memory access]] 

Typical memory organization, including [[CPU]] caches.
Increasing speed as we get closer to CPU, but with smaller capacity.
The [[Virtual Memory]] mention on [[Storage|secondary storage]] is referring to the [[Swap Space]] part of [[Memory Management|Virtual Memory Management]]
![[Pasted image 20251025232621.png|500]]



![[Locality]]


# Working Set
Which addresses show up in the cache when a [[Process]] runs?

# Context Switch
We do nothing. This is because we're using [[Physical Address]]es, unlike the [[Translation Lookaside Buffer|TLB]]

# Flushing
The cache must be flushed upon OS bringing in [[Paging#Page]] from [[Storage|disk]] and bypassing the cache, because if I/O bypasses the cache, any cache entries reference the I/O buffer will be invalid.

# Virtually Indexed Physically Tagged Cache
(Cache & [[Translation Lookaside Buffer|TLB]] accessed in parallel)
If you make the page offset the same bitsize as the index + block offset size, then you can start the cache read without waiting for the TLB.
![[Pasted image 20251028154708.png]]
The tradeoff is that the index determines the max size of the cache, limiting the size of the cache.
# Cache Organization
Cache... line = block = entry = element = one unit of cached data stored in the cache
* Cache Set: a "row" in the cache. The number of blocks per set is determined by the type of set.
	* DMC: n sets, 1 entry
	* P-way set associative: n/p sets, p entries
	* Fully associative: 1 set, n entries
![[Pasted image 20251028152235.png|400]]

## Direct Mapped Cache
* Any potential memory block only has one valid location in the cache. Least hardware complexity. Least flexible.
* For a $2^N$ size cache, the *index* into the cache is the last $N$ bits of the memory address. Hence, this kind of cache is called a direct cache, because you just perform modulus base cachesize to map the memory space into the cache space.
	* We use the last $N$ bits, because if we use the first $N$ bits, we will wreck our spatial locality
* The *tag* is remaining part of the memory address that isn't being used for the cache index. We use the tag to label and disambiguate the data in the cache.
* The *Valid Bit* indicates is the given entry is filled or garbage
![[Pasted image 20251026012931.png|400]]
![[Pasted image 20251026000450.png|400]]
![[Pasted image 20251026003655.png|400]]
* Benefits from both [[Locality#Spatial Locality]] and [[Locality#Temporal Locality]]
* Can cause inefficienct use of cache with overlapping [[#Working Set]]s
* There is an optimal zone for the size of the cache blocks, striking the balances between exploiting Spatial Locality and memory transfer of updating the working set becoming a bottleneck
	

In a realistic memory system, the size of a word, and the precision of addressability might not be the same. In this case, you would just some of the last bits, where those bits encode addresses in the same memory word.
![[Pasted image 20251026004647.png|300]]


## Fully Associative Cache
Any memory block can be place in any cache line. Most flexible.
Because a block can go anywhere, the cache uses a [[Replacement Algorithm]] to decide where the block should go
There is no notion of tag and index; the entire thing is a tag. This is because any address. There is still a block offset like the other organizations.
![[Pasted image 20251028144353.png|400]]
Requires more hardware complexity because it needs a word-sized comparator for every cache entry

Hit/Miss determined with a comparator per cache entry that inspects the tag. It also requires the entry to be valid.
![[Pasted image 20251028151907.png|400]]
## Set Associative Cache
Compromise between DMC and FAC. DMC and FAC are really just degenerate cases of SAC. DMC is 1-way SAC. FAC is N-way SAC.
4-way SAC. Really just 4 DMCs connected together.
![[Pasted image 20251028152846.png|400]]
2-Way SAC only needs one bit per entry for LRU.
For N-way SAC you need $\log_{2}(N!)$ bits per entry for LRU.
Index bits tell you which row (set) to look in, and then you have to look through all of the DMC (ways) to check for the entry
Cache entries have their row (set) determined DMC style, and then which DMC they are in (way) determined FAC style

# Misses
> [!warning] Super Important Nuance!
Check in this order: Compulsory > Capacity > Conflict
That is to say, if a word is being access for the first time, it will always be a compulsory miss, even if you happen to also be evicting an entry like in a conflict miss.
## Compulsory Miss
aka "Cold Miss"
The first time you access a word, you are guaranteed to have a cache miss, because that word cannot be in the cache yet.
## Capacity Miss
The cache is completely full, and the word we want isn't in the cache.
## Conflict Miss
We have to evict an entry from the cache even though the cache is not full, and it is not the first time we are accessing this word.
* E.g. `cache_index = address % cache_capacity`  -> all multiples of capacity will conflict
* Conflict misses are misses that would not occur if the cache were fully associative with LRU replacement. Fully associative caches can't have conflict misses, by definition.

# Effective Memory Access Time
#todo clean up this section
Hit rate $h$
Miss Rate $m$
Hit rate + Miss rate = 1
Cache access time $T_c$
Memory access time = Miss penalty = $T_m$
Memory cycle time, Memory access time

Effective Memory Access Time (EMAT) = $\text{EMAT}_{i} = T_{i} + M_{i} \cdot\text{EMAT}_{i+1}$
where $T_i$ is cache access time, and $M_i$ is the cache miss rate
![[Pasted image 20251025235902.png|300]]


# Memory Access Scenarios
![[Pasted image 20251026010400.png|500]]
## Read Scenarios
* Read Hit
	* The CPU requests data from memory, but the cache already has it, so the CPU can get that memory immediately
		* This is the *fastest* scenario
* Read Miss
	* The CPU requests data from memory, and the cache doesn't have it so it must be fetched from main memory and written to the cache
##  Write Policies
* Write Through
	* A write policy where the CPU simultaneously writes to the cache and main memory 
		* This ensures that there is no desync between main memory and caches, which is super important for shared memory between multiple CPUs
* Write Back
	* A write policy where the CPU initially only writes to the cache, and the main memory is updated later
		* A Write Buffer exists to buffer the writes before we have to write them back to main memory
		* A [[Dirty]] bit is maintained, similar to [[kswapd]] during [[Paging]]
			* This is an additional entry that would go in each cache entry, after the valid bit

# Cache Optimization
## Exploiting Spatial Locality
![[Pasted image 20251026012727.png|500]]

![[Pipeline#Pipeline with Caches]]

