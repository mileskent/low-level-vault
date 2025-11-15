---
aliases:
  - TCP
---
a [[Network Protocol]] used to establish a guaranteed, connection-oriented communication channel between communicating devices.  
A bidirectional stream protocol that delivers arbitrarily long streams of bytes
Sequence number in each direction to maintain packet order -> Each connection maintains 2 sequence numbers
SYN and ACK flag bits.
3 packets at beginning of TCP connection (3-way handshake) are SYN, SYN-ACK, ACK
This handshake is the two sides exchanging randomly chosen sequence numbers to sychronize data going in both directions.

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

# 3 Way Handshake
![[Pasted image 20251115140116.png]]
[[Client]] sends a packet iwth random sequence number and SYN flag
[[Server]] recognizes the packet with a SYN as a request to initiate a stream. If it accepts, the it responds by
* Putting the sequence number in the acknowledgement field
* Setting the ACK bit
* putting a different random sequence number in the packet
* Setting the SYN bit before sending the packet to the client
Client sends packet back with ACK field and populated data field
When either are done transmitting, they send a packet with the FIN bit set, which causes the other side to no longer expect to receive packets from the stream