Used in [[malloc]]. Verify that the user isn't writing outside the block provided, preventing corruption of the [[Heap]], during [[Heap Allocation]].

> [!abstract] 
> Canaries are metadata associated with malloc [[Arena|arenas]]. If they are corrupted, this is an indication that we have undefined and/or mallicious behavior. It is a warning sign.

> [!info]-
![[Pasted image 20250409172515.png|150]]
*Canary in a coal mine*
An allusion to caged canaries (birds) that miners would carry down into the mine tunnels with them. If dangerous gases such as carbon monoxide collected in the mine, the gases would kill the canary before killing the miners, thus providing a warning to exit the tunnels immediately[^1].
### See also
[[malloc]]

[^1]: https://en.wiktionary.org/wiki/canary_in_a_coal_mine
