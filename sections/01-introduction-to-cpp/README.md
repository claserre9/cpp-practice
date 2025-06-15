# Introduction to C++

## Overview
C++ is a high-performance programming language used for system/software development, game engines, and more. To start programming in C++, you need a C++ compiler such as GCC or Clang. The typical workflow involves writing code in a text editor, compiling it, and running the resulting executable. Modern C++ standards (C++11 and onward) bring numerous improvements that make the language safer and more expressive.

## Detailed Explanation
C++ programs are typically composed of one or more source files (`.cpp`) and header files (`.h` or `.hpp`). Compiling a simple program involves translating the source code into machine code using a compiler. The most basic program is the "Hello World" example, which demonstrates the minimal structure required to output text to the console.

To set up a compiler:
1. Install a compiler such as GCC or Clang.
2. Use an IDE (like Visual Studio or CLion) or a text editor with a build system.
3. Compile code via the IDE or command line (`g++ main.cpp -o main`).

The standard entry point for a C++ program is the `main` function which returns `int` and may take command line arguments.

## Code Examples
```cpp
#include <iostream>

int main() {
    std::cout << "Hello, World!" << std::endl; // Print greeting
    return 0; // Exit status
}
```
Compile using:
```bash
g++ main.cpp -o main
./main
```
Output should be `Hello, World!`.

## Common Pitfalls & Warnings
- Forgetting to include `<iostream>` will lead to compilation errors for `std::cout`.
- Missing `return 0;` in `main` is allowed (C++ implicitly returns 0), but explicit return clarifies intent.

## Best Practices
- Use modern compilers with C++17 or newer support to take advantage of language improvements.
- Compile with warnings enabled (`-Wall -Wextra`) to catch potential issues early.

## Mini Exercise
Write a program that prints your name and age on separate lines.

---
**Solution:**
```cpp
#include <iostream>

int main() {
    std::cout << "Name: John" << std::endl;
    std::cout << "Age: 30" << std::endl;
    return 0;
}
```
