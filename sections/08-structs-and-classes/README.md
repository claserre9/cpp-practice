# Structs and Classes

## Overview
C++ supports user-defined types through structs and classes. Both encapsulate data and functions, but classes default to private members while structs default to public. Encapsulation enables information hiding, and constructors allow initialization of objects when they are created.

## Detailed Explanation
A struct or class defines a blueprint for objects. Access specifiers (`public`, `protected`, `private`) control how members are accessed. Constructors initialize object state, and can be overloaded to handle different initialization scenarios. Member functions operate on the object's data. C++ uses RAII (Resource Acquisition Is Initialization) to manage resources within objects, ensuring cleanup through destructors.

## Code Examples
```cpp
#include <string>
#include <iostream>

class Person {
public:
    Person(std::string n, int a) : name{std::move(n)}, age{a} {}
    void greet() const { std::cout << "Hi, I'm " << name << std::endl; }
private:
    std::string name;
    int age{};
};

int main() {
    Person p{"Alice", 30};
    p.greet();
}
```

## Common Pitfalls & Warnings
- Forgetting to define a destructor when managing resources can lead to leaks.
- Exposing data members as `public` breaks encapsulation and can cause invariants to be violated.

## Best Practices
- Keep data members private and provide public member functions for interaction.
- Use initializer lists in constructors to initialize members efficiently.

## Mini Exercise
Define a `struct Point` with `x` and `y` integers and a constructor initializing both.

---
**Solution:**
```cpp
struct Point {
    int x;
    int y;
    Point(int xVal, int yVal) : x{xVal}, y{yVal} {}
};
```
