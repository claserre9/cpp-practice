# Templates and Generic Programming

## Overview
Templates enable writing code that works with any data type. They are the foundation of generic programming in C++. Templates can be used for functions and classes, allowing code reuse and type safety. The STL heavily relies on templates to implement containers and algorithms.

## Detailed Explanation
A template is a blueprint that the compiler uses to generate concrete functions or classes when needed. Function templates define operations that work for any type meeting certain requirements. Class templates, such as `std::vector<T>`, allow instantiation with different element types. Template parameters can be types or values, and from C++20, concepts let you constrain templates to types fulfilling specific properties.

## Code Examples
```cpp
#include <iostream>

template <typename T>
T add(T a, T b) { return a + b; }

int main() {
    std::cout << add(1, 2) << std::endl;      // int
    std::cout << add(1.5, 2.5) << std::endl;  // double
}
```

## Common Pitfalls & Warnings
- Template errors can produce long and confusing compiler messages.
- Defining templates in source files without exporting them can lead to linker errors; usually template definitions are in headers.

## Best Practices
- Keep templates simple and avoid unnecessary complexity.
- Use concepts (C++20) or `static_assert` to provide clearer error messages for invalid types.

## Mini Exercise
Create a function template `max_of` that returns the larger of two values using the `>` operator.

---
**Solution:**
```cpp
template <typename T>
T max_of(T a, T b) { return (a > b) ? a : b; }
```
