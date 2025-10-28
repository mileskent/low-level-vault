A lock is a general term for a synchronization mechanism that prevents multiple threads from accessing a resource simultaneously.
[[Mutex]]

# Coarse-Grained Lock
A lock that locks more than is required for correct logic, resulting in unneccessary serialization.

# Fine-Grained Lock
A lock that locks exactly what is required to maintain correct logic while maintain some level of [[Concurrency]]
