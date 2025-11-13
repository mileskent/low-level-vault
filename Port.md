a 16-bit unsigned number that uniquely identifies a [[Network]] application or service on a host. Port addresses are included in a [[Transmission Control Protocol|TCP]] or [[User Datagram Protocol|UDP]] header to associate a [[Payload]] with a specific process or service. Using a distinct port for each process or service allows a single device to simultaneously recognize multiple traffic types. Ex: A device can simultaneously receive website traffic and email traffic because each service is associated with a unique port.

# Well-Known
Privileged/Reserved
0-1023 reserved for commonly used services
# Registered
1024-49151 registered with IANA for specific use
# Ephemeral
Private/Higher Number/Dynamic
49152+ dynamically assigned