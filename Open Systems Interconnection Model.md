---
aliases:
  - OSI Model
  - OSI
---
a seven-layer network conceptual model created by the International Organization for Standardization (ISO)
![[Pasted image 20251113120424.png|500]]

# Application Layer
An upper-level layer (7) that manages the interaction between a [[Network Protocol]] and a network application
# Presentation Layer
An upper-level layer (6) that prepares data for transmission between the [[#Application Layer]] and [[#Session Layer]]
# Session Layer
An upper-level layer (5) that establishes a data transmission channel known as a ***session*** between communication devices
# Transport Layer
A lower-level layer (4) that takes data from the upper-level layers and divides it into smaller-sized blocks of data for faster transmission.

Includes the [[Network Protocol]]s: [[Transmission Control Protocol|TCP]] and [[User Datagram Protocol|UDP]]

Layer 4 devices are used to make forwarding decisions during [[Payload]] transport.
Many layer 4 devices function both at layer 4 and the upper-level layers for payload transport.

Common layer 4 devices include: [[Load Balancer]]s, [[Gateway]]s, [[Intrusion Detection System]]s, and [[Firewall]]s.

# Network Layer
A lower-level layer (3) where data receives logical address information needed to reach the recipient's network  
  
Creates the "packet" PDU  
  
A layer 3 device typically serves as a [[Network Node|Node]] used to connect an internal network to an external [[Network]]. 
Some vendors refer to a layer 3 device as a boundary, gateway, or edge device. Common layer 3 devices include [[Router]]s, [[Switch#Layer 3 Switch]]es, and WLAN controllers.

# Data Link Layer
A lower-level layer (2) where data is transmitted to the recipient [[Network Node|Node]].  

A layer 2 device typically serves as a central node providing connectivity to multiple [[Network|networked]] devices.
Common layer 2 devices: [[Bridge]], [[Switch]], [[WAP]], [[Network Interface Card|NIC]]
## Frame
the [[Protocol Data Unit|PDU]] created by layer 2 containing data transmission parameters and [[MAC Address|Physical Address]]. Two sublayers are used to construct a frame: [[Logical Link Control]] & [[Medium Access Control Layer|MAC]]. A frame needs to know how to reach the recipient node because not every node is directly connected.
## LLC
![[Logical Link Control]]
## MAC
![[Medium Access Control Layer|MAC]]

# Physical Layer
where a [[Payload]] is transmitted across a network medium (networking devices)
Common layer 1 devices: [[Hub]], [[Repeater]], [[Modem]], [[Cable]]. 