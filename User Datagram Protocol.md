---
aliases:
  - UDP
---
a [[Network Protocol]] used to provide non-guaranteed, connectionless data transport for communicating devices  

Anything that relies on lowest possible latency despite loss relies on UDP.

Exists in [[Open Systems Interconnection Model#Transport Layer]]

It has a [[Checksum]]. Besides that, no guarantees, unlike [[Transmission Control Protocol|TCP]]
# Datagram
Creates a "datagram" is the [[Protocol Data Unit|PDU]] created by UDP, and includes a UDP [[Header]]

# UDP Header
a 4-field, 8-byte header containing connection and payload delivery details for a datagram. A UDP header is used to provide best-effort payload delivery.