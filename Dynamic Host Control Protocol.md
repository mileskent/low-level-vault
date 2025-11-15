---
aliases:
  - DHCP
---
Assigns dynamic [[IP|IP Address]]es and provides other essential IP information, such as [[Domain Name System|DNS]] servers and [[Default Gateway]] addresses.
Configured per [[Subnet]]. [[Host]]s can be configured manually; [[Server]]s usually are. [[Client]]s often depend on DHCP to "lend" them an [[IP|IP Address]]
Dynamic IP addresses are leased, and can expire. DHCP clients must renew their lease to maintain their claim to an IP address.

# Acquiring a Dynamic IP
![[Pasted image 20251115155005.png|400]]
* Client [[IP#Broadcast]]s a DHCPDISCOVER [[User Datagram Protocol|UDP]] message requesting an address
* A DHCP server will response with a DHCPOFFER message offering an IP address. It may assign an IP based on a preregistered [[MAC Address]], or it may supply an address from a pool of addresses reserved for this purpose
* If the client accepts, it sends a DHCPREQUEST message for that address, this is because the client may get multiple offers from multiple DHCP servers (unlike *me* in this job market)
* The DHCP server responds back with a DHCPACK message and the client can begin to use this IP address
