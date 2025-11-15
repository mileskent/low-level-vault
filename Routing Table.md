* a rule table determining how a router routes a [[Payload]] based on the destination's [[IP|IP Address]]
* stores the destination prefix of an [[IP|IP Address]], and the next [[Hop]] required to go in that direction, allowing [[Packet]]s to navigate to their destinations.
* Each [[Host]]'s routing table has a default route, pointer to a [[Router]] of last resort on the subnet, called a [[Default Gateway]]
  * The router picks the match in the routing table with the longest [[Prefix]]
  * A destination accessible via [[Open Systems Interconnection Model#Data Link Layer]] will have `0.0.0.0` for its [[Gateway]], and will have something listed under its "Interface" like "enp0s1" for an [[Ethernet]] connection