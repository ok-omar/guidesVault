### **Comparable vs Comparator in Java**

In Java, both **Comparable** and **Comparator** are used to **sort objects** in a collection. However, they have different purposes and ways of implementation.

---
## **1. What is Comparable?**
- **Comparable** is an interface used to define the **natural ordering** of objects.
- It is used when an object **has a default way to be compared**.
- The class itself implements `Comparable<T>` and defines the `compareTo()` method.

### **Example of Comparable (Sorting by Age)**
```java
import java.util.*;

class Person implements Comparable<Person> {
    String name;
    int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    @Override
    public int compareTo(Person other) {
        return Integer.compare(this.age, other.age); // Sort by age (ascending)
    }

    @Override
    public String toString() {
        return name + " (" + age + ")";
    }
}

public class ComparableExample {
    public static void main(String[] args) {
        List<Person> people = new ArrayList<>();
        people.add(new Person("Alice", 30));
        people.add(new Person("Bob", 25));
        people.add(new Person("Charlie", 35));

        Collections.sort(people); // Uses compareTo()
        System.out.println(people); // Output: [Bob (25), Alice (30), Charlie (35)]
    }
}
```
📌 **Comparable is used when a class has a single natural order.**

---
## **2. What is Comparator?**
- **Comparator** is an interface used to define **custom ordering** of objects.
- It is used when you need **multiple sorting criteria**.
- Instead of implementing `Comparable<T>`, a separate class or lambda function is used to define sorting logic.

### **Example of Comparator (Sorting by Name & Age)**
```java
import java.util.*;

class Person {
    String name;
    int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    @Override
    public String toString() {
        return name + " (" + age + ")";
    }
}

// Comparator for sorting by name
class NameComparator implements Comparator<Person> {
    @Override
    public int compare(Person p1, Person p2) {
        return p1.name.compareTo(p2.name);
    }
}

// Comparator for sorting by age in descending order
class AgeComparator implements Comparator<Person> {
    @Override
    public int compare(Person p1, Person p2) {
        return Integer.compare(p2.age, p1.age); // Descending order
    }
}

public class ComparatorExample {
    public static void main(String[] args) {
        List<Person> people = new ArrayList<>();
        people.add(new Person("Alice", 30));
        people.add(new Person("Bob", 25));
        people.add(new Person("Charlie", 35));

        // Sorting by name using NameComparator
        Collections.sort(people, new NameComparator());
        System.out.println("Sorted by name: " + people);

        // Sorting by age (descending) using AgeComparator
        Collections.sort(people, new AgeComparator());
        System.out.println("Sorted by age (desc): " + people);
    }
}
```
📌 **Comparator is used when multiple sorting criteria are needed.**

---
## **3. Key Differences Between Comparable and Comparator**
| Feature | Comparable | Comparator |
|---------|-----------|------------|
| Interface | `Comparable<T>` | `Comparator<T>` |
| Method | `compareTo(T o)` | `compare(T o1, T o2)` |
| Purpose | Defines **natural ordering** | Allows **custom ordering** |
| Implementation | Implemented **inside the class** | Implemented **separately** |
| Modifiable | **Cannot** be changed dynamically | **Can** define multiple comparators |
| Usage | `Collections.sort(list)` | `Collections.sort(list, comparator)` or `list.sort(comparator)` |

---
## **4. When to Use Which?**
✔ **Use Comparable when:**
- You want a **single default sorting order** (e.g., sort `Person` by age by default).
- You can modify the class itself to implement `Comparable`.

✔ **Use Comparator when:**
- You need **multiple ways to sort** (e.g., sort `Person` by name or age).
- You **cannot modify** the class but still need custom sorting.

---
