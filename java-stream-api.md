# Java Stream API Coding Interview Questions - Comprehensive List

## Table of Contents
1. [Basic Stream Operations](#1-basic-stream-operations)
2. [Filtering & Mapping](#2-filtering--mapping)
3. [Sorting](#3-sorting)
4. [Reduction & Aggregation](#4-reduction--aggregation)
5. [Collectors - Basic](#5-collectors---basic)
6. [Collectors - GroupingBy](#6-collectors---groupingby)
7. [Collectors - Advanced](#7-collectors---advanced)
8. [FlatMap Operations](#8-flatmap-operations)
9. [String Manipulation](#9-string-manipulation)
10. [Finding & Matching](#10-finding--matching)
11. [Distinct & Unique Elements](#11-distinct--unique-elements)
12. [Parallel Streams](#12-parallel-streams)
13. [Employee Object Operations](#13-employee-object-operations)
14. [Map & Entry Operations](#14-map--entry-operations)
15. [Array & List Conversions](#15-array--list-conversions)
16. [Optional Operations](#16-optional-operations)
17. [Partitioning](#17-partitioning)
18. [Statistical Operations](#18-statistical-operations)
19. [File Operations with Streams](#19-file-operations-with-streams)
20. [Advanced & Complex Scenarios](#20-advanced--complex-scenarios)

---

## 1. Basic Stream Operations

### Creating & Converting Streams
1. Given a list of integers, convert it to a stream and print all elements.
2. Create a stream from an array of strings.
3. Create an infinite stream of random numbers and limit it to 10 elements.
4. Create a stream of integers from 1 to 100.
5. Convert an array to a list using streams.
6. Create a stream from a Map's keys.
7. Create a stream from a Map's values.
8. Create a stream from a Map's entries.
9. Create a stream of custom objects (e.g., Employee, Student).
10. Convert a Set to a List using streams.

### Counting & Iteration
11. Count the total number of elements in a list using streams.
12. Print all elements in a list using forEach.
13. Count the number of elements greater than a certain value.
14. Count how many strings start with a specific character.
15. Iterate over a stream and perform operations on each element.

---

## 2. Filtering & Mapping

### Filtering Operations
16. Filter all even numbers from a list of integers.
17. Filter all odd numbers from a list of integers.
18. Filter strings that start with a specific letter.
19. Filter strings that end with a specific letter.
20. Filter strings that contain a specific substring.
21. Filter numbers greater than a specific value.
22. Filter numbers less than a specific value.
23. Filter numbers within a specific range (e.g., between 10 and 50).
24. Filter null values from a list.
25. Filter empty strings from a list.
26. Filter blank/whitespace strings from a list.
27. Filter elements based on multiple conditions.
28. Filter numbers divisible by both 3 and 5.
29. Filter strings with length greater than 5.
30. Filter strings with length equal to a specific value.

### Mapping Operations
31. Convert all strings to uppercase using map.
32. Convert all strings to lowercase using map.
33. Extract the length of each string in a list.
34. Square all numbers in a list.
35. Multiply all numbers by a specific value.
36. Extract specific fields from a list of objects (e.g., get all employee names).
37. Convert a list of strings to a list of their lengths.
38. Convert a list of integers to a list of their squares.
39. Add a prefix to all strings in a list.
40. Add a suffix to all strings in a list.
41. Extract first character from each string.
42. Extract last character from each string.
43. Map integers to their corresponding strings.
44. Map objects to a different type (e.g., Employee to EmployeeDTO).
45. Convert a list of strings to integers.

---

## 3. Sorting

### Basic Sorting
46. Sort a list of integers in ascending order.
47. Sort a list of integers in descending order.
48. Sort a list of strings in alphabetical order.
49. Sort a list of strings in reverse alphabetical order.
50. Sort a list of strings by their length (ascending).
51. Sort a list of strings by their length (descending).
52. Sort a list ignoring case sensitivity.
53. Sort a list with custom comparator.

### Object Sorting
54. Sort a list of Employee objects by salary in ascending order.
55. Sort a list of Employee objects by salary in descending order.
56. Sort a list of Employee objects by name.
57. Sort a list of Employee objects by age.
58. Sort a list of Employee objects by multiple fields (e.g., department then salary).
59. Sort a list of Employee objects by joining date.
60. Sort and then reverse the order.

---

## 4. Reduction & Aggregation

### Sum, Min, Max, Average
61. Find the sum of all integers in a list.
62. Find the sum of all even numbers in a list.
63. Find the sum of all odd numbers in a list.
64. Find the product of all numbers in a list.
65. Find the minimum number in a list.
66. Find the maximum number in a list.
67. Find the average of all numbers in a list.
68. Find the sum of squares of all numbers.
69. Find the sum of squares of all even numbers.
70. Calculate the total salary of all employees.

### Reduce Operations
71. Concatenate all strings in a list using reduce.
72. Find the longest string using reduce.
73. Find the shortest string using reduce.
74. Multiply all numbers in a list using reduce.
75. Find the maximum number using reduce.
76. Find the minimum number using reduce.
77. Join all strings with a delimiter using reduce.
78. Calculate factorial using reduce.
79. Implement custom reduction logic.
80. Reduce with initial value vs without initial value.

---

## 5. Collectors - Basic

### toList, toSet, toMap
81. Collect stream elements to a List.
82. Collect stream elements to a Set.
83. Collect stream elements to a specific collection (e.g., TreeSet, LinkedList).
84. Convert a list to a Map with index as key.
85. Convert a list of objects to a Map (e.g., Employee ID as key, Employee as value).
86. Convert a list to a Map handling duplicate keys.
87. Collect to an unmodifiable list.
88. Collect to an unmodifiable set.
89. Collect to an unmodifiable map.
90. Convert stream to array.

### Joining Operations
91. Join all strings in a list with comma separator.
92. Join all strings with a custom delimiter.
93. Join strings with prefix and suffix.
94. Join strings with space separator.
95. Concatenate all strings without separator.

---

## 6. Collectors - GroupingBy

### Basic Grouping
96. Group strings by their length.
97. Group numbers by even/odd.
98. Group employees by department.
99. Group employees by gender.
100. Group employees by age.
101. Group employees by salary range.
102. Group strings by their first character.
103. Group numbers by their remainder when divided by a number.
104. Group employees by city.
105. Group employees by joining year.

### Counting with GroupingBy
106. Count employees in each department.
107. Count strings of each length.
108. Count even and odd numbers.
109. Count male and female employees.
110. Find department with maximum number of employees.
111. Find the frequency of each character in a string.
112. Count occurrences of each element in a list.
113. Find the most frequent element in a list.

### Downstream Collectors with GroupingBy
114. Group employees by department and collect their names.
115. Group employees by department and find average salary.
116. Group employees by department and find total salary.
117. Group employees by department and find maximum salary.
118. Group employees by department and find minimum salary.
119. Group employees by department and count them.
120. Group employees by department and find the highest paid employee.
121. Group employees by department and sort by salary.
122. Group students by grade and find average marks.
123. Group employees by department and collect to Set.
124. Group by multiple levels (nested grouping).

---

## 7. Collectors - Advanced

### PartitioningBy
125. Partition numbers into even and odd using partitioningBy.
126. Partition employees into high earners (>50000) and others.
127. Partition strings into palindromes and non-palindromes.
128. Partition employees by age (above 30 and below 30).
129. Partition products by availability (in stock or out of stock).

### Mapping Collector
130. Group employees by department and map to their names.
131. Group employees by department and map to their salaries.
132. Group strings by length and convert to uppercase.
133. Use mapping collector to transform data after grouping.

### FlatMapping Collector
134. Group employees by department and flatten their skills.
135. Flatten nested lists after grouping.
136. Group orders by customer and flatten line items.
137. Use flatMapping with groupingBy.

### CollectingAndThen
138. Group employees by department and get unmodifiable lists.
139. Find max element and wrap in custom object using collectingAndThen.
140. Calculate average and format result using collectingAndThen.
141. Sort after collecting using collectingAndThen.
142. Find second highest salary in each department.

### Filtering Collector
143. Group employees by department and filter those earning >50000.
144. Use filtering collector with groupingBy to exclude elements.
145. Filter and group in a single operation.

---

## 8. FlatMap Operations

### Basic FlatMap
146. Flatten a list of lists into a single list.
147. Flatten a list of arrays into a single list.
148. Convert a list of strings to a stream of characters.
149. Split strings and flatten the results.
150. Flatten a list of sets into a single list.
151. Flatten Optional values.
152. Flatten nested collections.

### Complex FlatMap Scenarios
153. Flatten a list of Employee lists (from multiple departments).
154. Split sentences into words and flatten.
155. Extract all unique characters from a list of strings.
156. Flatten a list of lists and filter results.
157. Flatten and map in combination.
158. Flatten a stream of streams.
159. Get all unique words from a list of sentences.
160. Flatten map values into a single list.

---

## 9. String Manipulation

### Character Operations
161. Find the first non-repeated character in a string.
162. Find all duplicate characters in a string.
163. Count the frequency of each character in a string.
164. Find the most frequent character in a string.
165. Remove duplicate characters from a string.
166. Check if two strings are anagrams.
167. Reverse each word in a sentence.
168. Reverse a string using streams.
169. Check if a string is a palindrome using streams.

### Word Operations
170. Find the longest word in a sentence.
171. Find the shortest word in a sentence.
172. Count the number of words in a sentence.
173. Count vowels in a string.
174. Count consonants in a string.
175. Find all palindromic words in a sentence.
176. Capitalize the first letter of each word.
177. Convert string to title case.
178. Remove all whitespace from a string.
179. Find words with a specific length.
180. Find words starting with a vowel.

---

## 10. Finding & Matching

### Find Operations
181. Find the first element in a stream.
182. Find any element in a parallel stream.
183. Find the first even number in a list.
184. Find the first string starting with 'A'.
185. Find the first employee with salary > 50000.
186. Find the first element greater than 100.
187. Find the last element in a stream.
188. Find the nth element in a stream.

### Matching Operations
189. Check if any element matches a condition (anyMatch).
190. Check if all elements match a condition (allMatch).
191. Check if no element matches a condition (noneMatch).
192. Check if any string contains a specific substring.
193. Check if all numbers are positive.
194. Check if all strings are non-empty.
195. Check if any employee salary is above 100000.
196. Check if all employees are adults (age >= 18).
197. Check if no employee has zero salary.
198. Check if any number is prime.

---

## 11. Distinct & Unique Elements

### Distinct Operations
199. Remove duplicate elements from a list.
200. Get distinct numbers from a list.
201. Get distinct strings (case-insensitive).
202. Find duplicate elements in a list.
203. Find all unique elements (appearing only once).
204. Get distinct employee names.
205. Remove duplicate objects based on a property.
206. Find elements appearing more than once.

### Set Operations
207. Find the intersection of two lists.
208. Find the union of two lists.
209. Find elements in list1 but not in list2.
210. Find common elements between two lists.
211. Combine two lists and remove duplicates.
212. Find symmetric difference between two sets.

---

## 12. Parallel Streams

### Parallel Processing
213. Calculate sum using parallel streams.
214. Find max element using parallel stream.
215. Filter and collect using parallel stream.
216. Sort a large list using parallel stream.
217. Process large dataset in parallel.
218. Compare performance: sequential vs parallel stream.
219. Use parallelStream() for CPU-intensive operations.
220. When to use parallel streams and when not to.
221. Handle thread safety in parallel streams.
222. Understand parallel stream performance implications.

---

## 13. Employee Object Operations

### Basic Employee Operations
223. Get list of all employee names.
224. Get list of all employee IDs.
225. Filter employees by department.
226. Filter employees by age greater than 30.
227. Filter employees by salary greater than 50000.
228. Filter employees by gender.
229. Filter employees who joined after a specific year.
230. Filter employees with age between 25 and 35.
231. Get distinct department names.
232. Count total number of employees.

### Employee Salary Operations
233. Find the highest paid employee.
234. Find the lowest paid employee.
235. Find the second highest salary.
236. Find the nth highest salary.
237. Find employees with salary above average.
238. Find employees with salary below average.
239. Calculate total salary of all employees.
240. Calculate average salary of all employees.
241. Find the salary range (min to max).

### Department-wise Operations
242. Group employees by department.
243. Count employees in each department.
244. Find department with maximum employees.
245. Find department with minimum employees.
246. Find average salary per department.
247. Find total salary per department.
248. Find highest paid employee in each department.
249. Find lowest paid employee in each department.
250. Find second highest paid employee in each department.
251. Sort employees by salary within each department.
252. List employee names grouped by department.

### Gender-based Operations
253. Count male and female employees.
254. Find average age of male and female employees.
255. Find average salary of male and female employees.
256. Find highest paid male employee.
257. Find highest paid female employee.
258. Group employees by gender.
259. Find the youngest male employee.
260. Find the youngest female employee.
261. Find the oldest employee in the organization.
262. Find the youngest employee in the organization.

### Advanced Employee Queries
263. Find employees whose name starts with a specific letter.
264. Find employees with age less than 30 in HR department.
265. Find the most senior employee (earliest joining date).
266. Find employees who joined in a specific year.
267. Get top N highest paid employees.
268. Get employee with maximum age in each department.
269. Find departments where average salary > 60000.
270. Find employees in multiple departments.
271. Find employees whose salary is in top 10%.
272. Create a salary increment report (increase by 10%).
273. Find employee with maximum experience.
274. List all unique cities where employees are located.
275. Find employees located in a specific city and sort by name.

---

## 14. Map & Entry Operations

### Map Creation & Manipulation
276. Convert list to map with custom key-value.
277. Create a frequency map from a list.
278. Merge two maps using streams.
279. Filter map entries based on key.
280. Filter map entries based on value.
281. Convert map keys to uppercase.
282. Convert map values to uppercase.
283. Swap keys and values in a map.
284. Sort map by keys.
285. Sort map by values.
286. Find the entry with maximum value in a map.
287. Find the entry with minimum value in a map.
288. Sum all values in a map.
289. Get top N entries from a map based on values.

### Map to List Conversions
290. Convert map to list of "key=value" strings.
291. Convert map entries to list of custom objects.
292. Extract all keys from map as a list.
293. Extract all values from map as a list.
294. Filter map and collect to list.

---

## 15. Array & List Conversions

### Array Operations
295. Convert array to list using streams.
296. Convert array to set using streams.
297. Filter array elements using streams.
298. Sort an array using streams.
299. Find max element in an array using streams.
300. Find min element in an array using streams.
301. Convert primitive array to list.
302. Convert list to primitive array.
303. Find sum of array elements.
304. Find average of array elements.

### IntStream, LongStream, DoubleStream
305. Create IntStream from range.
306. Use IntStream to generate numbers.
307. Convert IntStream to List.
308. Use mapToInt for primitive operations.
309. Use mapToDouble for decimal operations.
310. Calculate sum using IntStream.
311. Find max using IntStream.
312. Use summaryStatistics with IntStream.

---

## 16. Optional Operations

### Optional Handling
313. Use Optional.of() vs Optional.ofNullable().
314. Get value from Optional or provide default.
315. Use orElse() vs orElseGet().
316. Use orElseThrow() to throw exception.
317. Check if Optional is present.
318. Filter Optional values.
319. Map Optional values.
320. FlatMap with Optional.
321. Chain multiple Optional operations.
322. Convert null to Optional and handle gracefully.

---

## 17. Partitioning

### Partition Operations
323. Partition list into two groups based on condition.
324. Partition employees into juniors and seniors based on age.
325. Partition products into expensive and cheap.
326. Partition numbers into positive and negative.
327. Get counts of both partitions.
328. Process both partitions separately.

---

## 18. Statistical Operations

### Summary Statistics
329. Get summary statistics for a list of integers.
330. Calculate count, sum, min, max, and average in one operation.
331. Get statistics for employee salaries.
332. Use DoubleSummaryStatistics.
333. Use IntSummaryStatistics.
334. Use LongSummaryStatistics.
335. Get statistics per group (e.g., per department).

---

## 19. File Operations with Streams

### Reading Files
336. Read all lines from a file using streams.
337. Count number of lines in a file.
338. Find lines containing a specific word.
339. Count unique words in a file.
340. Find the longest line in a file.
341. Convert file content to uppercase.
342. Filter empty lines from a file.
343. Count occurrences of a word in a file.

### CSV Processing
344. Read and parse CSV file using streams.
345. Filter rows in CSV based on condition.
346. Group CSV data by a column.
347. Calculate aggregate statistics from CSV.
348. Convert CSV to list of objects.
349. Extract specific columns from CSV.

---

## 20. Advanced & Complex Scenarios

### Complex Combinations
350. Find pairs of numbers from a list that sum to a specific value.
351. Find all permutations using streams.
352. Find combinations of elements.
353. Implement custom collector.
354. Chain multiple stream operations.
355. Use peek() for debugging streams.
356. Limit and skip operations.
357. Create infinite streams and control them.

### Real-world Scenarios
358. Process JSON data using streams.
359. Handle exceptions in stream operations.
360. Convert between different date formats using streams.
361. Validate data using streams.
362. Implement caching with streams.
363. Batch process elements (e.g., process 100 at a time).
364. Compare two lists and find differences.
365. Implement pagination using streams.

### Performance & Optimization
366. When to use sequential vs parallel streams.
367. Avoid using streams for small collections.
368. Understand laziness in streams.
369. Avoid stateful operations in parallel streams.
370. Profile stream performance.
371. Optimize groupingBy operations.
372. Understand cost of boxing/unboxing.

### Multi-level Grouping
373. Group by department and then by gender.
374. Group by city, then by department.
375. Multi-level grouping with counting.
376. Multi-level grouping with averaging.
377. Create nested maps using groupingBy.
378. Group employees by department, city, and gender.

### Custom Object Scenarios
379. Filter products by category and price range.
380. Find top-selling products.
381. Calculate order totals.
382. Group orders by customer.
383. Find customers with most orders.
384. Calculate customer lifetime value.
385. Find students with highest marks.
386. Group students by grade and subject.
387. Calculate class averages.
388. Find students passing all subjects.

### Date & Time Operations
389. Filter dates in a range.
390. Group events by month.
391. Find the earliest and latest date.
392. Calculate duration between dates.
393. Filter weekend dates.
394. Group transactions by day/month/year.

### Stream of Streams
395. Flatten stream of streams.
396. Process nested collections.
397. Combine multiple streams.
398. Merge and deduplicate streams.

### Error Handling
399. Handle exceptions gracefully in stream pipelines.
400. Use try-catch inside stream operations.
401. Filter out elements that cause exceptions.
402. Wrap checked exceptions in unchecked exceptions.

### Stream Best Practices
403. Avoid modifying source during stream operations.
404. Understand terminal vs intermediate operations.
405. Know when streams can be reused (they can't).
406. Use method references where possible.
407. Prefer collection over reduce when appropriate.
408. Use specialized streams (IntStream) for primitives.
409. Avoid forEach for non-side-effect operations.
410. Understand short-circuiting operations.

### Tricky Scenarios
411. Handle null elements in streams.
412. Work with empty streams.
413. Difference between findFirst() and findAny().
414. Understanding of lazy evaluation.
415. Side effects in stream operations.
416. Stateless vs stateful operations.
417. Order of operations matters.
418. When distinct() should be used.
419. Performance implications of sorted().
420. Understanding collectors composition.

---

## Additional Challenge Questions

### Mixed Operations
421. Find employees with second highest salary per department.
422. Find the nth element without using skip.
423. Implement running sum using streams.
424. Find missing numbers in a sequence.
425. Rotate a list using streams.
426. Implement custom sorting logic.
427. Find elements at even indices.
428. Find elements at odd indices.
429. Chunk a list into sublists of size N.
430. Implement zip operation (combine two lists).

### String Challenges
431. Remove all special characters from strings.
432. Find the longest common prefix.
433. Group anagrams together.
434. Sort strings by number of vowels.
435. Find strings with unique characters only.
436. Implement string compression.
437. Check if strings are rotations of each other.
438. Find all substrings of a string.

### Number Challenges
439. Find prime numbers in a range.
440. Generate Fibonacci sequence using streams.
441. Find Armstrong numbers.
442. Check if a number is perfect number.
443. Find GCD of numbers in a list.
444. Find LCM of numbers in a list.
445. Convert decimal to binary using streams.
446. Find factors of a number.
447. Check if numbers form an arithmetic sequence.
448. Check if numbers form a geometric sequence.

### Collection Challenges
449. Rotate elements in a list by K positions.
450. Find the kth largest element.
451. Find the kth smallest element.
452. Implement sliding window operations.
453. Find majority element (appearing > n/2 times).
454. Find all triplets that sum to zero.
455. Implement custom partitioning logic.
456. Find longest consecutive sequence.
457. Implement LRU cache operations using streams.
458. Find equilibrium index of an array.

### Advanced Employee Questions
459. Find employees with duplicate names.
460. Find department with highest average salary.
461. Find employees earning more than their department average.
462. Find employees earning less than their department average.
463. Calculate salary percentile for each employee.
464. Find employees with same salary in different departments.
465. Get a map of salary ranges and employee counts.
466. Find employees who are in top 25% salary bracket.
467. Create a report of department-wise gender distribution.
468. Find correlation between age and salary.
469. Identify salary outliers.
470. Find employees with longest tenure.

### Stream Internals & Theory
471. Explain how peek() works vs forEach().
472. Why can't streams be reused?
473. Difference between Collection.stream() and Arrays.stream().
474. How does parallel stream split the work?
475. What is spliterator and how does it work?
476. Explain the stream pipeline execution.
477. What are characteristics of a collector?
478. How does groupingBy work internally?
479. Explain combiner function in reduce.
480. What is the difference between reduce and collect?

### Real Interview Scenarios
481. Given a sentence, find all words with length > 5 and convert to uppercase.
482. From a list of transactions, find total amount per category.
483. Find the 3 most expensive products.
484. Calculate moving average of stock prices.
485. Find employees who report to the same manager.
486. Implement a simple recommendation system using streams.
487. Process and aggregate sensor data.
488. Find peak hours from timestamp data.
489. Analyze log files for error patterns.
490. Calculate customer churn rate.

### Edge Cases & Corner Cases
491. Handle empty collections.
492. Handle single-element collections.
493. Handle very large collections.
494. Deal with null elements in streams.
495. Handle concurrent modifications.
496. Process infinite streams safely.
497. Handle streams with all identical elements.
498. Work with streams containing only nulls.
499. Process interleaved data streams.
500. Handle streams with irregular data patterns.

---

## End of Questions

**Note:** This comprehensive list contains **500+ most frequently asked and important Java Stream API coding interview questions** covering all major topics and scenarios.

### Tips for Mastering Stream API:

1. **Understand the Basics First**
   - Know the difference between intermediate and terminal operations
   - Understand lazy evaluation
   - Learn when to use which operation

2. **Practice Regularly**
   - Solve at least 5-10 questions daily
   - Start with basic and move to complex scenarios
   - Practice with real-world data

3. **Learn Common Patterns**
   - Filtering → Mapping → Collecting
   - GroupingBy with downstream collectors
   - FlatMap for nested structures
   - Reduce for aggregations

4. **Focus on These Key Areas**
   - Collectors (groupingBy, partitioningBy, mapping)
   - FlatMap operations
   - Employee/Object operations (most common in interviews)
   - Map and Entry manipulations
   - String operations

5. **Common Interview Topics**
   - Employee salary/department operations (80% of interviews)
   - String manipulation (character/word frequency)
   - List operations (sum, average, max, min)
   - Grouping and partitioning
   - Finding duplicates and unique elements

6. **Best Practices**
   - Use method references when possible
   - Prefer specialized streams (IntStream) for primitives
   - Understand when to use parallel streams
   - Know the performance implications
   - Write readable code with proper formatting

7. **Common Mistakes to Avoid**
   - Reusing streams (they can't be reused)
   - Side effects in stream operations
   - Unnecessary boxing/unboxing
   - Using forEach for transformations
   - Not understanding short-circuiting

8. **Advanced Topics to Master**
   - Custom collectors
   - Complex groupingBy with multiple downstream collectors
   - Combining multiple collectors
   - Performance optimization
   - Parallel stream considerations

### Interview Preparation Strategy:

**Week 1-2: Basics**
- Questions 1-150 (Basic operations, filtering, mapping, sorting)
- Focus on understanding core concepts

**Week 3-4: Intermediate**
- Questions 151-300 (Collectors, groupingBy, flatMap)
- Practice Employee object questions extensively

**Week 5-6: Advanced**
- Questions 301-450 (Complex scenarios, file operations, advanced grouping)
- Real-world problem solving

**Week 7-8: Expert**
- Questions 451-500 (Challenging problems, optimization, edge cases)
- Mock interviews and timed practice

### Most Frequently Asked in Interviews:
1. Employee operations (salary, department, gender-based queries) - **Very High**
2. String character/word frequency - **Very High**
3. Find duplicates/unique elements - **High**
4. GroupingBy operations - **High**
5. Sorting and finding nth highest/lowest - **High**
6. List operations (sum, average, max, min) - **Medium**
7. FlatMap scenarios - **Medium**
8. Map operations - **Medium**

### Resources to Practice:
- LeetCode (Java Stream problems)
- HackerRank (Functional Programming section)
- Practice with real datasets
- Build mini-projects using streams
- Code review and optimization exercises

**Good luck with your Java Stream API interview preparation!**
