A series of [[Local Area Network|LAN]] protocols, devices, and connection methods
[IEEE 802.2](https://en.wikipedia.org/wiki/IEEE_802.2)
Every ethernet device gets a burned-in [[MAC Address]]
# Ethernet Frame
a 6-field, 64-byte [[Header]] and [[Trailer]] containing data transmission parameters and [[MAC Address]]es
![[Pasted image 20251115160909.png]]
To send a frame:
* Wait until no one using cable (carrier sense)
* Assert carrier signal on the cable
* Broadcast the frame to all stations on the cable
* Retransmit after requeuing if there is [[Collision]] (if someone else raises carrier signal during your transmission)
If you hear a frame on the cable:
* Accept it if the destination [[MAC Address]] belongs to us, or if it has a broadcast or multicase destination MAC
* Drop it if you see a collision during its receipt or its CRC doesn't match
[[Packet]] is in the [[Payload]] here.

![[Manchester Encoding]]

# Ethernet Bridging Algorithm
![[Pasted image 20251115161924.png|400]]
* If the destination MAC is in the bridge table
	* Send the frame out the port listed in the BTE
* Otherwise
	* Flood the frame out all ports except the ingress port
* Put the source MAC in the bridge table, if neccessary, along with the frame ingress port and mark the entry "recently used"
* Remove any stale entries in the bridge table