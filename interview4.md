
# Java 17 and Design Patterns Interview Questions

---

### 1. What features were added in Java 17?

Java 17 is a Long-Term Support (LTS) release and includes several new features and enhancements:

- **Sealed Classes**: Restrict which classes can extend or implement a class/interface.
- **Pattern Matching for `instanceof`**: Simplifies type casting.
- **Switch Expressions Enhancements**: More concise and expressive.
- **Text Blocks**: Multi-line strings with better readability.
- **Foreign Function & Memory API (Incubator)**: Interact with native code and memory safely.
- **New macOS Rendering Pipeline**: Based on Metal API.
- **Deprecation and removal of older features**: Applet API, Security Manager (deprecated).

---

### 2. What are Creational Design Patterns? Explain them.

Creational design patterns deal with object creation mechanisms, trying to create objects in a manner suitable to the situation.

- **Singleton**: Ensures a class has only one instance and provides a global access point.
- **Factory Method**: Defines an interface for creating an object but lets subclasses alter the type of objects that will be created.
- **Abstract Factory**: Provides an interface to create families of related or dependent objects.
- **Builder**: Allows the construction of a complex object step-by-step.
- **Prototype**: Creates objects by cloning an existing object.

---

### 3. Program to Implement Singleton Pattern Handling Concurrency, Cloning, and Reflection

```java
import java.io.Serializable;

public class Singleton implements Serializable, Cloneable {

    private static volatile Singleton instance;

    private Singleton() {
        if (instance != null) {
            throw new RuntimeException("Use getInstance() method");
        }
    }

    public static Singleton getInstance() {
        if (instance == null) {
            synchronized (Singleton.class) {
                if (instance == null)
                    instance = new Singleton();
            }
        }
        return instance;
    }

    // Prevent cloning
    @Override
    protected Object clone() throws CloneNotSupportedException {
        throw new CloneNotSupportedException("Cloning is not allowed");
    }

    // Prevent serialization breaking singleton
    protected Object readResolve() {
        return getInstance();
    }
}
```

---

### 4. Program using Stream to Get the Second Max Number from a List

```java
import java.util.List;
import java.util.Comparator;

public class SecondMaxExample {
    public static void main(String[] args) {
        List<Integer> list = List.of(5, 3, 9, 1, 4, 9, 7);

        int secondMax = list.stream()
            .distinct()
            .sorted(Comparator.reverseOrder())
            .skip(1)
            .findFirst()
            .orElseThrow(() -> new RuntimeException("No second max found"));

        System.out.println("Second Max: " + secondMax);
    }
}
```

---

### 5. What is the Time Complexity of Getting an Element from an ArrayList?

**Time Complexity:** O(1)

Getting an element by index in an `ArrayList` is a constant-time operation because it is backed by an array and supports random access.

---

### 6. Difference Between HashMap and ConcurrentHashMap

| Feature              | HashMap                            | ConcurrentHashMap                      |
|----------------------|-------------------------------------|----------------------------------------|
| Thread Safety         | Not thread-safe                    | Thread-safe                             |
| Performance           | Faster in single-threaded          | Better in concurrent scenarios          |
| Null Keys/Values      | Allows one null key and values     | Does not allow null keys or values      |
| Synchronization       | Needs external sync for threads    | Uses internal bucket-level locking      |
| Use Case              | Single-threaded apps               | Multi-threaded apps                     |

---
