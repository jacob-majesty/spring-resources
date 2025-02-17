# Java Lead Interview Experience

Link: https://medium.com/coding-odyssey/jp-morgan-java-developer-interview-d9ee16c2260d

# 1. What is content negotiation in microservices?

Content negotiation in microservices refers to the process where a client and a server agree on the format of data to be exchanged during an HTTP request/response.

It enables a microservice to deliver responses in multiple formats, such as JSON, XML, or plain text, based on the client’s preference or capability.

## Content Negotiation Working

1. **Client Preference**: The client specifies its preferred data format(s) using HTTP headers:
   - `Accept` header: Specifies the media types the client can handle, e.g., `Accept: application/json, application/xml`.
   - `Content-Type` header: Specifies the format of the data sent in the request body, e.g., `Content-Type: application/json`.

2. **Server Response**: The server analyzes the `Accept` header and determines the best format it can provide. If multiple formats are supported, the server chooses the most appropriate one based on priority.

3. **Response**: The server sends the response in the agreed-upon format, along with the `Content-Type` header indicating the media type, e.g., `Content-Type: application/json`.

## Types of Content Negotiation

- **Server-Driven Negotiation**: The server decides the response format based on the `Accept` header from the client.
- **Client-Driven Negotiation**: The client requests specific formats through query parameters, such as `?format=json`.
- **Agent-Driven Negotiation**: Intermediary software or a proxy negotiates the content format.

## Benefits in Microservices

- **Flexibility**: Supports diverse client applications by delivering data in formats they understand.
- **Interoperability**: Enhances integration with systems using different data formats.
- **Scalability**: Allows services to evolve without breaking client compatibility by adding or deprecating formats.

## Example

Suppose a client sends the following request to a microservice:

```http
GET /users HTTP/1.1
Accept: application/json
```

- If the server supports JSON, it responds:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": 1,
  "name": "Shivam Srivastava"
}
```

- If the server cannot provide JSON, it might return:

```http
HTTP/1.1 406 Not Acceptable
```

Content negotiation ensures microservices can adapt to the needs of various clients, making them more versatile and interoperable.

# 2. Why do we use Java 8? Why was it introduced over Java 7?

We use Java 8 because it was introduced as a major upgrade over Java 7 to bring revolutionary features to the language, making it more modern, expressive, and efficient. Some of the features are:

- **Functional Programming**: Java 8 introduced functional programming paradigms, which simplify and improve how developers write code. This helps in writing cleaner, more readable, and concise code.
- **Stream API**: A powerful abstraction for processing collections of data in a functional style. Operations like filtering, mapping, and reducing large data sets are now easier and faster.
- **Better Concurrency**: Java 8 introduced parallel streams, which enable developers to process data in parallel with minimal effort, improving performance in multi-core systems.
- **Enhanced Productivity**: Features like lambda expressions, method references, and default methods reduce boilerplate code and increase developer productivity.
- **Date and Time API**: The new `java.time` package provides a modern, immutable, and thread-safe way to handle date and time, replacing the old, clunky `java.util.Date` and `java.util.Calendar`.
- **Backward Compatibility**: All features in Java 8 are fully backward-compatible, ensuring older codebases work seamlessly while benefiting from new features.
- **Improved Performance**: With advancements in the JVM and libraries, Java 8 provides better performance for both functional programming and overall application execution.

## Why Was Java 8 Introduced Over Java 7?

The real reason Java 8 was introduced is that Java started to lose market share to Python as Python was very efficient and reduced boilerplate code to a minimum.

Below are some of the reasons given by Oracle on the same:

1. **Functional Programming Revolution**:
   - Java 7 lacked functional programming capabilities, while languages like Scala, Python, and JavaScript were already popularizing this paradigm. To stay relevant and competitive, Java 8 added:
     - **Lambda Expressions**: Anonymous functions that simplify handling of single-method interfaces.
     - **Stream API**: To process data collections in a functional way.

2. **Modernization of the API**:
   - Java 7’s APIs were verbose and lacked flexibility. Java 8 improved this by:
     - Introducing default methods in interfaces, enabling backward compatibility and allowing interfaces to evolve without breaking existing implementations.
     - Updating APIs like Collections and Map to support streams and lambda expressions.

3. **Improved Handling of Date and Time**:
   - The existing `Date` and `Calendar` classes were mutable, cumbersome, and error-prone. Java 8 introduced the `java.time` package, inspired by Joda-Time, to provide:
     - Immutability for safety.
     - Intuitive APIs for date/time manipulations.

4. **Parallelism**:
   - Java 7 introduced the Fork/Join Framework, but it was complex for average developers. Java 8 simplified parallel processing with:
     - **Parallel Streams**: High-level abstraction for parallel data processing.

5. **Global Trends in Software Development**:
   - With the rise of big data, cloud computing, and modern software practices, Java 8 brought tools to address:
     - The need for efficient data processing (via Streams).
     - Improved scalability and concurrency (via parallel streams and performance improvements).

6. **Cleaner Codebase**:
   - Java 7 required verbose constructs for tasks like iterating over collections or implementing single-method interfaces. Java 8 introduced:
     - **Lambdas** for brevity.
     - **Method references** for better readability.

7. **Demand for Backward Compatibility with Innovation**:
   - Developers needed new features without breaking existing codebases. Java 8 allowed:
     - Introduction of default methods to extend interfaces without affecting existing implementations.
     - Full backward compatibility, making it easy for organizations to adopt it.

# 3. What is Dependency Injection and what are its advantages?

Dependency Injection (DI) is a technique used in object-oriented programming to achieve Inversion of Control (IoC).

It involves providing an object (called the dependent object) with its dependencies (other objects it depends on) from the outside, instead of the dependent object instantiating them itself.

This approach decouples the creation of objects from their behavior, making the code more modular, testable, and maintainable.

## Dependency Injection Working

At its core, DI involves:

- **Dependencies**: The objects or resources a class needs to function.
- **Injection**: The process of passing these dependencies to the dependent object.

DI can be implemented in three main ways:

1. **Constructor Injection**: Dependencies are passed to the object via its constructor.
2. **Setter Injection**: Dependencies are set through public setter methods.
3. **Interface Injection**: The dependency provides an injector method that the dependent class uses to receive its dependencies (less common).

## Example

### Without DI:

```java
public class Service {
    private Repository repository = new Repository(); // Tight coupling

    public void performService() {
        repository.save();
    }
}
```

### With DI:

```java
public class Service {
    private Repository repository;

    public Service(Repository repository) { // Constructor Injection
        this.repository = repository;
    }

    public void performService() {
        repository.save();
    }
}
```

Here, the `Repository` object is passed from outside, making `Service` independent of its creation logic.

## Advantages

1. **Loose Coupling**:
   - Classes are no longer responsible for creating their own dependencies, which makes the code more modular and easier to manage.

2. **Improved Testability**:
   - Dependencies can be easily mocked or stubbed for unit testing, as they are passed from outside rather than being hardcoded inside the class.

3. **Easier Maintenance**:
   - If a dependency changes (e.g., swapping a database implementation), you only need to update the dependency injection configuration, not the dependent class.

4. **Reusability**:
   - Dependencies can be reused across different classes, promoting a more DRY (Don’t Repeat Yourself) codebase.

5. **Scalability**:
   - Adding new functionality or dependencies becomes easier, as the code is modular and not tightly coupled.

6. **Adherence to SOLID Principles**:
   - Promotes the Single Responsibility Principle by separating the creation of dependencies from the use of dependencies.
   - Encourages the Dependency Inversion Principle, as classes depend on abstractions (interfaces) rather than concrete implementations.

7. **Configuration Flexibility**:
   - DI allows dynamic injection of dependencies based on runtime configurations, making the code adaptable to different environments (e.g., development, production).

8. **Better Code Readability**:
   - By delegating dependency management to a DI container or framework, the main code becomes cleaner and more focused on business logic.

# 4. What are the advantages of MongoDB over MySQL?

Below are some of the advantages of MongoDB over MySQL:

## Core Features:
- **Schema-less**: MongoDB is a NoSQL database, which means it doesn’t require a fixed schema. This allows for more flexibility in storing data.
- **Scalability**: MongoDB is designed to scale horizontally, making it easier to handle large amounts of data and high traffic loads.
- **Performance**: MongoDB can handle high read and write loads with low latency due to its document-oriented storage and indexing capabilities.

## Advanced Capabilities:
- **Aggregation Framework**: MongoDB provides a powerful aggregation framework that allows for complex data processing and analysis.
- **Sharding**: MongoDB supports automatic sharding, which distributes data across multiple servers to improve performance and scalability.
- **Replication**: MongoDB provides built-in replication for high availability and data redundancy.

## Use Cases:
- **Big Data**: MongoDB is well-suited for handling large volumes of unstructured or semi-structured data.
- **Real-time Analytics**: MongoDB’s aggregation framework and indexing capabilities make it ideal for real-time analytics.
- **Content Management**: MongoDB’s flexible schema makes it a good choice for content management systems where the data structure may change frequently.

# 5. Suppose you have 2 threads. One of them prints (1,2,3…) and the other one prints (A,B,C,..). How will you ensure that they run in a sequence, so that it prints (1,A,2,B…)?

To achieve this sequence of alternating outputs (1, A, 2, B, ...) from two threads, we can use synchronization mechanisms like a shared lock (`ReentrantLock` or `synchronized`) and a condition variable (`wait/notify`) to coordinate the execution of the threads.

Here’s how we can implement this in Java:

```java
class AlternatingPrinter {

    private final Object lock = new Object();
    private boolean numberTurn = true; // Indicates whether it's the number thread's turn

    public static void main(String[] args) {
        AlternatingPrinter printer = new AlternatingPrinter();
        Thread numberThread = new Thread(() -> printer.printNumbers());
        Thread letterThread = new Thread(() -> printer.printLetters());
        numberThread.start();
        letterThread.start();
    }

    public void printNumbers() {
        for (int i = 1; i <= 26; i++) { // Adjust the range as needed
            synchronized (lock) {
                while (!numberTurn) {
                    try {
                        lock.wait(); // Wait until it's this thread's turn
                    } catch (InterruptedException e) {
                        Thread.currentThread().interrupt();
                    }
                }
                System.out.print(i + " ");
                numberTurn = false; // Pass the turn to the letter thread
                lock.notifyAll(); // Notify the waiting thread
            }
        }
    }

    public void printLetters() {
        for (char c = 'A'; c <= 'Z'; c++) { // Adjust the range as needed
            synchronized (lock) {
                while (numberTurn) {
                    try {
                        lock.wait(); // Wait until it's this thread's turn
                    } catch (InterruptedException e) {
                        Thread.currentThread().interrupt();
                    }
                }
                System.out.print(c + " ");
                numberTurn = true; // Pass the turn to the number thread
                lock.notifyAll(); // Notify the waiting thread
            }
        }
    }
}
```

**Output**:

```
1 A 2 B 3 C ....
```

# 6. What is a Bean? What are the differences between normal Bean vs Spring Bean?

A **bean** is an object that is instantiated, assembled, and managed by a container.

In the context of Java, a bean is a reusable software component that adheres to specific conventions (e.g., having a no-argument constructor, being serializable, and providing getters and setters).

In Spring, a bean is any object that is managed by the Spring IoC (Inversion of Control) container.

## Example of a Normal Bean:

```java
public class NormalBean {
    private String name;

    public NormalBean() {}

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}
```

## Example of a Spring Bean:

### Using `@Component`:

```java
@Component
public class SpringBean {
    private String name;

    public SpringBean() {}

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}
```

### Defined in a configuration class:

```java
@Configuration
public class AppConfig {
    @Bean
    public SpringBean springBean() {
        return new SpringBean();
    }
}
```

## Differences:

| **Aspect**              | **Normal Bean**                          | **Spring Bean**                          |
|--------------------------|------------------------------------------|------------------------------------------|
| **Management**           | Managed by the application code.         | Managed by the Spring IoC container.     |
| **Lifecycle**            | Lifecycle is controlled by the developer.| Lifecycle is managed by Spring.          |
| **Dependency Injection** | Manual dependency injection.             | Automatic dependency injection.          |
| **Configuration**        | Configured in code.                      | Configured via XML, annotations, or Java config. |

# 7. How do you secure your microservices?

Below are some of the ways to secure your microservices:

1. **Authentication and Authorization**:
   - **Why**: To ensure only legitimate users or systems access the services.
   - **How**: Implement OAuth2.0 with tokens for users and system authentication. Centralize user identity management with solutions like Keycloak or Okta.

2. **API Gateway**:
   - Acts as the central entry point for requests and enforces security.
   - Use gateways like Kong, AWS API Gateway, or Spring Cloud Gateway for:
     - Authenticating requests.
     - Enforcing rate limits.
     - Applying access control policies.

3. **Secure Communication**:
   - Use TLS/SSL to encrypt all traffic between:
     - Clients and microservices.
     - Inter-microservice communication (using mutual TLS if possible).

4. **Service Mesh**:
   - A service mesh (e.g., Istio, Linkerd) provides:
     - Built-in mTLS for service-to-service communication.
     - Fine-grained traffic control policies.
     - Observability and logging features.

5. **Centralized Logging and Monitoring**:
   - Enable early detection of breaches or anomalies by:
     - Logging security events (e.g., failed logins).
     - Using monitoring tools (e.g., Prometheus, ELK Stack, or Splunk).

6. **Secure Secrets Management**:
   - Do not hard-code secrets like passwords or API keys in code.
   - Use secret management tools:
     - AWS Secrets Manager, Azure Key Vault, or HashiCorp Vault.

# 8. What are the differences between `@Component`, `@Service`, and `@Repository`?

| **Annotation** | **Purpose**                                                                 | **Usage**                                                                 |
|----------------|-----------------------------------------------------------------------------|---------------------------------------------------------------------------|
| `@Component`   | Generic stereotype for any Spring-managed component.                        | Used for any class that is a Spring bean.                                 |
| `@Service`     | Indicates that the class is a service component in the business logic layer. | Used for service classes that contain business logic.                     |
| `@Repository`  | Indicates that the class is a repository (data access object).              | Used for DAO classes that interact with the database or other data stores.|

# 9. Suppose you’ve a controller annotation and then you perform DB operation in it. What will happen in that case?

If you perform database operations directly inside a controller in a Spring application, it can technically work, but it’s considered a bad practice.

## What Happens:

- The controller will still handle the HTTP request and call the repository for the database operation. For example, you might inject a repository directly into the controller like this:

```java
@RestController
public class UserController {
    @Autowired
    private UserRepository userRepository;

    @GetMapping("/getUser/{id}")
    public User getUserById(@PathVariable Long id) {
        return userRepository.findById(id).orElse(null);
    }
}
```

- This would work, but the controller is now doing more than just handling HTTP requests — it’s also managing business logic and directly interacting with the database.

## Why It’s a Bad Practice:

- **Violation of Separation of Concerns (SoC)**: A controller’s primary responsibility is to handle HTTP requests and responses. By including database operations, you’re blurring the lines between the different layers of your application.
- **Harder to Maintain and Test**: Controllers become bloated with business logic, making them harder to maintain and test. For example, you can’t easily test the business logic separately without involving the HTTP layer.
- **Poor Scalability**: As your application grows, this approach makes it difficult to scale, since controllers will need to handle more responsibilities. This leads to tightly coupled code, which is harder to refactor.
- **Lack of Transaction Management**: If you don’t manage transactions properly (for example, using `@Transactional`), you risk running into issues with partial updates, especially if the database operations involve multiple steps.

## Correct Approach:

The best practice is to delegate database operations to the service layer. Here’s the right way to structure it:

### Controller: Handles incoming requests and delegates to the service layer.

```java
@RestController
public class UserController {
    @Autowired
    private UserService userService;

    @GetMapping("/getUser/{id}")
    public User getUserById(@PathVariable Long id) {
        return userService.getUserById(id);
    }
}
```

# Service Layer

Contains business logic and interacts with the repository layer.

```java
@Service
public class UserService {
    @Autowired
    private UserRepository userRepository;

    public User getUserById(Long id) {
        return userRepository.findById(id).orElse(null);
    }
}
```

# Repository Layer

Manages database interactions.

```java
@Repository
public interface UserRepository extends JpaRepository<User, Long> {
}
```

## Why This Is Better:

- **Separation of Concerns**: Each layer has its distinct responsibility — controllers handle requests, services contain business logic, and repositories manage data access.
- **Testability**: Business logic in services can be tested independently of the web layer.
- **Scalability**: As the application grows, this structure helps with maintainability and avoids bloated controllers.
- **Transaction Management**: You can easily use `@Transactional` at the service layer to manage transactions effectively.

---

## Benefits of Using DAO Layer

The DAO (Data Access Object) layer provides a structured way of interacting with a data source, abstracting the underlying data persistence mechanism.

### 1. Separation of Concerns
- The DAO layer separates data access logic from business logic.
- **Benefit**: Cleaner code where business logic does not deal with data retrieval or storage.

### 2. Maintainability
- Centralized data access logic allows easy database changes.
- **Benefit**: Easier to maintain and refactor.

### 3. Code Reusability
- Encapsulates common data access operations.
- **Benefit**: Less duplication across the application.

### 4. Data Source Independence
- Abstracts the data source to allow easy switching between databases.
- **Benefit**: Greater flexibility in database choices.

### 5. Simplified Unit Testing
- DAO can be mocked in unit tests.
- **Benefit**: Improves testability by isolating business logic from data persistence.

### 6. Transaction Management
- Centralized transaction handling.
- **Benefit**: Simplifies managing transactions.

### 7. Encapsulation and Security
- Controls database access and hides SQL complexities.
- **Benefit**: Enhances security and prevents vulnerabilities.

### 8. Improved Readability
- Abstracts database queries into reusable methods.
- **Benefit**: Better-organized code.

### 9. Flexibility with Data Handling
- Supports complex queries and custom transformations.
- **Benefit**: More control over data operations.

#### Example DAO Implementation:

```java
public class UserDAO {
    private EntityManager entityManager;

    public UserDAO(EntityManager entityManager) {
        this.entityManager = entityManager;
    }

    public void saveUser(User user) {
        entityManager.persist(user);
    }

    public User findUserById(Long id) {
        return entityManager.find(User.class, id);
    }

    public void deleteUser(Long id) {
        User user = findUserById(id);
        if (user != null) {
            entityManager.remove(user);
        }
    }
}
```

---

## Measuring Database Performance

### 1. Query Performance
- Measure execution time and optimize queries using `EXPLAIN`.

### 2. Response Time
- Track query response times and minimize latency.

### 3. Throughput
- Monitor queries handled per second/minute.

### 4. Database Connections
- Optimize connection pooling.

### 5. Disk I/O
- Measure read/write speeds and optimize storage.

### 6. CPU & Memory Usage
- Monitor system resource utilization.

### 7. Lock Contention
- Identify and resolve lock conflicts and deadlocks.

### 8. Cache Hit Ratio
- Optimize caching strategies.

### 9. Network Latency
- Minimize data transfer delays.

### 10. Slow Query Logs
- Capture and analyze slow queries.

### 11. Index Optimization
- Ensure efficient indexing and fragmentation management.

### 12. Query Execution Plan
- Use profiling tools like `EXPLAIN`.

### 13. Database Schema Design
- Optimize table structures for performance.

#### Monitoring Tools:
- **Prometheus, New Relic, MySQL EXPLAIN, Query Profiling**

---

## Designing a Scalable Database

To ensure scalability, focus on horizontal and vertical scaling strategies.

### 1. Database Schema Design
- Use **normalized schema** to reduce redundancy.
- Selectively **denormalize** for performance-critical operations.

### 2. Horizontal Scaling
- **Sharding**: Distribute data across multiple nodes.
- **Partitioning**: Divide large tables logically (e.g., time-based partitions).

### 3. Replication
- **Master-slave replication** for better read performance.
- **Multi-master replication** for write-heavy applications.

### 4. Caching
- Use **Redis/Memcached** to reduce database load.
- Implement **query-level caching**.

### 5. Load Balancing
- Distribute queries across multiple instances using **load balancers**.

### 6. Asynchronous Processing
- Use **Kafka/RabbitMQ** for write-intensive operations.

### 7. Distributed Databases
- Consider **Cassandra, CockroachDB, MongoDB** for large-scale applications.
- Use **cloud databases** like AWS RDS, Google Cloud SQL.

### 8. Monitoring and Optimization
- Track **query performance, CPU usage, memory utilization, disk I/O**.
- Optimize **slow queries** and update indexes.

### 9. Archiving and Data Management
- Archive old data separately to improve active dataset performance.

### Challenges and Mitigation Strategies

#### 1. Data Consistency
- Use **eventual consistency** models where acceptable.

#### 2. Shard Management
- Plan **sharding keys** carefully to avoid re-sharding issues.

#### 3. Query Optimization
- Minimize **joins across shards or replicas**.

---

# Exception Handling in Spring Boot Applications

Exception handling in a Spring Boot application can be managed in an organized way using several key approaches:

## 1. Using `@ControllerAdvice` and `@ExceptionHandler`

`@ControllerAdvice` is used to define a global exception handler for the entire application, combined with `@ExceptionHandler` to specify how to handle particular exceptions.

**Example:**

```java
@RestControllerAdvice
public class GlobalExceptionHandler {

    @ExceptionHandler(ResourceNotFoundException.class)
    public ResponseEntity<String> handleResourceNotFound(ResourceNotFoundException ex) {
        return new ResponseEntity<>(ex.getMessage(), HttpStatus.NOT_FOUND);
    }

    @ExceptionHandler(Exception.class)
    public ResponseEntity<String> handleGenericException(Exception ex) {
        return new ResponseEntity<>("An unexpected error occurred: " + ex.getMessage(), HttpStatus.INTERNAL_SERVER_ERROR);
    }
}
```

This ensures that exceptions are handled consistently and provides proper HTTP responses.

---

## 2. Using `@ResponseStatus` Annotation

The `@ResponseStatus` annotation maps exceptions to specific HTTP status codes.

**Example:**

```java
@ResponseStatus(HttpStatus.NOT_FOUND)
public class ResourceNotFoundException extends RuntimeException {
    public ResourceNotFoundException(String message) {
        super(message);
    }
}
```

When this exception is thrown, Spring automatically returns a 404 status with the custom message.

---

## 3. Custom Error Response Structure

For detailed error responses, create a custom error object containing fields like timestamp, error code, and message.

**Example:**

```java
public class ErrorResponse {
    private String timestamp;
    private String message;
    private String details;
    
    // Getters and setters
}
```

This custom object can be returned from the global exception handler:

```java
@ExceptionHandler(Exception.class)
public ResponseEntity<ErrorResponse> handleAllExceptions(Exception ex, WebRequest request) {
    ErrorResponse error = new ErrorResponse();
    error.setTimestamp(LocalDateTime.now().toString());
    error.setMessage(ex.getMessage());
    error.setDetails(request.getDescription(false));

    return new ResponseEntity<>(error, HttpStatus.INTERNAL_SERVER_ERROR);
}
```

---

## 4. Handling Validation Exceptions

When using `@Valid` or `@Validated`, Spring automatically throws `MethodArgumentNotValidException` for validation failures. This can be handled as follows:

```java
@ExceptionHandler(MethodArgumentNotValidException.class)
public ResponseEntity<String> handleValidationException(MethodArgumentNotValidException ex) {
    String errors = ex.getBindingResult().getAllErrors().stream()
                      .map(ObjectError::getDefaultMessage)
                      .collect(Collectors.joining(", "));
    return new ResponseEntity<>("Validation failed: " + errors, HttpStatus.BAD_REQUEST);
}
```

---

## 5. Logging Exceptions

All exceptions can be logged using SLF4J or a similar framework to ensure proper monitoring and debugging.

```java
private static final Logger logger = LoggerFactory.getLogger(GlobalExceptionHandler.class);

@ExceptionHandler(Exception.class)
public ResponseEntity<String> handleGenericException(Exception ex) {
    logger.error("An error occurred: ", ex);
    return new ResponseEntity<>("Something went wrong", HttpStatus.INTERNAL_SERVER_ERROR);
}
```

---

## 6. Fallback for Unhandled Exceptions

A fallback mechanism ensures unhandled exceptions are caught and returned with a generic error response.

---

# Writing Custom Methods in MongoDB

Creating a custom method in MongoDB depends on the context of its usage. If the goal is to implement custom queries or operations, it can be achieved through a combination of the following techniques:

## 1. Using the MongoDB Shell or Compass

Custom logic can be written directly using the JavaScript-based MongoDB shell. For example:

```javascript
db.collectionName.findCustom = function(criteria) {
    return this.find({ $or: [criteria] }).sort({ createdAt: -1 });
};
```

This adds a custom method (`findCustom`) to a collection that can be reused. However, this is typically used for quick testing or prototyping.

---

## 2. Using MongoDB Aggregation Framework

For complex queries, the aggregation framework can be used to implement custom logic.

**Example:**

```javascript
db.orders.aggregate([
    { $match: { status: "Pending" } },
    { $group: { _id: "$customerId", total: { $sum: "$amount" } } },
    { $sort: { total: -1 } }
]);
```

This retrieves all pending orders, groups them by customer, calculates the total amount, and sorts the result.

---

## 3. In Application Code (Custom Repository Methods)

Custom methods are often created in application code using a driver like Mongoose (Node.js) or Spring Data MongoDB (Java).

**Example: Using Spring Data MongoDB**

a) Define a Custom Repository Interface:

```java
public interface CustomUserRepository {
    List<User> findUsersByCustomCriteria(String status, int minAge);
}
```

b) Implement the Custom Repository:

```java
public class CustomUserRepositoryImpl implements CustomUserRepository {

    @Autowired
    private MongoTemplate mongoTemplate;

    @Override
    public List<User> findUsersByCustomCriteria(String status, int minAge) {
        Query query = new Query();
        query.addCriteria(Criteria.where("status").is(status).and("age").gte(minAge));
        return mongoTemplate.find(query, User.class);
    }
}
```

c) Integrate the Repository in a Service:

```java
@Service
public class UserService {
    @Autowired
    private CustomUserRepository customUserRepository;

    public List<User> getFilteredUsers(String status, int minAge) {
        return customUserRepository.findUsersByCustomCriteria(status, minAge);
    }
}
```

This approach allows clean separation of custom query logic and integrates seamlessly into the application.

---

## 4. Custom JavaScript Functions in MongoDB

For reusable custom logic, MongoDB allows custom JavaScript functions to be stored on the server.

a) Define a JavaScript Function:

```javascript
db.system.js.save({
    _id: "findUsersByAge",
    value: function(age) {
        return db.users.find({ age: { $gte: age } });
    }
});
```

b) Call the Function:

```javascript
db.loadServerScripts();
findUsersByAge(30);
```

---

## 5. Custom Commands

MongoDB supports defining custom commands at the database level using server-side scripts or through MongoDB plugins.

---

# Differences Between Maven and Gradle

| Feature                | Maven                                      | Gradle                                   |
|------------------------|--------------------------------------------|------------------------------------------|
| **Build Script**        | XML-based (`pom.xml`)                     | Groovy/Kotlin-based (`build.gradle`)     |
| **Performance**         | Slower due to XML parsing                 | Faster due to incremental builds         |
| **Flexibility**         | Less flexible, rigid structure            | Highly flexible, supports custom logic   |
| **Dependency Management| Centralized, uses repositories            | Supports multiple repositories           |
| **Learning Curve**      | Easier for beginners                      | Steeper due to Groovy/Kotlin syntax      |
| **Community Support**   | Large, mature community                   | Growing, modern community                |
| **Plugin Ecosystem**    | Extensive, but less dynamic               | Dynamic, easy to create custom plugins   |
| **Build Lifecycle**     | Fixed lifecycle phases                    | Customizable, task-based                 |
```
Here is the content rendered into a `.md` file format suitable for your GitHub repository:

```markdown
# Rebasing in Git

Rebasing in Git is a way to reapply commits from one branch onto another branch in a linear sequence. It essentially transfers the base of the branch you are working on to another branch, giving you a cleaner project history.

## How Rebasing Works

- Git replays the commits from your branch onto the target branch one by one.
- The commits are re-created with new commit hashes since they’re applied in a different context.

## Command

```bash
git checkout feature-branch
git rebase main
```

This moves the `feature-branch` commits to start after the `main` branch commits.

## Advantages

- **Clean History**: Keeps the commit history linear and easier to read.
- **Avoids Merge Commits**: Unlike merging, rebasing doesn’t create extra merge commits.

## When to Use

- For keeping feature branches up to date with the main branch.
- To clean up commit history before merging.

## Risks

- **Rewriting History**: Rebasing changes commit hashes, which can cause issues in shared branches.
- **Conflict Resolution**: Requires resolving conflicts for each commit being replayed.

---

# Advantages of Lambda Expressions

Lambda expressions in Java provide several advantages:

1. **Concise Code**: Reduces boilerplate code, making it more readable.
2. **Functional Programming**: Enables functional programming paradigms like passing behavior as a method argument.
3. **Improved APIs**: Enhances APIs like the Stream API for better data processing.
4. **Parallel Processing**: Simplifies parallel processing with streams.

---

# Contract Between `hashCode()` and `equals()` in Java

The contract between `hashCode()` and `equals()` can be described as follows:

1. **If two objects are equal (as per `equals()` method), they must have the same `hashCode()`**.
   - This ensures consistent behavior in hash-based collections.
2. **If two objects have the same `hashCode()`, they are not guaranteed to be equal**.
   - Collisions can occur, where different objects share the same hash code.
3. **Overriding `equals()` requires overriding `hashCode()` as well**.
   - Failing to do so can lead to inconsistent behavior in collections.

## Example

### Without Proper Implementation

```java
class Person {
    String name;

    Person(String name) {
        this.name = name;
    }

    @Override
    public boolean equals(Object o) {
        if (o instanceof Person) {
            return ((Person) o).name.equals(this.name);
        }
        return false;
    }
}
```

If `hashCode()` is not overridden, two `Person` objects with the same name may have different hash codes, leading to inconsistent behavior in collections.

### With Proper Implementation

```java
class Person {
    String name;

    Person(String name) {
        this.name = name;
    }

    @Override
    public boolean equals(Object o) {
        if (o instanceof Person) {
            return ((Person) o).name.equals(this.name);
        }
        return false;
    }

    @Override
    public int hashCode() {
        return name.hashCode();
    }
}
```

Now, objects with the same name will have the same hash code, ensuring consistent behavior in hash-based collections.

---

# What is a WeakHashMap?

A `WeakHashMap` is a type of map in Java where the keys are stored as weak references. This means that if there are no strong references to a key object, it can be garbage collected, even if it still exists in the map.

## Key Features

1. **Weak References for Keys**:
   - The keys are weakly referenced. If a key is no longer reachable by any active thread (i.e., no strong references exist to it), the entry for that key will be removed from the map during the next garbage collection cycle.
2. **Automatic Garbage Collection**:
   - This behavior is particularly useful for caching scenarios where we don’t want the keys to persist in memory unnecessarily once they are no longer used elsewhere.
3. **No Impact on Values**:
   - The values in the `WeakHashMap` are strong references, meaning they won’t be garbage collected unless they are no longer referenced by any object.

## Use Cases

- **Memory-sensitive caching**: When objects used as keys are large or expensive to create, you can let the garbage collector reclaim them if they are no longer in use.
- **Metadata management**: When you need to store temporary mappings that should not prevent the referenced objects from being garbage collected.

## Example

```java
import java.util.*;

public class WeakHashMapExample {
    public static void main(String[] args) {
        Map<String, String> map = new WeakHashMap<>();
        
        String key = new String("Key");
        map.put(key, "Value");
        System.out.println("Before GC: " + map);
        key = null;  // Remove strong reference to key
        
        // Suggesting garbage collection
        System.gc();
        System.out.println("After GC: " + map);  // Entry may be removed
    }
}
```

In this example, once the strong reference to `key` is removed (set to `null`), the garbage collector can reclaim it, and the entry may be removed from the `WeakHashMap`.

---

# Internal Working of ConcurrentHashMap

A `ConcurrentHashMap` is a thread-safe map introduced in Java 5, designed for high concurrency, which allows multiple threads to read and write to the map concurrently without blocking each other.

## Internal Working

1. **Segmented Locking (Bucket-Level Locking)**:
   - Internally, `ConcurrentHashMap` divides the map into segments, each of which is independently locked.
   - The map is divided into a number of segments (usually 16). Each segment behaves like a separate hash table, and each segment can be locked independently, which allows multiple threads to work on different segments simultaneously without contention.
2. **Buckets**:
   - Within each segment, the `ConcurrentHashMap` uses an array of buckets, just like a regular hash map. Each bucket holds a linked list of entries (key-value pairs) or uses a more advanced data structure like a balanced tree for high-concurrency scenarios.
3. **Concurrency Level**:
   - The concurrency level defines how many segments the map should be divided into. This can be adjusted during the map’s creation using the constructor. By default, it’s set to 16 segments, meaning 16 threads can work in parallel, with each thread accessing a different segment.
4. **Lock Striping**:
   - The segments implement lock striping, which allows each segment to be locked independently.
   - When a thread accesses the map and wants to perform an operation (like `put` or `remove`), it first calculates which segment the key belongs to using the hash value. Then it locks that particular segment.
5. **Non-Blocking Reads**:
   - One of the key features of `ConcurrentHashMap` is that reads are non-blocking. Multiple threads can read from the map simultaneously without locking, as long as they are not modifying the same segment. This significantly improves performance in high-concurrency scenarios.
6. **Write Operations (Locking)**:
   - When a thread performs a write operation (like `put` or `remove`), the corresponding segment is locked. However, since only one thread can modify a segment at a time, this minimizes contention.
   - For key-value pairs in buckets, the modification is done with finer granularity, locking only the specific segment and bucket being updated.
7. **Increased Scalability**:
   - The use of segments and lock striping increases the scalability of the `ConcurrentHashMap`. It’s particularly beneficial in multi-core systems where several threads can access different segments in parallel, reducing the overall contention and improving throughput.
8. **Rehashing**:
   - Just like `HashMap`, `ConcurrentHashMap` handles rehashing when the number of entries exceeds a certain threshold. However, during rehashing, only the segment being expanded is locked, so other segments are still available for concurrent operations.

## Operations

- **`put()`**:
  - The key’s hash value is used to determine the segment.
  - The corresponding segment is locked (if necessary), and the key-value pair is added to the appropriate bucket in that segment.
  - If the bucket’s size exceeds a threshold, a resize or rehashing may occur.
- **`get()`**:
  - The hash value is used to find the correct segment and bucket.
  - Reads can occur concurrently, and they don’t require locking the entire map or segment, which makes the operation faster.
- **`computeIfAbsent()`**:
  - A thread-safe method that computes a value if it’s absent, typically using a lambda expression to create or fetch the value.
  - This method ensures that only one thread can compute the value for a particular key at a time.

---

# Converting a List to a Set in Java

To convert a list of student names into a set, the list can be passed directly to the constructor of the `Set` interface, such as a `HashSet`.

## Example

```java
import java.util.*;

public class ListToSetExample {
    public static void main(String[] args) {
        List<String> studentNames = Arrays.asList("Alice", "Bob", "Alice", "Charlie", "Bob");
        // Convert list to set
        Set<String> uniqueNames = new HashSet<>(studentNames);
        // Print the set
        System.out.println("Unique Names: " + uniqueNames);
    }
}
```

## What Happens to Duplicate Names?

When converting the list to a set:

- Duplicate names are automatically removed because a `Set` does not allow duplicate elements.
- Only one instance of each name will remain in the set, ensuring all elements in the set are unique.

For example, if the list contains:
`["Alice", "Bob", "Alice", "Charlie", "Bob"]`,
the resulting set will contain:
`["Alice", "Bob", "Charlie"]`.

This behavior is particularly useful when the goal is to eliminate duplicates from a collection.

---

# Deep Copy in Java

A deep copy refers to creating an entirely new copy of an object, including its nested or referenced objects. In a deep copy, changes made to the copied object do not affect the original object and vice versa. This is because the deep copy creates new instances for all referenced objects as well.

## Example

Let’s demonstrate this with a `Student` class containing a nested `Address` object.

```java
class Address implements Cloneable {
    String city;
    String state;

    public Address(String city, String state) {
        this.city = city;
        this.state = state;
    }

    @Override
    protected Object clone() throws CloneNotSupportedException {
        return new Address(this.city, this.state); // Create a new Address instance
    }
}

class Student implements Cloneable {
    String name;
    Address address;

    public Student(String name, Address address) {
        this.name = name;
        this.address = address;
    }

    @Override
    protected Object clone() throws CloneNotSupportedException {
        // Perform deep copy
        Student clonedStudent = (Student) super.clone(); 
        clonedStudent.address = (Address) address.clone(); // Clone nested Address object
        return clonedStudent;
    }
}

public class DeepCopyExample {
    public static void main(String[] args) throws CloneNotSupportedException {
        // Original object
        Address address = new Address("New York", "NY");
        Student originalStudent = new Student("John", address);
        // Perform deep copy
        Student clonedStudent = (Student) originalStudent.clone();
        // Modify cloned object
        clonedStudent.name = "Alice";
        clonedStudent.address.city = "Los Angeles";
        // Print both objects
        System.out.println("Original Student: " + originalStudent.name + ", Address: " 
                + originalStudent.address.city + ", " + originalStudent.address.state);
        System.out.println("Cloned Student: " + clonedStudent.name + ", Address: " 
                + clonedStudent.address.city + ", " + clonedStudent.address.state);
    }
}
```

### Output

```
Original Student: John, Address: New York, NY  
Cloned Student: Alice, Address: Los Angeles, NY
```

## Advantages of Deep Copy

- Ensures complete independence between the original and the copied object.
- Ideal when the object contains nested objects or mutable fields.
```



