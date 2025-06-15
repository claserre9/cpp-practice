# STL Algorithms

## Overview
The Standard Template Library (STL) provides a rich set of algorithms for operating on containers. Common algorithms include sorting, searching, transforming, and accumulating. By combining algorithms with iterators, you can write concise and efficient code.

## Detailed Explanation
- **Sorting and Searching**: `std::sort` sorts elements in a range. `std::find` searches for a value. `std::binary_search` requires a sorted range and offers logarithmic complexity.
- **Transformations**: `std::transform` applies a function to each element in a range, storing the result elsewhere. `std::for_each` applies a function but ignores the return value.
- **Reduction**: `std::accumulate` sums or combines elements using a binary operation. C++17 introduced algorithms on parallel execution policies for performance.

Algorithms work with iterators, making them independent of container type.

## Code Examples
```cpp
#include <algorithm>
#include <numeric>
#include <vector>
#include <iostream>

int main() {
    std::vector<int> numbers{3, 1, 4, 1, 5};
    std::sort(numbers.begin(), numbers.end());

    int sum = std::accumulate(numbers.begin(), numbers.end(), 0);
    std::transform(numbers.begin(), numbers.end(), numbers.begin(),
                   [](int x) { return x * 2; });

    for (int n : numbers) std::cout << n << ' ';
    std::cout << "\nSum: " << sum << std::endl;
}
```

## Common Pitfalls & Warnings
- Passing incorrect iterator ranges (e.g., begin/end from different containers) causes undefined behavior.
- Using algorithms that expect sorted data on unsorted ranges can lead to incorrect results.

## Best Practices
- Prefer algorithms over manual loops to express intent clearly.
- Use the algorithm's return value (e.g., iterator positions) when provided.

## Mini Exercise
Use `std::count_if` to count how many numbers in a vector are even.

---
**Solution:**
```cpp
int evens = std::count_if(v.begin(), v.end(), [](int x) { return x % 2 == 0; });
```
