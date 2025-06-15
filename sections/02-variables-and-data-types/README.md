# Variables and Data Types

## Overview
Variables store data used by a program. In C++, data types specify the kind of value a variable can hold, such as integers, floating-point numbers, and booleans. Starting with C++11, type deduction (`auto`) allows the compiler to infer a variable's type. Choosing the right data type is critical for memory usage and program correctness.

## Detailed Explanation
C++ has fundamental built-in types: `int`, `float`, `double`, `char`, and `bool`. Declaring a variable reserves space in memory, and each type has a size determined by the compiler and platform. Type modifiers (`unsigned`, `long`) adjust the range of numeric types. C++11 introduced `auto`, enabling the compiler to deduce the type based on the initializer. This is particularly useful for complex types or iterators. Initialization can be done using copy, direct, or uniform initialization with braces.

## Code Examples
```cpp
int count = 42;            // integer
float price = 3.99f;       // single-precision floating point
bool done = false;         // boolean flag
auto total = count + 5;    // type deduced as int

// Uniform initialization (C++11)
int numbers[]{1, 2, 3};
```

## Common Pitfalls & Warnings
- Uninitialized variables lead to undefined behavior; always initialize variables.
- Beware of narrowing conversions when using brace initialization (e.g., `int x{3.14};` is ill-formed).

## Best Practices
- Prefer `auto` when the type is obvious from the initializer or overly verbose.
- Use `const` when a variable should not be modified after initialization.

## Mini Exercise
Declare a `double` variable for temperature, set it to 98.6, and print it.

---
**Solution:**
```cpp
#include <iostream>

int main() {
    double temperature = 98.6;
    std::cout << temperature << std::endl;
}
```
