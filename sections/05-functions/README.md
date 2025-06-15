# Functions

## Overview
Functions encapsulate reusable logic in C++. They are declared with a return type, name, and parameters. Defining functions helps break a program into modular pieces. C++ supports function overloading and allows functions to be defined in headers or separate source files.

## Detailed Explanation
A function declaration (prototype) tells the compiler about the function's name, return type, and parameters. The definition includes the body of the function. Parameters can be passed by value or by reference, and default parameter values are allowed. Overloading permits multiple functions with the same name but different parameter lists. Functions can also be `constexpr` (evaluated at compile time) or `inline` for performance hints.

## Code Examples
```cpp
#include <iostream>

int add(int a, int b);          // declaration

int main() {
    std::cout << add(2, 3) << std::endl; // prints 5
}

int add(int a, int b) {         // definition
    return a + b;
}
```

## Common Pitfalls & Warnings
- Declaring a function but forgetting to define it causes linker errors.
- Mismatching function signatures (e.g., parameter types) between declaration and definition leads to compilation errors.

## Best Practices
- Keep functions short and focused on a single task.
- Use `const` for reference parameters that should not modify the argument.

## Mini Exercise
Create a function `square` that returns the square of an integer.

---
**Solution:**
```cpp
int square(int x) {
    return x * x;
}
```
