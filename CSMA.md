---
aliases:
  - Carrier Sense Multiple Access
---
A [[Medium Access Control Layer]] method used to manage how devices share a [[Network Medium]], i.e. in the same [[Collision Domain]]
# Carrier Sense
Listen to the medium. If it's idle then transmit.
# Collision Detection
CSMA/CD
Used in wired [[Ethernet]] [[Local Area Network|LAN Network]]s
Manages [[Collision]]s after they occur, i.e. collision resolution
1. If the carrier sense doesn't match the current transmission, that indicates that there is a collision.
2. When there is a collision, abort the transmission and then send a jamming signal to ensure other stations know there's a collision.
3. Wait for a random length delay before attempting to retransmit
# Collision Avoidance
CSMA/CA
Used in [[Wireless Local Area Network|WLAN Network]]s
Prevents collisions before they occur
1. Optional Handshake.
2. Send frame, await ACK before sending next.
3. If collision, wait for a random length delay before attempting to retransmit