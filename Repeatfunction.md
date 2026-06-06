# Java `String.repeat()` Tutorial

`repeat()` is a String method introduced in **Java 11**.

It creates a new string by repeating the original string a specified number of times.

---

## Syntax

```java
String result = str.repeat(count);
```

- `str` → String to repeat
- `count` → Number of repetitions

---

## Basic Example

```java
String s = "*";

System.out.println(s.repeat(5));
```

Output:

```text
*****
```

---

## Repeat a Word

```java
System.out.println("Hi ".repeat(3));
```

Output:

```text
Hi Hi Hi
```

---

## Repeat Spaces

```java
System.out.println(" ".repeat(5) + "#");
```

Output:

```text
     #
```

This is commonly used for right-aligned patterns.

---

## Pattern Examples

### Left Triangle

```java
for (int i = 1; i <= 5; i++) {
    System.out.println("*".repeat(i));
}
```

Output:

```text
*
**
***
****
*****
```

---

### Right Triangle

```java
int n = 5;

for (int i = 1; i <= n; i++) {
    System.out.println(" ".repeat(n - i) + "*".repeat(i));
}
```

Output:

```text
    *
   **
  ***
 ****
*****
```

---

### Pyramid

```java
int n = 5;

for (int i = 1; i <= n; i++) {
    System.out.println(
        " ".repeat(n - i)
        + "*".repeat(2 * i - 1)
    );
}
```

Output:

```text
    *
   ***
  *****
 *******
*********
```

---

## Repeat Numbers

```java
System.out.println("1".repeat(5));
```

Output:

```text
11111
```

---

## Empty Repeat

```java
System.out.println("*".repeat(0));
```

Output:

```text

```

Returns an empty string.

---

## Invalid Repeat

```java
System.out.println("*".repeat(-1));
```

Output:

```text
Exception in thread "main"
java.lang.IllegalArgumentException
```

The count cannot be negative.

---

## How `repeat()` Replaces Loops

Without `repeat()`:

```java
for (int i = 0; i < 5; i++) {
    System.out.print("*");
}
```

With `repeat()`:

```java
System.out.println("*".repeat(5));
```

Much shorter and cleaner.

---

## Common Competitive Programming Uses

### Right Alignment

```java
" ".repeat(n - i)
```

### Triangle

```java
"*".repeat(i)
```

### Pyramid

```java
"*".repeat(2 * i - 1)
```

### Horizontal Line

```java
System.out.println("-".repeat(50));
```

---

## Interview Notes

- Available from **Java 11+**
- Returns a **new String**
- Original string is unchanged
- Throws `IllegalArgumentException` for negative counts

---

## Cheat Sheet

```java
"*".repeat(5);      // *****

"#".repeat(3);      // ###

" ".repeat(4);      // four spaces

"Hi".repeat(2);     // HiHi

"-".repeat(20);     // --------------------
```

For pattern questions, `" ".repeat(...)` and `"*".repeat(...)` are the two most useful forms to remember.
