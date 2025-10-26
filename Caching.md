---
aliases:
  - Cache
---
Ephermeral holding of data for the purpose of expediting future accesses. In this entry, the cache exists as hardware. For more algorithmic notions of caching, look at [[Memoization]].

Typical memory organization, including [[CPU]] caches.
Increasing speed as we get closer to CPU, but with smaller capacity.
The [[Virtual Memory]] mention on [[Storage|secondary storage]] is referring to the [[Swap Space]] part of [[Memory Management|Virtual Memory Management]]
![[Pasted image 20251025232621.png|500]]



![[Locality]]

# Cache Organization
![[Pasted image 20251026012931.png|400]]

## Direct Mapped Cache
* For a $2^N$ size cache, the *index* into the cache is the last $N$ bits of the memory address. Hence, this kind of cache is called a direct cache, because you just perform modulus base cachesize to map the memory space into the cache space.
	* We use the last $N$ bits, because if we use the first $N$ bits, we will wreck our spatial locality
* The *tag* is remaining part of the memory address that isn't being used for the cache index. We use the tag to label and disambiguate the data in the cache.
* The *Valid Bit* indicates is the given entry is filled or garbage
![[Pasted image 20251026000450.png|400]]
![[Pasted image 20251026003655.png|400]]
* Benefits from both [[Locality#Spatial Locality]] and [[Locality#Temporal Locality]]

In a realistic memory system, the size of a word, and the precision of addressability might not be the same. In this case, you would just some of the last bits, where those bits encode addresses in the same memory word.
![[Pasted image 20251026004647.png|300]]


## Fully Associative Cache
#todo
## Set Associative Cache
#todo

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

