---
aliases:
  - IP Address
  - Logical Address
  - Internet Protocol Address
---
The [[Open Systems Interconnection Model#Network Layer]] [[Network Protocol]] used to address data sent over the [[Internet]] or another [[Network]]
[[Packet Switched Network]]
# Network Connections
![[Pasted image 20251113132209.png|500]]

# IP Header
a header containing connection and payload delivery details for a packet. An IP header uses one of two formats because two versions of IP exist:  
IP version 4 (IPv4) is the fourth version of IP, which provides internetworking capabilities on the [[Internet]] and [[Packet Switched Network]]s.
IP version 6 (IPv6) is the sixth version of IP, which provides internetworking capabilities on the internet and packet-switched networks.
## IPv4 Header
a 14-field, 20- to 60-byte header containing connection and payload delivery details for an IPv4 packet. Two IPv4 header fields contain an IPv4 address to uniquely identify a network device. An IPv4 address is a unique 32-bit numeric address divided into four 8-bit octets.
## IPv6 Header
an 8-field, 40-byte header containing connection and payload delivery details for an IPv6 packet. Two IPv6 header fields contain an IPv6 address to uniquely identify a network device. An IPv6 address is a unique 128-bit number assigned to a [[Network Interface Card|Network Interface Controller]].

# IPv4 Public/Private Ranges
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

# Composition
Network Component is first 8 bytes, first 6 of that are the prefix length which describe the public topology. The last 2 are the subnet ID that describe the private topology.  
The Last 8 bytes are called the node component and uniquely identify the device on a network.  
  
## Unicast
A unicast address is a logical identifier representing a single network device. A unicast transmission sends IP packet data to a single destination.  
![[Pasted image 20251113132745.png]]
  
## Multicast
A multicast address is a logical identifier representing a group of network devices. A multicast transmission sends IP packet data to a group of destinations simultaneously. Streaming services benefit from this type of transmission, saving bandwidth.  
![[Pasted image 20251113132753.png]]
## Anycast
An anycast address is an address assigned to multiple network interfaces. An anycast transmission sends IP packet data to one network device in the group, usually the closest interface containing the anycast address. Anycast transmissions are usually used by servers in a content delivery network, or content distribution network (CDN). A content delivery network, or content distribution network (CDN), is a geographically distributed group of servers.  
![[Pasted image 20251113132759.png]]
  
## Broadcast
A broadcast address is a single IPv4 address used to send data to all devices on a network. A broadcast transmission sends IP packet data to all devices on the network simultaneously. Broadcasting causes excessive traffic, leading to collisions and network slowdowns. IPv6 does not support broadcast transmissions.
![[Pasted image 20251113132803.png]]