
# Java Interview Questions - Streams, Concurrency, Spring, JPA, Annotations

---
📺 [Watch the video on YouTube](https://youtu.be/EDgVmmzILjE)

### 1. How to get employees from a list of employees who are 30 years old and more using streams

```java
List<Employee> filtered = employees.stream()
    .filter(emp -> emp.getAge() >= 30)
    .collect(Collectors.toList());
```

---

### 2. What is a Future variable in concurrency?

`Future` represents the result of an asynchronous computation. It provides methods to check if the computation is complete, wait for its completion, and retrieve the result.

```java
ExecutorService service = Executors.newSingleThreadExecutor();
Future<Integer> future = service.submit(() -> 5 + 5);
```

---

### 3. What is an Optional?

`Optional` is a container object used to represent the presence or absence of a value, introduced in Java 8 to avoid `NullPointerException`.

```java
Optional<String> optional = Optional.ofNullable(getName());
```

---

### 4. What is a Serializable interface? Why is it used?

`Serializable` is a marker interface (no methods) used to allow objects to be converted into a byte stream. This is essential for saving objects to files or sending them over a network.

---

### 5. What is the relation of equals and hashCode method?

- If two objects are equal (`equals()` returns true), then their `hashCode()` must be the same.
- If two objects are not equal, their `hashCode()` may or may not be the same.

---

### 6. What is try-with-resources? Which classes are applicable for it?

`try-with-resources` is used to auto-close resources that implement `AutoCloseable` or `Closeable`.

```java
try (BufferedReader reader = new BufferedReader(new FileReader("file.txt"))) {
    System.out.println(reader.readLine());
}
```

---

### 7. How to create a Singleton class

```java
public class Singleton {
    private static Singleton instance;

    private Singleton() {}

    public static synchronized Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }
}
```

---

### 8. Which exception is prevented by ConcurrentHashMap?

`ConcurrentModificationException` is avoided in `ConcurrentHashMap` as it is thread-safe and does not throw this during concurrent access.

---

### 9. How to autowire an interface that has two implementations?

Use `@Qualifier` annotation to distinguish between implementations.

```java
@Autowired
@Qualifier("impl1")
private MyInterface myInterface;
```

---

### 10. List the annotations used in storing an employee's details from Postman to DB using Spring Data JPA

- `@RestController`
- `@PostMapping`
- `@RequestBody`
- `@Valid`
- `@Entity`
- `@Table`
- `@Id`
- `@GeneratedValue`
- `@Column`
- `@Autowired`
- `@Repository`
- `@Service`

---

### 11. Difference between @Valid used in Entity class vs Controller class

- In **Entity class**, annotations are used to define validation rules (e.g., `@NotNull`, `@Size`).
- In **Controller class**, `@Valid` triggers the validation rules defined in the entity.

---

### 12. How to create an annotation

```java
@Retention(RetentionPolicy.RUNTIME)
@Target(ElementType.METHOD)
public @interface MyAnnotation {
    String value();
}
```

---

### 13. What is externalization of configuration?

It means keeping configuration data outside the codebase (e.g., `application.properties`, YAML files) to make the application configurable without modifying the source code.

---

### 14. What are some entity class annotations?

- `@Entity`
- `@Table`
- `@Id`
- `@GeneratedValue`
- `@Column`
- `@OneToMany`, `@ManyToOne`, etc.

---

### 15. How is a composite key mapped in Hibernate?

Use `@Embeddable` and `@EmbeddedId`.

```java
@Embeddable
public class EmployeeId implements Serializable {
    private Long empId;
    private String deptCode;
}

@Entity
public class Employee {
    @EmbeddedId
    private EmployeeId id;
}
```

---

### 16. What are some annotations from JUnit?

- `@Test`
- `@BeforeEach`, `@BeforeAll`
- `@AfterEach`, `@AfterAll`
- `@Disabled`
- `@DisplayName`
- `@Nested`

---

### 17. Why does a functional interface have only one method?

To allow lambda expressions to work. A lambda must implement exactly one abstract method, so functional interfaces are restricted to one.

---

### 18. What is ExecutorService?

`ExecutorService` is part of the `java.util.concurrent` package. It manages and controls thread execution using a thread pool.

```java
ExecutorService executor = Executors.newFixedThreadPool(2);
executor.submit(() -> System.out.println("Task"));
executor.shutdown();
```

---
