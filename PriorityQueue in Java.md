A **PriorityQueue** is a special type of queue where elements are **ordered by priority**, not by the order they were added. It is part of Java's **Collection Framework**.

---
## **1. Key Features**
- **Orders elements by priority (not insertion order).**
- **Default: Smallest element comes first (Min-Heap).**
- **Duplicates are allowed.**
- **No `null` values allowed.**
- **Not thread-safe** (Use `PriorityBlockingQueue` for multi-threading).

---
## **2. Creating a PriorityQueue**

### **(i) Default Min-Heap (Smallest first)**
```java
import java.util.PriorityQueue;

public class MinHeapExample {
    public static void main(String[] args) {
        PriorityQueue<Integer> pq = new PriorityQueue<>();
        
        pq.add(10);
        pq.add(5);
        pq.add(20);
        pq.add(15);
        
        while (!pq.isEmpty()) {
            System.out.println(pq.poll()); // Output: 5, 10, 15, 20 (smallest first)
        }
    }
}
```

### **(ii) Max-Heap (Largest first) using Comparator**
```java
import java.util.Collections;
import java.util.PriorityQueue;

public class MaxHeapExample {
    public static void main(String[] args) {
        PriorityQueue<Integer> maxHeap = new PriorityQueue<>(Collections.reverseOrder());
        
        maxHeap.add(10);
        maxHeap.add(5);
        maxHeap.add(20);
        maxHeap.add(15);
        
        while (!maxHeap.isEmpty()) {
            System.out.println(maxHeap.poll()); // Output: 20, 15, 10, 5 (largest first)
        }
    }
}
```

### **(iii) PriorityQueue with Custom Objects**
Sorting employees by age:
```java
import java.util.PriorityQueue;
import java.util.Comparator;

class Employee {
    String name;
    int age;
    public Employee(String name, int age) {
        this.name = name;
        this.age = age;
    }
    @Override
    public String toString() {
        return name + " (" + age + ")";
    }
}

public class CustomObjectPQ {
    public static void main(String[] args) {
        PriorityQueue<Employee> pq = new PriorityQueue<>(Comparator.comparingInt(e -> e.age));

        pq.add(new Employee("Alice", 30));
        pq.add(new Employee("Bob", 25));
        pq.add(new Employee("Charlie", 35));

        while (!pq.isEmpty()) {
            System.out.println(pq.poll()); // Output: Bob (25), Alice (30), Charlie (35)
        }
    }
}
```

---
## **3. Important Methods**
| Method | Description |
|--------|-------------|
| `add(E e)` | Inserts an element (throws exception if full). |
| `offer(E e)` | Inserts an element (returns `false` if full). |
| `poll()` | Retrieves and removes the **smallest/largest** element. |
| `peek()` | Retrieves but does **not remove** the head element. |
| `remove(E e)` | Removes a specific element. |
| `size()` | Returns the number of elements. |
| `isEmpty()` | Checks if the queue is empty. |

---
## **4. When to Use PriorityQueue?**
✅ **Use when:**
- You need to process elements **by priority** (e.g., scheduling tasks).
- You need a **min-heap or max-heap**.

🚨 **Avoid if:**
- You need strict **FIFO** (use `LinkedList` or `ArrayDeque` instead).
- You need **fast random access** (use `ArrayList` instead).

---
## **5. Real-World Use Cases**
- **Task Scheduling** (e.g., CPU Scheduling, Print Jobs).
- **Graph Algorithms** (e.g., Dijkstra’s Shortest Path).
- **Handling Events by Priority** (e.g., emergency call center).

---

