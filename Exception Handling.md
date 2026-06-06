# Java Exception Handling Tutorial

Exception Handling is a mechanism to handle runtime errors so that the program can continue execution normally.

---

# What is an Exception?

An exception is an event that disrupts the normal flow of a program.

Example:

```java
int a = 10;
int b = 0;

System.out.println(a / b);
```

Output:

```text
Exception in thread "main" java.lang.ArithmeticException: / by zero
```

---

# Why Do We Need Exception Handling?

Without exception handling:

```java
System.out.println("Start");

int result = 10 / 0;

System.out.println("End");
```

Output:

```text
Start
Exception in thread "main" ...
```

The program terminates immediately.

With exception handling:

```java
try {
    int result = 10 / 0;
} catch (ArithmeticException e) {
    System.out.println("Cannot divide by zero");
}

System.out.println("Program Continues");
```

Output:

```text
Cannot divide by zero
Program Continues
```

---

# Exception Hierarchy

```text
Object
  │
  └── Throwable
       │
       ├── Error
       │    ├── StackOverflowError
       │    ├── OutOfMemoryError
       │    └── VirtualMachineError
       │
       └── Exception
            │
            ├── RuntimeException
            │    ├── ArithmeticException
            │    ├── NullPointerException
            │    ├── ArrayIndexOutOfBoundsException
            │    ├── NumberFormatException
            │    ├── ClassCastException
            │    └── IllegalArgumentException
            │
            ├── IOException
            │    ├── FileNotFoundException
            │    └── EOFException
            │
            ├── SQLException
            │
            └── InterruptedException
```

---

# Throwable

The root class of Java's exception hierarchy.

```java
Throwable t;
```

Everything that can be thrown inherits from `Throwable`.

Two major categories:

1. Error
2. Exception

---

# Error

Errors are serious problems generally not handled by applications.

Examples:

```java
StackOverflowError
OutOfMemoryError
```

Example:

```java
public class Main {

    static void test() {
        test();
    }

    public static void main(String[] args) {
        test();
    }
}
```

Output:

```text
StackOverflowError
```

---

# Exception

Conditions that applications can handle.

Examples:

```java
IOException
SQLException
ArithmeticException
```

---

# Checked vs Unchecked Exceptions

| Feature                 | Checked     | Unchecked            |
| ----------------------- | ----------- | -------------------- |
| Checked at Compile Time | ✅           | ❌                    |
| Inherits From           | Exception   | RuntimeException     |
| Must Handle             | ✅           | ❌                    |
| Example                 | IOException | NullPointerException |

---

# Checked Exception Example

```java
import java.io.*;

class Demo {
    public static void main(String[] args) throws IOException {

        FileReader file =
                new FileReader("abc.txt");
    }
}
```

Compiler forces handling.

---

# Unchecked Exception Example

```java
int a = 10 / 0;
```

Output:

```text
ArithmeticException
```

No compile-time checking.

---

# try Block

Contains code that may throw exceptions.

```java
try {
    int result = 10 / 0;
}
```

---

# catch Block

Handles exceptions.

```java
try {
    int result = 10 / 0;
}
catch (ArithmeticException e) {
    System.out.println("Division by zero");
}
```

Output:

```text
Division by zero
```

---

# finally Block

Executes whether an exception occurs or not.

```java
try {
    int result = 10 / 0;
}
catch (Exception e) {
    System.out.println("Error");
}
finally {
    System.out.println("Always Executes");
}
```

Output:

```text
Error
Always Executes
```

---

# Multiple catch Blocks

```java
try {

    String s = null;

    System.out.println(s.length());

} catch (ArithmeticException e) {

    System.out.println("Arithmetic Error");

} catch (NullPointerException e) {

    System.out.println("Null Error");

}
```

Output:

```text
Null Error
```

---

# Multi-Catch

Java 7+

```java
try {

} catch (ArithmeticException | NullPointerException e) {

    System.out.println("Handled");

}
```

---

# throw Keyword

Used to manually create exceptions.

```java
int age = 15;

if(age < 18) {
    throw new ArithmeticException(
            "Not Eligible");
}
```

Output:

```text
Exception in thread "main"
Not Eligible
```

---

# throws Keyword

Used to declare exceptions.

```java
void readFile() throws IOException {

}
```

Caller must handle it.

---

# Difference: throw vs throws

| throw                    | throws                     |
| ------------------------ | -------------------------- |
| Used inside method       | Used in method declaration |
| Throws one exception     | Can declare multiple       |
| Creates exception object | Only declares possibility  |

Example:

```java
throw new IOException();
```

```java
void read() throws IOException
```

---

# Custom Exception

Create your own exception class.

```java
class InvalidAgeException
        extends Exception {

    InvalidAgeException(String msg) {
        super(msg);
    }
}
```

Usage:

```java
class Demo {

    static void vote(int age)
            throws InvalidAgeException {

        if(age < 18) {
            throw new InvalidAgeException(
                    "Age must be 18+");
        }
    }

    public static void main(String[] args) {

        try {
            vote(15);
        } catch (InvalidAgeException e) {
            System.out.println(e.getMessage());
        }
    }
}
```

Output:

```text
Age must be 18+
```

---

# Common Runtime Exceptions

## ArithmeticException

```java
int a = 10 / 0;
```

---

## NullPointerException

```java
String s = null;
System.out.println(s.length());
```

---

## ArrayIndexOutOfBoundsException

```java
int[] arr = {1,2,3};

System.out.println(arr[5]);
```

---

## NumberFormatException

```java
int x = Integer.parseInt("abc");
```

---

## ClassCastException

```java
Object obj = "Java";

Integer i = (Integer) obj;
```

---

# Exception Handling Flow

```text
try
 │
 ├── No Exception
 │      │
 │      └── finally
 │
 └── Exception
        │
        ├── catch
        │
        └── finally
```

---

# Best Practices

### Catch Specific Exceptions

✅ Good

```java
catch (IOException e)
```

❌ Avoid

```java
catch (Exception e)
```

---

### Never Ignore Exceptions

❌ Bad

```java
catch(Exception e) {
}
```

✅ Good

```java
catch(Exception e) {
    e.printStackTrace();
}
```

---

### Use Try-With-Resources

```java
import java.io.*;

try (FileReader file =
        new FileReader("test.txt")) {

    // use file

} catch (IOException e) {

    e.printStackTrace();
}
```

Resource closes automatically.

---

# Interview Questions

### What is the difference between Error and Exception?

| Error                     | Exception            |
| ------------------------- | -------------------- |
| Serious system problem    | Application problem  |
| Usually not recoverable   | Recoverable          |
| Example: OutOfMemoryError | Example: IOException |

---

### What is the difference between Checked and Unchecked Exceptions?

| Checked              | Unchecked            |
| -------------------- | -------------------- |
| Compile-time checked | Runtime checked      |
| Must handle          | Optional handling    |
| IOException          | NullPointerException |

---

### Can we have try without catch?

✅ Yes, with finally.

```java
try {
}
finally {
}
```

---

### Can finally execute after return?

✅ Yes.

```java
public static int test() {

    try {
        return 10;
    } finally {
        System.out.println("Finally");
    }
}
```

Output:

```text
Finally
```

---

# Quick Revision Cheat Sheet

```text
Throwable
 ├── Error
 └── Exception
       ├── Checked
       └── RuntimeException

try      -> risky code
catch    -> handle exception
finally  -> always executes
throw    -> manually throw exception
throws   -> declare exception
```

### Memory Trick

```text
throw  = "I am throwing an exception"

throws = "This method may throw an exception"

try     = Risky code
catch   = Handle error
finally = Cleanup code
```
