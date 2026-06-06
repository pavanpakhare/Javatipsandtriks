# Java Collections Framework (JCF) Complete Tutorial

The Java Collections Framework (JCF) provides classes and interfaces to store and manipulate groups of objects efficiently.

---

# Collection Hierarchy

```text
Iterable
   |
Collection
   |
   +-- List
   |     +-- ArrayList
   |     +-- LinkedList
   |     +-- Vector
   |     +-- Stack
   |
   +-- Set
   |     +-- HashSet
   |     +-- LinkedHashSet
   |     +-- TreeSet
   |
   +-- Queue
         +-- PriorityQueue
         +-- ArrayDeque

Map (Separate Hierarchy)
   |
   +-- HashMap
   +-- LinkedHashMap
   +-- TreeMap
   +-- Hashtable
```

---

# 1. ArrayList

## Properties

- Dynamic Array
- Maintains insertion order
- Allows duplicates
- Fast random access
- Slow insertion/deletion in middle

## Declaration

```java
ArrayList<Integer> list = new ArrayList<>();
```

## Common Functions

```java
list.add(10);
list.add(20);

list.get(0);

list.set(0, 100);

list.remove(0);

list.contains(20);

list.size();

list.isEmpty();

list.clear();
```

## Time Complexity

| Operation | Complexity |
|------------|------------|
| Add End | O(1) |
| Get | O(1) |
| Set | O(1) |
| Search | O(n) |
| Remove End | O(1) |
| Remove Middle | O(n) |

## Space Complexity

```text
O(n)
```

---

# 2. LinkedList

## Properties

- Doubly Linked List
- Fast insertion/deletion
- Slow random access

## Declaration

```java
LinkedList<Integer> list = new LinkedList<>();
```

## Functions

```java
list.add(10);

list.addFirst(5);

list.addLast(20);

list.removeFirst();

list.removeLast();

list.getFirst();

list.getLast();
```

## Time Complexity

| Operation | Complexity |
|------------|------------|
| Add First | O(1) |
| Add Last | O(1) |
| Remove First | O(1) |
| Remove Last | O(1) |
| Search | O(n) |
| Get Index | O(n) |

## Space Complexity

```text
O(n)
```

---

# 3. Stack

## Properties

- LIFO
- Last In First Out

## Declaration

```java
Stack<Integer> stack = new Stack<>();
```

## Functions

```java
stack.push(10);

stack.pop();

stack.peek();

stack.isEmpty();

stack.size();
```

## Complexity

| Operation | Complexity |
|------------|------------|
| Push | O(1) |
| Pop | O(1) |
| Peek | O(1) |

---

# 4. Queue

## Properties

- FIFO
- First In First Out

## Declaration

```java
Queue<Integer> q = new LinkedList<>();
```

## Functions

```java
q.offer(10);

q.poll();

q.peek();

q.isEmpty();
```

## Complexity

| Operation | Complexity |
|------------|------------|
| Offer | O(1) |
| Poll | O(1) |
| Peek | O(1) |

---

# 5. PriorityQueue (Heap)

## Properties

- Min Heap by default
- Smallest element at top

## Declaration

```java
PriorityQueue<Integer> pq = new PriorityQueue<>();
```

## Functions

```java
pq.offer(10);

pq.offer(5);

pq.peek();

pq.poll();
```

## Complexity

| Operation | Complexity |
|------------|------------|
| Insert | O(log n) |
| Delete | O(log n) |
| Peek | O(1) |

---

# 6. HashSet

## Properties

- Unique elements only
- No insertion order
- Backed by HashMap

## Declaration

```java
HashSet<Integer> set = new HashSet<>();
```

## Functions

```java
set.add(10);

set.remove(10);

set.contains(10);

set.size();
```

## Complexity

| Operation | Complexity |
|------------|------------|
| Add | O(1) |
| Remove | O(1) |
| Search | O(1) |

---

# 7. LinkedHashSet

## Properties

- Unique elements
- Maintains insertion order

## Complexity

| Operation | Complexity |
|------------|------------|
| Add | O(1) |
| Remove | O(1) |
| Search | O(1) |

---

# 8. TreeSet

## Properties

- Sorted Set
- Red Black Tree

## Declaration

```java
TreeSet<Integer> set = new TreeSet<>();
```

## Functions

```java
set.add(10);

set.first();

set.last();

set.higher(10);

set.lower(10);
```

## Complexity

| Operation | Complexity |
|------------|------------|
| Add | O(log n) |
| Remove | O(log n) |
| Search | O(log n) |

---

# 9. HashMap

## Properties

- Key Value Pair
- No order
- Unique keys

## Declaration

```java
HashMap<Integer,String> map = new HashMap<>();
```

## Functions

```java
map.put(1,"A");

map.get(1);

map.remove(1);

map.containsKey(1);

map.containsValue("A");

map.keySet();

map.values();

map.entrySet();
```

## Complexity

| Operation | Complexity |
|------------|------------|
| Put | O(1) |
| Get | O(1) |
| Remove | O(1) |

---

# 10. LinkedHashMap

## Properties

- Maintains insertion order

## Complexity

| Operation | Complexity |
|------------|------------|
| Put | O(1) |
| Get | O(1) |
| Remove | O(1) |

---

# 11. TreeMap

## Properties

- Sorted by key
- Red Black Tree

## Functions

```java
map.firstKey();

map.lastKey();

map.higherKey(10);

map.lowerKey(10);
```

## Complexity

| Operation | Complexity |
|------------|------------|
| Put | O(log n) |
| Get | O(log n) |
| Remove | O(log n) |

---

# 12. ArrayDeque

## Properties

- Double Ended Queue
- Faster than Stack

## Declaration

```java
ArrayDeque<Integer> dq = new ArrayDeque<>();
```

## Functions

```java
dq.offerFirst(10);

dq.offerLast(20);

dq.pollFirst();

dq.pollLast();

dq.peekFirst();

dq.peekLast();
```

## Complexity

| Operation | Complexity |
|------------|------------|
| Insert Front | O(1) |
| Insert Rear | O(1) |
| Delete Front | O(1) |
| Delete Rear | O(1) |

---

# Collections Utility Class

```java
Collections.sort(list);

Collections.reverse(list);

Collections.max(list);

Collections.min(list);

Collections.shuffle(list);

Collections.frequency(list, 10);

Collections.binarySearch(list, 20);
```

---

# CP / LeetCode Cheat Sheet

| Data Structure | Use Case |
|----------------|-----------|
| ArrayList | Dynamic Array |
| LinkedList | Frequent Insert/Delete |
| Stack | DFS, Monotonic Stack |
| Queue | BFS |
| PriorityQueue | Top K Elements, Heap |
| HashSet | Unique Elements |
| HashMap | Frequency Count |
| TreeSet | Sorted Unique Data |
| TreeMap | Sorted Key Value |
| ArrayDeque | Sliding Window, Monotonic Queue |

---

# Most Important Interview Functions

## ArrayList

```java
add()
get()
set()
remove()
contains()
size()
```

## HashMap

```java
put()
get()
getOrDefault()
containsKey()
remove()
entrySet()
```

## HashSet

```java
add()
contains()
remove()
```

## PriorityQueue

```java
offer()
poll()
peek()
```

## ArrayDeque

```java
offerFirst()
offerLast()
pollFirst()
pollLast()
peekFirst()
peekLast()
```

---

# Must Memorize Complexities

```text
ArrayList Get           O(1)
ArrayList Search        O(n)

HashMap Put/Get         O(1)

HashSet Add/Search      O(1)

TreeMap Put/Get         O(log n)

TreeSet Add/Search      O(log n)

PriorityQueue Insert    O(log n)
PriorityQueue Peek      O(1)

Queue Offer/Poll        O(1)

Stack Push/Pop          O(1)
```

