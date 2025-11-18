---
aliases:
  - BGP
---
This is a [[Routing Protocol]] that uses a [[Hierarchical Routing Algorithm]]
* BGP is a path-vector protocol. (We're not going into much detail about that.)
* The gateway routers send path-vector messages to advertise the reachability of networks.
* Each router that receives a path vector message must verify the advertised path according to its policy.
* If the message is compliant, the router modifies its routing table and the message before sending the message to the next neighbor.
* It modifies the routing table to maintain the autonomous systems that are traversed in order to reach the destination system.
* It modifies the message to add its AS number and to replace the next router entry with its identification.