---
aliases:
  - NAT
---
Convert 
# Static NAT
A translation is configured so that source address or destination address is changed from/to the translated address on transit, and [[Checksum]]s are recalculated
# Dynamic NAT
Same as [[#Static NAT]], but a [[IP#Public IP|public address]] from a pool isn't translated until a [[IP#Private IP|private address]] attempts to cross the NAT device; the public address is teturned to the pool when the conversation ends

# Port Address Translation
Building upon [[#Dynamic NAT]], both the source address and source [[Port]] are translated to an address and port from the public pool; return traffic is translated by the destination address and port
Allows an entire household to run on one IP address.