# Namespaces and Modules

## Overview
Namespaces prevent name collisions by grouping related identifiers. C++20 introduced modules as a way to organize code and speed up compilation compared to traditional headers. Both mechanisms help manage large code bases and improve build times.

## Detailed Explanation
- **Namespaces**: Define a scope for identifiers. Use the `namespace` keyword to create one and qualify names with `::`. Anonymous namespaces provide internal linkage within a translation unit.
- **Modules**: Replace the textual inclusion model of headers. A module interface file exports declarations, and implementation units provide definitions. Modules reduce compile times and avoid many header-related issues, but require compiler support (C++20).

## Code Examples
```cpp
// mylib.h
namespace mylib {
    void foo();
}

// mylib.cpp
#include "mylib.h"
void mylib::foo() {}
```

Module syntax (simplified):
```cpp
// mylib.ixx (interface)
export module mylib;
export void foo();

// mylib.cpp (implementation)
module mylib;
void foo() {}
```

## Common Pitfalls & Warnings
- Using `using namespace` in headers can pollute the global namespace.
- Modules are not yet universally supported; check your compiler and build system.

## Best Practices
- Keep namespaces short and meaningful, reflecting project structure.
- Prefer modules over headers when targeting C++20 and later for faster builds.

## Mini Exercise
Create a namespace `math` with a function `square` returning `x * x`.

---
**Solution:**
```cpp
namespace math {
    int square(int x) { return x * x; }
}
```
