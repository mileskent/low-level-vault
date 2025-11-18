---
aliases:
  - networked
---
An assortment of at least two connection points, or [[Node]]s, capable of sharing technology resources via a link

A Network is a [[Graph]]

If the network bits of an [[IP]] address are the same between two devices, they are on the same network.

If you are on the same network as another device you can talk to that device directly through [[Open Systems Interconnection Model#Data Link Layer]], because all [[Host]]s on the same data link network must be assigned IP addresses with a common network part ([[Subnet]]) and [[Subnet#Subnet Mask]]

If you are on a different network, you cannot talk directly to another device without going through IP routing first ([[Open Systems Interconnection Model#Network Layer]]), i.e. going through a [[Router]]

# Network Performance Metrics
![[Network Performance Metric]]

# Misc
"Big packets will fail to ping when there are network issues, but small ones may get through"