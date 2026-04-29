# ☕⚛️ Java Full Stack with React — Coding & Scenario-Based Interview Questions

> **200+ must-know implementation & scenario questions** | No answers — challenge yourself!
> Role-specific: Java Full Stack Developer with React
> Each section covers one tech stack — test yourself per layer!

---

## 📋 Table of Contents

1. [Core Java — Coding & OOP Scenarios](#1-core-java--coding--oop-scenarios)
2. [Java 8+ Features — Streams, Lambdas & Functional Programming](#2-java-8-features--streams-lambdas--functional-programming)
3. [Spring Core & Dependency Injection](#3-spring-core--dependency-injection)
4. [Spring Boot — REST API Design & Implementation](#4-spring-boot--rest-api-design--implementation)
5. [Spring Security — JWT & OAuth2](#5-spring-security--jwt--oauth2)
6. [Hibernate / JPA — ORM & Database Mapping](#6-hibernate--jpa--orm--database-mapping)
7. [SQL & Database Design](#7-sql--database-design)
8. [Microservices Architecture](#8-microservices-architecture)
9. [React — Component & Hook Implementation](#9-react--component--hook-implementation)
10. [React — State Management & API Integration](#10-react--state-management--api-integration)
11. [JavaScript & TypeScript Coding](#11-javascript--typescript-coding)
12. [HTML & CSS Scenarios](#12-html--css-scenarios)
13. [Docker & Kubernetes — DevOps Scenarios](#13-docker--kubernetes--devops-scenarios)
14. [Git & CI/CD Scenarios](#14-git--cicd-scenarios)
15. [Full Stack System Design & Integration Scenarios](#15-full-stack-system-design--integration-scenarios)

---

## 1. Core Java — Coding & OOP Scenarios

> Focus: OOP principles, collections, multithreading, memory management, exception handling

### 🔷 OOP & Design

1. Implement a `BankAccount` class with `deposit()`, `withdraw()`, and `getBalance()` methods. Ensure `balance` cannot go below zero. Apply proper encapsulation.
2. Design a class hierarchy for `Shape → Circle, Rectangle, Triangle`. Override `area()` and `perimeter()` in each subclass. Use an abstract base class.
3. You have a `Vehicle` base class and `Car`, `Truck`, `Bike` subclasses. How would you implement polymorphism so that calling `start()` on any `Vehicle` reference calls the correct subclass method?
4. Implement the Singleton design pattern for a `DatabaseConnection` class. Ensure it is thread-safe without using `synchronized` on the entire method.
5. Implement the Builder pattern for a `User` object with fields: `id`, `name`, `email`, `phone`, `address`. Make `name` and `email` mandatory, others optional.
6. Implement the Observer pattern where multiple `EventListener` objects are notified when a `Button` is clicked.
7. Demonstrate the difference between method overloading and method overriding with a practical example in a `Calculator` class.
8. Write code to demonstrate how an interface with `default` and `static` methods works in Java 8+. Create a `Flyable` interface and implement it in `Bird` and `Airplane`.
9. Explain and demonstrate why Java does not support multiple inheritance through classes but allows it through interfaces. Show a diamond problem workaround using interfaces.
10. Implement a deep copy and a shallow copy of a `Student` object that contains a `List<Course>`. Show the difference in behavior when modifying the list after copying.

### 🔷 Collections & Data Structures

11. Write a program to find duplicate elements in a `List<Integer>` using Java Collections. Solve it in O(n) time.
12. Given a `List<String>` of names, write code to group them by their first letter using a `Map`. What collection type would you use?
13. Implement a custom `Stack<T>` using `LinkedList`. Provide `push()`, `pop()`, `peek()`, and `isEmpty()` methods.
14. Write a program that uses a `PriorityQueue` to find the top 3 highest-paid employees from a list of `Employee` objects.
15. You need a collection that maintains insertion order and does not allow duplicates. Which Java collection would you use and why? Demonstrate with code.
16. Implement `Comparable` and `Comparator` for sorting a list of `Product` objects — first by price (ascending), then by name (alphabetical) for ties.
17. Write code to convert a `List<Employee>` to a `Map<Department, List<Employee>>` using Java Collections only (without Streams).
18. Demonstrate the difference between `HashMap`, `LinkedHashMap`, and `TreeMap` with a practical example. When would you choose each?
19. Write a program to reverse a `LinkedList` in Java without using any built-in reverse utilities.
20. You are given a `ConcurrentHashMap` and a regular `HashMap`. Write code that demonstrates thread-safety differences between the two when accessed by multiple threads simultaneously.

### 🔷 Multithreading & Concurrency

21. Write a Java program using `ExecutorService` with a fixed thread pool of 5 to process 20 tasks concurrently. Print which thread processes which task.
22. Implement a producer-consumer problem in Java using `BlockingQueue`. Ensure the producer blocks when the queue is full and the consumer blocks when it is empty.
23. Write code to demonstrate a deadlock scenario between two threads. Then refactor it to prevent the deadlock.
24. Implement a thread-safe counter class using `AtomicInteger`. Compare the performance difference with a `synchronized` counter.
25. Write a Java program that uses `CompletableFuture` to fetch user data and order data simultaneously (simulated with `Thread.sleep()`), then combine the results.
26. You have a task that takes 10 seconds. Write code using `Future` and `Callable` to run it asynchronously and retrieve the result with a 5-second timeout.
27. Implement the `ReentrantLock` with a `tryLock()` to handle a scenario where one thread should skip processing if another thread is already accessing a shared resource.
28. Write a program demonstrating `volatile` keyword usage. Show a scenario where without `volatile`, a visibility bug occurs between threads.

### 🔷 Exception Handling & Memory

29. Write a custom checked exception `InsufficientFundsException` and a custom unchecked exception `InvalidAccountException`. Show their usage in a banking service.
30. Demonstrate the difference between `finally` block behavior when: (a) an exception is thrown, (b) no exception occurs, and (c) a `return` statement is inside the `try` block.
31. You suspect your application has a memory leak. Write code that demonstrates a common memory leak scenario (e.g., static collection growing indefinitely) and explain how to fix it.
32. Explain and demonstrate the difference between stack memory and heap memory using a Java code example with object creation and method calls.

---

## 2. Java 8+ Features — Streams, Lambdas & Functional Programming

> Focus: Stream API, lambda expressions, Optional, functional interfaces, method references

33. Given a `List<Employee>` with fields `name`, `department`, `salary`, write Stream API code to:
    - Filter employees with salary > 50,000
    - Group them by department
    - Find the average salary per department
    - Return results sorted by average salary descending

34. Write a Stream pipeline to find the second-highest salary from a `List<Integer>` without sorting the entire list. Handle the case where fewer than 2 elements exist.

35. Given a `List<Order>` where each `Order` has a `List<Item>`, use `flatMap()` to get a flat list of all items across all orders. Filter out items with quantity 0.

36. Implement the following using method references (not lambda expressions) wherever possible:
    - Print all strings in a list
    - Convert a list of strings to uppercase
    - Filter null values from a list

37. Write code using `Optional<T>` to safely handle a scenario where a user may not be found in the database. Chain `map()`, `filter()`, and `orElseThrow()` appropriately.

38. Demonstrate the difference between `map()` and `flatMap()` in Java Streams using a practical example with a `List<List<String>>`.

39. Write a custom `FunctionalInterface` called `TriFunction<A, B, C, R>` that takes three parameters and returns a result. Implement it using a lambda.

40. Given a `List<String>` of comma-separated words (e.g., `"apple,banana"`, `"cherry,date"`), write a single Stream pipeline to produce a sorted, distinct list of all individual words.

41. Write code to process a large file line by line using `Files.lines()` with Streams. Find all lines containing a specific keyword, count them, and collect the first 10 into a list.

42. Implement a `Collector` that collects a `Stream<String>` into a `Map<Integer, List<String>>` grouped by string length.

43. Use `reduce()` to implement: (a) sum of integers, (b) product of integers, (c) concatenation of strings, without using `sum()` or `collect()`.

44. Write a parallel stream example that processes 1 million integers. Discuss the scenarios where parallel streams would and would not improve performance.

45. Given `List<Transaction>` with `type` (CREDIT/DEBIT) and `amount`, use Streams to calculate the net balance. Use `Collectors.partitioningBy()` to split transactions by type.

46. Demonstrate the `Collectors.toUnmodifiableMap()` use and what happens if there are duplicate keys. Write code to handle the merge function.

---

## 3. Spring Core & Dependency Injection

> Focus: IoC container, bean lifecycle, annotations, AOP

47. Write a Spring configuration class (using `@Configuration` and `@Bean`) that defines a `DataSource` bean and a `JdbcTemplate` bean that depends on it. No XML configuration.

48. Implement constructor injection, setter injection, and field injection for the same `OrderService` class. Explain which approach you prefer in production code and why.

49. Write a Spring AOP aspect that logs the method name, arguments, and execution time for all methods in a `com.example.service` package. Use `@Around` advice.

50. Create a `@Component` called `EmailService`. Write a second `@Component` called `SmsService`. Create an `@Service` called `NotificationService` that uses both. Wire them using `@Qualifier`.

51. Write code demonstrating the difference between `@Bean` scope `singleton` and `prototype`. Show a scenario where using singleton for a stateful bean causes a bug.

52. Implement a Spring `BeanPostProcessor` that logs the name of every bean after it is initialized in the application context.

53. Write a Spring `@Conditional` annotation usage — create a bean that is only loaded when the application runs in a "production" profile.

54. Demonstrate how Spring resolves circular dependencies. Write two beans that depend on each other and show how `@Lazy` can break the cycle.

---

## 4. Spring Boot — REST API Design & Implementation

> Focus: Controller design, exception handling, validation, pagination, testing

55. Implement a complete REST API for a `Product` resource with endpoints:
    - `GET /api/products` — list all with pagination and sorting
    - `GET /api/products/{id}` — get by ID
    - `POST /api/products` — create new
    - `PUT /api/products/{id}` — full update
    - `PATCH /api/products/{id}` — partial update
    - `DELETE /api/products/{id}` — delete

56. Write a `@ControllerAdvice` global exception handler that:
    - Returns `404` with a custom JSON body for `ResourceNotFoundException`
    - Returns `400` with field-level validation errors for `MethodArgumentNotValidException`
    - Returns `500` with a generic message for all other exceptions

57. Add Bean Validation to a `UserDTO` class: `name` (not blank, 3-50 chars), `email` (valid format), `age` (18-100), `phone` (regex pattern). Wire it to a controller with `@Valid`.

58. Implement API versioning for a `CustomerController` supporting both `/api/v1/customers` and `/api/v2/customers` with different response structures. Use URI versioning.

59. Write a Spring Boot endpoint that accepts a file upload, validates the file type (PDF or image only) and size (max 5MB), saves it to a local directory, and returns the file URL.

60. Implement request/response logging using a `HandlerInterceptor`. Log: request method, URI, query params, response status, and execution time for every API call.

61. Write a Spring Boot controller that demonstrates all HTTP status codes: how to return `201 Created` with a `Location` header on POST, `204 No Content` on DELETE, and `206 Partial Content` for streaming.

62. Implement pagination for a `/api/employees` endpoint using Spring Data's `Pageable`. Return a response that includes: content, totalElements, totalPages, currentPage, pageSize.

63. You need to expose an endpoint that calls two external APIs simultaneously and returns a combined response. Implement this using `CompletableFuture` within a Spring Boot controller.

64. Write a Spring Boot scheduled job (`@Scheduled`) that runs every day at midnight, queries the database for orders placed more than 30 days ago with status PENDING, and marks them as EXPIRED.

65. Implement CORS configuration globally in Spring Boot to allow requests only from `https://myfrontend.com` with allowed methods `GET, POST, PUT, DELETE` and allow the `Authorization` header.

66. Write a Spring Boot filter that implements rate limiting — allow a maximum of 100 requests per IP address per minute. Return `429 Too Many Requests` when the limit is exceeded.

67. Scenario: Your REST API returns a `500 Internal Server Error` in production for a specific endpoint. Walk through your debugging process step by step — from logs to root cause identification.

68. Implement API documentation using Swagger/OpenAPI 3 in a Spring Boot application. Annotate a `ProductController` with descriptions, parameter types, and response schemas.

---

## 5. Spring Security — JWT & OAuth2

> Focus: Authentication, authorization, JWT, OAuth2, security configurations

69. Implement JWT-based authentication in Spring Boot:
    - A `POST /auth/login` endpoint that validates credentials and returns a JWT token
    - A `JwtAuthFilter` that validates the token on every subsequent request
    - Configure `SecurityFilterChain` to permit `/auth/**` and require authentication for all other endpoints

70. Write a Spring Security configuration that implements Role-Based Access Control (RBAC):
    - `ADMIN` role can access all `/api/admin/**` endpoints
    - `USER` role can access only `/api/user/**` endpoints
    - All users can access `/api/public/**`

71. Implement JWT token refresh logic:
    - Issue a short-lived access token (15 minutes) and a long-lived refresh token (7 days)
    - Create a `POST /auth/refresh` endpoint that issues a new access token given a valid refresh token
    - Invalidate refresh tokens on logout using a blacklist

72. Scenario: A user logs out. How do you invalidate their JWT token on the server side, given that JWTs are stateless by design? Implement a solution using a token blacklist in Redis.

73. Write code to implement OAuth2 login with Google in a Spring Boot application. Configure `application.yml` and create a success handler that extracts user details from the Google profile.

74. Implement method-level security using `@PreAuthorize`:
    - Only the owner of a resource or an ADMIN can delete it
    - `@PreAuthorize("hasRole('ADMIN') or #userId == authentication.principal.id")`

75. Write a `OncePerRequestFilter` that:
    - Extracts the JWT from the `Authorization: Bearer <token>` header
    - Validates the token signature and expiry
    - Sets the authentication in `SecurityContextHolder`
    - Returns `401 Unauthorized` with a JSON body if the token is invalid or expired

76. Scenario: Your Spring Boot API is being accessed from a React frontend running on `localhost:3000` during development. CORS preflight requests are failing. How do you configure Spring Security to handle CORS properly?

77. Implement password encoding using `BCryptPasswordEncoder`. Show how to: hash a password on registration, verify it on login, and why plain text comparison is insecure.

78. Scenario: You discover that your API's JWT secret key is hardcoded in the source code. What are the security risks, and how do you externalize and rotate the secret key?

---

## 6. Hibernate / JPA — ORM & Database Mapping

> Focus: Entity mapping, relationships, JPQL, performance, transactions

79. Map the following database relationship using JPA annotations:
    - `Student` has many `Courses` (Many-to-Many)
    - `Course` belongs to one `Department` (Many-to-One)
    - `Student` has one `Profile` (One-to-One)
    Write all entity classes with proper annotations, cascade types, and fetch types.

80. Write a JPA `Repository` interface for a `Product` entity that includes:
    - Find by category and price less than a value (using method naming convention)
    - Find top 5 most expensive products in a category (using `@Query` with JPQL)
    - A native SQL query to find products with the most orders

81. Implement a Spring Data JPA `Specification` for dynamic filtering of `Employee` objects by: department, salary range, hire date range, and name containing a keyword. Combine them dynamically.

82. Write JPQL queries to:
    - Fetch all orders placed in the last 7 days with their associated customer names
    - Calculate total revenue per product category
    - Find customers who have never placed an order (LEFT JOIN with null check)

83. Scenario: You have a `@OneToMany` relationship between `Order` and `OrderItem`. You notice your application is making N+1 queries when loading orders. How do you detect this and what solutions do you implement?

84. Implement a custom `@Converter` that stores a Java `enum` as a specific string value in the database (e.g., `Status.ACTIVE` → `"active"`, not `"ACTIVE"`).

85. Write a JPA entity with:
    - Optimistic locking using `@Version`
    - Audit fields (`createdAt`, `updatedAt`, `createdBy`) using `@EntityListeners(AuditingEntityListener.class)`
    - A composite primary key using `@EmbeddedId`

86. Scenario: A batch job needs to insert 100,000 records into the database. Implement this using Spring Data JPA with batch inserts configured properly. What settings in `application.properties` enable batch processing?

87. Write code demonstrating the difference between `FetchType.LAZY` and `FetchType.EAGER` in a parent-child entity relationship. Show the `LazyInitializationException` and how to fix it.

88. Implement a repository method using the `Criteria API` to build a dynamic query for searching `Employee` by any combination of: name, department, minimum salary, and city.

89. Write a `@Transactional` service method that:
    - Updates an order status
    - Sends a notification
    - If notification fails, rolls back only the notification but commits the order update
    Use `REQUIRES_NEW` propagation to achieve this.

90. Scenario: Two users simultaneously try to update the same product's stock. Without locking, both read quantity=10, both subtract 5, and both write 5 — resulting in incorrect stock of 5 instead of 0. Implement both optimistic and pessimistic locking solutions and explain the trade-offs.

---

## 7. SQL & Database Design

> Focus: Complex queries, joins, indexing, schema design, optimization

91. Write SQL to find the second highest salary from an `employees` table. Provide at least two different approaches (subquery, window function).

92. Given tables `orders(id, customer_id, amount, created_at)` and `customers(id, name, email)`, write SQL to:
    - Find top 10 customers by total order amount
    - Find customers who placed orders in every month of 2024
    - Find customers who placed an order in January 2024 but NOT in February 2024

93. Write a SQL query using window functions (`ROW_NUMBER`, `RANK`, `DENSE_RANK`) to rank employees by salary within each department. Return only the top 3 per department.

94. Design a database schema for an e-commerce platform with: `users`, `products`, `categories`, `orders`, `order_items`, `reviews`, `addresses`. Define primary keys, foreign keys, and appropriate indexes.

95. Write a SQL query to find all employees who earn more than the average salary of their own department. Use a correlated subquery and then rewrite it using a window function.

96. Given a `transactions(id, account_id, type, amount, created_at)` table, write SQL to compute the running balance for each account ordered by transaction date.

97. Scenario: A query that joins 4 large tables is running slowly (8+ seconds). Walk through how you would: analyze the execution plan, identify missing indexes, and optimize the query.

98. Write a SQL query to pivot the following data: monthly sales per product shown as columns (`Jan`, `Feb`, `Mar`, …) from a `sales(product_id, month, amount)` table.

99. Implement a stored procedure that:
    - Accepts `customer_id` and `discount_percentage` as input
    - Applies the discount to all PENDING orders for that customer
    - Returns the number of orders updated and total discount applied

100. Scenario: You need to delete 10 million old records from a table without locking the table and causing downtime. How would you design the deletion strategy?

101. Write SQL to detect and handle duplicate records in a `contacts` table where duplicates are defined as having the same `email`. Keep the record with the most recent `created_at`.

102. Design and write SQL for a self-referential table to represent an organizational hierarchy (employees with managers). Write a recursive CTE to show the full reporting chain for a given employee.

---

## 8. Microservices Architecture

> Focus: Service design, inter-service communication, fault tolerance, messaging

103. Scenario: You are breaking a monolithic Spring Boot application into microservices. How do you decide service boundaries? Apply Domain-Driven Design (DDD) principles to decompose an e-commerce application into services.

104. Implement a Spring Boot microservice for `Order Service` that:
    - Exposes REST endpoints for order management
    - Calls `Product Service` via `RestTemplate` or `WebClient` to check stock availability
    - Calls `Payment Service` to process payment
    - Uses circuit breaker (Resilience4j) for all external calls

105. Write a Resilience4j `@CircuitBreaker` on a service method that calls an external payment API. Define: failure threshold (50%), wait duration (10s), fallback method. Show how the circuit transitions from CLOSED → OPEN → HALF_OPEN.

106. Implement a Spring Cloud Gateway route configuration that:
    - Routes `/api/users/**` to User Service
    - Routes `/api/orders/**` to Order Service
    - Adds a `X-Request-Id` header to every request using a `GlobalFilter`
    - Implements rate limiting using Redis

107. Design a SAGA pattern for the following distributed transaction: User places an order → Reserve inventory → Process payment → Send confirmation email. Show both choreography and orchestration approaches.

108. Write a Kafka producer in Spring Boot that publishes an `OrderPlaced` event. Write a Kafka consumer in a separate service that listens to the topic and updates inventory. Handle consumer failures and dead letter queues.

109. Implement service discovery using Spring Cloud Eureka:
    - A Eureka Server application
    - Two instances of `Product Service` registered with Eureka
    - An `Order Service` that uses `@LoadBalanced RestTemplate` to call one of the `Product Service` instances

110. Scenario: Your `Payment Service` is experiencing intermittent timeouts, causing `Order Service` to block. How do you implement the Bulkhead pattern to isolate Payment Service failures and prevent cascading failures to Order Service?

111. Write the configuration for Spring Cloud Config Server backed by a Git repository. Show how a microservice reads its configuration from the Config Server and refreshes it at runtime without restart using `@RefreshScope`.

112. Scenario: An API call goes through: Gateway → Auth Service → Order Service → Inventory Service. How do you implement distributed tracing using Micrometer and Zipkin to trace this full request flow? What information is added to each request?

113. Design the database strategy for a microservices system. Explain Database-per-Service pattern. How do you handle cross-service queries that previously used JOINs in a monolith? Implement one approach.

114. Scenario: Your `User Service` and `Order Service` need to stay in sync — when a user is deleted, all their orders should be cancelled. Without a distributed transaction, how do you implement this using event-driven architecture (Outbox Pattern)?

---

## 9. React — Component & Hook Implementation

> Focus: Component design, custom hooks, state logic, performance patterns

115. Implement a reusable `<DataTable>` component that:
    - Accepts `columns` (with field, header, sortable flag) and `data` props
    - Supports client-side sorting by clicking column headers
    - Supports client-side search/filtering by a search string
    - Shows a loading spinner when `isLoading` prop is true
    - Shows an empty state when data is empty

116. Build a custom hook `useFetch(url)` that:
    - Fetches data from the given URL using `fetch`
    - Returns `{ data, isLoading, error }`
    - Handles component unmounting (cancel/abort the fetch)
    - Retries up to 3 times on failure with exponential backoff

117. Implement a `useDebounce(value, delay)` custom hook. Use it in a search input component that fetches results from an API only after the user stops typing for 500ms.

118. Build a `<InfiniteScrollList>` component that:
    - Fetches items in batches of 20 using pagination API
    - Detects when the user scrolls near the bottom using `IntersectionObserver`
    - Fetches the next page automatically
    - Shows a "Loading more..." indicator and handles end-of-list

119. Implement a `useLocalStorage(key, initialValue)` custom hook that syncs React state with `localStorage`. The hook should also listen for changes in other tabs.

120. Build a multi-step form wizard with 3 steps using React:
    - Step 1: Personal Info (name, email)
    - Step 2: Address (street, city, zip)
    - Step 3: Review & Submit
    - Preserve form data when navigating between steps
    - Show a progress indicator
    - Validate each step before proceeding

121. Implement a `<Virtualized List>` component using `react-window` that renders 100,000 items efficiently. Show why rendering all items at once causes performance issues.

122. Write a `useWebSocket(url)` custom hook that:
    - Connects to a WebSocket server
    - Returns `{ message, sendMessage, connectionStatus }`
    - Reconnects automatically on disconnect
    - Cleans up the connection on component unmount

123. Scenario: You have a deeply nested component tree and passing a "theme" (dark/light) object through props results in prop drilling through 6 levels. Refactor it using Context API. Then show how the React Compiler or `useMemo` prevents unnecessary re-renders.

124. Build a `<DragAndDrop>` kanban board with 3 columns (Todo, In Progress, Done). Cards can be dragged between columns. Implement the state management for this using `useReducer`.

---

## 10. React — State Management & API Integration

> Focus: Redux Toolkit, React Query, Axios, error handling, optimistic updates

125. Implement a Redux Toolkit slice for a shopping cart with actions:
    - `addItem(product)` — add item or increment quantity
    - `removeItem(productId)` — remove item
    - `updateQuantity({ productId, quantity })`
    - `clearCart()`
    - A selector `selectCartTotal` that computes the total price

126. Write a React component that uses `useQuery` from TanStack Query (React Query) to fetch a list of products. Handle:
    - Loading state with a skeleton UI
    - Error state with a retry button
    - Stale data with background refetching
    - Cache invalidation after a mutation

127. Implement an optimistic UI update using `useMutation` from React Query:
    - User clicks "Like" on a post
    - Immediately increment the like count in the UI
    - Make the API call in the background
    - Roll back the UI change if the API call fails

128. Build a React component that:
    - Has a search input
    - Cancels the previous API request when a new search is typed (using `AbortController` with Axios)
    - Shows the results in a dropdown
    - Handles no-results and error states

129. Implement an Axios interceptor in a React application that:
    - Adds the JWT `Authorization` header to every outgoing request
    - On a `401 Unauthorized` response, attempts to refresh the token
    - If token refresh fails, redirects to the login page
    - Queues all requests that arrive during token refresh

130. Scenario: Your React app fetches a large dataset (10,000 rows) from a Spring Boot API and renders it in a table. The page freezes for 2–3 seconds. What are at least 4 strategies to fix this — both frontend and backend?

131. Implement a file upload component in React that:
    - Supports drag-and-drop and click-to-browse
    - Shows upload progress (percentage bar) using `XMLHttpRequest` or Axios `onUploadProgress`
    - Supports cancelling an in-progress upload
    - Previews images before upload

132. Write React code to implement real-time notifications using Server-Sent Events (SSE) from a Spring Boot backend:
    - Spring Boot `SseEmitter` endpoint
    - React hook that connects to SSE and displays new notifications as they arrive

---

## 11. JavaScript & TypeScript Coding

> Focus: Async/await, closures, prototypes, TypeScript generics

133. Implement a `debounce(fn, delay)` function from scratch in JavaScript. Then implement `throttle(fn, limit)`. Explain the difference and use case for each.

134. Write a `deepClone(obj)` function in JavaScript that handles: nested objects, arrays, `null`, `Date`, and circular references.

135. Implement `Promise.all()` from scratch. Then implement `Promise.allSettled()`. Show the difference in behavior when one promise rejects.

136. Write a function `memoize(fn)` that caches the results of a function call. The cache should be keyed by the function arguments. Handle functions with multiple arguments.

137. Implement an `EventEmitter` class with `on(event, listener)`, `off(event, listener)`, `emit(event, ...args)`, and `once(event, listener)` methods.

138. Write a `pipe(...fns)` and `compose(...fns)` utility function. Demonstrate the difference between them with a real transformation example.

139. Implement TypeScript generic types for:
    - `Partial<T>` — make all properties optional
    - `Required<T>` — make all properties required
    - `Pick<T, K>` — select specific keys
    - Write a custom `DeepPartial<T>` that works recursively for nested objects

140. Write a TypeScript `type-safe` API client class for a REST API. Use generics so that `get<User>('/users/1')` returns `Promise<User>`.

141. Implement a TypeScript decorator `@Log` that logs the function name, arguments, and return value every time a class method is called.

142. Write a JavaScript function that flattens a deeply nested array to any specified depth without using `Array.prototype.flat()`.

143. Implement a `curry(fn)` function that converts a function of `n` arguments into a chain of `n` single-argument functions. `curry(add)(1)(2)(3)` should equal `add(1,2,3)`.

144. Scenario: You have an async function that calls 3 APIs in sequence, but each subsequent call depends on the result of the previous one. Refactor it to be as concurrent as possible while maintaining the dependencies.

---

## 12. HTML & CSS Scenarios

> Focus: Semantic HTML, responsive design, CSS layout, accessibility

145. Write semantic HTML for a blog post page including: navigation, article with sections, sidebar with related posts, footer. Use appropriate ARIA attributes for accessibility.

146. Implement a responsive CSS grid layout for a product card listing that:
    - Shows 4 columns on desktop (>1200px)
    - Shows 2 columns on tablet (768px–1200px)
    - Shows 1 column on mobile (<768px)
    - Uses CSS Grid only (no libraries)

147. Implement a CSS-only sticky header that:
    - Stays at the top of the viewport while scrolling
    - Has a shadow that only appears when the page is scrolled down
    - Use `position: sticky` and a CSS `@supports` fallback

148. Write CSS for a flex-based navigation bar that:
    - Has a logo on the left
    - Nav links centered
    - Login button on the right
    - Collapses to a hamburger menu on mobile (CSS only)

149. Implement a CSS animation for a loading skeleton screen for a card component (pulsing grey rectangles using `@keyframes`).

150. Scenario: A specific button in your React application is not accessible for screen reader users. What HTML attributes and ARIA roles would you add to make it accessible? How would you test it?

---

## 13. Docker & Kubernetes — DevOps Scenarios

> Focus: Containerization, orchestration, environment management

151. Write a multi-stage `Dockerfile` for a Spring Boot application that:
    - Stage 1: Uses a Maven image to build the JAR
    - Stage 2: Uses a minimal JRE Alpine image to run the JAR
    - Ensures secrets are not baked into the image
    - Minimizes final image size

152. Write a `Dockerfile` for a React application that:
    - Builds the React app with Node.js
    - Serves the static build files using Nginx
    - Configures Nginx to handle client-side routing (SPA fallback to `index.html`)

153. Write a `docker-compose.yml` that starts the full Java Full Stack application:
    - Spring Boot backend (port 8080)
    - React frontend served by Nginx (port 3000)
    - PostgreSQL database (port 5432) with a volume for persistence
    - Redis for caching (port 6379)
    - Environment variable injection from a `.env` file

154. Write a Kubernetes `Deployment` YAML for the Spring Boot application with:
    - 3 replicas
    - Resource requests and limits (CPU: 250m request, 500m limit; Memory: 256Mi/512Mi)
    - Liveness probe: `GET /actuator/health` every 30s
    - Readiness probe: `GET /actuator/health/readiness` every 10s
    - Rolling update strategy with `maxSurge: 1`, `maxUnavailable: 0`

155. Scenario: Your Spring Boot container keeps crashing in Kubernetes with `OOMKilled` errors. How would you diagnose this issue and what settings would you change in both the JVM and Kubernetes resource limits?

156. Write Kubernetes `ConfigMap` and `Secret` manifests for the Spring Boot application. Show how they are mounted as environment variables and as volume files into the pod.

157. Scenario: You need to perform a zero-downtime deployment of a new version of your Spring Boot service in Kubernetes. Walk through the complete deployment strategy — from pushing a new Docker image to traffic being fully routed to the new version.

158. Write a Kubernetes `HorizontalPodAutoscaler` that scales the Spring Boot deployment between 2–10 replicas based on CPU usage (target: 70%) and custom metric (requests per second > 1000).

---

## 14. Git & CI/CD Scenarios

> Focus: Version control workflows, pipeline design, automation

159. Scenario: You and a colleague both modified the same file in different branches. When you merge, there is a conflict. Walk through how you would resolve the conflict using Git CLI commands.

160. Design a complete GitHub Actions CI/CD pipeline for the Java Full Stack application that:
    - Triggers on push to `main` and pull requests
    - Stage 1: Run Java unit and integration tests with Maven
    - Stage 2: Run React tests with Jest
    - Stage 3: Build Docker images for backend and frontend
    - Stage 4: Push images to Docker Hub / ECR
    - Stage 5: Deploy to Kubernetes (on main branch only)

161. Scenario: A bad commit was deployed to production and is causing a critical bug. How do you: (a) immediately roll back to the previous version, and (b) permanently remove the bad commit from the branch history?

162. Describe a Git branching strategy for a team of 10 developers working on a Java Full Stack application. Include: branch naming conventions, how features, hotfixes, and releases are handled. Compare GitFlow vs trunk-based development.

163. Scenario: Your CI pipeline takes 25 minutes to run. Developers are frustrated by the slow feedback. Identify at least 5 strategies to reduce the pipeline time while maintaining quality.

164. Write a Jenkins pipeline (Declarative) that:
    - Pulls the repository
    - Runs `mvn test` and publishes test results
    - Builds the Docker image
    - Runs security scanning with Trivy
    - Deploys to a staging environment on success

---

## 15. Full Stack System Design & Integration Scenarios

> Focus: End-to-end architecture, integration patterns, scalability

165. **Design a full stack e-commerce checkout flow:**
    A user clicks "Buy Now" on a React frontend. Design the complete flow: React component → Axios call → Spring Boot controller → Service → JPA Repository → Database → Payment Gateway integration → Response back to React. Handle: loading states, payment failure, inventory out-of-stock.

166. **Scenario: React app + Spring Boot API running on separate domains.**
    A React app on `https://frontend.com` calls a Spring Boot API on `https://api.backend.com`. On login, the API returns a JWT. How do you store the JWT securely? Compare: `localStorage` vs `httpOnly cookie`. Implement the secure cookie approach end-to-end.

167. **Implement real-time order tracking:**
    A customer wants to see live order status updates (Pending → Processing → Shipped → Delivered) without refreshing the page. Design and implement this using either WebSockets or SSE between React and Spring Boot.

168. **Design and implement search with autocomplete:**
    - React: A search bar with debounced input (500ms delay)
    - Spring Boot: A `/api/search?q=keyword` endpoint
    - Database: A full-text search query using PostgreSQL `tsvector` or MySQL `FULLTEXT`
    - Optimization: Cache popular searches in Redis with a 5-minute TTL

169. **Scenario: Session management across microservices.**
    Your system has 5 microservices. A user logs in through the API Gateway. How do you propagate the user's identity (JWT claims) to all downstream services? Show the implementation from Gateway filter → downstream service extraction of user context.

170. **Implement soft delete across the full stack:**
    - Database: Add `deleted_at` column to entities. Records are never actually deleted.
    - Spring Boot: Use Hibernate filters or JPA `@Where` annotation to automatically exclude soft-deleted records from all queries.
    - API: `DELETE /api/products/{id}` sets `deleted_at` instead of removing the row.
    - React: The product disappears from the UI immediately (optimistic update).

171. **Design a notification system:**
    Users should receive notifications: in-app (React), email, and SMS. Design the architecture:
    - Spring Boot event publishing using Spring Events or Kafka
    - Separate `NotificationService` microservice
    - React polling vs SSE for in-app notifications
    - Rate limiting to prevent notification spam

172. **Scenario: You are hired to improve the performance of a sluggish full stack application.**
    Metrics: API average response time 3s, React initial load time 8s, Database queries averaging 2s. List and implement at least 8 specific optimizations across: React bundle size, API response caching (Redis), database indexing, lazy loading components, image optimization, connection pooling, and CDN usage.

173. **Implement multi-tenancy in a Java Full Stack SaaS application:**
    Each tenant (company) should have isolated data. Design: (a) database-per-tenant, (b) schema-per-tenant, or (c) row-level isolation using a `tenant_id` column. Show the Spring Boot implementation of option (c) using a `TenantContext` thread-local and a Hibernate interceptor.

174. **Design an audit trail system:**
    Every create, update, and delete operation on any entity must be logged. Log: who did it (user ID), when, what changed (before and after values), IP address.
    - Backend: Implement using Hibernate Envers or a custom AOP aspect
    - Database: Design the `audit_log` table
    - API: `GET /api/audit?entityType=Product&entityId=1` returns full history
    - React: Show an audit history timeline component

175. **Full Stack scenario interview — Build a mini task management app:**
    Design the complete architecture for a Trello-like task board:
    - Database schema: `boards`, `columns`, `tasks`, `users`, `labels`
    - REST API: CRUD for boards, columns, tasks; drag-and-drop order (reordering tasks)
    - React: Board view, drag-and-drop between columns (`@dnd-kit/core`), real-time collaboration using WebSockets
    - Security: Only board members can view and edit
    - Deployment: Dockerized, deployed on Kubernetes

---

## 🔑 Tech Stack Quick Reference — What You Must Know

| Layer | Core Technologies |
|---|---|
| **Language** | Java 17/21, JavaScript (ES2022+), TypeScript |
| **Frontend** | React 18/19, React Router v6, Redux Toolkit, React Query |
| **Backend Framework** | Spring Boot 3.x, Spring MVC, Spring Data JPA |
| **Security** | Spring Security 6, JWT, OAuth2, BCrypt |
| **ORM** | Hibernate 6, JPA, Spring Data Repositories |
| **Database** | MySQL / PostgreSQL, Redis, Liquibase/Flyway |
| **Messaging** | Apache Kafka, RabbitMQ |
| **Microservices** | Spring Cloud, Eureka, API Gateway, Resilience4j |
| **Containerization** | Docker, Docker Compose, Kubernetes |
| **CI/CD** | GitHub Actions, Jenkins, Maven, Git |
| **Testing** | JUnit 5, Mockito, Testcontainers, Jest, React Testing Library |
| **API Tooling** | Swagger/OpenAPI 3, Postman, Axios |
| **Monitoring** | Spring Actuator, Prometheus, Grafana, ELK Stack |

---

## 📌 Scenario-Based Interview Tips

- Always clarify the **scale** (10 users? 10 million users?) before answering system design questions
- For coding questions, talk through your approach before writing code — interviewers value thinking process
- Mention **trade-offs** in every technical decision (e.g., REST vs Kafka, Redis vs DB caching)
- Connect your answers to **business impact** (e.g., "This reduces DB load by 70%, cutting infrastructure cost")
- For full stack questions, show understanding of the **complete request flow** from React to DB and back
- Know your **annotations** cold: `@Transactional`, `@Entity`, `@RestController`, `@Service`, `@Repository`, `@Autowired`, `@Bean`, `@Configuration`

---

*Compiled from: GeeksforGeeks, InterviewBit, JavaGuides, CodingShuttle, Medium, DEV Community, GitHub repositories, C# Corner, Quescol, DataCamp, Hirist.tech — April 2026*

*Best of luck with your Java Full Stack + React interview! ☕⚛️🚀*
