
# Java and Microservices Interview Questions and Answers

---

### 1. Explain the architecture of microservices and its pros and cons. What are the components in a microservice?

**Architecture:**
Microservices architecture is a design approach where an application is composed of loosely coupled, independently deployable services. Each service focuses on a specific business capability and communicates over standard protocols (usually HTTP/REST or messaging).

**Core Components:**
- **Service Registry (e.g., Eureka):** Keeps track of service instances.
- **API Gateway:** Entry point for client requests.
- **Configuration Server:** Manages service configurations centrally.
- **Database per Service:** Each microservice manages its own data.
- **Communication Mechanism:** REST, gRPC, messaging queues.
- **Monitoring & Logging:** Tools like Prometheus, Grafana, ELK stack.
- **CI/CD Pipeline:** Automated testing and deployment tools.

**Pros:**
- Independent deployment and scaling
- Fault isolation
- Technology diversity
- Better alignment with agile and DevOps

**Cons:**
- Increased complexity
- Difficult distributed debugging
- Higher operational overhead
- Data consistency and transaction management issues

---

### 2. What is an API Gateway?

An API Gateway is a server that acts as a single entry point into a microservices system. It handles requests by routing them to the appropriate service, aggregating results, and enforcing cross-cutting concerns like authentication, logging, rate limiting, and CORS.

**Popular Tools:** Netflix Zuul, Spring Cloud Gateway, Kong, NGINX.

---

### 3. How to communicate between two microservices?

**Options:**
- **Synchronous:** RESTful APIs using HTTP (client blocks until a response).
- **Asynchronous:** Messaging queues like RabbitMQ, Kafka.

---

### 4. Synchronous and Asynchronous Way of Communication

- **Synchronous:**
  - Immediate request/response
  - Tight coupling
  - Example: REST APIs over HTTP

- **Asynchronous:**
  - Message-based communication
  - Loose coupling
  - Example: Kafka, RabbitMQ

---

### 5. What is a Messaging Queue?

A messaging queue is a form of asynchronous service-to-service communication used in microservices architecture. Producers send messages to a queue, and consumers process them independently.

**Examples:** RabbitMQ, Apache Kafka, ActiveMQ

---

### 6. How to secure a microservice?

- Use HTTPS
- OAuth2 and JWT for authentication and authorization
- API gateway for request filtering
- Role-based access control (RBAC)
- Secure service-to-service communication (e.g., mTLS)
- Input validation and sanitization

---

### 7. What is OAuth?

OAuth (Open Authorization) is an open standard protocol for token-based authorization. It allows a third-party application to access a user's resources without exposing credentials.

---

### 8. What is a Token? Explain various tokens in Java OAuth

A token is a digitally signed piece of data that represents the user's authentication and authorization information.

**Types:**
- **Access Token:** Grants access to protected resources.
- **Refresh Token:** Used to obtain a new access token.
- **ID Token (OIDC):** Contains user profile info.

**In Java:**
- Libraries like Spring Security OAuth2 or Keycloak handle token creation and validation.

---

### 9. What is a Stream?

Streams in Java (introduced in Java 8) are a new abstraction for processing sequences of data in a functional style.

**Key operations:**
- `map()`, `filter()`, `reduce()`, `collect()`
- Lazy evaluation and pipelining
- Parallel processing support

---

### 10. How is memory allocation done in Java 8?

Java 8 uses heap and non-heap memory:
- **Heap:** Divided into Young and Old Generation
- **Non-Heap:** Metaspace (replaces PermGen)

Memory allocation strategies are handled by the JVM's garbage collectors like G1, CMS.

---

### 11. What is Metaspace?

Metaspace is a memory area introduced in Java 8 that replaces PermGen. It stores class metadata and can grow dynamically based on the system's memory.

---

### 12. What are Functional Interfaces?

A functional interface is an interface with a single abstract method (SAM), used primarily in lambda expressions.

**Examples:**
- `Runnable`
- `Callable`
- `Comparator`
- Custom interfaces with `@FunctionalInterface`

---

### 13. What are Threads in Java?

A thread is a lightweight process and the smallest unit of CPU execution in Java. It allows concurrent execution of tasks.

---

### 14. How many ways can we create a thread in Java?

1. **Extending `Thread` class**
2. **Implementing `Runnable` interface**
3. **Using `ExecutorService`**
4. **Using `Callable` with `Future`**

---

### 15. What are the different stages of thread lifecycle and what methods are called in those stages?

1. **New** – Created but not started (`new Thread()`).
2. **Runnable** – `start()` called, waiting for CPU.
3. **Running** – Thread is executing.
4. **Blocked/Waiting** – Waiting for monitor lock or signal.
5. **Timed Waiting** – `sleep()`, `join()`, `wait(timeout)`
6. **Terminated** – Thread execution completed.

---

### 16. What is a RESTful Web Service?

RESTful web services use HTTP methods to expose CRUD operations on resources.

**Principles:**
- Stateless
- URI-based
- Use of standard HTTP methods (`GET`, `POST`, `PUT`, `DELETE`)

---

### 17. Difference between @PathParam and @PathVariable?

- `@PathParam` is used in JAX-RS (Jakarta/Java EE).
- `@PathVariable` is used in Spring MVC.
Both are used to extract values from the URI path.

---

### 18. Explain Polymorphism and its types?

Polymorphism allows objects to be treated as instances of their parent type.

**Types:**
- **Compile-time (Method Overloading)**
- **Runtime (Method Overriding)**

---

### 19. Explain Runtime Polymorphism and how to implement it?

Runtime polymorphism is achieved through method overriding where a subclass provides a specific implementation of a method declared in its superclass.

```java
class Animal {
    void sound() { System.out.println("Animal sound"); }
}

class Dog extends Animal {
    void sound() { System.out.println("Bark"); }
}
```

---

### 20. What is Maven?

Maven is a build automation and dependency management tool for Java projects.

**Key Features:**
- `pom.xml` for managing dependencies
- Lifecycle phases: `clean`, `compile`, `test`, `install`, `deploy`

---

### 21. What are Different Joins?

- **INNER JOIN:** Common rows in both tables
- **LEFT JOIN:** All from left + matching from right
- **RIGHT JOIN:** All from right + matching from left
- **FULL JOIN:** All rows from both tables
- **CROSS JOIN:** Cartesian product

---

### 22. What does the `repository` tag in Maven do?

The `<repository>` tag in `pom.xml` defines external repositories from which dependencies should be downloaded if not found in Maven Central.

---

### 23. How to print odd numbers using Stream?

```java
List<Integer> list = List.of(1, 2, 3, 4, 5);
list.stream().filter(n -> n % 2 != 0).forEach(System.out::println);
```

---

### 24. Difference between Spring and Spring Boot?

| Feature        | Spring              | Spring Boot                        |
|----------------|---------------------|------------------------------------|
| Setup          | Manual configuration| Auto-configuration                 |
| Deployment     | WAR files           | Embedded servers (Tomcat, Jetty)   |
| Complexity     | More boilerplate    | Reduced boilerplate                |

---

### 25. What is a ConcurrentHashMap?

A thread-safe variant of `HashMap` introduced in Java 5. It allows concurrent reads and updates without locking the entire map.

**Key Features:**
- High performance under concurrent access
- Segment-based locking in older versions
- Bucket-based locking in newer versions

---

### 26. What is Test Driven Development (TDD)?

TDD is a software development approach where tests are written before the actual code.

**Cycle:**
1. Write a failing test
2. Write minimal code to pass the test
3. Refactor the code

**Benefits:**
- Better design
- Fewer bugs
- Easier refactoring

---
