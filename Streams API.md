The **Streams API** in Java (introduced in Java 8) is used to process collections of data in a **functional** and **declarative** way. It allows operations like filtering, mapping, reducing, and sorting to be performed efficiently.

---
## **1. What is a Stream?**
A **Stream** in Java is a sequence of elements that supports **functional-style operations**. Streams do not store elements; instead, they **process data** on demand.

### **Key Characteristics:**
- **Does not store data** (operates on data source like collections, arrays, I/O channels).
- **Does not modify the original data source**.
- **Supports functional programming** (lambda expressions).
- **Lazily evaluated** (elements are processed only when needed).
- **Supports parallel execution** (via `parallelStream()`).

---
## **2. Creating Streams**
Streams can be created from different sources:
### **From a Collection (List, Set, etc.)**
```java
import java.util.List;
import java.util.stream.Stream;

public class StreamExample {
    public static void main(String[] args) {
        List<String> names = List.of("Alice", "Bob", "Charlie");
        Stream<String> stream = names.stream();
    }
}
```
### **From an Array**
```java
import java.util.Arrays;
import java.util.stream.Stream;

public class ArrayStreamExample {
    public static void main(String[] args) {
        String[] arr = {"Java", "Python", "C++"};
        Stream<String> stream = Arrays.stream(arr);
    }
}
```
### **Using `Stream.of()`**
```java
Stream<Integer> stream = Stream.of(1, 2, 3, 4, 5);
```

### **Generating an Infinite Stream**
```java
Stream<Integer> infiniteStream = Stream.iterate(1, n -> n + 1);
```

---
## **3. Most Used Stream Methods**
### **(i) Intermediate Operations (Transform the Stream)**
Intermediate operations return a **new Stream** and are **lazy** (executed when a terminal operation is called).

#### **1. `filter(Predicate<T>)` – Select elements based on a condition**
```java
List<Integer> numbers = List.of(1, 2, 3, 4, 5, 6);
numbers.stream()
       .filter(n -> n % 2 == 0)
       .forEach(System.out::println); // Output: 2, 4, 6
```

#### **2. `map(Function<T, R>)` – Transform elements**
```java
List<String> names = List.of("alice", "bob", "charlie");
names.stream()
     .map(String::toUpperCase)
     .forEach(System.out::println); // Output: ALICE, BOB, CHARLIE
```

#### **3. `sorted()` – Sort elements**
```java
List<Integer> nums = List.of(5, 1, 3, 9, 2);
nums.stream()
    .sorted()
    .forEach(System.out::println); // Output: 1, 2, 3, 5, 9
```

#### **4. `distinct()` – Remove duplicates**
```java
List<Integer> nums = List.of(1, 2, 2, 3, 4, 4, 5);
nums.stream()
    .distinct()
    .forEach(System.out::println); // Output: 1, 2, 3, 4, 5
```

#### **5. `limit(n)` – Limit the number of elements**
```java
Stream.of(1, 2, 3, 4, 5, 6)
      .limit(3)
      .forEach(System.out::println); // Output: 1, 2, 3
```

---
### **(ii) Terminal Operations (Trigger Processing)**
Terminal operations return **a result** (non-stream type) and **consume** the stream.
#### **6. `forEach(Consumer<T>)` – Perform an action on each element**
```java
List<String> fruits = List.of("Apple", "Banana", "Cherry");
fruits.stream()
      .forEach(System.out::println); // Output: Apple, Banana, Cherry
```

#### **7. `collect(Collectors.toList())` – Convert Stream to List**
```java
import java.util.List;
import java.util.stream.Collectors;

List<String> upperNames = names.stream()
                               .map(String::toUpperCase)
                               .collect(Collectors.toList());
System.out.println(upperNames); // Output: [ALICE, BOB, CHARLIE]
```

#### **8. `count()` – Count elements in a stream**
```java
long count = Stream.of("A", "B", "C", "D").count();
System.out.println(count); // Output: 4
```

#### **9. `reduce(BinaryOperator<T>)` – Reduce elements to a single value**
```java
int sum = Stream.of(1, 2, 3, 4, 5)
                .reduce(0, Integer::sum);
System.out.println(sum); // Output: 15
```

#### **10. `anyMatch()`, `allMatch()`, `noneMatch()` – Test conditions**
```java
List<Integer> numbers = List.of(2, 4, 6, 8);
boolean allEven = numbers.stream().allMatch(n -> n % 2 == 0);
System.out.println(allEven); // Output: true
```

---
### **(iii) Parallel Streams**
Parallel streams use **multi-threading** to process data faster.

#### **Convert a Stream to Parallel Stream**
```java
List<Integer> numbers = List.of(1, 2, 3, 4, 5);
numbers.parallelStream()
       .map(n -> n * 2)
       .forEach(System.out::println);
```

---
## **4. Summary of Common Stream Methods**
| Method | Type | Description |
|--------|------|-------------|
| `filter(Predicate<T>)` | Intermediate | Filters elements based on a condition |
| `map(Function<T, R>)` | Intermediate | Transforms elements |
| `sorted()` | Intermediate | Sorts elements |
| `distinct()` | Intermediate | Removes duplicate elements |
| `limit(n)` | Intermediate | Limits the number of elements |
| `forEach(Consumer<T>)` | Terminal | Performs an action on each element |
| `collect(Collectors.toList())` | Terminal | Converts Stream to List |
| `count()` | Terminal | Counts elements in the stream |
| `reduce(BinaryOperator<T>)` | Terminal | Reduces elements to a single value |
| `anyMatch(Predicate<T>)` | Terminal | Checks if any element matches a condition |
| `allMatch(Predicate<T>)` | Terminal | Checks if all elements match a condition |
| `noneMatch(Predicate<T>)` | Terminal | Checks if no element matches a condition |

---
### **5. When to Use Streams?**
✔ **When processing large collections of data efficiently**  
✔ **When you need a functional approach**  
✔ **For parallel execution in performance-critical scenarios**  

**Avoid Streams if:**
- You need to modify the original collection.
- You are working with simple loops (e.g., a basic `for` loop may be faster).

---

