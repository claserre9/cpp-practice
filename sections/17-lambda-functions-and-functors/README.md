# Lambda Functions and Functors

## Overview
Lambdas are anonymous function objects introduced in C++11, allowing inline, short-lived functions. Functors are objects that overload `operator()` to behave like functions. Both are useful for algorithms that require custom operations or predicates.

## Detailed Explanation
- **Lambda Syntax**: `[capture](params) -> return_type { body }`. Captures allow lambdas to access variables from the surrounding scope, either by copy or reference.
- **`std::function`**: A type-erasing wrapper that can hold any callable target, including lambdas and functors. It incurs some overhead but provides flexibility.
- **Functors**: Define a struct or class with `operator()` to encapsulate stateful behavior. They can be more efficient than `std::function` when inlined by the compiler.

## Code Examples
```cpp
#include <algorithm>
#include <functional>
#include <vector>
#include <iostream>

int main() {
    std::vector<int> nums{1, 2, 3, 4};
    int threshold = 2;

    // lambda with capture
    nums.erase(std::remove_if(nums.begin(), nums.end(),
                [threshold](int x) { return x <= threshold; }),
                nums.end());

    std::function<int(int)> square = [](int x) { return x * x; };
    std::cout << square(5) << std::endl; // 25
}
```

## Common Pitfalls & Warnings
- Dangling references may occur if captured references outlive the variables they reference.
- Capturing `this` implicitly may lead to unexpected behavior if the object is destroyed.

## Best Practices
- Capture only what you need and prefer explicit capture lists.
- Use `auto` for storing lambdas when possible; only use `std::function` when type erasure is needed.

## Mini Exercise
Write a lambda that adds two integers and assign it to `auto add`.

---
**Solution:**
```cpp
auto add = [](int a, int b) { return a + b; };
```
