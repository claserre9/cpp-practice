# Dynamic Memory Management

## Overview
Dynamic memory allows programs to allocate storage at runtime. In C++, this is traditionally done with `new` and `delete`, but modern C++ encourages the use of smart pointers (`std::unique_ptr`, `std::shared_ptr`) for safer resource management. Proper dynamic memory handling prevents leaks and dangling pointers.

## Detailed Explanation
- **`new` and `delete`**: `new` allocates memory from the free store and returns a pointer. `delete` releases that memory. For arrays, use `new[]` and `delete[]`.
- **Smart Pointers**: `std::unique_ptr` represents exclusive ownership of dynamically allocated memory, automatically deleting the object when it goes out of scope. `std::shared_ptr` allows shared ownership through reference counting, and `std::weak_ptr` provides a non-owning view.

Using RAII with smart pointers ensures that memory is released even if exceptions occur. This approach is preferred over manual `new`/`delete` because it reduces errors and simplifies code.

## Code Examples
```cpp
#include <memory>
#include <iostream>

int main() {
    auto ptr = std::make_unique<int>(42); // unique_ptr manages memory
    std::cout << *ptr << std::endl;

    std::shared_ptr<int> sp1 = std::make_shared<int>(10);
    std::shared_ptr<int> sp2 = sp1; // shared ownership
    std::cout << sp1.use_count() << std::endl; // prints 2
}
```

## Common Pitfalls & Warnings
- Forgetting to `delete` memory allocated with `new` leads to leaks.
- Mixing `new` with `delete[]` or vice versa results in undefined behavior.

## Best Practices
- Prefer smart pointers or standard containers (`std::vector`, `std::string`) over raw pointers.
- Avoid manual memory management unless absolutely necessary for performance reasons.

## Mini Exercise
Allocate an array of 5 integers with `std::unique_ptr` and initialize them to zero.

---
**Solution:**
```cpp
auto arr = std::make_unique<int[]>(5);
for (int i = 0; i < 5; ++i) arr[i] = 0;
```
