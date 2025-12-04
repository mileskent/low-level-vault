When a [[Thread]] wakes up from waiting on a [[Condition Variable]] but finds that the condition it was waiting for is still not met

Always put your `cond_wait` in a while loop!
```
while (!condition_b) {
	pthread_cond_wait(&condition_var, &lock);
}
```
