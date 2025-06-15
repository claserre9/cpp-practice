# Exception Handling

## Overview
Exceptions provide a way to handle error conditions and exceptional events in C++ programs. By using `try`, `catch`, and `throw`, developers can separate error handling from the main logic. Exception safety is an important aspect of writing robust code.

## Detailed Explanation
- **Throwing Exceptions**: Use `throw` followed by an expression (often an object) to signal an error.
- **Catching Exceptions**: Surround potentially throwing code with `try` and handle exceptions in `catch` blocks. Catch by const reference to avoid slicing.
- **`noexcept`**: A function marked `noexcept` promises not to throw. Violating this results in `std::terminate`.

Exceptions unwind the stack, calling destructors of automatic objects, so RAII helps manage resources even when exceptions occur.

## Code Examples
```cpp
#include <stdexcept>
#include <iostream>

int divide(int a, int b) {
    if (b == 0) throw std::runtime_error("divide by zero");
    return a / b;
}

int main() {
    try {
        std::cout << divide(4, 0);
    } catch (const std::exception& e) {
        std::cout << "Error: " << e.what() << std::endl;
    }
}
```

## Common Pitfalls & Warnings
- Throwing exceptions from destructors can lead to `std::terminate` if another exception is active.
- Catching by value can cause slicing and unnecessary copies.

## Best Practices
- Use standard exception types (`std::runtime_error`, etc.) or derive from `std::exception`.
- Keep exception handling localized and avoid broad catch-all blocks unless necessary.

## Mini Exercise
Write a function `safe_sqrt` that throws if given a negative number.

---
**Solution:**
```cpp
#include <stdexcept>
#include <cmath>

double safe_sqrt(double x) {
    if (x < 0) throw std::invalid_argument("negative");
    return std::sqrt(x);
}
```
