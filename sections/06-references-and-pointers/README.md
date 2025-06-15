# References and Pointers

## Overview
C++ uses references and pointers to allow functions to access and modify data outside their local scope. References act as aliases to existing variables, while pointers store memory addresses explicitly. Understanding these concepts is essential for working with dynamic memory and efficient parameter passing.

## Detailed Explanation
- **References**: Once bound to an object, a reference cannot be reseated. They are often used for pass-by-reference parameters, enabling modification of the argument without copying. C++11 introduced rvalue references (`T&&`) for move semantics.
- **Pointers**: A pointer is a variable that holds a memory address. It can be reseated and can point to `nullptr` to represent no address. Dereferencing a pointer (`*ptr`) accesses the value at that address. Pointers are fundamental for dynamic memory management and interoperability with C APIs.

## Code Examples
```cpp
void increment(int& ref) { ++ref; }

int main() {
    int value = 5;
    increment(value);   // ref modifies value

    int* ptr = &value;  // pointer to value
    *ptr = 10;          // modify via pointer
}
```

## Common Pitfalls & Warnings
- Dereferencing a `nullptr` leads to undefined behavior.
- References must be initialized; they cannot be null or unbound.

## Best Practices
- Prefer references for parameters when the argument must not be null.
- Use smart pointers for dynamic memory instead of raw pointers when possible.

## Mini Exercise
Create a pointer to an integer, assign it the address of a variable, and print its value via dereferencing.

---
**Solution:**
```cpp
int number = 7;
int* ptr = &number;
std::cout << *ptr << std::endl; // prints 7
```
