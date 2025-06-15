# Advanced Smart Pointers

## Overview
Beyond `std::unique_ptr` and `std::shared_ptr`, C++ offers `std::weak_ptr` for non-owning references. Smart pointers manage dynamic memory automatically through RAII, preventing leaks and simplifying resource management. Choosing the right smart pointer is key to safe and efficient programs.

## Detailed Explanation
- **`std::unique_ptr`**: Exclusive ownership, cannot be copied, but can be moved. Use for strict resource ownership.
- **`std::shared_ptr`**: Shared ownership via reference counting. Memory is freed when the last `shared_ptr` referencing it is destroyed.
- **`std::weak_ptr`**: Non-owning pointer that references a `shared_ptr`-managed object, avoiding reference cycles that would otherwise cause leaks.

Custom deleters can be supplied to smart pointers to handle non-standard cleanup actions. Smart pointers impose minimal overhead compared to raw pointers while providing safety.

## Code Examples
```cpp
#include <memory>
#include <iostream>

int main() {
    auto sp = std::make_shared<int>(5);
    std::weak_ptr<int> wp = sp; // does not increase ref count

    if (auto locked = wp.lock()) {
        std::cout << *locked << std::endl;
    }
}
```

## Common Pitfalls & Warnings
- Creating cyclic references with `std::shared_ptr` leads to memory leaks; use `std::weak_ptr` to break cycles.
- Accessing a `weak_ptr` without checking `lock()` may result in a null pointer.

## Best Practices
- Use `std::unique_ptr` by default; switch to `std::shared_ptr` only when shared ownership is required.
- Keep the scope of smart pointers as small as possible to control lifetimes explicitly.

## Mini Exercise
Convert a raw pointer managing a dynamically allocated `double` into a `std::unique_ptr`.

---
**Solution:**
```cpp
double* raw = new double(3.14);
std::unique_ptr<double> up{raw};
```
