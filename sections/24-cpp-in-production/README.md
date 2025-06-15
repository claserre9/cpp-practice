# C++ in Production

## Overview
Deploying C++ applications in production environments requires robust tooling, testing, and build systems. Key aspects include debugging tools, sanitizers, build automation with CMake, and incorporating unit tests to ensure code quality.

## Detailed Explanation
- **Debugging Tools**: Tools like `gdb` and Visual Studio's debugger help trace and fix issues. Compiler options (`-g`) include debug symbols.
- **Sanitizers**: Address Sanitizer (ASan), Undefined Behavior Sanitizer (UBSan), and others detect memory errors and undefined behavior at runtime.
- **Build Systems**: CMake is widely used to manage cross-platform builds, generating native makefiles or project files.
- **Unit Testing**: Frameworks like Google Test or Catch2 enable automated testing to catch regressions early.

Automation through continuous integration ensures consistent builds and test runs across environments.

## Code Examples
CMake `CMakeLists.txt` snippet:
```cmake
cmake_minimum_required(VERSION 3.10)
project(MyApp)
add_executable(myapp main.cpp)
target_compile_features(myapp PRIVATE cxx_std_17)
```

Google Test example:
```cpp
#include <gtest/gtest.h>

TEST(MathTest, Add) {
    EXPECT_EQ(2 + 2, 4);
}
```

## Common Pitfalls & Warnings
- Failing to enable compiler warnings can allow bugs to slip into production.
- Ignoring sanitizer output may lead to undetected memory errors.

## Best Practices
- Use continuous integration to build and test automatically.
- Compile with `-Wall -Wextra -Werror` and enable sanitizers in debug builds.

## Mini Exercise
Create a basic `CMakeLists.txt` for a project with a single source file `main.cpp`.

---
**Solution:**
```cmake
cmake_minimum_required(VERSION 3.10)
project(MyProject)
add_executable(main main.cpp)
```
