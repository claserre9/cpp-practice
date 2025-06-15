# Standard Library Containers

## Overview
The C++ Standard Library provides a suite of containers that manage collections of objects. These include sequence containers (`std::vector`, `std::list`, `std::deque`) and associative containers (`std::map`, `std::set`, `std::unordered_map`, etc.). Using these containers helps avoid manual memory management and provides common algorithms for manipulation.

## Detailed Explanation
- **`std::vector`**: Dynamic array that resizes automatically. Provides fast random access and is the go-to container for most use cases.
- **`std::map` / `std::set`**: Ordered associative containers implemented as balanced trees. Offer log-time insertion and lookup.
- **`std::unordered_map` / `std::unordered_set`**: Hash-table-based containers providing average constant-time operations.
- **`std::list`**: Doubly linked list allowing fast insertion/removal anywhere, but with slower traversal.

Containers work seamlessly with iterators and algorithms from the STL, and they handle resource management via RAII.

## Code Examples
```cpp
#include <vector>
#include <map>
#include <iostream>

int main() {
    std::vector<int> nums{1, 2, 3};
    nums.push_back(4);
    for (int n : nums) std::cout << n << ' ';

    std::map<std::string, int> ages{{"Alice", 30}, {"Bob", 25}};
    ages["Charlie"] = 35;
    std::cout << "\nBob is " << ages["Bob"] << std::endl;
}
```

## Common Pitfalls & Warnings
- Iterators become invalid after modifying a container in certain ways (e.g., inserting into a `vector` may reallocate memory).
- Using `operator[]` on a map creates a new element if the key does not exist.

## Best Practices
- Choose the container that best matches your performance requirements and access patterns.
- Prefer range-based for loops and STL algorithms for readability.

## Mini Exercise
Create an `std::unordered_set` of strings and insert three names, then check if one of them exists.

---
**Solution:**
```cpp
#include <unordered_set>
#include <iostream>

std::unordered_set<std::string> names{"Ann", "Bob", "Cara"};
if (names.contains("Bob")) {
    std::cout << "Found Bob" << std::endl;
}
```
