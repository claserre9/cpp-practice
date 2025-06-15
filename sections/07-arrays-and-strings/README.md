# Arrays and Strings

## Overview
Arrays store sequences of elements of the same type, while strings represent sequences of characters. C++ provides C-style arrays and C-strings, but the standard library `std::array` and `std::string` offer safer and more convenient abstractions. Understanding how to use arrays and strings is fundamental for managing collections of data and text processing.

## Detailed Explanation
- **C-style Arrays**: Declared with a fixed size known at compile time. They do not track their own length and decay to pointers when passed to functions.
- **C-strings**: Null-terminated arrays of characters used by many C APIs. Manipulation requires manual memory management and caution to avoid buffer overflows.
- **`std::array`**: A container that wraps a fixed-size array and provides standard container semantics (size, iteration). Available since C++11.
- **`std::string`**: Manages dynamic character sequences, supporting concatenation, substring, and more. It handles memory allocation automatically.

## Code Examples
```cpp
#include <array>
#include <string>
#include <iostream>

std::array<int, 3> numbers{{1, 2, 3}}; // std::array
std::string greeting{"Hello"};        // std::string

int main() {
    numbers[0] = 10;
    greeting += ", World";
    std::cout << greeting << " size: " << greeting.size() << std::endl;
}
```

## Common Pitfalls & Warnings
- Exceeding array bounds is undefined behavior; always check indices.
- Forgetting the null terminator when working with C-strings can lead to runtime errors.

## Best Practices
- Prefer `std::array` or `std::vector` over raw arrays for safety and functionality.
- Use `std::string` or `std::string_view` instead of raw C-strings whenever possible.

## Mini Exercise
Create a `std::string` with value "C++" and append " rocks" to it, then print it.

---
**Solution:**
```cpp
std::string s{"C++"};
s += " rocks";
std::cout << s << std::endl; // prints "C++ rocks"
```
