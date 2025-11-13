---
aliases:
  - TCP
---
a [[Network Protocol]] used to establish a guaranteed, connection-oriented communication channel between communicating devices.  

Exists in the [[Open Systems Interconnection Model#Transport Layer]]
Anything that wants a session with continuity uses TCP.

![[Stop and Wait Protocol]]

![[Go Back N]]

![[Sliding Window Protocol]]
# Segment
Creates a [[Protocol Data Unit|PDU]] called a "segment" which includes a TCP [[Header]] consisting of connection state information known as a "TCP flag"
![[Pasted image 20251113140827.png|400]]
Window size is size of [[Sliding Window Protocol|sliding window]]
The only place Professor Forsyth has even seen the urgent ptr actually be used is in Ctrl-C quit over [[SSH]].
# TCP Header
a 10-field, 20-byte header containing connection and payload delivery details for a segment. A TCP header is used to establish a three-way handshake for payload delivery.