# 🚀 Java Full Stack with React — Interview Questions
### Code Implementation & Scenario-Based Questions (No Answers)
> Covers all major tech stacks in a Java Full Stack + React role | Updated 2025–2026

---

## 📋 Table of Contents

1. [Core Java](#1-core-java)
2. [Java 8+ Features (Streams, Lambdas, Functional)](#2-java-8-features)
3. [Data Structures & Algorithms (Java)](#3-data-structures--algorithms-java)
4. [OOP & Design Patterns](#4-oop--design-patterns)
5. [Spring Core & Dependency Injection](#5-spring-core--dependency-injection)
6. [Spring Boot](#6-spring-boot)
7. [Spring Security & JWT](#7-spring-security--jwt)
8. [Spring Data JPA & Hibernate](#8-spring-data-jpa--hibernate)
9. [REST API Design & Development](#9-rest-api-design--development)
10. [Microservices Architecture](#10-microservices-architecture)
11. [SQL & Database Design](#11-sql--database-design)
12. [NoSQL — MongoDB](#12-nosql--mongodb)
13. [React — Core Concepts](#13-react--core-concepts)
14. [React Hooks](#14-react-hooks)
15. [React State Management (Redux / Context API)](#15-react-state-management-redux--context-api)
16. [React — Advanced Patterns](#16-react--advanced-patterns)
17. [JavaScript & TypeScript (ES6+)](#17-javascript--typescript-es6)
18. [HTML & CSS](#18-html--css)
19. [API Integration (React ↔ Spring Boot)](#19-api-integration-react--spring-boot)
20. [Testing (JUnit, Mockito, React Testing Library)](#20-testing-junit-mockito-react-testing-library)
21. [Docker & DevOps / CI-CD](#21-docker--devops--ci-cd)
22. [System Design & Architecture](#22-system-design--architecture)
23. [Security Best Practices](#23-security-best-practices)
24. [Scenario-Based Full Stack Integration Questions](#24-scenario-based-full-stack-integration-questions)

---

## 1. Core Java

### Code Implementation Questions

1. Implement a thread-safe singleton class in Java using double-checked locking.
2. Write a Java program to find all duplicate characters in a string without using any collection library.
3. Implement your own `HashMap` in Java — explain how `put()`, `get()`, and collision handling work internally.
4. Write a Java program to reverse a linked list both iteratively and recursively.
5. Implement a blocking queue from scratch using `wait()` and `notifyAll()`.
6. Write a program to detect a cycle in a linked list using Floyd's algorithm.
7. Implement a custom `Iterator` for a generic stack class.
8. Write a multithreaded program where two threads print odd and even numbers alternately up to 100.
9. Implement `Comparable` and `Comparator` for a custom `Employee` class and sort a list by salary, then by name.
10. Write a Java program to serialize and deserialize a custom object to/from JSON manually.
11. Demonstrate the difference between `String`, `StringBuilder`, and `StringBuffer` with a performance benchmark.
12. Implement a producer-consumer problem using `BlockingQueue`.
13. Write a Java program to find the longest palindrome substring in a given string.
14. Implement a generic `Pair<A, B>` class in Java.
15. Write a program using `ExecutorService` to run 10 tasks concurrently and collect results.

### Scenario-Based Questions

16. **Scenario:** Your application is throwing `ConcurrentModificationException` intermittently in production while iterating a list. What is the root cause and how do you fix it?
17. **Scenario:** You have a critical section that is causing a deadlock between two threads each waiting for the other's lock. How would you identify and resolve this?
18. **Scenario:** A method in your code is returning `Optional.empty()` but downstream code is calling `.get()` on it, throwing `NoSuchElementException`. How do you refactor this safely?
19. **Scenario:** Your Java application is consuming excessive heap memory. Walk through the steps you take to identify the leak and fix it using tools like JVisualVM or JProfiler.
20. **Scenario:** You need to make a legacy method thread-safe without modifying its signature. What approaches do you consider?

---

## 2. Java 8+ Features

### Code Implementation Questions

1. Write a Java 8 Stream pipeline that reads a list of employees, filters those with salary > 50000, groups them by department, and counts each group.
2. Implement a functional interface `Transformer<T, R>` and use it with a lambda expression and method reference.
3. Use `Stream.flatMap()` to flatten a list of lists of integers and find the sum of distinct elements.
4. Write a program using `Collectors.toMap()` that converts a list of `Product` objects to a `Map<String, Double>` (name → price), handling duplicate keys.
5. Demonstrate `CompletableFuture.supplyAsync()`, `thenApply()`, and `exceptionally()` for an async task chain.
6. Write a program using `Optional` chaining: `Optional.ofNullable()` → `map()` → `filter()` → `orElseGet()`.
7. Use `Predicate`, `Function`, `Consumer`, and `Supplier` functional interfaces in a single program.
8. Implement a parallel stream to compute the average salary of employees and compare its performance with a sequential stream.
9. Write a program using `Stream.reduce()` to compute the product of all elements in a list.
10. Demonstrate the use of `Collectors.partitioningBy()` and `Collectors.groupingBy()` on a student result list.
11. Use `Map.computeIfAbsent()`, `merge()`, and `getOrDefault()` in a word frequency counter.
12. Write a program to find the second-highest salary in a list using Java 8 Streams.
13. Implement a custom `Collector` that joins strings with a delimiter and wraps them in brackets.
14. Use `IntStream.range()` and `Stream.iterate()` to generate Fibonacci numbers.
15. Write a program using `LocalDate`, `LocalDateTime`, and `DateTimeFormatter` to calculate working days between two dates.

### Scenario-Based Questions

16. **Scenario:** A senior developer says "replace all for-loops with streams." When should you NOT use streams, and what trade-offs do you consider?
17. **Scenario:** Your stream pipeline is producing incorrect results with a stateful lambda. Identify the problem and refactor it.
18. **Scenario:** A `CompletableFuture` chain is silently swallowing exceptions. How do you add proper error handling?
19. **Scenario:** You need to process 10 million records from a database using Java streams without loading all into memory. How do you design this?
20. **Scenario:** You have a method returning `Optional<User>` but a team member keeps calling `.get()` without checking. How do you enforce safe usage at the design level?

---

## 3. Data Structures & Algorithms (Java)

### Code Implementation Questions

1. Implement binary search on a rotated sorted array.
2. Write a Java program to implement LRU Cache using `LinkedHashMap`.
3. Implement merge sort and quick sort and analyze their time complexities.
4. Write a program to find the kth largest element in an unsorted array without full sorting.
5. Implement a Trie data structure supporting insert, search, and startsWith operations.
6. Write a program to check if two strings are anagrams of each other using O(n) time.
7. Implement BFS and DFS for a graph represented as an adjacency list.
8. Write a program to find all subsets of a set (power set) using recursion and bitmasking.
9. Implement a stack that supports `push`, `pop`, and `getMin` in O(1) time.
10. Write a program to find the longest common subsequence of two strings using dynamic programming.
11. Implement Dijkstra's algorithm to find the shortest path in a weighted graph.
12. Write a program to detect and return the starting node of a cycle in a linked list.
13. Implement a `PriorityQueue`-based solution for the "Top K Frequent Elements" problem.
14. Write a program to solve the 0/1 Knapsack problem using dynamic programming.
15. Implement an in-place algorithm to move all zeros to the end of an array.

### Scenario-Based Questions

16. **Scenario:** Your API's search feature has O(n²) complexity and is slow for large datasets. How do you optimize it using appropriate data structures?
17. **Scenario:** You are asked to design an autocomplete feature for a search bar. Which data structure do you use and why?
18. **Scenario:** A recursive function is causing stack overflow on deep inputs. How do you convert it to an iterative approach?

---

## 4. OOP & Design Patterns

### Code Implementation Questions

1. Implement the Builder pattern for a complex `HttpRequest` object with optional fields.
2. Write a Java example of the Strategy pattern for a payment gateway (CreditCard, PayPal, UPI).
3. Implement the Observer pattern where a `StockMarket` notifies multiple `Investor` objects on price change.
4. Write a Factory Method pattern to create different types of database connections.
5. Implement the Decorator pattern to add logging and caching behavior to an existing service class without modifying it.
6. Demonstrate polymorphism with method overriding — create a shape hierarchy and compute areas.
7. Implement the Proxy pattern to add lazy initialization and access control to a resource-heavy service.
8. Write an example of the Chain of Responsibility pattern for request validation middleware.
9. Implement the Template Method pattern for a data export pipeline (CSV, PDF, Excel).
10. Demonstrate composition over inheritance with a real-world example.

### Scenario-Based Questions

11. **Scenario:** You have a class with 15 constructor parameters. Multiple teams are calling it differently, causing bugs. Which pattern do you apply and why?
12. **Scenario:** Your codebase violates the Open/Closed Principle — adding a new payment method requires modifying existing code. Refactor it using an appropriate pattern.
13. **Scenario:** You need to add audit logging to 20 service methods without modifying each one. What approach do you use?

---

## 5. Spring Core & Dependency Injection

### Code Implementation Questions

1. Write a Spring application demonstrating constructor injection, setter injection, and field injection — and explain which is preferred and why.
2. Implement a custom `BeanPostProcessor` to log bean initialization times.
3. Write a `@Configuration` class that conditionally registers a bean based on an environment variable using `@ConditionalOnProperty`.
4. Implement a Spring AOP aspect that logs method execution time for all methods in a service layer.
5. Demonstrate the difference between `@Component`, `@Service`, `@Repository`, and `@Controller` with practical examples.
6. Write a Spring application showing `@Scope("prototype")` vs `@Scope("singleton")` behavior with a counter bean.
7. Implement a custom Spring annotation that triggers validation logic via AOP.
8. Write a Spring `@EventListener` and `ApplicationEventPublisher` example for a user registration event.
9. Demonstrate how circular dependency is resolved in Spring using `@Lazy`.
10. Implement a custom `ApplicationContextInitializer` to load external configuration.

### Scenario-Based Questions

11. **Scenario:** Two beans of the same type are registered. Injection is failing with `NoUniqueBeanDefinitionException`. How do you resolve it?
12. **Scenario:** Your Spring AOP advice is not being applied to methods called within the same bean. Why, and how do you fix it?
13. **Scenario:** A `@Prototype`-scoped bean is injected into a `@Singleton` bean and always returns the same instance. What went wrong?

---

## 6. Spring Boot

### Code Implementation Questions

1. Create a Spring Boot REST API with full CRUD operations for a `Product` entity using `@RestController`, `@RequestMapping`, `@PathVariable`, and `@RequestBody`.
2. Implement global exception handling using `@ControllerAdvice` and `@ExceptionHandler` that returns structured error responses.
3. Write a Spring Boot application with multiple profiles (`dev`, `qa`, `prod`) using `application-{profile}.yml` files.
4. Implement pagination and sorting for a `GET /users` endpoint using Spring Data's `Pageable`.
5. Write a Spring Boot scheduled task using `@Scheduled(cron = "...")` that sends a daily summary report.
6. Implement file upload and download endpoints in Spring Boot using `MultipartFile`.
7. Add request validation to a `POST /orders` endpoint using `@Valid`, `@NotNull`, `@Size`, and custom constraint annotations.
8. Write a Spring Boot application exposing custom Actuator endpoints to report application health metrics.
9. Implement API versioning in Spring Boot (URI-based, header-based, and parameter-based approaches).
10. Create a Spring Boot application that reads configuration from a `@ConfigurationProperties` class with nested objects.
11. Implement rate limiting on a REST endpoint using Spring Boot and Bucket4j or Redis.
12. Write a Spring Boot filter (`OncePerRequestFilter`) that adds a correlation ID to every request and response.
13. Implement an asynchronous REST endpoint using `@Async` and `CompletableFuture` in Spring Boot.
14. Write a Spring Boot application that integrates with Apache Kafka — produce and consume messages.
15. Implement caching in Spring Boot using `@Cacheable`, `@CachePut`, and `@CacheEvict` with Redis.

### Scenario-Based Questions

16. **Scenario:** Your Spring Boot application starts fine locally but throws `Port 8080 already in use` in CI/CD. How do you handle this programmatically?
17. **Scenario:** An API endpoint works for small payloads but times out for large ones. Walk through the performance investigation and fix.
18. **Scenario:** You need to disable a specific auto-configuration in Spring Boot for a test environment. How do you do it?
19. **Scenario:** A `@Transactional` method is not rolling back on a checked exception. Why, and how do you fix it?
20. **Scenario:** Your Spring Boot application's memory usage grows over hours in production. List the steps to diagnose and resolve the leak.
21. **Scenario:** Multiple microservices share common configuration. How do you centralize this using Spring Cloud Config Server?
22. **Scenario:** You are asked to implement graceful shutdown for a Spring Boot app that is processing messages from a queue. How do you approach this?

---

## 7. Spring Security & JWT

### Code Implementation Questions

1. Implement JWT-based authentication in a Spring Boot application — include token generation, validation filter, and securing endpoints.
2. Write a `UserDetailsService` implementation that loads user details from a database.
3. Implement role-based access control with `@PreAuthorize("hasRole('ADMIN')")` and `@Secured`.
4. Write a Spring Security configuration class (using `SecurityFilterChain` bean pattern from Spring Security 6) that permits public endpoints and secures the rest.
5. Implement refresh token functionality — generate, store, validate, and rotate refresh tokens.
6. Write a custom `AuthenticationProvider` to support OTP-based authentication.
7. Implement OAuth2 login with Google using Spring Security OAuth2 client.
8. Write a filter that blacklists JWT tokens upon user logout.
9. Implement method-level security using `@PostFilter` and `@PreFilter` on a list-returning service method.
10. Configure CORS globally in a Spring Security 6 application.

### Scenario-Based Questions

11. **Scenario:** Users are being logged out unexpectedly after a few minutes. You suspect the JWT expiry is too short. How do you implement a seamless token refresh mechanism?
12. **Scenario:** Your API is vulnerable to CSRF attacks. How do you protect it when using JWT (stateless) vs session-based (stateful) auth?
13. **Scenario:** An attacker is making repeated login attempts (brute force). How do you implement account lockout using Spring Security?
14. **Scenario:** A user's role is changed in the database, but their existing JWT still grants them old permissions. How do you solve this?

---

## 8. Spring Data JPA & Hibernate

### Code Implementation Questions

1. Write a Spring Data JPA repository with a custom JPQL query to find top 5 products by sales grouped by category.
2. Implement a one-to-many bidirectional relationship between `Order` and `OrderItem` with proper cascade and fetch type configuration.
3. Write a Hibernate entity with an `@Embeddable` address class and demonstrate its use.
4. Implement optimistic locking using `@Version` annotation on a `BankAccount` entity.
5. Write a Spring Data specification to build dynamic queries for a product filter (price range, category, availability).
6. Implement a many-to-many relationship between `Student` and `Course` with a join table using `@ManyToMany` and `@JoinTable`.
7. Write a native SQL query using `@Query(nativeQuery = true)` to fetch paginated results with a custom sort.
8. Implement soft delete (logical delete) in a JPA entity using `@Where` and `@SQLDelete`.
9. Write a `@NamedEntityGraph` to eagerly fetch associated entities for a specific query.
10. Implement an `AuditingEntityListener` to automatically populate `createdAt`, `updatedAt`, `createdBy`, `updatedBy` fields.
11. Write a Spring Batch job using Spring Boot to read from a CSV, process records, and write to a database.
12. Demonstrate the N+1 query problem with a code example and fix it using `JOIN FETCH` or `@EntityGraph`.
13. Implement a projection interface to retrieve only specific fields from a JPA query.
14. Write a `@Transactional` service method that updates multiple entities and demonstrate rollback behavior.
15. Implement database migration using Flyway with versioned SQL scripts in Spring Boot.

### Scenario-Based Questions

16. **Scenario:** Your application is making 101 SQL queries for a list of 100 orders with their items. Identify the problem and solve it.
17. **Scenario:** Two concurrent transactions are updating the same record. You're getting stale data overwrites. How do you prevent this using JPA?
18. **Scenario:** `LazyInitializationException` is thrown when accessing a lazily loaded collection outside of a transaction. How do you handle it?
19. **Scenario:** Hibernate is generating cartesian product queries for a multi-level fetch join. How do you resolve it?
20. **Scenario:** Your entity has a `@OneToMany` collection that grows to millions of rows. Fetching the parent entity is extremely slow. How do you fix this?

---

## 9. REST API Design & Development

### Code Implementation Questions

1. Design and implement a RESTful API for an e-commerce order management system — include resources, HTTP methods, status codes, and request/response bodies.
2. Implement HATEOAS in a Spring Boot REST API using Spring HATEOAS library.
3. Write a REST API that supports partial updates using `HTTP PATCH` and JSON Merge Patch.
4. Implement an API with idempotency keys for payment endpoints to prevent duplicate processing.
5. Write a REST API with content negotiation supporting both JSON and XML responses.
6. Implement long-polling or Server-Sent Events (SSE) for a real-time notification endpoint.
7. Write a REST API with request throttling — allow 100 requests per minute per user.
8. Implement API documentation with Swagger/OpenAPI 3.0 annotations in Spring Boot.
9. Write a REST API with conditional GET using ETags and `If-None-Match` headers.
10. Implement a batch API endpoint that accepts multiple operations and returns results for each.

### Scenario-Based Questions

11. **Scenario:** A client is calling your API and sometimes gets 200 OK with an error message in the body. What is wrong with this design and how do you fix it?
12. **Scenario:** Your API is consumed by both a mobile app and a web app. The mobile app needs fewer fields. How do you handle this without creating two separate APIs?
13. **Scenario:** You need to deprecate a REST API endpoint without breaking existing clients. What strategies do you use?
14. **Scenario:** A client is making 50 API calls to populate one screen. How do you optimize this using API aggregation or BFF (Backend for Frontend) pattern?

---

## 10. Microservices Architecture

### Code Implementation Questions

1. Write a Spring Boot microservice that registers with Eureka Discovery Server and calls another service using `WebClient` with load balancing.
2. Implement a circuit breaker using Resilience4j `@CircuitBreaker` annotation on a service call.
3. Write a Spring Cloud Gateway configuration with routing, rate limiting, and JWT validation filter.
4. Implement distributed tracing across microservices using Spring Boot + Zipkin/Sleuth (Micrometer Tracing).
5. Write a Saga pattern implementation (choreography-based) for a distributed order processing flow.
6. Implement an event-driven communication between two services using Apache Kafka — produce domain events and consume them.
7. Write a Spring Boot application that implements the Outbox Pattern to ensure reliable event publishing with database changes.
8. Implement a retry mechanism with exponential backoff using Resilience4j on an HTTP client call.
9. Write a config server setup with Spring Cloud Config and a client that refreshes configuration at runtime.
10. Implement a bulkhead pattern using Resilience4j to isolate thread pools for different service calls.

### Scenario-Based Questions

11. **Scenario:** Service A calls Service B, which calls Service C. Service C is down and the failure is cascading upstream. How do you prevent this?
12. **Scenario:** Two microservices need to update their own databases as part of a single business transaction. How do you maintain data consistency without a distributed transaction?
13. **Scenario:** A message has been published to Kafka, but the corresponding database write failed. The system is now in an inconsistent state. What pattern prevents this?
14. **Scenario:** Your microservices deployment has 10 services, each requiring different environment variables. How do you manage this centrally?
15. **Scenario:** You need to implement authentication across all microservices without duplicating code in each. What approach do you take?

---

## 11. SQL & Database Design

### Code Implementation Questions

1. Write a SQL query to find the second highest salary per department using window functions.
2. Design a normalized database schema for an online learning platform with users, courses, lessons, enrollments, and progress.
3. Write a SQL query using `WITH` (CTE) to calculate a running total of daily sales for the last 30 days.
4. Implement an SQL query with self-join to find employees who earn more than their managers.
5. Write a stored procedure in MySQL/PostgreSQL that accepts a department ID and returns the top 3 earners.
6. Implement a SQL trigger that logs every `UPDATE` on an `orders` table to an `audit_log` table.
7. Write SQL to find duplicate rows in a table and delete all but the most recently created one.
8. Implement a query using `PIVOT` (or equivalent) to show monthly sales totals for each product category in columns.
9. Write an optimized query to get all products with no sales in the last 6 months using `NOT EXISTS` vs `LEFT JOIN` — compare both.
10. Implement a recursive CTE to traverse a hierarchical employee-manager tree.
11. Write a query to calculate the month-over-month growth percentage in revenue.
12. Design and implement indexes for a `users` table with frequent queries on `email`, `city`, and `created_at` combinations.
13. Write a SQL query using `RANK()`, `DENSE_RANK()`, and `ROW_NUMBER()` and explain their difference.
14. Implement a transaction in SQL that transfers funds between two accounts with proper locking.
15. Write a query to identify slow queries and explain how you would optimize them using `EXPLAIN ANALYZE`.

### Scenario-Based Questions

16. **Scenario:** A query that joins 5 tables takes 8 seconds on 10 million rows. Walk through your optimization strategy.
17. **Scenario:** You added an index on a `status` column with only 3 distinct values, but queries are still doing full table scans. Why?
18. **Scenario:** Your database is experiencing deadlocks during concurrent batch updates. How do you detect and resolve them?
19. **Scenario:** You need to add a column to a table with 500 million rows in production without downtime. How do you approach this?

---

## 12. NoSQL — MongoDB

### Code Implementation Questions

1. Write a MongoDB aggregation pipeline that groups orders by customer, calculates total spend, and returns the top 10 customers.
2. Implement a Spring Boot repository using `MongoRepository` with a custom query using `@Query` annotation.
3. Write a MongoDB query to update a nested array element using `$elemMatch` and `$set`.
4. Design a document schema for a social media feed (posts, comments, likes) and justify embedding vs referencing decisions.
5. Implement a full-text search index and query in MongoDB for a product catalog.
6. Write a Spring Boot application using `ReactiveMongoRepository` with project reactor for non-blocking database access.
7. Implement a TTL index in MongoDB to automatically expire session documents after 30 minutes.
8. Write an aggregation query using `$lookup` to join data from two collections.
9. Implement optimistic concurrency control in MongoDB using a version field.
10. Write a MongoDB change stream listener in Spring Boot to react to database changes in real-time.

### Scenario-Based Questions

11. **Scenario:** Your MongoDB documents have deeply nested objects, and querying on nested fields is slow. How do you redesign the schema?
12. **Scenario:** You need ACID transactions across two MongoDB collections. How do you implement this?
13. **Scenario:** A MongoDB collection is growing by 10 GB per day. How do you plan archival and cleanup strategies?

---

## 13. React — Core Concepts

### Code Implementation Questions

1. Build a reusable `Button` component in React that accepts `variant` (primary/secondary/danger), `size`, `disabled`, and `onClick` props.
2. Implement a `DataTable` component that renders a list of objects dynamically with sortable columns.
3. Write a controlled form component in React for user registration with real-time field validation.
4. Build a `Modal` component in React using a portal (`ReactDOM.createPortal`) so it renders outside the main DOM tree.
5. Implement a higher-order component (HOC) `withAuth` that redirects unauthenticated users to the login page.
6. Write a React component that implements infinite scroll loading more items when the user reaches the bottom.
7. Build a breadcrumb navigation component that automatically generates from the current React Router path.
8. Implement a `DragAndDrop` list in React where items can be reordered by dragging.
9. Write a React component that renders a tree structure (nested categories) recursively.
10. Build a `Tabs` component with keyboard navigation support (Arrow keys to switch tabs).
11. Implement a `Tooltip` component that positions itself dynamically based on available screen space.
12. Write a `CountdownTimer` component in React that counts down to a target date and shows days, hours, minutes, and seconds.
13. Build a multi-step form wizard in React with back/next navigation and step validation before advancing.
14. Implement a `VirtualList` component that only renders visible items for a list of 100,000 records.
15. Write a `SearchableDropdown` component with debounced API calls on every keystroke.

### Scenario-Based Questions

16. **Scenario:** A React component re-renders 20 times per user keystroke in a search input, causing visible lag. How do you diagnose and optimize this?
17. **Scenario:** You need to render a list of 10,000 items in React without degrading UI performance. What approaches do you use?
18. **Scenario:** A child component is modifying a parent's state directly through a prop, causing unexpected side effects. What is the correct pattern to fix this?
19. **Scenario:** Your app needs to render different UI for admin vs regular users. How do you implement role-based UI rendering cleanly?
20. **Scenario:** You need to share state between two sibling components that don't have a common parent. What approaches do you consider?

---

## 14. React Hooks

### Code Implementation Questions

1. Write a custom hook `useFetch(url)` that handles loading, data, and error states for any API call.
2. Implement a `useDebounce(value, delay)` custom hook and use it to debounce a search input.
3. Write a `useLocalStorage(key, defaultValue)` hook that syncs React state with localStorage.
4. Implement a `useIntersectionObserver` hook to trigger a callback when an element enters the viewport.
5. Write a `usePrevious(value)` hook that returns the previous render's value of a variable.
6. Implement `useWindowSize()` hook that returns the current window width and height and updates on resize.
7. Write a `useOnClickOutside(ref, handler)` hook to close a dropdown when clicking outside it.
8. Implement `useThrottle(fn, limit)` hook for rate-limiting function calls.
9. Write a `useEventListener(event, handler, element)` hook that properly attaches and cleans up event listeners.
10. Implement `useMediaQuery(query)` hook that returns a boolean whether the given CSS media query matches.
11. Write a custom `useFormValidation(initialValues, validationRules)` hook for reusable form logic.
12. Implement a `useWebSocket(url)` hook that maintains a WebSocket connection and reconnects on disconnect.
13. Write `useMemo` and `useCallback` examples showing when they improve performance and when they don't.
14. Demonstrate the difference between `useEffect` with no dependency array, empty array, and specific dependencies using three separate examples.
15. Implement a `useReducer` hook for a shopping cart with actions: ADD_ITEM, REMOVE_ITEM, UPDATE_QUANTITY, CLEAR_CART.

### Scenario-Based Questions

16. **Scenario:** A `useEffect` in your component triggers an infinite loop. What are the common causes and how do you debug it?
17. **Scenario:** You need to run an effect only once after the first render, but ESLint is warning about missing dependencies. How do you handle this correctly?
18. **Scenario:** `useState` in a component is not updating in an event listener callback. Why does this happen (stale closure) and how do you fix it?
19. **Scenario:** Multiple components need access to user authentication state. How do you design a custom hook to centralize this logic?
20. **Scenario:** A `useEffect` that makes an API call is causing a memory leak warning when the component unmounts. How do you properly clean this up?

---

## 15. React State Management (Redux / Context API)

### Code Implementation Questions

1. Implement a Redux Toolkit slice for a shopping cart with `addItem`, `removeItem`, `updateQuantity`, and `clearCart` actions.
2. Write a Redux middleware that intercepts all API action requests, shows a global loader, and hides it on completion.
3. Implement `createAsyncThunk` to fetch a list of products from an API with pending/fulfilled/rejected states.
4. Build a Redux store with `redux-persist` so that the cart state persists across page refreshes.
5. Write a `useSelector` usage that uses memoized selectors with `createSelector` from Reselect to avoid unnecessary re-renders.
6. Implement a Context API + `useReducer` solution to manage a global theme (light/dark) and user language preference.
7. Write a React application using Zustand for global state management — implement a counter and a user profile store.
8. Implement the Redux DevTools integration and demonstrate time-travel debugging.
9. Write a Redux Observable epic that debounces a search input action and calls an API.
10. Build a multi-context architecture where `AuthContext`, `ThemeContext`, and `CartContext` are separate providers.

### Scenario-Based Questions

11. **Scenario:** Your Redux store has grown to a 500-line single reducer. How do you restructure it using `combineReducers` and feature-based slices?
12. **Scenario:** Context API is causing the entire component tree to re-render when only one context value changes. How do you optimize this?
13. **Scenario:** A component is subscribing to the Redux store but not re-rendering when the state changes. What do you check?
14. **Scenario:** Multiple developers on your team are creating Redux actions inconsistently. How do you enforce a standard pattern?

---

## 16. React — Advanced Patterns

### Code Implementation Questions

1. Implement a Compound Component pattern for a custom `Select` component with `Select.Option` sub-components.
2. Write a Render Props pattern to share mouse-position tracking logic with any component.
3. Implement a generic `ErrorBoundary` class component and use it to gracefully handle runtime errors in a subtree.
4. Write a code-splitting implementation using `React.lazy()` and `Suspense` for route-based splitting.
5. Implement a `DataProvider` component using the Provider pattern to supply remote data to deeply nested consumers.
6. Write a `useImperativeHandle` + `forwardRef` example to expose methods from a child component to its parent.
7. Implement a memoized list item component using `React.memo` and demonstrate when it prevents re-renders.
8. Write a controlled `RichTextEditor` wrapper component integrating a third-party editor.
9. Implement a Server-Side Rendering (SSR) compatible React component with `useEffect` hydration handling.
10. Build a plugin system for a React application where new features can be registered and rendered dynamically.

### Scenario-Based Questions

11. **Scenario:** Your `ErrorBoundary` is not catching errors thrown in asynchronous code or event handlers. How do you handle these cases?
12. **Scenario:** You need to share stateful behavior between 15 components without a centralized state manager. What React patterns do you apply?
13. **Scenario:** A third-party library does not play well with React's rendering cycle and causes DOM conflicts. How do you isolate it?

---

## 17. JavaScript & TypeScript (ES6+)

### Code Implementation Questions

1. Write a JavaScript function to deeply clone an object without using `JSON.parse/stringify` (handle circular references and functions).
2. Implement a `Promise.all`, `Promise.race`, `Promise.allSettled`, and `Promise.any` from scratch.
3. Write a JavaScript debounce function and a throttle function from scratch.
4. Implement a `pipe()` and `compose()` function using array `reduce()`.
5. Write a JavaScript event emitter class with `on`, `off`, and `emit` methods.
6. Implement a memoization function that caches results for any function using a `Map`.
7. Write a currying function `curry(fn)` that works for any number of arguments.
8. Implement a `deepEqual(a, b)` function to compare two objects recursively.
9. Write TypeScript generics: implement a `Repository<T>` interface with `findById`, `findAll`, `save`, and `delete`.
10. Implement a TypeScript utility types exercise using `Partial<T>`, `Readonly<T>`, `Pick<T,K>`, `Omit<T,K>`, `Record<K,V>`.
11. Write an async/await function with proper error handling, retry logic, and timeout cancellation using `AbortController`.
12. Implement a TypeScript `Result<T, E>` type (similar to Rust's Result) for type-safe error handling.
13. Write a JavaScript Proxy to intercept property access and validate types on an object.
14. Implement a `Queue` and `Stack` class in TypeScript using generics.
15. Write a TypeScript decorator `@Log` that logs the arguments and return value of any method.

### Scenario-Based Questions

16. **Scenario:** Your application throws `TypeError: Cannot read properties of undefined` in production but not in development. How do you track this down?
17. **Scenario:** A JavaScript closure in a loop is capturing the wrong variable. Identify the bug and fix it.
18. **Scenario:** TypeScript is showing no errors but the runtime crashes with a type error. How is this possible and how do you prevent it?
19. **Scenario:** You need to migrate a large React codebase from JavaScript to TypeScript incrementally. What is your strategy?

---

## 18. HTML & CSS

### Code Implementation Questions

1. Build a responsive navigation bar using only HTML and CSS (no JavaScript) that collapses into a hamburger menu on mobile.
2. Implement a CSS grid-based dashboard layout with a fixed sidebar, header, and scrollable main content area.
3. Write HTML and CSS for a card component with hover animation, a shadow effect, and a smooth transition.
4. Implement a pure CSS loading spinner and skeleton screen component.
5. Build a CSS sticky header that shrinks when the user scrolls down using `position: sticky` and CSS custom properties.
6. Write semantic HTML for a blog post page with proper use of `article`, `section`, `aside`, `header`, `footer`, and `nav`.
7. Implement a CSS `flex`-based responsive form layout that stacks vertically on mobile.
8. Build an accessible modal dialog in HTML with focus trapping and keyboard (Escape) close support.
9. Write CSS for a star rating widget using only radio buttons and labels (no JavaScript).
10. Implement CSS custom properties (variables) for a theming system with light and dark mode.

### Scenario-Based Questions

11. **Scenario:** A CSS animation on a scroll-heavy page is causing frame drops. How do you optimize it?
12. **Scenario:** Your team's CSS is growing unmanageable with specificity conflicts. How do you restructure it using BEM or CSS Modules?
13. **Scenario:** An image on your page is causing layout shift (CLS) during load. How do you fix it?

---

## 19. API Integration (React ↔ Spring Boot)

### Code Implementation Questions

1. Write a React service layer using `axios` with a base configuration, request/response interceptors for JWT token injection and 401 auto-refresh.
2. Implement a React component that fetches paginated data from a Spring Boot API and displays a "Load More" button.
3. Build a React form that uploads a file to a Spring Boot `/upload` endpoint using `FormData` and shows upload progress.
4. Write a React custom hook `useApi(endpoint, method, body)` that abstracts all API call logic.
5. Implement CORS configuration in Spring Boot to allow requests from a React app on a different origin.
6. Write a React application that uses React Query (`TanStack Query`) to manage server state from a Spring Boot API.
7. Implement optimistic updates in React — update the UI immediately before the API call completes and roll back on error.
8. Write a React application with WebSocket integration connecting to a Spring Boot WebSocket endpoint for real-time chat.
9. Implement a token refresh flow in React: when an API returns 401, transparently refresh the JWT and retry the original request.
10. Write an integration where React reads and displays paginated + filtered results from a Spring Boot API with query parameters.

### Scenario-Based Questions

11. **Scenario:** Your React app receives a CORS error when calling the Spring Boot API. The server logs show the request is received. Where is the misconfiguration?
12. **Scenario:** An API call in React returns stale data after a successful mutation. How do you handle cache invalidation?
13. **Scenario:** The React app and Spring Boot API are deployed on different subdomains. Cookies set by the API are not sent with requests. How do you fix this?
14. **Scenario:** A React form's submit button must be disabled until all required fields are valid AND the username availability API confirms the username is free. How do you implement this?

---

## 20. Testing (JUnit, Mockito, React Testing Library)

### Code Implementation Questions

1. Write a JUnit 5 unit test for a `calculateDiscount(order)` service method using `@ParameterizedTest` with multiple input scenarios.
2. Implement a Mockito test for a Spring Boot service that calls a repository — mock the repository and verify interactions.
3. Write a Spring Boot integration test using `@SpringBootTest` and `MockMvc` to test a `POST /api/users` endpoint end-to-end.
4. Implement a React Testing Library test for a login form — simulate user input, form submission, and assert API call and navigation.
5. Write a Jest test for a custom `useDebounce` hook using `act()` and fake timers.
6. Implement a Mockito `@Captor` test to verify the exact arguments passed to a repository's `save()` method.
7. Write a `@DataJpaTest` integration test for a Spring Data JPA repository with an H2 in-memory database.
8. Implement a React component test that mocks an API module and verifies the component renders loading, data, and error states correctly.
9. Write a `@WebMvcTest` for a Spring Boot controller that validates request body constraints and checks the 400 Bad Request response.
10. Implement a contract test using Spring Cloud Contract between a producer (Spring Boot) and consumer (React/another service).

### Scenario-Based Questions

11. **Scenario:** A unit test that mocked a service is passing, but the integration test is failing on the same feature. What could be the cause?
12. **Scenario:** You need to test a component that depends on `window.localStorage`. How do you mock browser APIs in Jest?
13. **Scenario:** Your test suite takes 45 minutes to run. How do you identify and optimize slow tests?

---

## 21. Docker & DevOps / CI-CD

### Code Implementation Questions

1. Write a multi-stage `Dockerfile` for a Spring Boot application that produces a minimal production image.
2. Write a `docker-compose.yml` that starts a Spring Boot API, React app (via Nginx), and MySQL database with networking and volumes.
3. Implement a GitHub Actions CI/CD pipeline that builds, tests, and deploys a Spring Boot + React application to AWS EC2.
4. Write a `Jenkinsfile` with stages: Checkout → Build → Unit Test → Integration Test → Docker Build → Deploy.
5. Implement a Kubernetes `Deployment`, `Service`, and `ConfigMap` YAML for a Spring Boot microservice.
6. Write an Nginx configuration to serve a React SPA and proxy `/api/*` requests to a Spring Boot backend.
7. Implement a Docker health check for a Spring Boot application using the Actuator `/health` endpoint.
8. Write a Helm chart for deploying a microservice to a Kubernetes cluster with environment-specific values.

### Scenario-Based Questions

9. **Scenario:** A Docker container works on your machine but fails in the CI pipeline with a different OS. How do you diagnose and prevent this?
10. **Scenario:** Your Kubernetes pods are crashing with `OOMKilled`. How do you investigate and set proper resource limits?
11. **Scenario:** Your CI/CD pipeline runs all tests on every push, making it slow. How do you optimize by running only relevant tests?
12. **Scenario:** You need to roll back a bad deployment in Kubernetes immediately. What commands do you use and what is your process?

---

## 22. System Design & Architecture

### Scenario-Based Design Questions

1. **Design a URL shortener** (like bit.ly) — system design covering the API, database schema, hashing strategy, redirect mechanism, and scalability.
2. **Design an e-commerce cart and checkout system** — handle concurrent users, inventory locking, payment processing, and order confirmation.
3. **Design a notification system** (email, push, SMS) — handle 10 million notifications per day with delivery guarantees.
4. **Design a real-time chat application** — architecture covering WebSockets, message persistence, read receipts, and offline message delivery.
5. **Design an authentication system** supporting social login, MFA, session management, and token revocation at scale.
6. **Design a file storage service** (like Google Drive) — handle uploads, chunking, deduplication, sharing, and versioning.
7. **Design a search autocomplete service** — handle typo tolerance, ranking, and sub-100ms response times at scale.
8. **Design a rate limiter** that works across a distributed cluster of API servers.
9. **Design a Job Scheduling System** — reliably execute millions of scheduled tasks with at-least-once delivery.
10. **Design a reporting dashboard** for a multi-tenant SaaS platform — real-time data aggregation, caching, and tenant isolation.

### Code-Level Architecture Questions

11. How would you structure a large React application with 50+ screens and 10+ developers — folder structure, module boundaries, and shared components?
12. How would you design a Spring Boot multi-module Maven project for a microservices architecture?
13. Design the JWT token structure and expiry strategy for a multi-role, multi-tenant application.
14. How would you implement a CQRS (Command Query Responsibility Segregation) pattern in Spring Boot?
15. Design the database schema for a multi-tenant application where each tenant has isolated data.

---

## 23. Security Best Practices

### Code Implementation Questions

1. Write a Spring Boot endpoint that prevents SQL injection by using parameterized queries — contrast with a vulnerable version.
2. Implement XSS prevention in a React application — sanitize user-generated HTML content before rendering.
3. Write a Spring Boot configuration that enforces HTTPS, sets HSTS headers, and adds `Content-Security-Policy`.
4. Implement CSRF protection in a Spring Boot + React application — explain the token flow.
5. Write a secure password hashing and verification implementation using BCrypt in Spring Boot.
6. Implement rate limiting on a login endpoint to prevent brute force attacks.
7. Write a React component that handles sensitive data (e.g., credit card numbers) without logging or caching it.
8. Implement input validation and sanitization on both the React form and the Spring Boot API endpoint.

### Scenario-Based Questions

9. **Scenario:** A security audit finds that your API returns full stack traces in error responses to clients. How do you fix this?
10. **Scenario:** Your application stores JWT tokens in localStorage and a security reviewer flags this as vulnerable to XSS. What do you recommend instead?
11. **Scenario:** A penetration test reveals that your API endpoints are accessible without authentication in a staging environment. How did this happen and how do you prevent it?
12. **Scenario:** You receive a report that user A can view user B's orders by changing the `userId` in the URL. What vulnerability is this and how do you fix it?

---

## 24. Scenario-Based Full Stack Integration Questions

These questions test your ability to think across the entire stack simultaneously.

1. **Scenario:** Build a real-time inventory dashboard — when stock changes in the database (via any service), all connected React clients update automatically without polling. Design the full stack architecture including Spring Boot, WebSocket or SSE, and React.

2. **Scenario:** A user submits an order in the React app. The request reaches Spring Boot, but the database transaction fails halfway through (payment saved, inventory not decremented). How do you handle this, and how does the React UI communicate the failure?

3. **Scenario:** Your React app is making 30 API calls on the dashboard page load, causing a slow user experience. Walk through optimizations on both the React (frontend) and Spring Boot (backend) sides.

4. **Scenario:** You need to implement a feature where a large report is generated asynchronously. The user clicks "Generate Report" and should get a notification when it's ready. Design the full stack flow from button click to notification delivery.

5. **Scenario:** Your application needs to support both light and dark mode. The user's preference should persist across devices (stored server-side). Design the React component structure, Spring Boot API, and database model for this.

6. **Scenario:** A React form allows users to upload images. Images must be validated (type, size), resized to multiple dimensions, stored in S3, and the URL stored in the database. Walk through the complete implementation on both React and Spring Boot sides.

7. **Scenario:** Your Spring Boot API responses are being cached by browsers, causing users to see stale data after updates. How do you configure cache headers in Spring Boot and cache invalidation in React?

8. **Scenario:** You need to implement a multi-step checkout — each step saves progress. If the user drops off, they can resume. Design the React state management, API endpoints, and database schema.

9. **Scenario:** Your application receives a sudden 10x traffic spike. Walk through how each layer (React CDN, Spring Boot, database) scales independently.

10. **Scenario:** You are onboarding a new feature that needs A/B testing — 50% of users see the old UI (React), 50% see the new UI. The Spring Boot API may also differ. How do you implement feature flags across the full stack?

11. **Scenario:** A critical bug in production is causing financial data to be calculated incorrectly. You need to hotfix this without a full deployment cycle and with zero downtime. Walk through your process from identification to deploy.

12. **Scenario:** Your application must meet GDPR compliance. A user requests "right to be forgotten." How do you implement data deletion across the entire stack — React, Spring Boot APIs, SQL database, Kafka event logs, and S3?

---

## 📌 Quick Reference: Tech Stack Covered

| Layer | Technologies |
|---|---|
| **Frontend** | React 18+, Redux Toolkit, React Query, React Router, TypeScript, Jest, React Testing Library |
| **Styling** | HTML5, CSS3, Tailwind CSS, CSS Modules, BEM |
| **Backend** | Java 17+, Spring Boot 3.x, Spring MVC, Spring Security 6, Spring AOP |
| **Data Layer** | Spring Data JPA, Hibernate, JDBC, Flyway, Liquibase |
| **Databases** | MySQL, PostgreSQL, MongoDB, Redis |
| **Messaging** | Apache Kafka, RabbitMQ |
| **Microservices** | Spring Cloud, Eureka, Feign, Resilience4j, Spring Cloud Gateway |
| **DevOps** | Docker, Kubernetes, Jenkins, GitHub Actions, Nginx |
| **Security** | JWT, OAuth2, Spring Security, HTTPS, CSRF, XSS prevention |
| **Testing** | JUnit 5, Mockito, MockMvc, H2, React Testing Library, Jest |
| **Tools** | Maven, Git, Postman, Swagger/OpenAPI, Zipkin |

---

> 💡 **Tip:** For each question, practice explaining your thought process out loud before writing code. Interviewers value problem-solving approach as much as the final answer.

> 📅 **Last Updated:** April 2026 | Total Questions: 300+
