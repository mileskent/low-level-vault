Also called "Leader-Follower Flip Flop"
* Makes it so that one input is not outputted more than once per Clock cycle.
* [[Leading Edge Triggered]] 

1. On rising edge of [[Clock]] -> [[Leader]] [[Register]] records input 
2. Top of [[Clock]] -> Leader outputs whatever it recorded, [[Follower]] [[Register]] outputs whatever the Leader outputs
3. Clock falls -> Follower records its inputs
4. Bottom of Clock -> Leader outputs its inputs again, Follower outputs what it recorded

![[Pasted image 20250130222910.png]]
![[Pasted image 20250130222735.png|300]]