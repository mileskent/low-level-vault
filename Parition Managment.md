Management of paritions of memory in [[Memory]]
Each parition is a block of memory assigned to a [[Process]]
You can have fixed or variable sized partitions. Variable sized paritions eliminate [[Fragmentation#Internal Fragmentation]]
Some ideas are similar to how [[malloc]] manages the [[Freelist]]
For example, you may want to coelesce paritions like you can blocks in malloc
[[Relocatibility#Dynamically Relocatable]] allows rearrangement for reducing [[Fragmentation]]

# Algorithms
## First Fit Algorithm
Quicker
Cheapest
## Best Fit Algorithm
Better memory utilization
## Next Fit Algorithm
Less space efficient in average case
But quicker than [[#First Fit Algorithm]]
