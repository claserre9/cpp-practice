# Control Flow

## Overview
Control flow statements determine the order in which instructions execute. In C++, the primary constructs are `if`/`else`, `switch`, loops (`for`, `while`, `do-while`), and control statements like `break` and `continue`. Proper control flow allows a program to make decisions and repeat operations efficiently.

## Detailed Explanation
- **Conditional Statements**: `if` checks a condition and executes a block if true. `else` or `else if` handle alternative paths. `switch` is used for selecting among multiple values of an integral or enumeration type.
- **Loops**: `for` loops are ideal when the number of iterations is known. `while` loops run as long as a condition remains true. `do-while` executes the body first and then checks the condition.
- **Control Statements**: `break` exits a loop or `switch`, while `continue` skips to the next iteration of a loop.

## Code Examples
```cpp
for (int i = 0; i < 5; ++i) {
    std::cout << i << " ";
}

int value = 2;
switch (value) {
    case 1: std::cout << "one"; break;
    case 2: std::cout << "two"; break;
    default: std::cout << "other";
}
```

## Common Pitfalls & Warnings
- Omitting `break` in a `switch` causes fall-through to the next case.
- Infinite loops can occur when loop conditions never become false.

## Best Practices
- Prefer `for` loops for counting iterations and range-based loops for containers.
- Keep loop bodies small and consider extracting complex logic into functions.

## Mini Exercise
Write a loop that prints the numbers 10 down to 1.

---
**Solution:**
```cpp
for (int i = 10; i >= 1; --i) {
    std::cout << i << " ";
}
```
