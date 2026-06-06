# Method Overloading vs Method Overriding in Java

| Feature              | Method Overloading                     | Method Overriding                                       |
| -------------------- | -------------------------------------- | ------------------------------------------------------- |
| Definition           | Same method name, different parameters | Same method name and parameters in parent & child class |
| Inheritance Required | ❌ No                                   | ✅ Yes                                                   |
| Parameters           | Must be different                      | Must be same                                            |
| Return Type          | Can be same or different*              | Must be same or covariant                               |
| Polymorphism Type    | Compile-time (Static)                  | Runtime (Dynamic)                                       |
| Method Binding       | Early Binding                          | Late Binding                                            |
| Purpose              | Increase readability                   | Change inherited behavior                               |

* Return type alone cannot distinguish overloaded methods.

---

# 1. Method Overloading

Multiple methods with the same name but different parameter lists.

```java
class Calculator {

    int add(int a, int b) {
        return a + b;
    }

    int add(int a, int b, int c) {
        return a + b + c;
    }

    double add(double a, double b) {
        return a + b;
    }
}
```

Usage:

```java
Calculator c = new Calculator();

System.out.println(c.add(10, 20));
System.out.println(c.add(10, 20, 30));
System.out.println(c.add(10.5, 20.5));
```

Output:

```text
30
60
31.0
```

### Rules for Overloading

✅ Change number of parameters

```java
void show(int a)
void show(int a, int b)
```

✅ Change type of parameters

```java
void show(int a)
void show(String s)
```

❌ Cannot overload only by return type

```java
int show()
double show() // Error
```

---

# 2. Method Overriding

A child class provides its own implementation of a parent class method.

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
Animal a = new Dog();
a.sound();
```

Output:

```text
Bark
```

### Rules for Overriding

✅ Same method name

✅ Same parameters

✅ Same or covariant return type

❌ Cannot reduce access level

```java
class A {
    public void show() {}
}

class B extends A {
    private void show() {} // Error
}
```

❌ Cannot override `final` methods

```java
final void show() {}
```

❌ Cannot override `static` methods (they are hidden)

---

# Compile-Time vs Runtime Example

## Overloading (Compile-Time)

```java
class Demo {
    void show(int a) {
        System.out.println("int");
    }

    void show(String s) {
        System.out.println("String");
    }
}
```

The compiler decides which method to call.

---

## Overriding (Runtime)

```java
Animal a = new Dog();
a.sound();
```

The JVM decides at runtime which method to execute.

---

# Real-World Example

### Overloading

```java
System.out.println(10);
System.out.println("Hello");
System.out.println(10.5);
```

`println()` is overloaded.

---

### Overriding

```java
List<String> list = new ArrayList<>();
list.add("Java");
```

Many collection classes override methods from parent classes/interfaces.

---

# Interview Answer (Short)

### Method Overloading

* Same method name
* Different parameter list
* No inheritance required
* Compile-time polymorphism

### Method Overriding

* Same method name and parameters
* Requires inheritance
* Runtime polymorphism
* Child class changes parent behavior

## Memory Trick

```text
Overloading = Same class + Different parameters

Overriding = Parent class method
             ↓
          Child class replaces implementation
```
