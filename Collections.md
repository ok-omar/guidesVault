## **Java Collections Overview**

In Java, **collections** are part of the **Java Collections Framework (JCF)**, which provides various data structures to manage and manipulate groups of objects efficiently. Here’s a breakdown of each collection type you mentioned, along with their key methods.

---

## **1. Stack (LIFO - Last In, First Out)**
A **Stack** is a linear data structure that follows the **LIFO** principle. The last element added is the first to be removed.

### **Main Methods:**
- `push(E item)` – Adds an item to the top of the stack.
- `pop()` – Removes and returns the item from the top of the stack.
- `peek()` – Returns the top element without removing it.
- `isEmpty()` – Checks if the stack is empty.
- `search(Object o)` – Returns the position of an object in the stack (1-based index).

### **Example:**
```java
import java.util.Stack;

public class StackExample {
    public static void main(String[] args) {
        Stack<Integer> stack = new Stack<>();
        stack.push(10);
        stack.push(20);
        stack.push(30);

        System.out.println(stack.pop()); // 30 (LIFO)
        System.out.println(stack.peek()); // 20
    }
}
```
---
## **2. Queue in Java**

A **Queue** is a **FIFO (First In, First Out)** data structure where elements are added at the rear and removed from the front. It is part of Java's **Collection Framework** and is implemented using the `Queue` interface in `java.util` package.

### **Main Methods:**
- `add(E e)` – Inserts an element into the queue (throws exception if full).
- `offer(E e)` – Inserts an element into the queue (returns `false` if full).
- `poll()` – Retrieves and removes the first element (returns `null` if empty).
- `remove()` – Retrieves and removes the first element (throws exception if empty).
- `peek()` – Retrieves but does **not remove** the first element (returns `null` if empty).
- `element()` – Retrieves but does **not remove** the first element (throws exception if empty).
- `isEmpty()` – Checks if the queue is empty.
- `size()` – Returns the number of elements in the queue.

### **Example:**
```java
import java.util.LinkedList;
import java.util.Queue;

public class QueueExample {
    public static void main(String[] args) {
        Queue<Integer> queue = new LinkedList<>();
        
        queue.add(10);
        queue.add(20);
        queue.add(30);

        System.out.println(queue.poll()); // Output: 10 (removes first element)
        System.out.println(queue.peek()); // Output: 20 (does not remove)
    }
}
```
---

## **3. Deque (Double-Ended Queue) in Java**

A **Deque** (pronounced "deck") is a **double-ended queue** that allows insertion and removal from **both ends** (front and rear). It extends the `Queue` interface and is implemented using `ArrayDeque` or `LinkedList`.

### **Main Methods:**
- `addFirst(E e)` – Inserts an element at the front.
- `addLast(E e)` – Inserts an element at the rear.
- `offerFirst(E e)` – Inserts an element at the front (returns `false` if full).
- `offerLast(E e)` – Inserts an element at the rear (returns `false` if full).
- `pollFirst()` – Retrieves and removes the first element (returns `null` if empty).
- `pollLast()` – Retrieves and removes the last element (returns `null` if empty).
- `peekFirst()` – Retrieves but does **not remove** the first element.
- `peekLast()` – Retrieves but does **not remove** the last element.

### **Example:**
```java
import java.util.Deque;
import java.util.ArrayDeque;

public class DequeExample {
    public static void main(String[] args) {
        Deque<String> deque = new ArrayDeque<>();
        
        deque.addFirst("Apple");
        deque.addLast("Banana");
        deque.addFirst("Cherry");

        System.out.println(deque.pollFirst()); // Output: Cherry (removes first element)
        System.out.println(deque.pollLast());  // Output: Banana (removes last element)
    }
}
```
---

## **4. Vector**
A **Vector** is a **resizable array** that is synchronized (thread-safe). It is similar to an `ArrayList` but slower due to synchronization.

### **Main Methods:**
- `add(E e)` – Adds an element to the vector.
- `add(int index, E e)` – Inserts an element at a specific index.
- `remove(Object o)` – Removes the first occurrence of the specified element.
- `remove(int index)` – Removes the element at the specified index.
- `get(int index)` – Retrieves the element at the specified index.
- `size()` – Returns the number of elements in the vector.

### **Example:**
```java
import java.util.Vector;

public class VectorExample {
    public static void main(String[] args) {
        Vector<String> vector = new Vector<>();
        vector.add("Apple");
        vector.add("Banana");
        vector.add(1, "Cherry");

        System.out.println(vector.get(1)); // Cherry
        vector.remove("Banana");
    }
}
```

---

## **5. List (Ordered Collection)**
A **List** is an **ordered collection** that allows duplicate elements.

### **(i) LinkedList**
A **LinkedList** is a doubly linked list where elements are stored in **nodes** containing data and pointers to the next and previous elements.

#### **Main Methods:**
- `add(E e)` – Adds an element at the end.
- `addFirst(E e)` – Adds an element at the beginning.
- `addLast(E e)` – Adds an element at the end.
- `remove()` – Removes the first element.
- `remove(int index)` – Removes an element at a specific index.
- `get(int index)` – Retrieves an element at the specified index.

#### **Example:**
```java
import java.util.LinkedList;

public class LinkedListExample {
    public static void main(String[] args) {
        LinkedList<String> list = new LinkedList<>();
        list.add("A");
        list.add("B");
        list.addFirst("C");

        System.out.println(list.get(1)); // A
        list.remove("B");
    }
}
```

---

### **(ii) ArrayList**
An **ArrayList** is a resizable array implementation of `List`.

#### **Main Methods:**
- `add(E e)` – Adds an element at the end.
- `add(int index, E e)` – Inserts an element at a specific index.
- `remove(int index)` – Removes the element at the given index.
- `get(int index)` – Retrieves an element at a given index.
- `size()` – Returns the number of elements.

#### **Example:**
```java
import java.util.ArrayList;

public class ArrayListExample {
    public static void main(String[] args) {
        ArrayList<Integer> list = new ArrayList<>();
        list.add(1);
        list.add(2);
        list.add(1, 3);

        System.out.println(list.get(1)); // 3
        list.remove(2);
    }
}
```

---

## **4. HashMap (Key-Value Pair Storage)**
A **HashMap** stores **key-value** pairs and allows fast lookups. Keys are unique, but values can be duplicated.

### **Main Methods:**
- `put(K key, V value)` – Adds a key-value pair.
- `get(K key)` – Retrieves the value associated with the key.
- `remove(K key)` – Removes the key-value pair.
- `containsKey(K key)` – Checks if the key exists.
- `containsValue(V value)` – Checks if a value exists.
- `keySet()` – Returns a set of all keys.

### **Example:**
```java
import java.util.HashMap;

public class HashMapExample {
    public static void main(String[] args) {
        HashMap<Integer, String> map = new HashMap<>();
        map.put(1, "One");
        map.put(2, "Two");

        System.out.println(map.get(1)); // One
        map.remove(2);
    }
}
```

---

## **5. HashSet (Unique Elements)**
A **HashSet** is a collection of unique elements with no specific order.

### **Main Methods:**
- `add(E e)` – Adds an element if it’s not already present.
- `remove(E e)` – Removes an element.
- `contains(E e)` – Checks if an element exists.
- `size()` – Returns the number of elements.

### **Example:**
```java
import java.util.HashSet;

public class HashSetExample {
    public static void main(String[] args) {
        HashSet<String> set = new HashSet<>();
        set.add("A");
        set.add("B");
        set.add("A"); // Ignored, since duplicates are not allowed

        System.out.println(set.contains("B")); // true
        set.remove("A");
    }
}
```

---

## **Summary Table:**

| Collection  | Ordering | Duplicates | Key Methods |
|------------|----------|------------|-------------|
| **Stack** | LIFO | Yes | `push()`, `pop()`, `peek()` |
| **Vector** | Ordered | Yes | `add()`, `remove()`, `get()` |
| **LinkedList** | Ordered | Yes | `addFirst()`, `addLast()`, `remove()` |
| **ArrayList** | Ordered | Yes | `add()`, `remove()`, `get()` |
| **HashMap** | Key-Value | Keys Unique | `put()`, `get()`, `remove()` |
| **HashSet** | Unordered | No Duplicates | `add()`, `remove()`, `contains()` |


