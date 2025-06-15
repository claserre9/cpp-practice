# Function Overloading and Defaults

## Overview
C++ allows multiple functions with the same name but different parameter lists, known as function overloading. Default parameters provide fallback values when arguments are omitted. These features enable flexible APIs and simplify function interfaces.

## Detailed Explanation
Overload resolution selects the correct function based on the number and types of arguments. This happens at compile time. Care must be taken to avoid ambiguous overloads. Default parameters are specified in function declarations and must appear at the end of the parameter list. They reduce the need for multiple overloads when only a few parameters vary.

## Code Examples
```cpp
#include <iostream>

void greet() { std::cout << "Hello"; }
void greet(const std::string& name) { std::cout << "Hello, " << name; }

void log(const std::string& msg, int level = 0) {
    std::cout << "level " << level << ": " << msg << std::endl;
}

int main() {
    greet();
    greet("Bob");
    log("init");       // uses default level 0
    log("error", 2);
}
```

## Common Pitfalls & Warnings
- Ambiguous calls occur when the compiler cannot determine the best overload.
- Default arguments should be specified either in the declaration or definition, not both.

## Best Practices
- Avoid unnecessary overloads; use default parameters where appropriate.
- Prefer passing const references for expensive-to-copy types.

## Mini Exercise
Write overloaded `print` functions: one taking `int`, another taking `std::string`.

---
**Solution:**
```cpp
void print(int x) { std::cout << x; }
void print(const std::string& s) { std::cout << s; }
```
