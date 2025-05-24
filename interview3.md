```markdown
# Java and Microservices Interview Questions

---

## 1. Explain the Architecture of Microservices and Its Pros and Cons
**Architecture:**
- Collection of loosely coupled services
- Each service is independently deployable and scalable
- Services communicate via REST, messaging, or events

**Pros:**
- Scalability and flexibility
- Independent deployment
- Technology diversity
- Improved fault isolation

**Cons:**
- Complex management
- Distributed system challenges (latency, data consistency)
- Higher testing complexity

---

## 2. What are the Components in a Microservices Architecture?
- API Gateway
- Discovery Server (Eureka, Consul)
- Configuration Server
- Service Registry
- Load Balancer
- Monitoring (Prometheus, ELK, Zipkin)
- Centralized Logging
- CI/CD Pipeline

---

## 3. What is an API Gateway?
- Entry point for all client requests.
- Handles routing, security, rate limiting, load balancing, and protocol translation.
- Examples: Spring Cloud Gateway, Netflix Zuul, Kong

---

## 4. How to Communicate Between Two Microservices?
**Synchronous:**
- REST APIs using HTTP

**Asynchronous:**
- Messaging queues (RabbitMQ, Kafka)

---

## 5. Synchronous and Asynchronous Communication
**Synchronous:**
- Real-time response
- Tight coupling

**Asynchronous:**
- Message/event-based
- Loose coupling, high scalability

---

## 6. What is a Messaging Queue?
- Middleware for asynchronous communication.
- Stores and forwards messages (RabbitMQ, Kafka, ActiveMQ).
- Ensures decoupling and resilience.

---

## 7. How to Secure a Microservice?
- Use OAuth2 / JWT tokens
- API Gateway authentication
- HTTPS for secure communication
- Role-based access control
- Service-to-service authentication

---

## 8. What is OAuth?
- Open standard for authorization.
- Allows third-party apps to access user data without exposing credentials.
- Used with JWT, access and refresh tokens.

---

## 9. What is a Token? Types in Java OAuth
**Token:** Credential for accessing resources.
- Access Token: Short-lived token for accessing APIs
- Refresh Token: Used to obtain a new access token
- JWT Token: Self-contained token with claims (JSON Web Token)

---

## 10. What is a Stream?
- Java 8 feature for processing collections functionally.
- Supports map, filter, reduce, collect, etc.

---

## 11. How is Memory Allocation Done in Java 8?
- Heap: Stores objects
- Stack: Stores method calls and local vars
- Metaspace: Stores class metadata (replaces PermGen)

---

## 12. What is Metaspace?
- Replaces PermGen in Java 8
- Grows automatically
- Stores class metadata outside of heap

---

## 13. What are Functional Interfaces?
- Interface with one abstract method
- Used with lambdas and streams

Example:
```java
@FunctionalInterface
interface MyFunc {
    void execute();
}
```

---

## 14. What Are Threads in Java?
- Lightweight sub-processes for concurrent execution.
- Each thread has its own call stack.

---

## 15. Ways to Create a Thread in Java
- Extend `Thread` class
- Implement `Runnable` interface
- Implement `Callable` + use `Future`
- Using `Executors`

---

## 16. Thread Lifecycle Stages and Methods
- New → `new Thread()`
- Runnable → `start()`
- Running
- Blocked / Waiting / Timed Waiting → `sleep()`, `join()`, `wait()`
- Terminated → run method completes

---

## 17. What is a RESTful Web Service?
- Web service based on REST architecture.
- Uses HTTP methods (GET, POST, PUT, DELETE)
- Stateless, resource-based, URI-driven

---

## 18. Difference Between @PathParam and @PathVariable
- `@PathParam`: JAX-RS (javax.ws.rs)
- `@PathVariable`: Spring MVC
- Both extract values from URI path

---

## 19. Explain Polymorphism and Its Types
- Ability to take many forms
- Types:
  - Compile-time (Method Overloading)
  - Runtime (Method Overriding)

---

## 20. Explain Runtime Polymorphism and Implementation
- Method overriding at runtime
- Achieved using inheritance and reference of parent class

```java
Animal a = new Dog();
a.sound();
```

---

## 21. What is Maven?
- Build automation tool
- Handles dependencies, builds, packaging, testing
- Uses `pom.xml`

---

## 22. Different Types of SQL Joins
- INNER JOIN
- LEFT JOIN
- RIGHT JOIN
- FULL OUTER JOIN
- SELF JOIN
- CROSS JOIN

---

## 23. What Does <repository> Tag Do in Maven?
- Specifies location of remote repositories
- Used when dependencies are not available in central repo

---

## 24. How to Print Odd Numbers Using Stream?
```java
IntStream.range(1, 100).filter(n -> n % 2 != 0).forEach(System.out::println);
```

---

## 25. Difference Between Spring and Spring Boot
| Feature       | Spring               | Spring Boot           |
|---------------|----------------------|------------------------|
| Configuration | Manual               | Auto-configuration     |
| Setup         | Verbose              | Simple                 |
| Server        | External (Tomcat)    | Embedded               |

---

## 26. What is ConcurrentHashMap?
- Thread-safe version of HashMap
- High concurrency via segmented locking (Java 7) or bucket-level sync (Java 8+)
- No need for external synchronization

---

## 27. What is Test Driven Development (TDD)?
- Development process:
  1. Write test first (fail)
  2. Write minimal code to pass test
  3. Refactor
- Ensures code correctness and test coverage

---
```
