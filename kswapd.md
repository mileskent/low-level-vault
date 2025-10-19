[[Paging]] [[daemon]] on [[Linux]]
* Proactively manages memory such that a (small) pool of [[Paging#Page Frame]]s are always free for use (~2% of memory), meaning that if it does its job effectively, [[Process]]es never have to wait for [[Page Replacement Algorithms]]
* Memory usage will gradually accumulate over time, as any process that needs memory will be supplied it, until eventually it reaches a steady state of ~2% free, maintained by the intermittent management of kswapd
	* If you run a program multiple times, its pages are already in memory, so it doesn't have to refetch them
	* If you open a file, its pages remain in memory, so they don't have to be refetched
	* Basically this behavior creates [[Caching]] behavior
* When kswap is running
	* If a page is [[Dirty]], write it out to [[Storage|disk]] to clean it.
	* Uses a modified version of [[Page Replacement Algorithms#Second Chance]] for page eviction
	* Evicts pages
