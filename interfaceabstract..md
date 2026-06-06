# Difference Between Interface, Abstract Class, and Concrete Class

| Feature         | Interface                   | Abstract Class         | Concrete Class          |
| --------------- | --------------------------- | ---------------------- | ----------------------- |
| Object Creation | ❌ Cannot create             | ❌ Cannot create        | ✅ Can create            |
| Methods         | Abstract + Default + Static | Abstract + Concrete    | Concrete methods        |
| Variables       | `public static final` only  | Any type               | Any type                |
| Constructor     | ❌ No                        | ✅ Yes                  | ✅ Yes                   |
| Inheritance     | Multiple interfaces         | Single abstract class  | Single class            |
| Purpose         | Define contract             | Partial implementation | Complete implementation |
| Keyword         | `interface`                 | `abstract class`       | `class`                 |

---

# 1. Interface

An interface defines **what a class should do**, but not how.

```java
interface Animal {
    void sound();
}
```

Implementation:

```java
class Dog implements Animal {
    public void sound() {
        System.out.println("Bark");
    }
}
```

Usage:

```java
Animal a = new Dog();
a.sound();
```

Output:

```text
Bark
```

### Features

* Supports multiple inheritance
* Methods are public and abstract by default
* Variables are `public static final`

---

# 2. Abstract Class

An abstract class provides **partial implementation**.

```java
abstract class Animal {

    abstract void sound();

    void eat() {
        System.out.println("Eating");
    }
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
d.eat();
```

Output:

```text
Bark
Eating
```

### Features

* Can have abstract and concrete methods
* Can have constructors
* Can have instance variables

---

# 3. Concrete Class

A normal class with complete implementation.

```java
class Dog {

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

### Features

* Can create objects directly
* All methods implemented
* Most commonly used class type

---

# Real-World Example

## Interface (Contract)

```java
interface Payment {
    void pay();
}
```

---

## Abstract Class (Common Functionality)

```java
abstract class OnlinePayment implements Payment {

    void validateUser() {
        System.out.println("User Validated");
    }
}
```

---

## Concrete Class (Actual Implementation)

```java
class UpiPayment extends OnlinePayment {

    public void pay() {
        System.out.println("Payment Successful");
    }
}
```

Usage:

```java
UpiPayment p = new UpiPayment();

p.validateUser();
p.pay();
```

Output:

```text
User Validated
Payment Successful
```

---

# When to Use Which?

### Use Interface When

* Multiple classes follow the same contract
* You need multiple inheritance

Example:

```java
interface Flyable {
    void fly();
}
```

---

### Use Abstract Class When

* Some common code can be shared
* Some methods should be forced

Example:

```java
abstract class Vehicle {
    abstract void start();

    void stop() {
        System.out.println("Stopped");
    }
}
```

---

### Use Concrete Class When

* Everything is fully implemented
* Objects need to be created

Example:

```java
class Car {
    void start() {
        System.out.println("Car Started");
    }
}
```

---

# Interview Answer (Short)

* **Interface** → Defines a contract; supports multiple inheritance; mostly method declarations.
* **Abstract Class** → Provides partial implementation; can contain both abstract and concrete methods.
* **Concrete Class** → Fully implemented class; objects can be created directly.

### Easy Memory Trick

```text
Interface      = WHAT to do
Abstract Class = WHAT + SOME HOW
Concrete Class = COMPLETE HOW
```
