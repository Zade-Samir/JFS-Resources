# Core Java Interview Questions - Comprehensive List

## Table of Contents
1. [Java Basics](#1-java-basics)
2. [Object-Oriented Programming (OOP)](#2-object-oriented-programming-oop)
3. [String Handling](#3-string-handling)
4. [Collections Framework](#4-collections-framework)
5. [Multithreading & Concurrency](#5-multithreading--concurrency)
6. [Exception Handling](#6-exception-handling)
7. [Java 8 Features](#7-java-8-features)
8. [Memory Management & JVM](#8-memory-management--jvm)
9. [Generics](#9-generics)
10. [Input/Output (I/O)](#10-inputoutput-io)
11. [JDBC & Database](#11-jdbc--database)
12. [Design Patterns](#12-design-patterns)
13. [Java Advanced Topics](#13-java-advanced-topics)

---

## 1. Java Basics

### Core Concepts
1. What is Java? What are the main features of Java?
2. Is Java a purely object-oriented programming language? Why or why not?
3. What is the difference between JDK, JRE, and JVM?
4. Explain the concept of platform independence in Java.
5. What is bytecode in Java?
6. How does the Java compilation process work?
7. What is the difference between C++ and Java?

### Data Types & Variables
8. What are the primitive data types in Java?
9. What are wrapper classes in Java? Why do we need them?
10. What is autoboxing and unboxing?
11. What is the difference between `int` and `Integer`?
12. What are literals in Java?
13. What is type casting? Explain implicit and explicit casting.
14. What is the difference between widening and narrowing conversion?

### Operators & Control Statements
15. What is the difference between `==` and `.equals()` method?
16. What is the difference between `&` and `&&` operators?
17. What is the difference between `++i` and `i++`?
18. Explain the switch statement. Can we use String in switch case?
19. What is the difference between `break` and `continue`?
20. What is the enhanced for loop (for-each loop)?

### Arrays
21. What is an array in Java? How do you declare and initialize arrays?
22. What is the limitation of using arrays in Java?
23. Can we change the size of an array at runtime?
24. What is a multidimensional array?
25. How do you copy arrays in Java?

### Methods
26. What is method overloading?
27. What are the rules for method overloading?
28. Can we overload the main method in Java?
29. What is variable arguments (varargs)?
30. What is the difference between pass by value and pass by reference?
31. Does Java support pass by reference?

### Keywords & Modifiers
32. What is the `static` keyword in Java?
33. What is a static variable and static method?
34. Can we declare a static variable inside a method?
35. What is the `final` keyword in Java?
36. Can we change the value of a final variable?
37. What is a blank final variable?
38. What is the `this` keyword? When and how is it used?
39. What is the `super` keyword? When and how is it used?

---

## 2. Object-Oriented Programming (OOP)

### Classes & Objects
40. What is a class in Java?
41. What is an object in Java?
42. What is the difference between a class and an object?
43. How many ways can we create an object in Java?
44. What is a constructor in Java?
45. What are the types of constructors?
46. What is a default constructor?
47. Can we have a constructor with different access modifiers?
48. What is constructor overloading?
49. Can we call a constructor from another constructor?
50. What is constructor chaining?

### Inheritance
51. What is inheritance in Java?
52. What are the types of inheritance in Java?
53. Why does Java not support multiple inheritance through classes?
54. How can we achieve multiple inheritance in Java?
55. What is the diamond problem?
56. What is the difference between `extends` and `implements`?
57. Can we override static methods?
58. Can we override private methods?
59. What is method overriding?
60. What are the rules for method overriding?
61. What is the use of the `super` keyword in inheritance?
62. Can a constructor be inherited?

### Polymorphism
63. What is polymorphism in Java?
64. What are the types of polymorphism?
65. What is compile-time polymorphism (static binding)?
66. What is runtime polymorphism (dynamic binding)?
67. What is the difference between method overloading and method overriding?
68. Can we achieve runtime polymorphism by data members?
69. What is dynamic method dispatch?
70. What is the difference between early binding and late binding?

### Abstraction
71. What is abstraction in Java?
72. What is an abstract class?
73. Can an abstract class have a constructor?
74. Can we create an object of an abstract class?
75. Can an abstract class have final methods?
76. Can an abstract class have static methods?
77. What is an interface in Java?
78. What is the difference between an abstract class and an interface?
79. Can an interface extend another interface?
80. Can a class implement multiple interfaces?
81. What are marker interfaces? Give examples.

### Encapsulation
82. What is encapsulation in Java?
83. How do you achieve encapsulation?
84. What are getters and setters?
85. Why should we use private access modifiers for data members?
86. What is data hiding?

### Access Modifiers
87. What are access modifiers in Java?
88. Explain the four types of access modifiers.
89. What is the default access modifier?
90. What is the difference between public, private, protected, and default?
91. Can we have a private constructor?
92. What is the purpose of a private constructor?

### Inner Classes
93. What is an inner class?
94. What are the types of inner classes?
95. What is a static nested class?
96. What is the difference between a static nested class and a non-static inner class?
97. What is an anonymous inner class?
98. What is a local inner class?

---

## 3. String Handling

### String Basics
99. What is String in Java? Is it a primitive or object?
100. Why are Strings immutable in Java?
101. What are the benefits of String immutability?
102. How do you create a String object?
103. What is the String constant pool?
104. What is the difference between String created using `new` and literal?
105. What is String interning?

### String Comparison
106. What is the difference between `==` and `.equals()` for Strings?
107. What is the `.compareTo()` method?
108. How does the String `.hashCode()` method work?

### String Methods
109. What are the important methods of the String class?
110. How do you reverse a String?
111. How do you check if a String is palindrome?
112. How do you count the occurrences of a character in a String?
113. How do you remove leading and trailing spaces from a String?

### StringBuffer & StringBuilder
114. What is the difference between String, StringBuffer, and StringBuilder?
115. When should we use StringBuffer and StringBuilder?
116. Which is faster: StringBuffer or StringBuilder?
117. Are StringBuffer and StringBuilder mutable?
118. What is the default capacity of StringBuffer and StringBuilder?

---

## 4. Collections Framework

### Collections Basics
119. What is the Collection framework in Java?
120. What are the main interfaces in the Collection framework?
121. What is the difference between Collection and Collections?
122. What is the hierarchy of the Collection framework?
123. What are the advantages of the Collection framework over arrays?
124. What is the difference between Collection and Stream?

### List Interface
125. What is the List interface?
126. What is the difference between ArrayList and LinkedList?
127. When should we use ArrayList over LinkedList?
128. What is the difference between ArrayList and Vector?
129. Is ArrayList synchronized or not?
130. How do you synchronize an ArrayList?
131. What is the initial capacity of ArrayList?
132. How does ArrayList grow in size?
133. What is CopyOnWriteArrayList?
134. What is the difference between `remove(int index)` and `remove(Object o)`?

### Set Interface
135. What is the Set interface?
136. What is the difference between HashSet and TreeSet?
137. How does HashSet maintain uniqueness?
138. What is the difference between HashSet and LinkedHashSet?
139. Can we add null values to a Set?
140. How many null values can a HashSet contain?
141. What is a SortedSet?
142. What is a NavigableSet?

### Map Interface
143. What is the Map interface?
144. What is the difference between HashMap and Hashtable?
145. How does HashMap work internally?
146. What is hashing?
147. What is a hash collision? How is it handled in HashMap?
148. What is the load factor in HashMap?
149. What is the initial capacity of HashMap?
150. What is the difference between HashMap and LinkedHashMap?
151. What is the difference between HashMap and TreeMap?
152. What is the difference between HashMap and ConcurrentHashMap?
153. Can we store null keys and null values in HashMap?
154. How many null keys can a HashMap have?
155. What is WeakHashMap?
156. What is IdentityHashMap?

### Queue Interface
157. What is the Queue interface?
158. What is the difference between Queue and Deque?
159. What is PriorityQueue?
160. What is the difference between PriorityQueue and TreeSet?
161. What is BlockingQueue?
162. What are the different types of BlockingQueue?

### Iterator
163. What is an Iterator?
164. What is the difference between Iterator and ListIterator?
165. What is the difference between Iterator and Enumeration?
166. What is fail-fast and fail-safe iterator?
167. Which collections are fail-fast and which are fail-safe?
168. Can we remove elements while iterating through a collection?

### Comparable & Comparator
169. What is the Comparable interface?
170. What is the Comparator interface?
171. What is the difference between Comparable and Comparator?
172. When should we use Comparable and when should we use Comparator?
173. How do you sort a collection in Java?

### Concurrent Collections
174. What are concurrent collections in Java?
175. What is ConcurrentHashMap?
176. How does ConcurrentHashMap work internally?
177. What is the difference between ConcurrentHashMap and Hashtable?
178. What is CopyOnWriteArrayList?
179. What is CopyOnWriteArraySet?
180. What is ConcurrentLinkedQueue?

---

## 5. Multithreading & Concurrency

### Thread Basics
181. What is a thread in Java?
182. What is multithreading?
183. What is the difference between process and thread?
184. What are the benefits of multithreading?
185. What is the difference between user thread and daemon thread?
186. How do you create a thread in Java?
187. What is the difference between extending Thread class and implementing Runnable interface?
188. Which approach is better: extending Thread or implementing Runnable?
189. Can we start a thread twice?
190. What happens if we call the `run()` method directly instead of `start()`?

### Thread Lifecycle
191. What are the different states of a thread?
192. What is the thread lifecycle in Java?
193. What is the difference between `sleep()` and `wait()`?
194. What is the difference between `sleep()` and `yield()`?
195. What is the `join()` method?
196. What is thread priority?
197. Can we change the priority of a thread?
198. What is the default priority of a thread?

### Synchronization
199. What is synchronization in Java?
200. Why do we need synchronization?
201. What is a synchronized method?
202. What is a synchronized block?
203. What is the difference between synchronized method and synchronized block?
204. Can we use synchronized keyword with variables?
205. What is class-level lock and object-level lock?
206. What is static synchronization?
207. What is the difference between `notify()` and `notifyAll()`?
208. What is deadlock? How can you avoid it?
209. What is livelock?
210. What is thread starvation?

### Concurrency Utilities
211. What is the java.util.concurrent package?
212. What is an Executor framework?
213. What is ExecutorService?
214. What is ThreadPoolExecutor?
215. What are the different types of thread pools?
216. What is a ScheduledExecutorService?
217. What is the difference between `execute()` and `submit()` methods?
218. What is a Future in Java?
219. What is a Callable interface?
220. What is the difference between Callable and Runnable?
221. What is CompletableFuture?

### Locks & Synchronizers
222. What is the Lock interface?
223. What is ReentrantLock?
224. What is the difference between synchronized and ReentrantLock?
225. What are ReadWriteLock and ReentrantReadWriteLock?
226. What is a Semaphore?
227. What is CountDownLatch?
228. What is CyclicBarrier?
229. What is the difference between CountDownLatch and CyclicBarrier?
230. What is Exchanger?
231. What is Phaser?

### Thread Safety
232. What is thread safety?
233. How do you achieve thread safety in Java?
234. What is the volatile keyword?
235. What is the difference between volatile and synchronized?
236. What is the Java Memory Model (JMM)?
237. What is happens-before relationship?
238. What are atomic operations?
239. What are atomic classes in Java?
240. What is the difference between AtomicInteger and synchronized int?

---

## 6. Exception Handling

### Exception Basics
241. What is an exception in Java?
242. What is exception handling?
243. What are the advantages of exception handling?
244. What is the hierarchy of exception classes?
245. What is the difference between Error and Exception?
246. What is the difference between checked and unchecked exceptions?
247. Give examples of checked exceptions.
248. Give examples of unchecked exceptions.

### Try-Catch-Finally
249. What are the keywords used in exception handling?
250. What is a try block?
251. What is a catch block?
252. Can we have multiple catch blocks for a single try?
253. What is the order of catch blocks?
254. What is a finally block?
255. When is the finally block executed?
256. Will finally block execute if there is a return statement in try/catch?
257. Will finally block execute if there is `System.exit()`?
258. Can we have a try block without a catch block?
259. Can we have try with multiple finally blocks?

### Throw & Throws
260. What is the difference between `throw` and `throws`?
261. What is the purpose of the `throw` keyword?
262. What is the purpose of the `throws` keyword?
263. Can we throw multiple exceptions using throws clause?
264. What is exception propagation?
265. What is exception re-throwing?

### Custom Exceptions
266. What is a custom exception?
267. How do you create a custom exception in Java?
268. When should we create custom exceptions?
269. Should custom exceptions be checked or unchecked?

### Try-with-Resources
270. What is try-with-resources?
271. What is AutoCloseable interface?
272. What are the benefits of try-with-resources?
273. Can we use multiple resources in try-with-resources?

### Advanced Exception Handling
274. What is exception chaining?
275. What is a suppressed exception?
276. What is the difference between `final`, `finally`, and `finalize`?
277. Can we override a method that throws a checked exception with one that throws an unchecked exception?
278. What are the best practices for exception handling?
279. What is the multi-catch block?
280. Can we catch Error in Java?

---

## 7. Java 8 Features

### Lambda Expressions
281. What is a lambda expression in Java?
282. What are the benefits of lambda expressions?
283. What is the syntax of a lambda expression?
284. What is a functional interface?
285. What is the @FunctionalInterface annotation?
286. Can a functional interface have multiple default methods?
287. What are the built-in functional interfaces in Java?
288. What is a Predicate?
289. What is a Consumer?
290. What is a Supplier?
291. What is a Function?
292. What is a BiFunction?

### Stream API
293. What is the Stream API?
294. What is the difference between Collection and Stream?
295. What are the characteristics of Stream?
296. What is the difference between intermediate and terminal operations?
297. What are some examples of intermediate operations?
298. What are some examples of terminal operations?
299. What is lazy evaluation in streams?
300. What is the difference between `map()` and `flatMap()`?
301. What is the difference between `filter()` and `map()`?
302. What is the `reduce()` operation?
303. What is the `collect()` operation?
304. What are Collectors in Stream API?
305. What is the difference between `findFirst()` and `findAny()`?
306. What is the difference between `peek()` and `forEach()`?
307. How do you create a Stream?
308. What is a parallel stream?
309. What is the difference between sequential and parallel streams?
310. When should we use parallel streams?

### Method References
311. What is a method reference?
312. What are the types of method references?
313. What is the syntax of method reference?
314. What is a constructor reference?
315. What is the difference between lambda expression and method reference?

### Optional
316. What is Optional in Java?
317. How do you create an Optional object?
318. What is the purpose of Optional?
319. What are the methods available in Optional class?
320. What is the difference between `Optional.of()` and `Optional.ofNullable()`?
321. What is the difference between `get()` and `orElse()`?
322. What is `orElseThrow()`?

### Default & Static Methods in Interfaces
323. What are default methods in interfaces?
324. Why were default methods introduced in Java 8?
325. Can we override default methods?
326. What are static methods in interfaces?
327. What is the difference between default and static methods in interfaces?
328. Can we have multiple interfaces with the same default method?

### Date & Time API
329. What is the new Date and Time API in Java 8?
330. What are the main classes in java.time package?
331. What is LocalDate?
332. What is LocalTime?
333. What is LocalDateTime?
334. What is ZonedDateTime?
335. What is Period and Duration?
336. What are the advantages of the new Date and Time API?

### Other Java 8 Features
337. What is Nashorn?
338. What are StringJoiners?
339. What is the forEach() method?
340. What is the difference between Iterator forEach() and Stream forEach()?

---

## 8. Memory Management & JVM

### JVM Architecture
341. What is JVM?
342. What are the components of JVM architecture?
343. What is Class Loader?
344. What are the types of class loaders?
345. What is JIT compiler?
346. What is the difference between JVM, JRE, and JDK?

### Memory Areas
347. What are the different memory areas in JVM?
348. What is the heap memory?
349. What is the stack memory?
350. What is the difference between heap and stack memory?
351. What is stored in heap memory?
352. What is stored in stack memory?
353. What is PermGen space?
354. What is Metaspace?
355. What is the difference between PermGen and Metaspace?
356. What is the difference between young generation and old generation?
357. What is Eden space, Survivor space?

### Garbage Collection
358. What is Garbage Collection?
359. How does Garbage Collection work in Java?
360. What are the types of Garbage Collectors?
361. What is the difference between minor GC and major GC?
362. What is a full GC?
363. What is the `finalize()` method?
364. When is the `finalize()` method called?
365. Can we force garbage collection?
366. What are memory leaks in Java?
367. How can we prevent memory leaks?
368. What are the different GC algorithms?

### Object Creation & Destruction
369. What happens when an object is created in Java?
370. How many ways can we create objects in Java?
371. What is cloning in Java?
372. What is shallow copy vs deep copy?
373. What is the `clone()` method?
374. What is the Cloneable interface?

---

## 9. Generics

### Generics Basics
375. What are generics in Java?
376. Why do we need generics?
377. What are the advantages of generics?
378. What is type safety?
379. What is a generic class?
380. What is a generic method?
381. What is a generic interface?

### Type Parameters
382. What is a type parameter?
383. What are the naming conventions for type parameters?
384. What is bounded type parameter?
385. What is the difference between `<? extends T>` and `<? super T>`?
386. What is an upper bounded wildcard?
387. What is a lower bounded wildcard?
388. What is an unbounded wildcard?
389. What is type erasure?
390. What are the limitations of generics?

---

## 10. Input/Output (I/O)

### I/O Basics
391. What is I/O in Java?
392. What are the types of streams in Java?
393. What is the difference between byte stream and character stream?
394. What is InputStream and OutputStream?
395. What is Reader and Writer?

### File I/O
396. What is the File class?
397. How do you read a file in Java?
398. How do you write to a file in Java?
399. What is FileInputStream and FileOutputStream?
400. What is FileReader and FileWriter?
401. What is BufferedReader and BufferedWriter?
402. What is the difference between FileReader and BufferedReader?

### Serialization
403. What is serialization in Java?
404. What is deserialization?
405. Why do we need serialization?
406. What is the Serializable interface?
407. What is serialVersionUID?
408. What is transient keyword?
409. What is Externalizable interface?
410. What is the difference between Serializable and Externalizable?

### NIO
411. What is Java NIO?
412. What is the difference between IO and NIO?
413. What are channels in NIO?
414. What are buffers in NIO?
415. What are selectors in NIO?

---

## 11. JDBC & Database

### JDBC Basics
416. What is JDBC?
417. What are the components of JDBC?
418. What are the steps to connect to a database using JDBC?
419. What is DriverManager?
420. What is Connection interface?
421. What is Statement interface?
422. What is PreparedStatement?
423. What is CallableStatement?
424. What is the difference between Statement and PreparedStatement?
425. What is ResultSet?
426. What are the types of ResultSet?

### Database Operations
427. How do you execute a SQL query in JDBC?
428. How do you execute a stored procedure in JDBC?
429. What is batch processing in JDBC?
430. What is transaction management in JDBC?
431. How do you commit and rollback transactions?
432. What is connection pooling?
433. What is SQLException?

---

## 12. Design Patterns

### Creational Patterns
434. What are design patterns?
435. What is Singleton pattern?
436. How do you implement a thread-safe Singleton?
437. What is Factory pattern?
438. What is Abstract Factory pattern?
439. What is Builder pattern?
440. What is Prototype pattern?

### Structural Patterns
441. What is Adapter pattern?
442. What is Decorator pattern?
443. What is Proxy pattern?
444. What is Facade pattern?
445. What is Composite pattern?

### Behavioral Patterns
446. What is Strategy pattern?
447. What is Observer pattern?
448. What is Template Method pattern?
449. What is Iterator pattern?
450. What is Command pattern?

---

## 13. Java Advanced Topics

### Reflection
451. What is Reflection in Java?
452. What are the uses of Reflection?
453. How do you get Class object in Java?
454. What is the difference between `Class.forName()` and `ClassLoader.loadClass()`?
455. How do you invoke a method using Reflection?

### Annotations
456. What are annotations in Java?
457. What are the built-in annotations in Java?
458. What is @Override annotation?
459. What is @Deprecated annotation?
460. What is @SuppressWarnings annotation?
461. What is @FunctionalInterface annotation?
462. How do you create custom annotations?
463. What are meta-annotations?

### Regular Expressions
464. What are regular expressions?
465. What is the Pattern class?
466. What is the Matcher class?
467. How do you validate an email using regex?

### Networking
468. What is networking in Java?
469. What is the Socket class?
470. What is the ServerSocket class?
471. What is URL and URLConnection?
472. What is the difference between TCP and UDP?

### Immutability
473. What is an immutable class?
474. How do you create an immutable class?
475. Why is String immutable?
476. What are the benefits of immutability?

### Object Class Methods
477. What are the important methods of Object class?
478. What is the `equals()` method?
479. What is the `hashCode()` method?
480. What is the contract between `equals()` and `hashCode()`?
481. What is the `toString()` method?
482. What is the `clone()` method?
483. What is the `finalize()` method?
484. What is the `wait()`, `notify()`, and `notifyAll()` methods?

### Best Practices
485. What are the SOLID principles?
486. What is the DRY principle?
487. What is the KISS principle?
488. What is the YAGNI principle?
489. What are coding standards in Java?
490. What are some common Java best practices?

### Performance & Optimization
491. How do you improve Java application performance?
492. What is profiling?
493. What are memory leaks and how to prevent them?
494. What is the difference between `==` and `.equals()` in terms of performance?
495. When should you use StringBuilder over String concatenation?

### Java Versions
496. What are the new features in Java 9?
497. What are the new features in Java 10?
498. What are the new features in Java 11?
499. What are the new features in Java 17?
500. What is the difference between LTS and non-LTS versions of Java?

---

## Additional Important Questions

### Miscellaneous
501. What is the difference between `abstract class` and `interface`?
502. What is composition vs inheritance?
503. What is tight coupling vs loose coupling?
504. What is dependency injection?
505. What is the difference between aggregation and composition?
506. What is cohesion and coupling?
507. What is the instanceof operator?
508. What is type casting? When do we use it?
509. What is the difference between `Comparable` and `Comparator`?
510. What is the difference between `Array` and `ArrayList`?
511. What is the difference between `HashSet` and `TreeSet`?
512. What is the difference between `HashMap` and `TreeMap`?
513. What is the purpose of the `transient` keyword?
514. What is the purpose of the `native` keyword?
515. What is the purpose of the `strictfp` keyword?
516. What is covariant return type?
517. What is method hiding in Java?
518. What is the diamond problem and how is it solved in Java 8?
519. Can we have a return statement in finally block?
520. What happens if both try and finally blocks have return statements?

---

## End of Questions

**Note:** This list contains the most frequently asked and important Core Java interview questions covering all major topics. For a successful interview:

1. Understand the concepts deeply, not just memorize answers
2. Practice coding problems regularly
3. Be ready with real-world examples
4. Understand when and why to use specific features
5. Keep yourself updated with the latest Java versions and features

**Good luck with your interviews!**
