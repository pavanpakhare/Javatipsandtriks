# Java Modifiers Tutorial

Modifiers in Java are keywords used to control the **access**, **behavior**, and **lifecycle** of classes, methods, variables, and constructors.

There are two types of modifiers:

1. **Access Modifiers**
2. **Non-Access Modifiers**

---

# 1. Access Modifiers

Access modifiers control where a class member can be accessed.

| Modifier              | Same Class | Same Package | Subclass | Other Package |
| --------------------- | ---------- | ------------ | -------- | ------------- |
| `private`             | ✅          | ❌            | ❌        | ❌             |
| Default (no modifier) | ✅          | ✅            | ❌        | ❌             |
| `protected`           | ✅          | ✅            | ✅        | ❌*            |
| `public`              | ✅          | ✅            | ✅        | ✅             |

* Accessible through inheritance.

---

## Private Modifier

Accessible only within the same class.

```java
class Employee {
    private int salary = 50000;

    public void display() {
        System.out.println(salary);
    }
}
```

### Use Case

* Data hiding
* Encapsulation

---

## Default Modifier

No modifier is specified.

```java
class Employee {
    int age = 25;
}
```

Accessible only within the same package.

---

## Protected Modifier

Accessible within the package and by subclasses.

```java
class Animal {
    protected void sound() {
        System.out.println("Animal Sound");
    }
}
```

---

## Public Modifier

Accessible from anywhere.

```java
public class Main {
    public void display() {
        System.out.println("Hello");
    }
}
```

---

# 2. Non-Access Modifiers

These modify behavior rather than accessibility.

---

## final Modifier

Used to restrict changes.

### Final Variable

```java
final int MAX = 100;
```

Cannot be reassigned.

---

### Final Method

```java
class A {
    final void show() {
        System.out.println("Hello");
    }
}
```

Cannot be overridden.

---

### Final Class

```java
final class A {
}
```

Cannot be inherited.

---

## static Modifier

Belongs to the class instead of objects.

### Static Variable

```java
class Student {
    static String college = "ABC";
}
```

Shared by all objects.

---

### Static Method

```java
class MathUtil {
    static int square(int x) {
        return x * x;
    }
}
```

Call without creating an object.

```java
System.out.println(MathUtil.square(5));
```

Output:

```
25
```

---

## abstract Modifier

Used for incomplete classes and methods.

### Abstract Class

```java
abstract class Animal {
    abstract void sound();
}
```

Cannot create objects directly.

---

### Abstract Method

```java
class Dog extends Animal {
    void sound() {
        System.out.println("Bark");
    }
}
```

Must be implemented by subclasses.

---

## synchronized Modifier

Allows only one thread at a time to execute a method.

```java
class Counter {
    synchronized void increment() {
        // thread-safe code
    }
}
```

Used in multithreading.

---

## volatile Modifier

Ensures a variable's value is always read from main memory.

```java
class Shared {
    volatile boolean running = true;
}
```

Used in multithreaded applications.

---

## transient Modifier

Prevents a variable from being serialized.

```java
class User implements Serializable {
    String name;
    transient String password;
}
```

`password` will not be saved during serialization.

---

## native Modifier

Indicates a method is implemented in another language (usually C/C++).

```java
public native void display();
```

Used with JNI (Java Native Interface).

---

## strictfp Modifier

Ensures consistent floating-point calculations across platforms.

```java
strictfp class Calculator {
}
```

Rarely used in modern Java.

---

# Which Modifiers Can Be Used Together?

| Modifier     | Class         | Method | Variable |
| ------------ | ------------- | ------ | -------- |
| public       | ✅             | ✅      | ✅        |
| private      | ❌ (top-level) | ✅      | ✅        |
| protected    | ❌ (top-level) | ✅      | ✅        |
| static       | ❌ (top-level) | ✅      | ✅        |
| final        | ✅             | ✅      | ✅        |
| abstract     | ✅             | ✅      | ❌        |
| synchronized | ❌             | ✅      | ❌        |
| volatile     | ❌             | ❌      | ✅        |
| transient    | ❌             | ❌      | ✅        |
| native       | ❌             | ✅      | ❌        |
| strictfp     | ✅             | ✅      | ❌        |

---

# Common Interview Questions

### Can a class be `final` and `abstract`?

❌ No

```java
final abstract class A {
}
```

A class cannot be both:

* `abstract` → must be inherited
* `final` → cannot be inherited

---

### Can a constructor be `final`?

❌ No

Constructors are never inherited.

---

### Can a method be `static` and `abstract`?

❌ No

```java
static abstract void show();
```

Invalid because:

* `static` belongs to class
* `abstract` requires overriding by objects

---

### Can a variable be `abstract`?

❌ No

Only classes and methods can be abstract.

---

# Quick Revision Cheat Sheet

```text
public      -> Accessible everywhere
private     -> Accessible only inside class
protected   -> Package + subclass access
default     -> Package access only

final       -> Cannot change/override/inherit
static      -> Belongs to class
abstract    -> Incomplete implementation
synchronized-> Thread-safe method
volatile    -> Read/write from main memory
transient   -> Skip serialization
native      -> Implemented in C/C++
strictfp    -> Consistent floating-point calculations
```

### Interview Rule

* **Access Modifiers** → Control visibility (`public`, `private`, `protected`, default).
* **Non-Access Modifiers** → Control behavior (`final`, `static`, `abstract`, `synchronized`, `volatile`, `transient`, `native`, `strictfp`).
