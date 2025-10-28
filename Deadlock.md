A [[Thread]] does not unlock a [[Mutex]] after locking it. This prevents all other threads from making progress.

# Livelock
A special case of deadlock in whic the threads change state while waiting, i.e. they are busy-waiting and wasting CPU resources while waiting infinitely