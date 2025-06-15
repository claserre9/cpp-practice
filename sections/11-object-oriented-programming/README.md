# Object-Oriented Programming

## Overview
Object-oriented programming (OOP) in C++ organizes code around objects that combine data and behavior. Key concepts include inheritance, polymorphism, and encapsulation. OOP allows code reuse and extensibility by creating class hierarchies and overriding behavior in derived classes.

## Detailed Explanation
- **Inheritance**: A derived class inherits members of a base class, enabling code reuse. Use `public` inheritance to model "is-a" relationships.
- **Polymorphism**: Achieved via virtual functions, allowing derived classes to override base class behavior. A pointer or reference to the base class can invoke the overridden function at runtime.
- **Virtual Functions**: Mark a member function with `virtual` to enable dynamic dispatch. Use `override` in derived classes to indicate overriding.

C++'s OOP features are powerful but require careful management of object lifetimes, especially when using base class pointers.

## Code Examples
```cpp
#include <iostream>

class Animal {
public:
    virtual void speak() const { std::cout << "generic sound"; }
    virtual ~Animal() = default; // virtual destructor
};

class Dog : public Animal {
public:
    void speak() const override { std::cout << "woof"; }
};

int main() {
    Animal* a = new Dog();
    a->speak(); // prints "woof"
    delete a;
}
```

## Common Pitfalls & Warnings
- Failing to declare a virtual destructor in a base class leads to undefined behavior when deleting derived objects via base pointers.
- Slicing occurs when assigning a derived object to a base object by value, losing derived members.

## Best Practices
- Mark overridden functions with `override` to catch errors at compile time.
- Use smart pointers (`std::unique_ptr`) for polymorphic objects to ensure automatic cleanup.

## Mini Exercise
Create a base class `Shape` with a virtual function `area()` and derive `Circle` with a radius member implementing `area`.

---
**Solution:**
```cpp
class Shape {
public:
    virtual double area() const = 0;
    virtual ~Shape() = default;
};

class Circle : public Shape {
public:
    double radius;
    explicit Circle(double r) : radius{r} {}
    double area() const override { return 3.14159 * radius * radius; }
};
```
