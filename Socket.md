---
aliases:
  - Network Socket
---
The [[Server]] sets up a *Listener* that's bound to a specific destination [[Port]]
The client makes a *Connect* request to the Listener
The Listener accepts the connection
Now the client and server can send data back and forth using send/recv system calls.
![[Pasted image 20251115153237.png|400]]