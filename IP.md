---
aliases:
  - IP Address
  - Logical Address
  - Internet Protocol Address
---
The [[Open Systems Interconnection Model#Network Layer]] [[Network Protocol]] used to address data sent over the [[Internet]] or another [[Network]]

[[Open Systems Interconnection Model#Network Layer]]

IP addresses are assigned to [[Network Interface Card|Network Interface Controller]]s, not Computers.

[[Packet Switched Network]]
# Network Connections
![[Pasted image 20251113132209.png|500]]
# IPv4
4 decimal dotted quad / 4 octet / 32 bit
130.207.7.31 / 0x82CF071F / 0b10000010110011111100000101111111
IP address has [[Network]] and [[Host]] part
The network part is leading part of the IP, and what you get from [[AND]]ing with the [[Subnet#Subnet Mask]]

![[Subnet]]
## IPv4 Public/Private Ranges
## Public  
### Class A  
1.0.0.0 to 9.255.255.255  
11.0.0.0 to 126.255.255.255  
### Class B
128.0.0.0 to 172.15.255.255172.32.0.0 to 191.255.255.255  
### Class C  
192.0.0.0 to 192.167.255.255  
192.169.0.0 to 223.255.255.255  
## Private  
### Class A  
10.0.0.0 to 10.255.255.255  
### Class B  
172.16.0.0 to 172.31.255.255  
### Class C  
192.168.0.0 To 192.168.255.255

# IPv6
#todo

# Composition
## Unicast
A unicast address is a logical identifier representing a single network device. A unicast transmission sends IP packet data to a single destination.  
![[Pasted image 20251113132745.png|200]]
## Multicast
A multicast address is a logical identifier representing a group of network devices. A multicast transmission sends IP packet data to a group of destinations simultaneously. Streaming services benefit from this type of transmission, saving bandwidth.  
![[Pasted image 20251113132753.png|200]]
## Anycast
An anycast address is an address assigned to multiple network interfaces. An anycast transmission sends IP packet data to one network device in the group, usually the closest interface containing the anycast address. Anycast transmissions are usually used by servers in a content delivery network, or content distribution network (CDN). A content delivery network, or content distribution network (CDN), is a geographically distributed group of servers.  
![[Pasted image 20251113132759.png|200]]
  
## Broadcast
A broadcast address is a single IPv4 address used to send data to all devices on a network. A broadcast transmission sends IP packet data to all devices on the network simultaneously. Broadcasting causes excessive traffic, leading to collisions and network slowdowns. IPv6 does not support broadcast transmissions.
![[Pasted image 20251113132803.png|200]]