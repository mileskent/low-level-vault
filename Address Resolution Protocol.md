---
aliases:
  - ARP
---
Used with [[Ethernet]] to discover [[IP|IP Address]]es (How [[Open Systems Interconnection Model#Data Link Layer]] and [[Open Systems Interconnection Model#Network Layer]] communicate)
The IP Stack needs to send to an IP address *A* on the same ethernet, but doesn't know what destination [[MAC Address]] to use
[[IP#Broadcast]] an ARP-request message to the ethernet [[Network]]: "Who has IP address *A*?"
Wait on [[IP#Unicast]] ARP-reply: "I have IP address *A*"
Store response in *ARP Table*, discarding entries as they become stale
Use ARP Table to set ethernet frame's destination MAC address