# Java Threads Complete Tutorial

A **Thread** is the smallest unit of execution in a program.

Normally Java executes code sequentially using a single thread:

```text
Main Thread
    |
    +--> Task 1
    +--> Task 2
    +--> Task 3
```

With multiple threads:

```text
Main Thread
    |
    +--> Thread A
    +--> Thread B
    +--> Thread C
```

Tasks can run concurrently.

---

# Why Use Threads?

- Multitasking
- Background tasks
- File downloads
- Games
- Web servers
- Parallel processing

---

# Creating a Thread

There are two common ways.

---

# Method 1: Extend Thread Class

```java
class MyThread extends Thread {

    public void run() {
        System.out.println("Thread is running");
    }
}

public class Main {
    public static void main(String[] args) {
        MyThread t = new MyThread();
        t.start();
    }
}
```

Output:

```text
Thread is running
```

---

# Method 2: Implement Runnable

Recommended approach.

```java
class MyTask implements Runnable {

    public void run() {
        System.out.println("Task running");
    }
}

public class Main {

    public static void main(String[] args) {

        Thread t = new Thread(new MyTask());

        t.start();
    }
}
```

Output:

```text
Task running
```

---

# start() vs run()

Wrong:

```java
t.run();
```

Correct:

```java
t.start();
```

### run()

Runs on current thread.

```text
Main Thread
```

### start()

Creates a new thread.

```text
Main Thread
Worker Thread
```

---

# Example

```java
class MyThread extends Thread {

    public void run() {

        for(int i = 1; i <= 5; i++) {
            System.out.println(i);
        }

    }
}

public class Main {

    public static void main(String[] args) {

        MyThread t = new MyThread();

        t.start();

        System.out.println("Main");
    }
}
```

Possible Output:

```text
Main
1
2
3
4
5
```

or

```text
1
Main
2
3
4
5
```

Order is not guaranteed.

---

# Thread Sleep

Pause a thread.

```java
try {
    Thread.sleep(2000);
} catch (InterruptedException e) {
    e.printStackTrace();
}
```

Sleep for 2 seconds.

Example:

```java
for(int i = 1; i <= 5; i++) {

    System.out.println(i);

    Thread.sleep(1000);
}
```

Output:

```text
1
(wait 1 sec)
2
(wait 1 sec)
3
...
```

---

# Thread Name

```java
Thread.currentThread().getName();
```

Example:

```java
System.out.println(Thread.currentThread().getName());
```

Output:

```text
main
```

---

# Set Thread Name

```java
t.setName("Worker");
```

```java
System.out.println(t.getName());
```

Output:

```text
Worker
```

---

# Multiple Threads

```java
class MyThread extends Thread {

    public void run() {

        for(int i = 1; i <= 5; i++) {
            System.out.println(
                Thread.currentThread().getName()
            );
        }

    }
}

public class Main {

    public static void main(String[] args) {

        MyThread t1 = new MyThread();
        MyThread t2 = new MyThread();

        t1.setName("A");
        t2.setName("B");

        t1.start();
        t2.start();
    }
}
```

Output:

```text
A
B
A
B
A
...
```

---

# Thread Join

Wait for a thread to finish.

```java
Thread t = new Thread(() -> {

    for(int i = 1; i <= 5; i++) {
        System.out.println(i);
    }

});

t.start();

t.join();

System.out.println("Finished");
```

Output:

```text
1
2
3
4
5
Finished
```

---

# Thread Priority

```java
t.setPriority(Thread.MAX_PRIORITY);
```

Values:

```java
Thread.MIN_PRIORITY // 1

Thread.NORM_PRIORITY // 5

Thread.MAX_PRIORITY // 10
```

Example:

```java
t.setPriority(10);
```

Priority is only a hint to JVM.

---

# Thread States

```text
NEW
RUNNABLE
BLOCKED
WAITING
TIMED_WAITING
TERMINATED
```

Lifecycle:

```text
NEW
 |
start()
 |
RUNNABLE
 |
RUNNING
 |
TERMINATED
```

---

# Synchronization

Problem:

```java
count++;
```

Multiple threads may update simultaneously.

Wrong result possible.

---

## Synchronized Method

```java
class Counter {

    int count = 0;

    synchronized void increment() {
        count++;
    }
}
```

Only one thread enters at a time.

---

# Lambda Thread

Java 8+

```java
Thread t = new Thread(() -> {

    System.out.println("Hello");

});

t.start();
```

Most common interview style.

---

# ExecutorService

Modern thread management.

```java
import java.util.concurrent.*;

ExecutorService executor =
        Executors.newFixedThreadPool(3);

executor.submit(() -> {
    System.out.println("Task");
});

executor.shutdown();
```

Preferred in real applications.

---

# Useful Thread Methods

| Method | Purpose |
|----------|----------|
| start() | Start thread |
| run() | Thread logic |
| sleep() | Pause thread |
| join() | Wait for completion |
| getName() | Get name |
| setName() | Set name |
| currentThread() | Current thread |
| setPriority() | Set priority |
| isAlive() | Check running |

---

# Interview Questions

## Difference Between start() and run()

```text
start() -> Creates new thread

run() -> Executes in current thread
```

---

## Why Runnable Is Preferred?

```text
Allows class to extend another class.
```

Java supports only single inheritance.

---

## What Is Synchronization?

```text
Protects shared resources from race conditions.
```

---

## What Is a Race Condition?

```text
Multiple threads modify data simultaneously.
```

---

## What Is Deadlock?

```text
Two threads waiting forever for each other.
```

---

# Thread Cheat Sheet

```java
Thread t = new Thread(() -> {

    System.out.println("Task");

});

t.start();

t.join();

Thread.sleep(1000);

Thread.currentThread().getName();

t.isAlive();
```

---

# CP / Interview Focus

Memorize:

```text
Thread
Runnable
start()
run()
sleep()
join()
synchronized
ExecutorService
```

These are the most commonly asked thread concepts in Java developer interviews and multithreading rounds.
