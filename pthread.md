---
aliases:
  - pthreads
  - POSIX thread
  - POSIX threads
---

A standard feature of the POSIX standards-compliant [[C]] library that enables [[Multithreading]]

* Creating
	* `pthread_t pthread_create(top-level procedure, args)`
* Termination
	* return from top-level procedure
	* explicitly kill the thread
* Rendezvous
	* Creator can wait for children to complete before proceding
		* `pthread_join(child_tid)`
* Synchronization
	* [[Mutex]]
		* pthread_mutex_t lock
		* pthread_mutex_trylock(lock)
		* pthread_mutex_lock(&lock) // acquire lock
		* pthread_mutex_unlock(&lock) // release lock
	* [[Condition Variable]]
		* pthread_cond_wait: block for signal
		* pthread_cond_signal: signal one wiaitng thread
		* pthread_cond_broadcast: signal all waiting threads
