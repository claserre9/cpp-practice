# Operators and Expressions

## Overview
Operators in C++ perform actions on operands and form expressions. These include arithmetic, logical, relational, and bitwise operators. Understanding operator precedence and associativity is crucial for writing correct expressions. C++ provides both built-in operators and the ability to overload them for user-defined types.

## Detailed Explanation
Arithmetic operators (`+`, `-`, `*`, `/`, `%`) manipulate numerical values. Logical operators (`&&`, `||`, `!`) combine boolean expressions. Relational operators (`<`, `>`, `==`, `!=`) compare values. Bitwise operators (`&`, `|`, `^`, `~`, `<<`, `>>`) operate on the binary representation of integers. Operator precedence determines the order in which operations are evaluated, while associativity resolves the order for operators of the same precedence. Parentheses can be used to explicitly specify evaluation order.

## Code Examples
```cpp
int a = 5, b = 2;
int sum = a + b;          // 7
int mod = a % b;          // 1
bool result = (a > 3) && (b < 3); // true

int bit = a << 1;         // 10 in decimal (shift left)
```

## Common Pitfalls & Warnings
- Division by zero leads to undefined behavior; ensure the divisor is nonzero.
- Bitwise operators on signed integers can produce unexpected results due to sign bits.

## Best Practices
- Use parentheses to clarify complex expressions, even when not strictly necessary.
- Prefer explicit comparisons (`if (x == 0)`) over relying on implicit conversions to bool.

## Mini Exercise
Compute the average of two integers using arithmetic operators.

---
**Solution:**
```cpp
#include <iostream>

int main() {
    int x = 7;
    int y = 3;
    double avg = (x + y) / 2.0; // ensure floating-point division
    std::cout << avg << std::endl;
}
```
