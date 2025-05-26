# Java and Spring Boot Interview Questions and Answers

---
Here are the parts of the tutorial series:

- Part 1: [Watch on YouTube](https://youtu.be/1IKL-hRkuZA)
- Part 2: [Watch on YouTube](https://youtu.be/YX8z3nZ1suA)
- Part 3: [Watch on YouTube](https://youtu.be/7W3SUF8YwRQ)

## 1. Difference between Java 8, 17, and 21
**Java 8 (2014):**
- Introduced **Lambdas**, **Streams**, **Functional Interfaces**
- **Default and static methods in interfaces**
- **Optional class** for better null handling
- New Date and Time API (java.time.*)
- Nashorn JavaScript Engine
- Parallel array operations

**Java 17 (2021 - LTS):**
- Sealed classes
- Pattern Matching for instanceof
- New macOS rendering pipeline (Metal)
- Deprecation/removal of older APIs (like Applet API)
- Strong encapsulation of JDK internals

**Java 21 (2023 - LTS):**
- Virtual Threads (Project Loom)
- Record patterns, unnamed patterns
- Pattern matching for switch
- String templates (Preview)
- Sequenced Collections
- Structured concurrency (Preview)

Java 17 and 21 focus more on performance, language enhancements, and concurrency improvements.

---

## 2. Java 8 Features
- Lambda Expressions
- Functional Interfaces
- Streams API
- Default and Static Methods in Interfaces
- New Date and Time API
- Optional Class
- Nashorn JavaScript Engine
- Method References
- Repeatable Annotations

---

## 3. Why Should We Use Predicate?
- `Predicate<T>` is a functional interface with a method `boolean test(T t)`.
- Used for filtering and matching conditions (e.g., in Streams).
- Promotes clean, declarative style code.

Example:
```java
List<String> names = List.of("John", "Jane", "Doe");
names.stream().filter(name -> name.startsWith("J")).forEach(System.out::println);
```

---

## 4. What is a Functional Interface?
- An interface with exactly one abstract method.
- Can have multiple default or static methods.
- Used with Lambda expressions.

Example:
```java
@FunctionalInterface
interface MyFunction {
    void apply();
}
```

---

## 5. Default Methods in Interfaces
- Introduced in Java 8 to allow methods with body in interfaces.
- Helps in interface evolution without breaking implementation classes.

**Calling Default/Static Method Example:**
```java
interface Demo {
    default void show() {
        System.out.println("Default Method");
    }

    static void display() {
        System.out.println("Static Method");
    }
}

class Test implements Demo {}

new Test().show();
Demo.display();
```

---

## 6. Can We Create Object of an Interface?
- No, interfaces cannot be instantiated directly.
- They can be implemented by classes or used via anonymous inner classes/lambdas.

---

## 7. What is a Lambda Expression?
- A short block of code which takes in parameters and returns a value.
- Syntax: `(parameters) -> expression`

Example:
```java
Runnable r = () -> System.out.println("Hello World");
r.run();
```

---

## 8. Difference Between Abstract Class and Interface
| Feature         | Abstract Class | Interface       |
|-----------------|----------------|-----------------|
| Inheritance     | Single         | Multiple        |
| Access Modifiers| Can use        | Only public     |
| Fields          | Yes            | Only static final |
| Constructors    | Yes            | No              |
| Default Impl    | Yes            | Yes (Java 8+)   |

---

## 9. Can We Create Object of Abstract Class?
- No, but we can call concrete methods via subclass.

Example:
```java
abstract class Animal {
    void sound() { System.out.println("Sound"); }
}

class Dog extends Animal {}
new Dog().sound();
```

---

## 10. What is Method Overriding?
- Redefining a superclass method in a subclass with the same signature.
- Used for runtime polymorphism.

---

## 11. What if Return Type is Changed in Overriding?
- Must be covariant: child return type must be subtype of parent return type.
- Changing from `int` to `String` causes compile-time error.

---

## 12. What is Method Overloading?
- Same method name with different parameters.

Example:
```java
void print(int a) {}
void print(String a) {}
```

---

## 13. Does Overloading Apply in Inheritance?
- Yes. Overloaded methods can be inherited and further overloaded.

---

## 14. What is a Stream?
- Introduced in Java 8 for processing collections in a functional way.
- Operations: filter, map, reduce, collect, sorted.
- Types: Sequential, Parallel

---

## 15. Map vs FlatMap
- `map` transforms each element.
- `flatMap` flattens nested structure.

Example:
```java
list.stream().map(String::toUpperCase);
listOfLists.stream().flatMap(List::stream);
```

---

## 16. What is a Singleton Class? How Can We Make It?
- A class that allows only one instance.
- Ensures controlled access to the only instance.

Example:
```java
public class Singleton {
    private static final Singleton instance = new Singleton();
    private Singleton() {}
    public static Singleton getInstance() {
        return instance;
    }
}
```

---

## 17. What is a Synchronized Keyword?
- Used to prevent thread interference and memory consistency errors.
- Applies lock to method or block so only one thread can execute.

---

## 18. notify vs notifyAll
- `notify()` wakes a single waiting thread.
- `notifyAll()` wakes all waiting threads.
- Both used in inter-thread communication with `wait()`.

---

## 19. Thread Lifecycle
1. New
2. Runnable
3. Running
4. Waiting
5. Timed Waiting
6. Terminated

---

## 20. What is Runnable? How Many Methods?
- Functional interface to define a task for threads.
- Has one method: `void run();`

---

## 21. Can We Call start() on a Thread Multiple Times?
- No. Once a thread is started, calling `start()` again throws `IllegalThreadStateException`.

---

## 22. What is an Immutable Class?
- State cannot be modified after creation.
- All fields `final`, private constructor, no setters.

---

## 23. What is final, finally, and finalize?
- `final`: constant or unchangeable (variable, method, class)
- `finally`: block always executed after try-catch
- `finalize()`: method called before object is garbage collected (deprecated)

---

## 24. What is try-with-resources?
- Introduced in Java 7.
- Simplifies closing of resources (like Streams, Connections).
- Automatically closes resources implementing `AutoCloseable`.

Example:
```java
try (BufferedReader br = new BufferedReader(new FileReader("file.txt"))) {
    System.out.println(br.readLine());
} catch (IOException e) {
    e.printStackTrace();
}
```

---

## 25. What if I Declare NullPointerException in Catch and It Is Thrown?
- It will be caught if it's declared correctly.
```java
try {
    String s = null;
    s.length();
} catch (NullPointerException e) {
    System.out.println("Caught NPE");
}
```

---

## 26. What Is an Unchecked Exception? Give an Example
- Runtime exceptions, not checked at compile time.
- Example: `NullPointerException`, `ArrayIndexOutOfBoundsException`

---

## 27. How to Make a Custom Exception?
```java
class MyException extends Exception {
    public MyException(String message) {
        super(message);
    }
}
```

---

## 28. How to Handle Exceptions in Spring Boot?
- Using `@ControllerAdvice` with `@ExceptionHandler`
```java
@ControllerAdvice
public class GlobalExceptionHandler {
    @ExceptionHandler(CustomException.class)
    public ResponseEntity<String> handleException(CustomException e) {
        return new ResponseEntity<>(e.getMessage(), HttpStatus.BAD_REQUEST);
    }
}
```

---

## 29. What is 400 Status Code?
- **Bad Request**: The server cannot process the request due to client error.

---

## 30. What is @RestController?
- Combines `@Controller` + `@ResponseBody`
- Used to build RESTful APIs.
- Returns JSON/XML instead of views.

---

## 31. Difference Between @Controller and @RestController?
| Feature       | @Controller           | @RestController              |
|---------------|------------------------|------------------------------|
| Purpose       | Web MVC (HTML/JSP)     | REST API (JSON/XML)          |
| @ResponseBody | Must be added manually | Implicitly present           |

---

## 32. What Are Idempotent Methods?
- Same result no matter how many times called.
- HTTP Methods: GET, PUT, DELETE are idempotent; POST is not.

---

## 33. What Are Stereotype Annotations?
- Spring annotations that define roles:
  - `@Component`
  - `@Service`
  - `@Repository`
  - `@Controller`

---

## 34. What Do We Use @SpringBootApplication For?
- Combines `@Configuration`, `@EnableAutoConfiguration`, and `@ComponentScan`
- Entry point for Spring Boot application.

---

## 35. Is @EnableConfiguration IOC Configuration?
- `@EnableAutoConfiguration` is more accurate.
- Part of enabling Spring Boot's inversion of control and auto-config.

---

## 36. What is Dependency Injection?
- Design pattern to inject dependencies at runtime.
- Reduces tight coupling, improves testability.
- Done using `@Autowired`, constructor injection, or setter.

---

## 37. Why Use @Autowired for Dependency Injection?
- Automatically resolves and injects beans.
- Eliminates the need for explicit instantiation.

---

## 38. Where Are Beans Stored in Spring Boot?
- ApplicationContext container.
- Retrieved using `@Autowired` or `context.getBean()`.

---

## 39. What is IOC and Its Types? How to Achieve It?
- Inversion of Control: Delegating creation of objects to container.
- Types:
  - Constructor Injection
  - Setter Injection
- Achieved via Spring Beans and Dependency Injection.

---

## 40. @Bean vs @Component
| Feature     | @Bean                         | @Component           |
|-------------|-------------------------------|-----------------------|
| Placement   | Used in @Configuration class  | Used on class itself  |
| Usage       | Manual bean declaration       | Auto-detection by Spring |

---

## 41. What is @Transactional and When to Use?
- Marks method or class as transactional.
- Used for database consistency: commit or rollback as a unit.

---

## 42. What is OAuth Authentication?
- Open standard for token-based authorization.
- Used for delegated access (e.g., Google/Facebook login).

---

## 43. How to Authenticate Multiple Microservices Using OAuth?
- Use centralized OAuth provider.
- Services verify token with provider (e.g., Keycloak, Auth0).

---

## 44. What is API Gateway Design Pattern?
- Entry point for microservices.
- Handles routing, rate limiting, authentication, logging.
- Example: Netflix Zuul, Spring Cloud Gateway

---

## 45. Authentication vs Authorization
| Authentication     | Authorization                |
|--------------------|------------------------------|
| Who you are        | What you can do              |
| Performed first    | Performed after auth         |

---

## 46. In JPA, Flow of Getting All Data from a Table
1. Define Entity Class with `@Entity`
2. Create Repository Interface extending `JpaRepository`
3. Use method like `findAll()`

```java
List<Employee> employees = employeeRepository.findAll();
```

---

## 47. How to Handle Pagination in JPA?
- Use `Pageable` interface from Spring Data:
```java
Page<Employee> page = employeeRepository.findAll(PageRequest.of(0, 10));
```

---

## 48. What is Circuit Breaker Pattern and Its Types?
- Prevents system failure from cascading when service fails.
- Types:
  - **Closed**: Requests pass through
  - **Open**: Requests blocked
  - **Half-Open**: Limited test requests

Example: Resilience4j, Hystrix

---

## 49. What is a Discovery Server? How to Achieve in Spring Boot?
- Used to register and discover microservices.
- Example: Eureka Server
- Add dependency `spring-cloud-starter-netflix-eureka-server`

---

## 50. How Many Indexes Can Be Provided in a Table?
- Technically unlimited, but performance and RDBMS constraints exist.
- Best practice: Use indexes wisely based on query patterns.

---

## 51. Can We Create Multiple Primary Keys in a Table?
- No. Only one primary key, but it can be **composite** (multiple columns).

---

## 52. What is a Composite Key?
- Primary key using more than one column.

```java
@Embeddable
class OrderId implements Serializable {
    private Long orderId;
    private Long productId;
}

@Entity
@IdClass(OrderId.class)
class Order {
    @Id private Long orderId;
    @Id private Long productId;
}
```

---

## 53. Primary Key vs Unique Key
| Feature      | Primary Key           | Unique Key          |
|--------------|------------------------|----------------------|
| Null Values  | Not allowed            | Allowed (one null)  |
| Count        | Only one               | Multiple allowed     |
| Purpose      | Entity identity        | Enforce uniqueness   |

---

## 54. How to Get Second Salary in PostgreSQL?
```sql
SELECT DISTINCT salary
FROM employee
ORDER BY salary DESC
OFFSET 1 LIMIT 1;
```

---

## 55. How to Get Second Salary Using JPA?
- Use `@Query`:
```java
@Query("SELECT DISTINCT e.salary FROM Employee e ORDER BY e.salary DESC")
List<Double> findSalaries(Pageable pageable);
```
- Then call with offset:
```java
findSalaries(PageRequest.of(1, 1));
```

---

## 56. What is Self Join? When to Use? Example?
- Join table with itself.
- Useful for hierarchical data (e.g., employees & managers).

```sql
SELECT A.name, B.name AS manager
FROM employee A
JOIN employee B ON A.manager_id = B.id;
```

---

## 57. Difference Between UNION and UNION ALL
| Feature      | UNION          | UNION ALL         |
|--------------|----------------|-------------------|
| Duplicates   | Removes        | Keeps             |
| Performance  | Slower         | Faster            |

---

## 58. How to Get Common Data from Two Tables? Which Join to Use?
- Use `INNER JOIN`

```sql
SELECT *
FROM table1 t1
JOIN table2 t2 ON t1.id = t2.id;
```

---

## 59. How Many Joins Are There?
- INNER JOIN
- LEFT JOIN (LEFT OUTER)
- RIGHT JOIN (RIGHT OUTER)
- FULL JOIN (FULL OUTER)
- SELF JOIN
- CROSS JOIN

---

## 60. Difference Between Agile and Waterfall
| Feature        | Agile                  | Waterfall             |
|----------------|-------------------------|------------------------|
| Approach       | Iterative & Incremental | Sequential             |
| Flexibility    | High                    | Low                   |
| Feedback       | Continuous              | End of development    |
| Testing        | Concurrent              | After development     |

---

## 61. What is a Feature Branch in Git?
- A dedicated branch to develop a specific feature.
- Isolated from main/master branch.
- Allows team to work independently without affecting production code.

---
