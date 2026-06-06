## Difference Between `final`, `finally`, and `finalize()` in Java

| Feature        | `final`                            | `finally`             | `finalize()`                                          |
| -------------- | ---------------------------------- | --------------------- | ----------------------------------------------------- |
| Type           | Keyword                            | Block                 | Method                                                |
| Purpose        | Restricts modification/inheritance | Executes cleanup code | Called by Garbage Collector before object destruction |
| Used With      | Variables, methods, classes        | `try-catch`           | Objects                                               |
| Mandatory?     | No                                 | No                    | No                                                    |
| Current Status | Commonly used                      | Commonly used         | Deprecated (avoid using)                              |

---

## 1. `final` Keyword

Used to make a variable constant, prevent method overriding, or prevent class inheritance.

### Final Variable

```java
final int AGE = 25;

// AGE = 30; // Compile-time error
```

### Final Method

```java
class A {
    final void show() {
        System.out.println("Hello");
    }
}

class B extends A {
    // void show() {} // Error: Cannot override final method
}
```

### Final Class

```java
final class A {
}

// class B extends A {} // Error
```

---

## 2. `finally` Block

A `finally` block executes whether an exception occurs or not.

```java
try {
    int x = 10 / 0;
} catch (Exception e) {
    System.out.println("Exception caught");
} finally {
    System.out.println("Finally block executed");
}
```

Output:

```
Exception caught
Finally block executed
```

### Use Cases

* Close files
* Close database connections
* Release resources

---

## 3. `finalize()` Method

Called by the Garbage Collector before an object is removed from memory.

```java
class Test {
    @Override
    protected void finalize() {
        System.out.println("Finalize called");
    }
}

public class Main {
    public static void main(String[] args) {
        Test t = new Test();
        t = null;

        System.gc();
    }
}
```

### Important

* `finalize()` execution is **not guaranteed**.
* Deprecated since Java 9.
* Modern Java uses:

  * `try-with-resources`
  * Explicit resource cleanup methods

---

## Interview Answer (Short)

* **`final`** → Used to restrict changes (constant variable, non-overridable method, non-inheritable class).
* **`finally`** → Block that always executes after `try-catch`.
* **`finalize()`** → Method called by the garbage collector before object destruction (deprecated and should be avoided).
