---
aliases:
  - CIDR
---
CIDR is the modern way the [[Internet]] respresents and allocates [[IP]] address ranges. It replaces the old, wasteful [[Classful Addressing System]].

In [[Classful Addressing System]], the address contains information about the [[Subnet#Subnet Mask]] through its class, which is determined by its most significant bits. 

As it turns out, knowing the [[Subnet#Subnet Mask]] only actually matters if you're connected to that network. Because of this, CIDR does not encode the subnet mask. This allows the mask to be variable length, allowing best utilization of address space.

If you're not on the network, and you're routing to that network, all you need to know is what direction do I go for my next [[Hop]] to route to this particular [[Prefix]]?

The [[Routing Table]] answers this question by storing the destination prefix, and the next hop required to go in that direction.