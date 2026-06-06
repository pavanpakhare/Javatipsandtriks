# Java OOPs (Object-Oriented Programming System) Complete Tutorial

## What is OOP?

**Object-Oriented Programming (OOP)** is a programming paradigm that organizes code using **objects and classes**.

Instead of writing everything as functions, OOP models real-world entities as objects.

Example:

```text
Car
 ├── Color
 ├── Speed
 └── Start()
```

Here:

* Color and Speed are properties (data)
* Start() is behavior (method)

---

# Why Do We Need OOP?

Without OOP:

```java
String car1Color = "Red";
int car1Speed = 100;

String car2Color = "Blue";
int car2Speed = 120;
```

As the application grows, code becomes difficult to manage.

With OOP:

```java
Car car1 = new Car();
Car car2 = new Car();
```

Benefits:

* Code Reusability
* Better Organization
* Easier Maintenance
* Security
* Scalability

---

# Class and Object

## What is a Class?

A class is a blueprint for creating objects.

Example:

```java
class Car {

    String color;
    int speed;

    void start() {
        System.out.println("Car Started");
    }
}
```

---

## What is an Object?

An object is an instance of a class.

```java
Car car = new Car();
```

Object creation:

```java
Car car = new Car();

car.color = "Red";
car.speed = 120;

car.start();
```

Output:

```text
Car Started
```

---

# Constructor

## Definition

A constructor is a special method that initializes objects.

Rules:

* Same name as class
* No return type

Example:

```java
class Student {

    String name;

    Student() {
        name = "Unknown";
    }
}
```

Usage:

```java
Student s = new Student();

System.out.println(s.name);
```

Output:

```text
Unknown
```

---

# Parameterized Constructor

```java
class Student {

    String name;

    Student(String name) {
        this.name = name;
    }
}
```

Usage:

```java
Student s = new Student("Pavan");

System.out.println(s.name);
```

Output:

```text
Pavan
```

---

# Four Pillars of OOP

```text
1. Encapsulation
2. Inheritance
3. Polymorphism
4. Abstraction
```

---

# 1. Encapsulation

## Definition

Encapsulation means binding data and methods together and hiding internal implementation.

## Why Needed?

To protect data from unauthorized access.

Example:

```java
class Employee {

    private int salary;

    public void setSalary(int salary) {
        this.salary = salary;
    }

    public int getSalary() {
        return salary;
    }
}
```

Usage:

```java
Employee e = new Employee();

e.setSalary(50000);

System.out.println(e.getSalary());
```

Output:

```text
50000
```

Benefits:

* Data Security
* Better Control
* Easy Maintenance

---

# 2. Inheritance

## Definition

Inheritance allows one class to acquire properties and methods of another class.

## Why Needed?

To reuse existing code.

Example:

```java
class Animal {

    void eat() {
        System.out.println("Eating");
    }
}

class Dog extends Animal {

    void bark() {
        System.out.println("Barking");
    }
}
```

Usage:

```java
Dog d = new Dog();

d.eat();
d.bark();
```

Output:

```text
Eating
Barking
```

---

# Types of Inheritance

## Single Inheritance

```text
Animal
   |
   Dog
```

---

## Multilevel Inheritance

```text
Animal
   |
Dog
   |
Puppy
```

---

## Hierarchical Inheritance

```text
      Animal
      /    \
    Dog    Cat
```

---

# 3. Polymorphism

## Definition

Polymorphism means one thing having multiple forms.

## Why Needed?

To improve flexibility and code reuse.

Two Types:

```text
1. Compile-Time Polymorphism
2. Run-Time Polymorphism
```

---

# Method Overloading

Same method name but different parameters.

```java
class Calculator {

    int add(int a, int b) {
        return a + b;
    }

    int add(int a, int b, int c) {
        return a + b + c;
    }
}
```

Usage:

```java
Calculator c = new Calculator();

System.out.println(c.add(2, 3));
System.out.println(c.add(2, 3, 4));
```

Output:

```text
5
9
```

---

# Method Overriding

```java
class Animal {

    void sound() {
        System.out.println("Animal Sound");
    }
}

class Dog extends Animal {

    @Override
    void sound() {
        System.out.println("Bark");
    }
}
```

Usage:

```java
Dog d = new Dog();

d.sound();
```

Output:

```text
Bark
```

---

# 4. Abstraction

## Definition

Abstraction hides implementation details and shows only essential features.

## Why Needed?

To reduce complexity.

Example:

```text
ATM Machine

You know:
- Withdraw
- Deposit

You don't know:
- Internal Banking Logic
```

---

# Abstract Class

```java
abstract class Animal {

    abstract void sound();
}
```

Subclass:

```java
class Dog extends Animal {

    void sound() {
        System.out.println("Bark");
    }
}
```

Usage:

```java
Dog d = new Dog();

d.sound();
```

Output:

```text
Bark
```

---

# Interface

## Definition

An interface provides 100% abstraction.

Example:

```java
interface Vehicle {

    void start();
}
```

Implementation:

```java
class Car implements Vehicle {

    public void start() {
        System.out.println("Car Started");
    }
}
```

Usage:

```java
Car c = new Car();

c.start();
```

Output:

```text
Car Started
```

---

# Abstract Class vs Interface

| Feature              | Abstract Class      | Interface         |
| -------------------- | ------------------- | ----------------- |
| Methods              | Abstract + Concrete | Abstract (mostly) |
| Variables            | Allowed             | Constants         |
| Constructor          | Yes                 | No                |
| Multiple Inheritance | No                  | Yes               |

---

# this Keyword

Refers to current object.

```java
class Student {

    String name;

    Student(String name) {
        this.name = name;
    }
}
```

---

# super Keyword

Refers to parent class.

```java
class Animal {

    String type = "Animal";
}

class Dog extends Animal {

    void display() {
        System.out.println(super.type);
    }
}
```

Output:

```text
Animal
```

---

# static Keyword

Belongs to class instead of object.

```java
class Student {

    static String college = "ABC";
}
```

Usage:

```java
System.out.println(Student.college);
```

Output:

```text
ABC
```

---

# final Keyword

Cannot be modified.

Variable:

```java
final int AGE = 18;
```

Method:

```java
final void show() {}
```

Class:

```java
final class A {}
```

---

# Object Class Methods

Every class inherits from Object.

Common Methods:

```java
toString()

equals()

hashCode()

getClass()
```

Example:

```java
System.out.println(obj.toString());
```

---

# OOP Interview Cheat Sheet

## Class

Blueprint for objects.

## Object

Instance of a class.

## Constructor

Initializes objects.

## Encapsulation

Data hiding using private variables.

## Inheritance

Code reusability.

## Polymorphism

Multiple forms of a method.

## Abstraction

Hide implementation details.

## Interface

Contract for classes.

## this

Current object.

## super

Parent object.

## static

Belongs to class.

## final

Cannot be changed.

---

# Most Asked Interview Questions

1. What is OOP?
2. Difference between Class and Object?
3. What is Encapsulation?
4. What is Inheritance?
5. What is Method Overloading?
6. What is Method Overriding?
7. Difference between Abstract Class and Interface?
8. What is Polymorphism?
9. What is Abstraction?
10. Difference between this and super?
11. What is static?
12. What is final?

---

# Final Summary

```text
Class          -> Blueprint
Object         -> Instance

Encapsulation  -> Security
Inheritance    -> Reusability
Polymorphism   -> Flexibility
Abstraction    -> Simplicity

Interface      -> Contract
Abstract Class -> Partial Abstraction

this           -> Current Object
super          -> Parent Object
static         -> Class Level
final          -> Constant
```
