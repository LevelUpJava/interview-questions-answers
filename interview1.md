# Backend Developer Interview Questions and Answers

📺 <a href="https://youtu.be/m8LuiZZtHm8" target="_blank">Watch the video on YouTube</a>

## 1. What is JasperReports and how is it used in Java applications?
JasperReports is an open-source reporting engine written in Java. It's widely used to generate dynamic content like PDFs, Excel files, or HTML reports directly from Java applications. It relies on **JRXML** templates (XML-based report designs), which define the layout, fields, parameters, and data sources. These templates are compiled to `.jasper` files and filled with data at runtime.

**Use cases:**
- Generating invoices
- Exporting database query results into PDF
- Creating charts, dashboards, and business reports

It integrates well with **Spring Boot** using libraries like `jasperreports` and `spring-boot-starter-data-jpa`.

---

## 2. What is the compatibility matrix between Java versions and Spring Boot versions?
Spring Boot versions are tightly coupled with specific Java versions due to dependency and bytecode compatibility. 

| Spring Boot Version | Supported Java Versions     |
|---------------------|-----------------------------|
| 2.3 to 2.7          | Java 8 to Java 17           |
| 3.x                 | Java 17 and above only      |

Spring Boot 3 and onwards use **Jakarta EE 9+**, so all `javax.*` imports have changed to `jakarta.*`.

---

## 3. How can a Spring Boot application be deployed on AWS?
Several options exist:

1. **Elastic Beanstalk** – Upload the `.jar`, AWS handles provisioning and scaling.
2. **EC2** – Manually install Java and run the `.jar` on a virtual machine.
3. **ECS or EKS** – Containerize the app and deploy via ECS or Kubernetes.
4. **Lambda** – Deploy as a function using AWS Serverless Java container.

You can also use RDS for managed databases and S3 for static assets.

---

## 4. What is the difference between a Docker image and a Spring Boot JAR file?
- A **Spring Boot JAR** is a standalone Java executable requiring a JVM.
- A **Docker image** includes the JAR, JVM, OS, and dependencies — it's portable and environment-independent.

Docker is better suited for CI/CD and cloud deployments due to its consistency.

---

## 5. Should you run a database inside a Docker container? What are the pros and cons?
**Yes**, for development and testing. **No**, or cautiously in production.

**Pros:**
- Easy to set up
- Consistent across environments
- Useful in CI pipelines

**Cons:**
- Risk of data loss
- Backup/restore challenges
- Lower performance
- Not ideal for clustered DBs

---

## 6. What are intermediate and terminal operations in Java Streams?
**Intermediate operations:** Lazy, return a stream (`map`, `filter`, `sorted`, `distinct`)
**Terminal operations:** Eager, trigger processing (`collect`, `forEach`, `reduce`, `count`)

```java
List<String> names = List.of("Tom", "Jerry", "Anna", "Tom");
List<String> result = names.stream()
    .filter(name -> name.length() > 3)
    .distinct()
    .collect(Collectors.toList());
```

---

## 7. What are the different repository interfaces in Spring Data JPA?
1. `CrudRepository<T, ID>` – Basic CRUD
2. `PagingAndSortingRepository<T, ID>` – Adds pagination/sorting
3. `JpaRepository<T, ID>` – Adds JPA features like `flush`, `deleteInBatch`

Prefer `JpaRepository` for full capabilities.

---

## 8. What are ACID properties in databases?
1. **Atomicity** – All or nothing
2. **Consistency** – Valid state before/after transaction
3. **Isolation** – Concurrent transactions don’t interfere
4. **Durability** – Persisted changes survive crashes

Essential for transactional reliability.

---

## 9. How can you improve the performance of a slow SQL query?
- Use indexes
- Avoid `SELECT *`
- Optimize joins
- Analyze using `EXPLAIN`
- Avoid nested subqueries
- Cache frequent queries

---

## 10. What is a database view? What are its types?
A **view** is a virtual table from a SQL query.

**Types:**
- **Simple View**: Single table
- **Complex View**: Joins/aggregations
- **Materialized View**: Physically stored query results

Useful for abstraction and reusability.

---

## 11. What is indexing in a database and what are its benefits?
Indexing creates a sorted data structure (e.g., B-Tree) for quick lookups.

**Benefits:**
- Faster queries
- Efficient filtering, sorting
- Better JOIN performance

---

## 12. When can indexing hurt performance instead of improving it?
- Write-heavy operations (INSERT/UPDATE/DELETE)
- Index on low-cardinality fields
- Too many indexes increase storage and overhead

---

## 13. How to find the frequency of numbers in a list and sort by count?
```java
List<Integer> list = List.of(1, 2, 1, 3, 3, 3, 2, 2);
Map<Integer, Long> freq = list.stream()
    .collect(Collectors.groupingBy(n -> n, Collectors.counting()));

freq.entrySet().stream()
    .sorted(Map.Entry.<Integer, Long>comparingByValue().reversed())
    .forEach(e -> System.out.println(e.getKey() + ": " + e.getValue()));
```

---

## 14. What is the purpose of the @Transactional annotation in Spring?
Marks a method or class to be executed within a transaction. Supports rollback on exceptions, propagation control, and isolation levels.

Maintains **data integrity** by ensuring consistent execution.

---

## 15. What is the difference between @Component, @Service, and @Repository?
- `@Component`: Generic bean
- `@Service`: Business logic layer
- `@Repository`: Data access layer; adds exception translation

All are picked up by component scanning.

---

## 16. What is the N+1 problem in JPA and how can it be avoided?
Occurs when fetching a list of entities also loads each related entity separately.

**Avoid using:**
- `@EntityGraph`
- `JOIN FETCH`
- DTO projections

---

## 17. How does Spring Boot auto-configure your application?
Uses `@EnableAutoConfiguration` to scan the classpath and automatically register beans.

Example: If H2 and Spring Data JPA are on the classpath, Spring auto-configures a datasource and repository support.

---

## 18. What is the difference between eager and lazy loading in JPA?
- **Eager**: Fetch related entities immediately
- **Lazy**: Load on access

Prefer lazy to avoid unnecessary DB hits.

---

## 19. How do you implement pagination in Spring Data JPA?
Use `Pageable` interface:
```java
Page<Employee> page = repository.findAll(PageRequest.of(0, 10, Sort.by("name")));
```

Provides total elements, pages, and content.

---

## 20. How do you secure a Spring Boot application?
- Use **Spring Security**
- JWT-based authentication
- Method-level protection (`@PreAuthorize`)
- HTTPS enforcement

Supports OAuth2, LDAP, and basic auth as well.
