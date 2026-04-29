# Java Full Stack with React — Interview Questions
### Code Implementation & Scenario-Based Questions (Without Answers)

> **Role Focus:** Java Full Stack Developer with React  
> **Tech Stack Coverage:** Core Java | Spring Boot | Spring Security | Hibernate & JPA | REST APIs | React.js | JavaScript (ES6+) | HTML & CSS | SQL & Databases | Microservices | Git | Docker | AWS / Cloud | Testing  
> **Difficulty Levels:** ⚡ Basic | 🔥 Intermediate | 💀 Advanced

---

## Table of Contents

1. [Core Java](#1-core-java)
2. [Spring Framework & Spring Boot](#2-spring-framework--spring-boot)
3. [Spring Security & JWT](#3-spring-security--jwt)
4. [Hibernate & JPA](#4-hibernate--jpa)
5. [REST API Design](#5-rest-api-design)
6. [Microservices](#6-microservices)
7. [JavaScript (ES6+)](#7-javascript-es6)
8. [React.js — Core Concepts](#8-reactjs--core-concepts)
9. [React Hooks](#9-react-hooks)
10. [React State Management (Redux / Context API)](#10-react-state-management-redux--context-api)
11. [React Performance Optimization](#11-react-performance-optimization)
12. [HTML & CSS](#12-html--css)
13. [SQL & Databases](#13-sql--databases)
14. [Git & Version Control](#14-git--version-control)
15. [Docker & Containerization](#15-docker--containerization)
16. [AWS & Cloud Deployment](#16-aws--cloud-deployment)
17. [Testing (JUnit, Mockito, React Testing)](#17-testing-junit-mockito-react-testing)
18. [Full Stack Integration Scenarios](#18-full-stack-integration-scenarios)
19. [System Design & Architecture](#19-system-design--architecture)
20. [DSA & Problem Solving (Java)](#20-dsa--problem-solving-java)

---

## 1. Core Java

### ⚡ Basic

1. Implement a Java program that demonstrates the use of `final`, `finally`, and `finalize` in three separate, meaningful scenarios.
2. Write a program to find duplicate elements in an array without using any built-in Java Collection methods.
3. Implement a Singleton class in Java that is thread-safe. What happens if you don't make it thread-safe?
4. Write code to demonstrate the difference between `==` and `.equals()` with String objects. When would `==` return `true` for two different String variables?
5. Implement a custom `Comparator` that sorts a list of `Employee` objects first by department name (A–Z), then by salary (descending).
6. Write a program using a functional interface and a lambda expression to filter a list of integers that are divisible by both 3 and 5.
7. What is the output of this code? Explain step by step:
   ```java
   String s1 = "hello";
   String s2 = new String("hello");
   String s3 = s2.intern();
   System.out.println(s1 == s2);
   System.out.println(s1 == s3);
   System.out.println(s2 == s3);
   ```
8. Implement a generic stack class in Java with `push`, `pop`, `peek`, and `isEmpty` operations.

### 🔥 Intermediate

9. Explain the difference between `HashMap`, `LinkedHashMap`, and `TreeMap`. Write a code scenario where using the wrong one would cause a bug.
10. Implement a program using Java Streams API to: group a list of employees by department, find the highest-paid employee in each department, and print the result sorted by department name.
11. Write a code example where `ConcurrentModificationException` is thrown. How do you fix it? Implement the fix using `CopyOnWriteArrayList` and using an `Iterator`.
12. Given the following code, identify the memory leak and fix it:
    ```java
    public class Cache {
        private static Map<String, byte[]> store = new HashMap<>();
        public static void add(String key, byte[] data) {
            store.put(key, data);
        }
    }
    ```
13. Implement a `CompletableFuture` chain that: fetches a user by ID (async), then fetches their orders (async), then calculates the total order value, and handles any exception gracefully with a fallback value.
14. Explain method references in Java 8. Write a code example using all four types: static method reference, instance method reference of a particular object, instance method reference of an arbitrary object, and constructor reference.
15. Implement a program that demonstrates the difference between `synchronized` method and `synchronized` block. When would you prefer one over the other?

### 💀 Advanced

16. Explain how the Java Memory Model works. Write a code example where lack of `volatile` keyword causes a visibility issue between threads.
17. Implement a thread-safe `LRU (Least Recently Used) Cache` in Java using `LinkedHashMap`.
18. Scenario: Your application is experiencing frequent `OutOfMemoryError: Java heap space` in production. Walk through the steps and tools you'd use to diagnose and resolve this, including heap dump analysis.
19. Implement a custom `BlockingQueue` using `wait()` and `notify()` (without using `java.util.concurrent` classes).
20. Explain the difference between `Callable` and `Runnable`. In which scenario would using an `ExecutorService` with `Callable` and `Future` be better than creating raw threads?
21. Write a program that demonstrates how Java's Garbage Collector can be affected by creating too many short-lived objects in a loop, and how you can optimize using object pooling.

---

## 2. Spring Framework & Spring Boot

### ⚡ Basic

1. Create a simple Spring Boot REST controller that exposes a `GET /api/hello` endpoint returning a JSON response `{"message": "Hello, World!"}`.
2. What is the difference between `@Component`, `@Service`, `@Repository`, and `@Controller`? When would you use each?
3. Explain `@Autowired`, `@Qualifier`, and `@Primary`. Write a scenario where you have two implementations of the same interface and need to inject a specific one.
4. What is `application.properties` vs `application.yml`? Write the same multi-level database configuration in both formats.
5. Implement a Spring Boot application that reads custom properties from `application.properties` using `@Value` and `@ConfigurationProperties`.
6. What does `@SpringBootApplication` annotation do internally? Which three annotations does it combine?

### 🔥 Intermediate

7. Implement a global exception handler using `@ControllerAdvice` and `@ExceptionHandler` that returns a standardized JSON error response for `ResourceNotFoundException` and `ValidationException`.
8. Scenario: You have a Spring Boot app in dev, QA, and prod environments, each requiring different database URLs, logging levels, and third-party API keys. How would you set up and activate Spring Profiles? Write the configuration.
9. Implement a scheduled task using `@Scheduled` that runs every day at 2:00 AM and cleans up stale records from the database.
10. Write a Spring Boot filter that logs the HTTP method, URI, request duration, and response status code for every incoming request.
11. Explain the difference between `@RestController` and `@Controller`. When would you use `@Controller` with `@ResponseBody` vs `@RestController`?
12. Implement pagination and sorting in a Spring Boot REST API. Show the controller, service, and repository layer code for fetching paginated employee records sorted by name.
13. Scenario: Your Spring Boot application takes too long to start in production. What are the possible causes and how would you optimize startup time?
14. Implement request validation using `@Valid`, `@NotNull`, `@Email`, and custom constraint annotations. Show how to return field-level error messages in the response.

### 💀 Advanced

15. Explain Spring Boot's auto-configuration mechanism. Walk through how `@EnableAutoConfiguration` works internally with `spring.factories` (or `AutoConfiguration.imports` in Spring Boot 3+).
16. Scenario: You need to connect your Spring Boot app to two different databases — one MySQL for transactional data and one MongoDB for analytics. Implement the multiple `DataSource` configuration with separate JPA repositories for each.
17. Implement a Spring Boot application with Aspect-Oriented Programming (AOP) to: log method execution time for all service layer methods, and retry a method up to 3 times if it throws a specific exception.
18. Explain `BeanFactory` vs `ApplicationContext`. What extra capabilities does `ApplicationContext` provide?
19. Scenario: After deploying a new version, your Spring Boot app is returning stale cached data. Walk through how you would implement and manage caching using `@Cacheable`, `@CacheEvict`, and `@CachePut` with Redis.
20. Write a Spring Boot Actuator custom endpoint that returns the current application's health metrics including database connection pool stats.

---

## 3. Spring Security & JWT

### ⚡ Basic

1. What is the difference between Authentication and Authorization? Give a real-world example for each in context of a Spring Boot REST API.
2. Explain how JWT (JSON Web Token) works. What are the three parts of a JWT and what does each contain?
3. Implement a basic HTTP Basic Authentication configuration in Spring Security for a REST API.

### 🔥 Intermediate

4. Implement a complete JWT-based authentication flow in Spring Boot: user login endpoint that validates credentials and returns a JWT, a JWT filter that validates the token on each request, and securing specific endpoints while allowing public access to `/api/auth/**`.
5. Scenario: A user's JWT token is stolen. Since JWTs are stateless, how would you implement token revocation? Implement a blacklist-based approach using Redis.
6. Implement Role-Based Access Control (RBAC) where `ADMIN` can access all endpoints, `MANAGER` can access read and write, and `USER` can only access read endpoints. Show the Spring Security configuration and the controller annotations.
7. What is CSRF and why is it disabled by default for REST APIs in Spring Security? In what scenario would you need to enable it?
8. Implement OAuth2 login in Spring Boot using Google as the identity provider. Show the `application.yml` configuration and how to customize the user info mapping.

### 💀 Advanced

9. Scenario: Your application issues both access tokens (short-lived, 15 min) and refresh tokens (long-lived, 7 days). Implement the complete refresh token flow including storing refresh tokens in the database, rotating them on each refresh, and invalidating them on logout.
10. Explain the difference between `@PreAuthorize`, `@PostAuthorize`, `@Secured`, and `@RolesAllowed`. Write scenarios where each is most appropriate.
11. Implement method-level security to ensure a user can only update their own profile and not another user's profile, using `@PreAuthorize` with SpEL expressions.

---

## 4. Hibernate & JPA

### ⚡ Basic

1. What is the difference between JPA and Hibernate? Can you use JPA without Hibernate?
2. Explain the JPA entity lifecycle states: Transient, Persistent, Detached, and Removed. Write a code example showing transitions between states.
3. Write a JPA entity `Employee` with proper annotations: `@Entity`, `@Table`, `@Id`, `@GeneratedValue`, `@Column`, and a `@ManyToOne` relationship to `Department`.
4. What is the difference between `save()`, `persist()`, `merge()`, and `saveOrUpdate()` in Hibernate?
5. Explain what the `spring.jpa.hibernate.ddl-auto` property does. What are the differences between `create`, `update`, `validate`, and `none`?

### 🔥 Intermediate

6. Implement a `@OneToMany` bidirectional relationship between `Order` and `OrderItem`. What is the `mappedBy` attribute and which side is the owner of the relationship?
7. Scenario: Your application has an `N+1 query problem` when fetching a list of orders with their items. Identify the problem in code, explain why it happens, and fix it using `JOIN FETCH` or `@EntityGraph`.
8. Explain the difference between `FetchType.LAZY` and `FetchType.EAGER`. What is `LazyInitializationException` and how do you fix it without making everything `EAGER`?
9. Write a Spring Data JPA repository with: a derived query method, a `@Query` annotation with JPQL, a `@Query` with native SQL, and a `@Modifying` update query.
10. Implement a Hibernate entity with optimistic locking using `@Version`. What happens when two users try to update the same record simultaneously?
11. Explain Hibernate's first-level cache and second-level cache. Implement second-level caching using EhCache for the `Product` entity.

### 💀 Advanced

12. Scenario: Your production database has a table with 50 million rows. Your queries are timing out. How would you diagnose and solve this using indexes, query optimization, and Hibernate-level changes?
13. Implement inheritance mapping for a payment system with `Payment` as a base entity and `CreditCardPayment`, `BankTransferPayment` as subclasses. Compare `SINGLE_TABLE`, `JOINED`, and `TABLE_PER_CLASS` strategies with their tradeoffs.
14. Write a custom `UserType` in Hibernate to map a Java `enum` to a specific string format in the database, different from the default `ORDINAL` or `STRING` mapping.
15. Scenario: You notice Hibernate is generating inefficient SQL with unnecessary joins. How would you use Hibernate's `show_sql`, `format_sql`, and `Statistics` API to diagnose the problem?

---

## 5. REST API Design

### ⚡ Basic

1. Design the RESTful API endpoints (URL, HTTP method, request/response body) for a complete CRUD `Product` resource.
2. What is the difference between `PUT` and `PATCH`? Give a code scenario where using `PUT` instead of `PATCH` causes an unintended side effect.
3. What HTTP status codes would you return for: resource not found, validation error, unauthorized access, server error, and successful resource creation?
4. Implement a Spring Boot REST endpoint that accepts a JSON body, validates it, and saves to a database. Include proper error handling.

### 🔥 Intermediate

5. Implement REST API versioning. Compare and implement all four approaches: URI versioning (`/api/v1/`), request parameter versioning, header versioning, and media type versioning. Which would you choose and why?
6. Implement file upload and download endpoints in Spring Boot. How would you handle large files to avoid memory issues?
7. Scenario: Your public REST API is being hit with thousands of requests per second from a single client. Implement rate limiting using Spring Boot and a `RateLimiter`.
8. Write a Spring Boot REST API that supports filtering, pagination, and sorting dynamically based on query parameters (e.g., `/api/employees?department=IT&page=0&size=10&sort=name,asc`).
9. What is HATEOAS? Implement a REST response for a `Product` resource that includes hypermedia links for related actions (self, update, delete).
10. Implement CORS configuration in Spring Boot to allow requests only from `https://myapp.com` for `GET` and `POST` methods.

### 💀 Advanced

11. Scenario: Your REST API needs to return partial responses to reduce payload size (like the `fields` parameter in Google APIs). Implement a mechanism to return only the requested fields from a response.
12. Design an idempotent REST API for payment processing. How do you handle the scenario where a client retries a payment request due to a network timeout?
13. Implement a REST API with Long Polling for real-time notifications. When should you choose Long Polling over WebSockets?

---

## 6. Microservices

### ⚡ Basic

1. What is the difference between a monolithic application and a microservices architecture? What are the challenges of microservices that don't exist in a monolith?
2. What is an API Gateway? What responsibilities does it have in a microservices system?
3. Explain the difference between synchronous (REST/gRPC) and asynchronous (Kafka/RabbitMQ) communication in microservices. When would you choose each?

### 🔥 Intermediate

4. Implement Service Discovery using Spring Cloud Eureka. Show how to register a microservice and how another service discovers and calls it using `FeignClient`.
5. Implement the Circuit Breaker pattern using Resilience4j in Spring Boot. Show how it opens when a downstream service fails and returns a fallback response.
6. Scenario: You have an `OrderService` that calls `InventoryService` and `PaymentService` sequentially. The `PaymentService` is down. How does this failure cascade? Implement bulkhead and timeout configurations to prevent it.
7. Implement distributed tracing across three microservices using Spring Cloud Sleuth and Zipkin. How would you correlate logs from all services for a single request?
8. Explain the Saga Pattern for distributed transactions. Compare Choreography-based Saga vs Orchestration-based Saga. Implement a simple order fulfillment saga.

### 💀 Advanced

9. Scenario: In a microservices setup, `UserService` updates user data, and `OrderService` has a local copy of the user name for performance. How do you keep them in sync without tight coupling? Implement Event-Driven synchronization using Kafka.
10. Explain the CQRS (Command Query Responsibility Segregation) pattern. In what scenarios would you implement CQRS, and what are the tradeoffs?
11. Implement an outbox pattern to guarantee reliable event publishing to Kafka even if the service crashes after committing a database transaction but before publishing the event.
12. Scenario: Your microservices deployment runs 10 instances of `OrderService`. A specific bug is only reproducible on 2 instances. How do you debug this in production without taking instances down?

---

## 7. JavaScript (ES6+)

### ⚡ Basic

1. Explain `var`, `let`, and `const` with examples. What is the temporal dead zone?
2. What is the output of the following and why?
   ```javascript
   console.log(typeof null);
   console.log(null instanceof Object);
   console.log([] == false);
   console.log([] === false);
   ```
3. Write an ES6 arrow function that takes an array of numbers and returns a new array with only even numbers, doubled.
4. Explain destructuring assignment. Write examples for object destructuring, array destructuring, and destructuring with default values and renaming.
5. What is the difference between `==` and `===` in JavaScript? Give three examples where `==` produces an unexpected result.

### 🔥 Intermediate

6. Explain the JavaScript event loop, call stack, and microtask queue. What is the output order of this code and why?
   ```javascript
   console.log('1');
   setTimeout(() => console.log('2'), 0);
   Promise.resolve().then(() => console.log('3'));
   console.log('4');
   ```
7. Explain closures in JavaScript with a practical example. How can closures cause memory leaks and how do you prevent them?
8. Implement a `debounce` function from scratch. Then implement a `throttle` function. Explain the difference and give a UI use case for each.
9. What is the difference between `Promise.all`, `Promise.allSettled`, `Promise.race`, and `Promise.any`? Write code examples showing different failure scenarios for each.
10. Implement a `deep clone` function for a JavaScript object without using `JSON.parse(JSON.stringify())`. Handle circular references.
11. Write an `async/await` function that fetches user data, then fetches their posts in parallel, and handles errors gracefully using `try/catch`.

### 💀 Advanced

12. Explain `Prototype` and `Prototype Chain` in JavaScript. How does `class` syntax in ES6 differ from prototype-based inheritance internally?
13. Implement a `curry` function that converts `add(1, 2, 3)` to `add(1)(2)(3)` and also handles partial application.
14. Scenario: A colleague's code has a memory leak in a single-page application. The memory usage grows every time a user navigates between pages. How would you diagnose and fix it using Chrome DevTools?
15. Implement an observable/reactive pattern from scratch (a simplified version of RxJS `Observable`).

---

## 8. React.js — Core Concepts

### ⚡ Basic

1. Explain the difference between a Controlled Component and an Uncontrolled Component. Implement a login form using both approaches.
2. What is JSX? What does it compile to? Write a JSX expression that renders a list of names and explain what the `key` prop does.
3. Explain the difference between `props` and `state`. Can a child component modify its own `props`? Why or why not?
4. Implement a `Counter` component with increment, decrement, and reset buttons using `useState`.
5. What is the Virtual DOM? How does React's reconciliation algorithm (`diffing`) work?
6. What is the difference between a class component and a functional component? Why does the React team recommend functional components?

### 🔥 Intermediate

7. Implement a reusable `Table` component that accepts `columns` (array of column definitions) and `data` (array of objects) as props and renders a dynamic HTML table.
8. Scenario: You have a deeply nested component tree where a prop needs to be passed 5 levels deep, but only the leaf component uses it. This is called "prop drilling." Show the problem with code and implement the solution using Context API.
9. Implement a Higher-Order Component (HOC) called `withAuth` that redirects unauthenticated users to the login page when they try to access a protected component.
10. Explain React's component lifecycle (for class components). Map each lifecycle method to its equivalent in hooks.
11. Implement a `Modal` component using `React Portals` that renders outside the parent DOM hierarchy. Why would you use Portals for modals?
12. What is the difference between `React.Fragment` and a wrapping `<div>`? When does it matter semantically and for performance?
13. Implement a form with multiple input fields, validation (required, email format, min length), and show validation errors inline without any form library.

### 💀 Advanced

14. Explain React's Concurrent Mode and the concept of `startTransition`. Write a scenario where marking a state update as a transition prevents UI jank.
15. Implement an `ErrorBoundary` class component. What types of errors does it catch and what doesn't it catch? How do you use `react-error-boundary` library in modern React?
16. Scenario: Your React app renders a list of 10,000 items and is extremely slow. Walk through your optimization strategy including `React.memo`, `useMemo`, `useCallback`, virtualization with `react-window`, and `code splitting`.
17. Explain React's rendering phases: the Render Phase and the Commit Phase. Why must the render phase be pure?
18. What are React Server Components (RSC)? How do they differ from regular components? What are the rules and benefits?

---

## 9. React Hooks

### ⚡ Basic

1. What are the two rules of Hooks? What happens if you call `useState` inside an `if` statement?
2. Implement a component that fetches data from an API using `useEffect` and `useState`. Handle loading and error states.
3. What is the purpose of the dependency array in `useEffect`? Explain the difference between `[]`, `[dep]`, and omitting the array entirely.
4. Implement a simple `useRef` example that focuses an input field when a button is clicked.

### 🔥 Intermediate

5. Scenario: This `useEffect` has a bug that causes an infinite loop. Identify the bug and fix it:
   ```javascript
   const [user, setUser] = useState({});
   useEffect(() => {
     fetch('/api/user')
       .then(r => r.json())
       .then(data => setUser(data));
   }, [user]);
   ```
6. Implement a custom hook `useFetch(url)` that handles data fetching, caching, loading state, error handling, and request cancellation using `AbortController`.
7. Explain the difference between `useCallback` and `useMemo`. Write a scenario where using `useCallback` is necessary to prevent a child component from re-rendering unnecessarily.
8. Implement a custom hook `useLocalStorage(key, initialValue)` that syncs state with `localStorage` and updates across browser tabs using the `storage` event.
9. What is `useReducer`? Implement a shopping cart using `useReducer` with actions: `ADD_ITEM`, `REMOVE_ITEM`, `UPDATE_QUANTITY`, and `CLEAR_CART`.
10. Implement a custom `useDebounce(value, delay)` hook and use it to implement a search input that makes an API call only after the user stops typing for 500ms.
11. What is `useLayoutEffect`? Write a scenario where `useEffect` causes a visible flicker but `useLayoutEffect` fixes it.

### 💀 Advanced

12. Implement a `useIntersectionObserver` custom hook for infinite scrolling — loading more items when the user reaches the bottom of the list.
13. Explain how `useContext` + `useReducer` can replace Redux for medium-sized applications. Implement a global auth state using this pattern.
14. Scenario: A component using `useEffect` inside a recursive data structure causes a stack overflow. How do you refactor it?
15. What is the `use` hook introduced in React 19? How does it differ from `useEffect` for data fetching? Implement a component using it with Suspense.
16. Implement a `useWebSocket` custom hook that manages a WebSocket connection with automatic reconnection logic.

---

## 10. React State Management (Redux / Context API)

### ⚡ Basic

1. What problem does Redux solve? When would you NOT use Redux in a React application?
2. Explain the three core principles of Redux: single source of truth, state is read-only, and changes are made with pure functions.
3. What is the difference between Redux Toolkit's `createSlice` and the traditional `action creator + reducer` approach?

### 🔥 Intermediate

4. Implement a Redux Toolkit slice for a `cartSlice` with state, reducers for `addToCart`, `removeFromCart`, `updateQuantity`, and selectors. Connect it to a `CartComponent`.
5. What is Redux middleware? Implement a custom Redux middleware that logs every dispatched action and the state before and after.
6. Implement an async operation in Redux Toolkit using `createAsyncThunk` to fetch products from an API. Handle `pending`, `fulfilled`, and `rejected` states.
7. Scenario: Your Redux store has grown to over 30 slices and page load performance is suffering. How would you implement code splitting for Redux reducers using `replaceReducer`?
8. Explain the difference between `useSelector` and `connect`. When is `useSelector` with `shallowEqual` important for performance?

### 💀 Advanced

9. Implement the Context API + `useReducer` pattern as a drop-in replacement for a Redux auth module. What are the limitations compared to Redux DevTools?
10. Scenario: Two unrelated components in different parts of the tree need to share and update the same data. Compare and implement solutions using: prop lifting, Context API, Redux Toolkit, and Zustand.
11. Implement optimistic UI updates in Redux — update the UI immediately before the server confirms the action, and roll back on error.

---

## 11. React Performance Optimization

### 🔥 Intermediate

1. Explain why `React.memo` doesn't always prevent re-renders. Write a scenario where a memoized child still re-renders due to a new object reference in props.
2. Implement code splitting in a React app using `React.lazy` and `Suspense` for route-based code splitting. What is the difference between route-level and component-level splitting?
3. Scenario: Your React app's bundle size is 4MB. Walk through the steps to analyze and reduce it using webpack-bundle-analyzer, tree shaking, and dynamic imports.
4. Implement a virtualized list using `react-window` that renders 100,000 rows performantly.
5. What is the `key` prop and how does misusing it cause performance issues? Give a code example of using `index` as a key causing a bug.

### 💀 Advanced

6. Explain React's batching behavior in React 17 vs React 18 (`automatic batching`). Write a scenario where React 17 doesn't batch updates but React 18 does.
7. Implement a `useMemo` optimization for an expensive computation (e.g., filtering and sorting a large dataset) and explain how to measure if the optimization is actually helping using React DevTools Profiler.
8. Scenario: A React page with a complex form re-renders entirely on every keystroke. Diagnose using React Profiler and optimize using `memo`, `useCallback`, and `useId`.

---

## 12. HTML & CSS

### ⚡ Basic

1. What is the difference between `id` and `class` attributes in HTML? What is CSS specificity and how is it calculated?
2. Implement a responsive navigation bar using only CSS Flexbox that collapses into a hamburger menu on mobile.
3. Explain the CSS Box Model. What is the difference between `content-box` and `border-box` in `box-sizing`?
4. What is the difference between `position: relative`, `absolute`, `fixed`, and `sticky`? Create a scenario for each.

### 🔥 Intermediate

5. Implement a responsive 3-column card layout using CSS Grid that switches to 2 columns on tablets and 1 column on mobile.
6. Implement CSS animations and transitions to create a smooth button hover effect and a loading spinner.
7. Explain `z-index` and stacking context. Write a scenario where `z-index: 9999` doesn't work as expected.
8. What is the difference between `display: none`, `visibility: hidden`, and `opacity: 0`? How does each affect layout, accessibility, and animations?
9. Implement CSS custom properties (variables) for a theme system that supports dark mode toggle.

### 💀 Advanced

10. Implement a CSS-only accordion component. What are the accessibility considerations (`aria-expanded`, keyboard navigation)?
11. Scenario: Your React app has CSS specificity conflicts causing styles from one component to bleed into another. What are the strategies to solve this? Compare CSS Modules, Styled-Components, Tailwind CSS, and BEM.
12. Explain Critical Rendering Path. How would you optimize CSS delivery to improve First Contentful Paint (FCP)?

---

## 13. SQL & Databases

### ⚡ Basic

1. Write SQL to find the second highest salary from an `Employee` table (handle ties correctly).
2. Explain the difference between `INNER JOIN`, `LEFT JOIN`, `RIGHT JOIN`, and `FULL OUTER JOIN` with examples.
3. What is the difference between `WHERE` and `HAVING` clauses? When can you not use `WHERE` instead of `HAVING`?
4. Write a SQL query to find all departments that have more than 5 employees earning above $50,000.
5. What is the difference between `DELETE`, `TRUNCATE`, and `DROP`? Which is fastest and why?

### 🔥 Intermediate

6. Write a SQL query using a window function (`ROW_NUMBER`, `RANK`, `DENSE_RANK`) to find the top 3 highest-paid employees per department.
7. Scenario: A query `SELECT * FROM orders WHERE customer_id = 12345` is taking 8 seconds on a table with 50 million rows. What steps would you take to optimize it? Include index strategy.
8. Implement a stored procedure that accepts a date range and returns a sales summary by product category, including total sales, average order value, and number of orders.
9. Explain database normalization (1NF, 2NF, 3NF, BCNF). Give a real-world example of a table that violates 2NF and normalize it.
10. Write a SQL query to detect duplicate rows in a `customers` table based on `email` and delete the duplicates while keeping the one with the lowest `id`.
11. What is a database transaction? Explain ACID properties with real examples. Write a SQL transaction for transferring money between two bank accounts.

### 💀 Advanced

12. Scenario: Your MySQL database replication is lagging by 30 minutes during peak hours. What are the possible causes and how do you diagnose and fix replication lag?
13. Explain the difference between optimistic locking and pessimistic locking in databases. Implement both in a Spring Boot + JPA application for concurrent ticket booking.
14. What is a database index? Explain B-Tree index, composite index, covering index, and partial index. When can an index make performance worse?
15. Implement a SQL query using Common Table Expressions (CTEs) to find all subordinates of a specific manager in a self-referencing `employees` table (hierarchical data).

---

## 14. Git & Version Control

### ⚡ Basic

1. What is the difference between `git merge` and `git rebase`? When would you use each? What does "fast-forward merge" mean?
2. Explain the difference between `git fetch`, `git pull`, and `git clone`.
3. Scenario: You accidentally committed sensitive credentials (API keys) to a public repository. What are the immediate steps you take?

### 🔥 Intermediate

4. Scenario: You are working on a feature branch. Your colleague merged a hotfix to `main` that you also need. How do you get those changes without merging the entire `main` into your branch?
5. Explain the GitFlow branching strategy. What are the branches involved and what purpose does each serve?
6. Scenario: You need to undo the last 3 commits that have already been pushed to the remote `main` branch. How would you do this safely without rewriting history for other developers?
7. What is `git cherry-pick`? Write a scenario where it is useful and implement the commands step by step.
8. Explain `git stash`. What is the difference between `git stash pop` and `git stash apply`? How do you stash only specific files?

---

## 15. Docker & Containerization

### ⚡ Basic

1. What is the difference between a Docker Image and a Docker Container?
2. Write a `Dockerfile` for a Spring Boot application. Include best practices like using a specific base image, multi-stage builds, and a non-root user.
3. What is the difference between `CMD` and `ENTRYPOINT` in a Dockerfile?

### 🔥 Intermediate

4. Write a `docker-compose.yml` file that spins up a Spring Boot application, a MySQL database, and a Redis cache. Include health checks, volume mounts for data persistence, and environment variables.
5. Scenario: Your Docker container is running but the Spring Boot app inside is crashing with an `Address already in use` error on port 8080. How do you diagnose and fix it?
6. Implement a multi-stage Docker build for a React + Spring Boot application. Explain why multi-stage builds are important and how they reduce image size.
7. What is Docker networking? Explain the difference between `bridge`, `host`, and `overlay` networks.
8. Scenario: Your Docker image for the application is 2GB. How would you reduce it to under 200MB? List concrete steps and Dockerfile changes.

### 💀 Advanced

9. Scenario: Your containerized application running in Docker has a memory leak. How do you set memory limits, monitor usage, and diagnose the leak inside the container?
10. Explain the difference between Docker Swarm and Kubernetes. When would you use Docker Swarm in production?
11. Implement a CI/CD pipeline using Jenkins and Docker where: code push triggers a build, runs unit tests in a Docker container, builds a Docker image, pushes to Docker Hub, and deploys to a staging server.

---

## 16. AWS & Cloud Deployment

### ⚡ Basic

1. What is the difference between EC2, ECS, and EKS in AWS? When would you choose each for deploying a Java microservice?
2. What is an S3 bucket? Implement a Spring Boot service that uploads a file to S3 and generates a pre-signed URL for temporary access.
3. Explain the difference between `Horizontal Scaling` and `Vertical Scaling`. How does AWS Auto Scaling Group help?

### 🔥 Intermediate

4. Implement a CI/CD pipeline on AWS using: CodeCommit or GitHub for source, CodeBuild to build and test the Spring Boot app, ECR for Docker image storage, and CodeDeploy to deploy to ECS Fargate.
5. Scenario: Your Spring Boot app deployed on EC2 is intermittently throwing 504 Gateway Timeout errors. Walk through the debugging steps using AWS CloudWatch Logs, ALB access logs, and EC2 metrics.
6. What is AWS RDS? How do you configure a Spring Boot application to use RDS Aurora MySQL with connection pooling using HikariCP? What parameters would you tune?
7. Implement a Spring Boot application that uses AWS Secrets Manager to retrieve database credentials at startup instead of hardcoding them in `application.yml`.
8. Scenario: Your production API is experiencing traffic spikes 3x normal during business hours. How would you architect a solution using AWS ALB, Auto Scaling, and ElastiCache?

### 💀 Advanced

9. Design and implement a serverless architecture for a file processing pipeline: user uploads a CSV to S3, S3 triggers an AWS Lambda (Java), Lambda parses the file and puts messages on SQS, another Lambda processes each message and writes to DynamoDB.
10. Explain the difference between Blue-Green Deployment and Canary Deployment. Implement Canary releases using AWS CodeDeploy or Kubernetes.
11. Scenario: Your AWS bill spiked 300% last month. How would you audit the AWS cost using Cost Explorer, identify the top 5 causes, and implement cost optimization strategies?
12. Explain VPC, Subnets, Security Groups, and NACLs. Design the network architecture for a secure 3-tier application (React frontend, Spring Boot backend, RDS database) on AWS.

---

## 17. Testing (JUnit, Mockito, React Testing)

### ⚡ Basic

1. What is the difference between Unit Testing, Integration Testing, and End-to-End Testing? Give an example of each for a Java Full Stack application.
2. Write a JUnit 5 unit test for a `calculateDiscount(double price, int quantity)` method that has different discount tiers. Use `@ParameterizedTest` with `@CsvSource`.
3. Write a Mockito test for a `UserService.getUserById(Long id)` method that calls `UserRepository.findById()`. Mock the repository and verify the interaction.

### 🔥 Intermediate

4. Write a Spring Boot integration test using `@SpringBootTest` and `MockMvc` that tests a `POST /api/users` endpoint end-to-end with a test database (H2).
5. Implement a Jest + React Testing Library test suite for a `LoginForm` component that: tests form rendering, tests validation error messages, tests successful form submission with mocked API, and tests loading state.
6. Scenario: Your team has 5% test coverage. You need to bring it to 80% in 2 months. How do you prioritize what to test and what testing strategy do you follow?
7. What is Test-Driven Development (TDD)? Write a failing test first for a `BankAccount` class, then implement the code to make it pass. Use the Red-Green-Refactor cycle.
8. Implement contract testing between a React frontend and Spring Boot backend using Pact. What problem does contract testing solve?

### 💀 Advanced

9. Scenario: Your Mockito test is behaving differently from production because the mock isn't capturing async behavior correctly. How do you test asynchronous service calls using `CompletableFuture` with Mockito?
10. Implement a TestContainer-based integration test for a Spring Boot application that spins up a real PostgreSQL container, runs Flyway migrations, and tests the repository layer.
11. What is mutation testing? Set up PIT (PITest) for a Spring Boot project and explain what it reveals that code coverage metrics miss.

---

## 18. Full Stack Integration Scenarios

These questions test your ability to connect the entire stack.

1. **Scenario:** Implement a full-stack feature: A React form submits employee data to a Spring Boot REST API, which validates, saves to MySQL using JPA, and returns the created resource. Include: React form with validation, Axios API call with error handling, Spring Boot controller + service + repository, JPA entity, and proper HTTP status codes.

2. **Scenario:** Your React app calls a Spring Boot API and gets a `403 Forbidden` response even though the user is logged in. How do you debug this step by step — from the browser network tab to Spring Security configuration?

3. **Scenario:** Implement JWT authentication across the full stack: React login form → POST to Spring Boot `/auth/login` → returns JWT → React stores JWT in `httpOnly` cookie → subsequent React requests include the cookie → Spring Boot validates JWT on each request.

4. **Scenario:** Implement real-time notifications using WebSockets: Spring Boot `@EnableWebSocketMessageBroker` server with STOMP, React client using `SockJS + stomp.js` to subscribe to a topic and display notifications.

5. **Scenario:** A user uploads a large file (500MB video) from a React frontend. Design the entire flow: React multipart upload with progress bar, Spring Boot multipart endpoint with streaming (avoiding loading into memory), storage to AWS S3, and status feedback to the user.

6. **Scenario:** You need to implement infinite scroll in a React app backed by a paginated Spring Boot API. Implement both sides: Spring Boot `Pageable` endpoint and React `useIntersectionObserver` + `useEffect` to fetch the next page when the user reaches the bottom.

7. **Scenario:** Your React app and Spring Boot API are deployed on different domains. The React app gets CORS errors only in production, not locally. Diagnose the issue and show the fix at both the Spring Boot level and potential reverse proxy (Nginx) level.

8. **Scenario:** Implement a role-based UI in React where the menu items, buttons, and routes are conditionally rendered based on the user's roles stored in the JWT. How do you prevent users from accessing protected routes by directly typing the URL?

---

## 19. System Design & Architecture

1. **Design a URL Shortener** (like bit.ly): Define the API, database schema, encoding algorithm, and how you'd handle 100 million URLs with high read throughput and low latency. What caching strategy would you use?

2. **Design a Notification System**: Support email, SMS, and push notifications. The system must handle 10 million notifications per day with delivery guarantees, retry on failure, and user preferences. Which queuing system would you use?

3. **Design a Real-Time Chat Application**: Support 1M concurrent users. Define the architecture using WebSockets, message persistence, message ordering, read receipts, and how you'd handle user going offline and reconnecting.

4. **Design an E-Commerce Product Search**: With a catalog of 50 million products, you need full-text search, filters, facets, and auto-complete. Compare Elasticsearch vs a relational database for this use case. Design the indexing strategy.

5. **Design a Rate Limiter**: Implement a token bucket or sliding window rate limiter that limits each API key to 1000 requests per minute. How would this work in a distributed system with multiple API server instances?

6. **Scenario:** Your Spring Boot monolith handles 500 requests/second and you need to scale to 5000 requests/second in 3 months. Design the migration path: what to extract as microservices first, how to handle the strangler fig pattern, and how to ensure zero downtime during migration.

7. **Design an Authentication System** supporting: username/password login, OAuth2 (Google, GitHub), multi-factor authentication (TOTP), and session management. How do you handle "remember me" functionality securely?

---

## 20. DSA & Problem Solving (Java)

These are frequently asked live coding problems in Java Full Stack interviews.

### Arrays & Strings

1. Given an array of integers, find the maximum sum of a contiguous subarray (Kadane's Algorithm). Write the solution and explain the time complexity.
2. Implement a function to check if two strings are anagrams of each other without using sorting. What is the time and space complexity?
3. Given a string, find the longest substring without repeating characters. Implement using a sliding window approach.
4. Rotate an array of `n` elements to the right by `k` steps. Implement the in-place solution.
5. Given an array of integers, find all pairs that sum to a target value. Return them without duplicates.

### Linked Lists & Trees

6. Reverse a singly linked list iteratively and recursively.
7. Detect a cycle in a linked list (Floyd's cycle detection algorithm). Return the node where the cycle begins.
8. Given the root of a binary tree, find the level-order traversal (BFS). Return each level as a separate list.
9. Implement a function to find the Lowest Common Ancestor (LCA) of two nodes in a Binary Search Tree.
10. Check if a binary tree is balanced (height-balanced). What is the time complexity of your solution?

### Sorting, Searching & Hashing

11. Implement Merge Sort and explain why it's preferred over QuickSort for linked lists.
12. Given a list of `intervals`, merge all overlapping intervals and return the result.
13. Implement a function using a stack to evaluate a mathematical expression in Reverse Polish Notation (RPN).
14. Given an unsorted array, find the first missing positive integer in O(n) time and O(1) space.
15. Implement a `LRU Cache` with O(1) get and O(1) put operations. What data structures would you use?

### Java Streams & Functional Programming (Coding)

16. Using Java Streams, write a single stream pipeline to: take a list of `Transaction` objects, filter transactions above $1000, group them by currency, and find the maximum transaction amount per currency.
17. Implement `flatMap` from scratch using a custom functional interface. Demonstrate its use with a list of lists.
18. Write a Java Stream pipeline that reads a list of sentences, splits them into words, filters words longer than 5 characters, converts to uppercase, removes duplicates, and collects into a sorted list.

---

## Quick Scenario Reference Cards

| Scenario | Key Concepts to Cover |
|---|---|
| App is slow in production | Profiling, DB indexes, caching, N+1 queries, thread pool tuning |
| API returning 403 | Spring Security chain, JWT validation, CORS, role mapping |
| Memory leak in Java | Heap dump, VisualVM, static references, unclosed streams |
| React page is laggy | React Profiler, memo, useCallback, virtualization, bundle size |
| DB queries timing out | Explain plan, indexing, query rewrite, connection pool |
| Microservice is down | Circuit breaker, fallback, health checks, retry logic |
| Deployment failed | Rollback strategy, blue-green, Docker logs, CI/CD pipeline |
| CORS error in production | Spring CORS config, Nginx proxy config, preflight requests |
| JWT token issues | Expiry, signing key, filter chain order, token storage |
| Build too slow | Parallel builds, incremental compilation, dependency caching |

---

*Last updated: 2025–2026 | For Java Full Stack with React roles*  
*Tech Stack: Java 17+, Spring Boot 3+, React 18+, MySQL/PostgreSQL, Docker, AWS, Git*
