# Move Semantics and Rvalue References

## Overview
Move semantics, introduced in C++11, optimize performance by transferring resources from temporary objects rather than copying them. Rvalue references (`T&&`) enable move constructors and move assignment operators, allowing efficient handling of expensive-to-copy objects.

## Detailed Explanation
- **Rvalue References**: Bind to temporaries or objects that can be moved from. They are used to implement move constructors and move assignment operators.
- **`std::move`**: A utility that casts an lvalue to an rvalue reference, signaling that the object's resources can be moved.
- **Move Constructor/Assignment**: Classes managing resources (e.g., dynamic memory) should define move operations to transfer ownership. After moving, the source object should be left in a valid but unspecified state.

## Code Examples
```cpp
#include <vector>
#include <iostream>

int main() {
    std::vector<int> a{1,2,3};
    std::vector<int> b = std::move(a); // move contents of a into b
    std::cout << "size of a: " << a.size() << std::endl; // 0
}
```

## Common Pitfalls & Warnings
- Using moved-from objects without reinitializing can lead to unexpected behavior.
- Declaring a move operation incorrectly (e.g., forgetting `&&`) prevents moves and may cause copies instead.

## Best Practices
- Mark move constructors `noexcept` when possible for better container performance.
- Avoid creating unnecessary temporaries; use `emplace` methods on containers to construct elements in place.

## Mini Exercise
Implement a simple move constructor for a class owning a `std::string` member.

---
**Solution:**
```cpp
class Wrapper {
public:
    std::string data;
    Wrapper(std::string d) : data{std::move(d)} {}
    Wrapper(Wrapper&& other) noexcept : data{std::move(other.data)} {}
};
```
