# condition variable
Any thread that intends to wait on a std::condition_variable must: 
1. Acquire a `std::unique_lock<std::mutex>` on the mutex used to protect the shared variable.
2. Do one of the following:
  a. Check the condition, in case it was already updated and notified.
  b. Call `wait`, `wait_for` or `wait_until` on the std::condition_variable (atomically releases the mutex and suspends thread execution until the condition is notified, a timeout expires, or a `spurious wakeup` occurs, then atomically acquires the mutex before returning).
  3. check the condition and resume waiting if not satisfied.
  
or:
  
  1. Use the predicated overload of `wait`, `wait_for`, and `wait_until`, which performs the same three steps.
