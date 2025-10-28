Need to link against [[pthread]]
[std::thread](https://en.cppreference.com/w/cpp/thread/thread.html) represents a [[Thread]]
[std::tread::join](https://en.cppreference.com/w/cpp/thread/thread/join.html) will wait until the thread it is called on is finished

Do multiple threads like
```
vector<thread> threads;
for (int i = 0; i < N; ++i)
	threads.push_back(thread(&func, i));
for (int i = 0; i < N; ++i)
	threads[i].join();
```

[std::jthread](https://en.cppreference.com/w/cpp/thread/jthread.html) implements std::thread but with [[Resource Aquisition is Initialization|RAII]], so join will be called at the end of the scope of the jthread

[std::mutex](https://en.cppreference.com/w/cpp/thread/mutex.html)See [[Mutex]]. Standard behavior is to lock the mutex at the beginning of the shared resource access, and to unlock it at end of the access. This makes sure two accessing won't happen concurrently, preventing a [[Data Race]]

[std::lock_guard](https://en.cppreference.com/w/cpp/thread/lock_guard.html) wraps std::mutex but with [[Resource Aquisition is Initialization|RAII]], so unlock will be called at the end of the scope of the lock_guard

[std::atomic](https://en.cppreference.com/w/cpp/atomic/atomic.html) wraps shared values, such that they can be modified atomically, ONLY if you use an overloaded operator of the atomic class, such as ++, +=, etc. If you use an interleaved expression you will not achieve an atomic operation!

[std::condition_variable](https://en.cppreference.com/w/cpp/thread/condition_variable.html) you will need a boolean condition, a condition variable, and a worker a reporter thread. The reporter thread will condition_variable::wait if the condition is not met. The worker thread will set the condition, and condition_variable::notify_one

[std::unique_lock](https://en.cppreference.com/w/cpp/thread/unique_lock.html) std::lock_guard but with more bells and whistles

[std::async](https://en.cppreference.com/w/cpp/thread/async.html) and [std::future](https://en.cppreference.com/w/cpp/thread/future.html)
Ex 1
```
std::future<int> async_function = std::async(&do_something, 0);
/* Do a bunch of work here in the main thread */
int result = async_function.get(); // calls wait
```
Ex 2
```
bool async_function() {
	// does some async work for main thread
	return success;
}
std::future<bool> async_function = std::async(std::launch::async, background_function);
std::future_status status;
while (true) {
	// Do main thread stuff, e.g. graphics or something
	// give async_function a maximum of 1 millisecond to 
	// return the result
	status = async_function.wait_for(std::chrono::milliseconds(1));
	if (status == std::future_status::ready) {
		break;
	}
}
```