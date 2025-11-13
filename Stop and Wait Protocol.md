Send a packet.
Await an acknowledgement before sending the next [[Packet]].
Repeat.
![[Pasted image 20251113133326.png|500]]
![[Pasted image 20251113133613.png|400]]
Retransmission after timeout
![[Pasted image 20251113133717.png|400]]
Because we might not get an ACK, we must buffer a packet a the sender and receiver.
Use a monotonically increasing sequence number to keep track of ordering.
