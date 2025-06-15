# Iterators and Ranges

## Overview
Iterators provide a uniform way to traverse containers, while ranges (C++20) extend this concept to compose sequences and algorithms more cleanly. Understanding iterators is essential for using STL containers and algorithms effectively.

## Detailed Explanation
- **Iterators**: Objects that behave like pointers, supporting operations such as increment (`++`) and dereference (`*`). Different iterator categories (input, output, forward, bidirectional, random access) offer varying capabilities.
- **Range-based For Loop**: Introduced in C++11, allows iterating over any container with `begin()` and `end()`.
- **Ranges (C++20)**: Provide range views and the pipe (`|`) syntax to combine algorithms lazily. `std::ranges::view` types can filter, transform, or take elements without copying.

## Code Examples
```cpp
#include <vector>
#include <ranges>
#include <iostream>

int main() {
    std::vector<int> data{1, 2, 3, 4, 5};
    for (int x : data) std::cout << x << ' ';

    auto evens = data | std::views::filter([](int x) { return x % 2 == 0; });
    for (int x : evens) std::cout << x << ' '; // 2 4
}
```

## Common Pitfalls & Warnings
- Using invalidated iterators after container modifications can cause crashes.
- Ranges require compiler support for C++20; ensure your toolchain is up to date.

## Best Practices
- Prefer range-based loops and algorithms over manual iterator manipulation for readability.
- Use `auto` with iterators to avoid verbose type names.

## Mini Exercise
Iterate over a `std::vector<int>` and print only the elements greater than 5 using ranges.

---
**Solution:**
```cpp
for (int x : vec | std::views::filter([](int n) { return n > 5; })) {
    std::cout << x << ' ';
}
```
