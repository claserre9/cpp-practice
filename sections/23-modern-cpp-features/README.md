# Modern C++ Features

## Overview
Modern C++ (C++11 and later) introduced numerous features that simplify code and enhance performance. Highlights include `auto` type deduction, `decltype`, `constexpr` functions, and structured bindings. Embracing modern features leads to more expressive, safer, and maintainable code.

## Detailed Explanation
- **`auto`**: Allows the compiler to deduce the type from the initializer.
- **`decltype`**: Yields the type of an expression without evaluating it.
- **`constexpr`**: Specifies that a function or variable can be evaluated at compile time, enabling optimizations.
- **Structured Bindings**: Introduced in C++17, they decompose objects into named variables.
Other modern features include range-based loops, smart pointers, and the `[[nodiscard]]` attribute for safety.

## Code Examples
```cpp
#include <tuple>
#include <iostream>

constexpr int square(int x) { return x * x; }

int main() {
    auto value = 5;                // auto deduces int
    decltype(value) another = 6;   // same type as value
    constexpr int n = square(3);   // computed at compile time

    std::tuple<int, double> t{1, 2.5};
    auto [i, d] = t;               // structured binding
    std::cout << i << ", " << d << std::endl;
}
```

## Common Pitfalls & Warnings
- Overusing `auto` can make code harder to read when the type is not obvious.
- `constexpr` functions have restrictions: they must contain only one return statement pre-C++14.

## Best Practices
- Use modern features to reduce boilerplate but keep readability in mind.
- Combine `constexpr` with templates for compile-time computations when possible.

## Mini Exercise
Write a `constexpr` function `cube` that returns the cube of its argument.

---
**Solution:**
```cpp
constexpr int cube(int x) { return x * x * x; }
```
