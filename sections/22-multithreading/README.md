# Multithreading

## Overview
Multithreading enables concurrent execution of code to utilize multiple CPU cores and manage asynchronous tasks. C++11 introduced the `<thread>` library, along with synchronization primitives like mutexes and condition variables. Proper synchronization is crucial to avoid data races and undefined behavior.

## Detailed Explanation
- **`std::thread`**: Represents a single thread of execution. A thread starts running when constructed with a callable object.
- **Mutexes**: `std::mutex` provides mutual exclusion to protect shared data. Use `std::lock_guard` or `std::unique_lock` for RAII-style locking.
- **Condition Variables**: Allow threads to wait for certain conditions. Combined with mutexes, they help implement producer-consumer patterns.

Thread communication requires careful design to avoid deadlocks and ensure thread safety.

## Code Examples
```cpp
#include <thread>
#include <mutex>
#include <iostream>

std::mutex m;
int counter = 0;

void work() {
    for (int i = 0; i < 1000; ++i) {
        std::lock_guard<std::mutex> lock(m);
        ++counter;
    }
}

int main() {
    std::thread t1(work);
    std::thread t2(work);
    t1.join();
    t2.join();
    std::cout << counter << std::endl;
}
```

## Common Pitfalls & Warnings
- Forgetting to join or detach a thread results in termination or resource leaks.
- Data races occur when multiple threads access shared data without proper synchronization.

## Best Practices
- Use RAII wrappers (`std::lock_guard`) for locks to ensure mutexes are released.
- Keep critical sections small to minimize contention and improve scalability.

## Mini Exercise
Spawn two threads that each print "Hello" to the console.

---
**Solution:**
```cpp
std::thread a([]{ std::cout << "Hello"; });
std::thread b([]{ std::cout << "Hello"; });
a.join();
b.join();
```
