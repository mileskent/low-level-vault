![[Pasted image 20251118170700.png|400]]
Let $S$ be the time for data to make its way the sender's [[Protocol Stack]]
* In modern times, often negligible
Let $R$ be the time for data to make its way the receiver's Protocol Stack
* In modern times, often negligible
Let $T_{W}$ is the wire delay (how long does it take to put the packet onto the wire)
Let $T_{f}$ is the flight time (the time it takes the packet to get from source to destination, e.g. Georgia Tech Eduroam [[Campus Area Network|CAN]] to Chennai Datacenter)
* Limited by the speed of light in the medium (of the wire)
## Wire Delay
$$
T_{W} = \frac{\text{Message Size}}{\text{Network Bandwidth}}
$$

> [!Warning]
> * Message size is often in bytes, whereas [[Bandwidth|Network Bandwidth]] is often in bits.
> * When Network Bandwidth is listed as K or M or G, it is powers of 10, not 2
## Transmission Time
aka "End-to-end latency"
$$
\text{Transmission Time} = S + T_{W} + T_{f} + R
$$
## Message Throughput
$$
\text{Message Throughput} = \frac{\text{Message Size}}{\text{Transmission Time}}
$$
## Example
![[Pasted image 20251118172631.png]]