---
aliases:
  - PSN
---

a [[Network]] where the network parts, or planes, are configured to break down data into smaller pieces, or [[Packet]]s, for transmission using any available link

Assumptions: 
* Packet loss is possible
* Packets may be reordered or arbitrarily delayed
* Packets may be damaged in transit

Because of these assumptions, we uses a monotonically increasing sequence number to keep track of ordering.