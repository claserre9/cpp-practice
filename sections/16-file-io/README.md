# File I/O

## Overview
File input/output allows programs to read from and write to files. The C++ standard library provides `std::ifstream` for reading, `std::ofstream` for writing, and `std::fstream` for both. Proper file handling includes checking that files opened successfully and closing them when done.

## Detailed Explanation
To open a file, construct an `std::ifstream` or `std::ofstream` with the file path. Use stream operators (`>>`, `<<`) or member functions (`read`, `write`) to transfer data. Streams automatically close when they go out of scope, but you can call `.close()` explicitly. When reading structured data, handle whitespace and delimiters carefully.

## Code Examples
```cpp
#include <fstream>
#include <iostream>

int main() {
    std::ofstream out{"data.txt"};
    out << "Hello\n";

    std::ifstream in{"data.txt"};
    std::string line;
    if (std::getline(in, line)) {
        std::cout << line << std::endl;
    }
}
```

## Common Pitfalls & Warnings
- Failing to check if a file stream opened successfully can result in silent errors.
- Forgetting to close a file (if not relying on RAII) may cause resource leaks.

## Best Practices
- Use RAII: let the file stream close automatically when it goes out of scope.
- Prefer `std::getline` for reading lines to avoid issues with spaces and tabs.

## Mini Exercise
Write code that reads integers from a file `nums.txt` and prints their sum.

---
**Solution:**
```cpp
std::ifstream in{"nums.txt"};
int value, sum = 0;
while (in >> value) sum += value;
std::cout << sum << std::endl;
```
