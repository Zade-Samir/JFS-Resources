# Java Stream API Coding Interview Questions — Part 3 (Q201–Q300)

> **Series:** Part 3 of 5 | Questions 201–300
> **Topics:** Distinct & Unique Elements (continued), Parallel Streams, Employee Object Operations, Map & Entry Operations, Array & List Conversions (Q295–Q300 start)

---

## 11. Distinct & Unique Elements *(continued)*

### Distinct Operations *(continued)*

**Q201. Get distinct strings (case-insensitive).**

```java
List<String> names = Arrays.asList("Alice", "alice", "BOB", "bob", "Charlie");
List<String> distinct = names.stream()
                             .map(String::toLowerCase)
                             .distinct()
                             .collect(Collectors.toList());
// [alice, bob, charlie]
```

---

**Q202. Find duplicate elements in a list.**

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 2, 4, 3, 5);
Set<Integer> seen = new HashSet<>();
List<Integer> duplicates = numbers.stream()
                                  .filter(n -> !seen.add(n))
                                  .collect(Collectors.toList());
// [2, 3]
```

---

**Q203. Find all unique elements (appearing only once).**

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 2, 4, 3, 5);
Map<Integer, Long> freq = numbers.stream()
    .collect(Collectors.groupingBy(n -> n, Collectors.counting()));

List<Integer> unique = freq.entrySet().stream()
    .filter(e -> e.getValue() == 1)
    .map(e -> e.getKey())
    .collect(Collectors.toList());
// [1, 4, 5]
```

---

**Q204. Get distinct employee names.**

```java
List<String> distinctNames = employees.stream()
                                      .map(Employee::getName)
                                      .distinct()
                                      .collect(Collectors.toList());
```

---

**Q205. Remove duplicate objects based on a property.**

```java
// Remove duplicate employees based on name
Map<String, Employee> seen = new LinkedHashMap<>();
List<Employee> distinct = employees.stream()
    .filter(e -> seen.putIfAbsent(e.getName(), e) == null)
    .collect(Collectors.toList());
```

---

**Q206. Find elements appearing more than once.**

```java
List<String> names = Arrays.asList("Alice", "Bob", "Alice", "Charlie", "Bob");
List<String> moreThanOnce = names.stream()
    .collect(Collectors.groupingBy(s -> s, Collectors.counting()))
    .entrySet().stream()
    .filter(e -> e.getValue() > 1)
    .map(e -> e.getKey())
    .collect(Collectors.toList());
// [Alice, Bob]
```

---

### Set Operations

**Q207. Find the intersection of two lists.**

```java
List<Integer> list1 = Arrays.asList(1, 2, 3, 4, 5);
List<Integer> list2 = Arrays.asList(3, 4, 5, 6, 7);
List<Integer> intersection = list1.stream()
                                  .filter(list2::contains)
                                  .collect(Collectors.toList());
// [3, 4, 5]
```

---

**Q208. Find the union of two lists.**

```java
List<Integer> list1 = Arrays.asList(1, 2, 3, 4);
List<Integer> list2 = Arrays.asList(3, 4, 5, 6);
List<Integer> union = Stream.concat(list1.stream(), list2.stream())
                            .distinct()
                            .collect(Collectors.toList());
// [1, 2, 3, 4, 5, 6]
```

---

**Q209. Find elements in list1 but not in list2.**

```java
List<Integer> list1 = Arrays.asList(1, 2, 3, 4, 5);
List<Integer> list2 = Arrays.asList(3, 4, 5, 6, 7);
List<Integer> diff = list1.stream()
                          .filter(n -> !list2.contains(n))
                          .collect(Collectors.toList());
// [1, 2]
```

---

**Q210. Find common elements between two lists.**

```java
List<String> list1 = Arrays.asList("Alice", "Bob", "Charlie");
List<String> list2 = Arrays.asList("Bob", "David", "Alice");
List<String> common = list1.stream()
                           .filter(list2::contains)
                           .collect(Collectors.toList());
// [Alice, Bob]
```

---

**Q211. Combine two lists and remove duplicates.**

```java
List<Integer> list1 = Arrays.asList(1, 2, 3);
List<Integer> list2 = Arrays.asList(2, 3, 4, 5);
List<Integer> combined = Stream.concat(list1.stream(), list2.stream())
                               .distinct()
                               .collect(Collectors.toList());
// [1, 2, 3, 4, 5]
```

---

**Q212. Find symmetric difference between two sets.**

```java
List<Integer> list1 = Arrays.asList(1, 2, 3, 4, 5);
List<Integer> list2 = Arrays.asList(3, 4, 5, 6, 7);

// Elements in one list but not the other
List<Integer> symDiff = Stream.concat(
    list1.stream().filter(n -> !list2.contains(n)),
    list2.stream().filter(n -> !list1.contains(n))
).collect(Collectors.toList());
// [1, 2, 6, 7]
```

---

## 12. Parallel Streams

**Q213. Calculate sum using parallel streams.**

```java
List<Integer> numbers = IntStream.rangeClosed(1, 1000).boxed().collect(Collectors.toList());
int sum = numbers.parallelStream()
                 .mapToInt(n -> n)
                 .sum();
System.out.println(sum); // 500500
```

---

**Q214. Find max element using parallel stream.**

```java
List<Integer> numbers = Arrays.asList(3, 7, 1, 9, 4, 6, 8);
Optional<Integer> max = numbers.parallelStream()
                               .max(Integer::compareTo);
System.out.println(max.get()); // 9
```

---

**Q215. Filter and collect using parallel stream.**

```java
List<Integer> numbers = IntStream.rangeClosed(1, 100).boxed().collect(Collectors.toList());
List<Integer> evens = numbers.parallelStream()
                             .filter(n -> n % 2 == 0)
                             .collect(Collectors.toList());
```

---

**Q216. Sort a large list using parallel stream.**

```java
List<Integer> numbers = IntStream.rangeClosed(1, 10000)
                                 .boxed()
                                 .collect(Collectors.toList());
Collections.shuffle(numbers);
List<Integer> sorted = numbers.parallelStream()
                              .sorted()
                              .collect(Collectors.toList());
```

---

**Q217. Process large dataset in parallel.**

```java
// Process 1 million records in parallel
List<Employee> result = largeEmployeeList.parallelStream()
                                         .filter(e -> e.getSalary() > 50000)
                                         .map(e -> { e.setSalary(e.getSalary() * 1.1); return e; })
                                         .collect(Collectors.toList());
```

---

**Q218. Compare performance: sequential vs parallel stream.**

```java
List<Integer> numbers = IntStream.rangeClosed(1, 10_000_000).boxed().collect(Collectors.toList());

long seqStart = System.currentTimeMillis();
long seqSum = numbers.stream().mapToLong(Integer::longValue).sum();
long seqTime = System.currentTimeMillis() - seqStart;

long parStart = System.currentTimeMillis();
long parSum = numbers.parallelStream().mapToLong(Integer::longValue).sum();
long parTime = System.currentTimeMillis() - parStart;

System.out.println("Sequential: " + seqTime + "ms, Parallel: " + parTime + "ms");
```

---

**Q219. Use parallelStream() for CPU-intensive operations.**

```java
// Compute sum of squares for large list
long result = LongStream.rangeClosed(1, 1_000_000)
                        .parallel()
                        .map(n -> n * n)
                        .sum();
System.out.println(result);
```

---

**Q220. When to use parallel streams and when not to.**

```java
// Use parallel for large datasets and CPU-heavy work
List<Integer> largeLst = IntStream.range(0, 1_000_000).boxed().collect(Collectors.toList());
long count = largeLst.parallelStream().filter(n -> isPrime(n)).count();

// Avoid parallel for small collections (overhead > benefit)
List<Integer> smallList = Arrays.asList(1, 2, 3, 4, 5);
int sum = smallList.stream().mapToInt(n -> n).sum(); // use sequential here
```

---

**Q221. Handle thread safety in parallel streams.**

```java
// WRONG — not thread-safe:
List<Integer> results = new ArrayList<>();
numbers.parallelStream().forEach(n -> results.add(n)); // race condition!

// CORRECT — use thread-safe collector:
List<Integer> safeResults = numbers.parallelStream()
                                   .filter(n -> n % 2 == 0)
                                   .collect(Collectors.toList()); // Collectors.toList() is thread-safe
```

---

**Q222. Understand parallel stream performance implications.**

```java
// Parallel streams split data using Spliterator
// Best for: ArrayList, arrays (random access)
// Worse for: LinkedList (sequential access)

// Good candidate:
List<Integer> arrayList = new ArrayList<>(largeLst);
long sumA = arrayList.parallelStream().mapToLong(n -> n).sum();

// Poor candidate:
LinkedList<Integer> linkedList = new LinkedList<>(largeLst);
long sumL = linkedList.parallelStream().mapToLong(n -> n).sum(); // slower due to poor splitting
```

---

## 13. Employee Object Operations

### Basic Employee Operations

**Q223. Get list of all employee names.**

```java
List<String> names = employees.stream()
                              .map(Employee::getName)
                              .collect(Collectors.toList());
```

---

**Q224. Get list of all employee IDs.**

```java
List<Integer> ids = employees.stream()
                             .map(Employee::getId)
                             .collect(Collectors.toList());
```

---

**Q225. Filter employees by department.**

```java
List<Employee> itEmployees = employees.stream()
                                      .filter(e -> e.getDept().equals("IT"))
                                      .collect(Collectors.toList());
```

---

**Q226. Filter employees by age greater than 30.**

```java
List<Employee> result = employees.stream()
                                 .filter(e -> e.getAge() > 30)
                                 .collect(Collectors.toList());
```

---

**Q227. Filter employees by salary greater than 50000.**

```java
List<Employee> result = employees.stream()
                                 .filter(e -> e.getSalary() > 50000)
                                 .collect(Collectors.toList());
```

---

**Q228. Filter employees by gender.**

```java
List<Employee> females = employees.stream()
                                  .filter(e -> e.getGender().equals("Female"))
                                  .collect(Collectors.toList());
```

---

**Q229. Filter employees who joined after a specific year.**

```java
List<Employee> result = employees.stream()
                                 .filter(e -> e.getJoiningDate().getYear() > 2018)
                                 .collect(Collectors.toList());
```

---

**Q230. Filter employees with age between 25 and 35.**

```java
List<Employee> result = employees.stream()
                                 .filter(e -> e.getAge() >= 25 && e.getAge() <= 35)
                                 .collect(Collectors.toList());
```

---

**Q231. Get distinct department names.**

```java
List<String> depts = employees.stream()
                              .map(Employee::getDept)
                              .distinct()
                              .collect(Collectors.toList());
```

---

**Q232. Count total number of employees.**

```java
long count = employees.stream().count();
System.out.println(count);
```

---

### Employee Salary Operations

**Q233. Find the highest paid employee.**

```java
Optional<Employee> highest = employees.stream()
    .max(Comparator.comparingDouble(Employee::getSalary));
highest.ifPresent(e -> System.out.println(e.getName()));
```

---

**Q234. Find the lowest paid employee.**

```java
Optional<Employee> lowest = employees.stream()
    .min(Comparator.comparingDouble(Employee::getSalary));
lowest.ifPresent(e -> System.out.println(e.getName()));
```

---

**Q235. Find the second highest salary.**

```java
Optional<Double> secondHighest = employees.stream()
    .map(Employee::getSalary)
    .distinct()
    .sorted(Collections.reverseOrder())
    .skip(1)
    .findFirst();
System.out.println(secondHighest.orElse(0.0));
```

---

**Q236. Find the nth highest salary.**

```java
int n = 3;
Optional<Double> nthHighest = employees.stream()
    .map(Employee::getSalary)
    .distinct()
    .sorted(Collections.reverseOrder())
    .skip(n - 1)
    .findFirst();
System.out.println(nthHighest.orElse(0.0));
```

---

**Q237. Find employees with salary above average.**

```java
double avg = employees.stream()
                      .mapToDouble(Employee::getSalary)
                      .average()
                      .orElse(0.0);

List<Employee> aboveAvg = employees.stream()
                                   .filter(e -> e.getSalary() > avg)
                                   .collect(Collectors.toList());
```

---

**Q238. Find employees with salary below average.**

```java
double avg = employees.stream()
                      .mapToDouble(Employee::getSalary)
                      .average()
                      .orElse(0.0);

List<Employee> belowAvg = employees.stream()
                                   .filter(e -> e.getSalary() < avg)
                                   .collect(Collectors.toList());
```

---

**Q239. Calculate total salary of all employees.**

```java
double totalSalary = employees.stream()
                              .mapToDouble(Employee::getSalary)
                              .sum();
System.out.println(totalSalary);
```

---

**Q240. Calculate average salary of all employees.**

```java
OptionalDouble avg = employees.stream()
                              .mapToDouble(Employee::getSalary)
                              .average();
System.out.println(avg.orElse(0.0));
```

---

**Q241. Find the salary range (min to max).**

```java
DoubleSummaryStatistics stats = employees.stream()
                                         .mapToDouble(Employee::getSalary)
                                         .summaryStatistics();
System.out.println("Min: " + stats.getMin() + ", Max: " + stats.getMax());
```

---

### Department-wise Operations

**Q242. Group employees by department.**

```java
Map<String, List<Employee>> byDept = employees.stream()
                                              .collect(Collectors.groupingBy(Employee::getDept));
```

---

**Q243. Count employees in each department.**

```java
Map<String, Long> count = employees.stream()
    .collect(Collectors.groupingBy(Employee::getDept, Collectors.counting()));
```

---

**Q244. Find department with maximum employees.**

```java
String maxDept = employees.stream()
    .collect(Collectors.groupingBy(Employee::getDept, Collectors.counting()))
    .entrySet().stream()
    .max((a, b) -> Long.compare(a.getValue(), b.getValue()))
    .map(Map.Entry::getKey)
    .orElse("None");
```

---

**Q245. Find department with minimum employees.**

```java
String minDept = employees.stream()
    .collect(Collectors.groupingBy(Employee::getDept, Collectors.counting()))
    .entrySet().stream()
    .min((a, b) -> Long.compare(a.getValue(), b.getValue()))
    .map(Map.Entry::getKey)
    .orElse("None");
```

---

**Q246. Find average salary per department.**

```java
Map<String, Double> avgByDept = employees.stream()
    .collect(Collectors.groupingBy(Employee::getDept,
             Collectors.averagingDouble(Employee::getSalary)));
```

---

**Q247. Find total salary per department.**

```java
Map<String, Double> totalByDept = employees.stream()
    .collect(Collectors.groupingBy(Employee::getDept,
             Collectors.summingDouble(Employee::getSalary)));
```

---

**Q248. Find highest paid employee in each department.**

```java
Map<String, Optional<Employee>> highestByDept = employees.stream()
    .collect(Collectors.groupingBy(Employee::getDept,
             Collectors.maxBy(Comparator.comparingDouble(Employee::getSalary))));
```

---

**Q249. Find lowest paid employee in each department.**

```java
Map<String, Optional<Employee>> lowestByDept = employees.stream()
    .collect(Collectors.groupingBy(Employee::getDept,
             Collectors.minBy(Comparator.comparingDouble(Employee::getSalary))));
```

---

**Q250. Find second highest paid employee in each department.**

```java
Map<String, Optional<Employee>> result = employees.stream()
    .collect(Collectors.groupingBy(
        Employee::getDept,
        Collectors.collectingAndThen(
            Collectors.toList(),
            list -> list.stream()
                        .sorted(Comparator.comparingDouble(Employee::getSalary).reversed())
                        .skip(1)
                        .findFirst()
        )
    ));
```

---

**Q251. Sort employees by salary within each department.**

```java
Map<String, List<Employee>> sorted = employees.stream()
    .collect(Collectors.groupingBy(
        Employee::getDept,
        Collectors.collectingAndThen(
            Collectors.toList(),
            list -> list.stream()
                        .sorted(Comparator.comparingDouble(Employee::getSalary))
                        .collect(Collectors.toList())
        )
    ));
```

---

**Q252. List employee names grouped by department.**

```java
Map<String, List<String>> namesByDept = employees.stream()
    .collect(Collectors.groupingBy(
        Employee::getDept,
        Collectors.mapping(Employee::getName, Collectors.toList())
    ));
```

---

### Gender-based Operations

**Q253. Count male and female employees.**

```java
Map<String, Long> countByGender = employees.stream()
    .collect(Collectors.groupingBy(Employee::getGender, Collectors.counting()));
```

---

**Q254. Find average age of male and female employees.**

```java
Map<String, Double> avgAgeByGender = employees.stream()
    .collect(Collectors.groupingBy(Employee::getGender,
             Collectors.averagingInt(Employee::getAge)));
```

---

**Q255. Find average salary of male and female employees.**

```java
Map<String, Double> avgSalaryByGender = employees.stream()
    .collect(Collectors.groupingBy(Employee::getGender,
             Collectors.averagingDouble(Employee::getSalary)));
```

---

**Q256. Find highest paid male employee.**

```java
Optional<Employee> highestMale = employees.stream()
    .filter(e -> e.getGender().equals("Male"))
    .max(Comparator.comparingDouble(Employee::getSalary));
```

---

**Q257. Find highest paid female employee.**

```java
Optional<Employee> highestFemale = employees.stream()
    .filter(e -> e.getGender().equals("Female"))
    .max(Comparator.comparingDouble(Employee::getSalary));
```

---

**Q258. Group employees by gender.**

```java
Map<String, List<Employee>> byGender = employees.stream()
    .collect(Collectors.groupingBy(Employee::getGender));
```

---

**Q259. Find the youngest male employee.**

```java
Optional<Employee> youngestMale = employees.stream()
    .filter(e -> e.getGender().equals("Male"))
    .min(Comparator.comparingInt(Employee::getAge));
```

---

**Q260. Find the youngest female employee.**

```java
Optional<Employee> youngestFemale = employees.stream()
    .filter(e -> e.getGender().equals("Female"))
    .min(Comparator.comparingInt(Employee::getAge));
```

---

**Q261. Find the oldest employee in the organization.**

```java
Optional<Employee> oldest = employees.stream()
    .max(Comparator.comparingInt(Employee::getAge));
oldest.ifPresent(e -> System.out.println(e.getName() + " - " + e.getAge()));
```

---

**Q262. Find the youngest employee in the organization.**

```java
Optional<Employee> youngest = employees.stream()
    .min(Comparator.comparingInt(Employee::getAge));
youngest.ifPresent(e -> System.out.println(e.getName() + " - " + e.getAge()));
```

---

### Advanced Employee Queries

**Q263. Find employees whose name starts with a specific letter.**

```java
List<Employee> result = employees.stream()
    .filter(e -> e.getName().startsWith("A"))
    .collect(Collectors.toList());
```

---

**Q264. Find employees with age less than 30 in HR department.**

```java
List<Employee> result = employees.stream()
    .filter(e -> e.getAge() < 30 && e.getDept().equals("HR"))
    .collect(Collectors.toList());
```

---

**Q265. Find the most senior employee (earliest joining date).**

```java
Optional<Employee> mostSenior = employees.stream()
    .min(Comparator.comparing(Employee::getJoiningDate));
mostSenior.ifPresent(e -> System.out.println(e.getName()));
```

---

**Q266. Find employees who joined in a specific year.**

```java
int year = 2020;
List<Employee> result = employees.stream()
    .filter(e -> e.getJoiningDate().getYear() == year)
    .collect(Collectors.toList());
```

---

**Q267. Get top N highest paid employees.**

```java
int n = 3;
List<Employee> topN = employees.stream()
    .sorted(Comparator.comparingDouble(Employee::getSalary).reversed())
    .limit(n)
    .collect(Collectors.toList());
```

---

**Q268. Get employee with maximum age in each department.**

```java
Map<String, Optional<Employee>> result = employees.stream()
    .collect(Collectors.groupingBy(Employee::getDept,
             Collectors.maxBy(Comparator.comparingInt(Employee::getAge))));
```

---

**Q269. Find departments where average salary > 60000.**

```java
List<String> depts = employees.stream()
    .collect(Collectors.groupingBy(Employee::getDept,
             Collectors.averagingDouble(Employee::getSalary)))
    .entrySet().stream()
    .filter(e -> e.getValue() > 60000)
    .map(Map.Entry::getKey)
    .collect(Collectors.toList());
```

---

**Q270. Find employees in multiple departments.**

```java
List<String> targetDepts = Arrays.asList("IT", "Finance");
List<Employee> result = employees.stream()
    .filter(e -> targetDepts.contains(e.getDept()))
    .collect(Collectors.toList());
```

---

**Q271. Find employees whose salary is in top 10%.**

```java
DoubleSummaryStatistics stats = employees.stream()
    .mapToDouble(Employee::getSalary).summaryStatistics();
double threshold = stats.getMax() * 0.90;

List<Employee> top10 = employees.stream()
    .filter(e -> e.getSalary() >= threshold)
    .collect(Collectors.toList());
```

---

**Q272. Create a salary increment report (increase by 10%).**

```java
List<String> report = employees.stream()
    .map(e -> e.getName() + ": " + e.getSalary() + " -> " + (e.getSalary() * 1.10))
    .collect(Collectors.toList());
report.forEach(System.out::println);
```

---

**Q273. Find employee with maximum experience.**

```java
Optional<Employee> mostExperienced = employees.stream()
    .min(Comparator.comparing(Employee::getJoiningDate)); // earliest join = most experience
```

---

**Q274. List all unique cities where employees are located.**

```java
List<String> cities = employees.stream()
    .map(Employee::getCity)
    .distinct()
    .sorted()
    .collect(Collectors.toList());
```

---

**Q275. Find employees located in a specific city and sort by name.**

```java
List<Employee> result = employees.stream()
    .filter(e -> e.getCity().equals("Mumbai"))
    .sorted(Comparator.comparing(Employee::getName))
    .collect(Collectors.toList());
```

---

## 14. Map & Entry Operations

### Map Creation & Manipulation

**Q276. Convert list to map with custom key-value.**

```java
Map<String, Double> nameToSalary = employees.stream()
    .collect(Collectors.toMap(Employee::getName, Employee::getSalary));
```

---

**Q277. Create a frequency map from a list.**

```java
List<String> words = Arrays.asList("apple", "banana", "apple", "cherry", "banana", "apple");
Map<String, Long> freq = words.stream()
    .collect(Collectors.groupingBy(s -> s, Collectors.counting()));
// {apple=3, banana=2, cherry=1}
```

---

**Q278. Merge two maps using streams.**

```java
Map<String, Integer> map1 = Map.of("a", 1, "b", 2);
Map<String, Integer> map2 = Map.of("b", 3, "c", 4);

Map<String, Integer> merged = Stream.concat(map1.entrySet().stream(), map2.entrySet().stream())
    .collect(Collectors.toMap(
        Map.Entry::getKey,
        Map.Entry::getValue,
        (v1, v2) -> v1 + v2 // merge strategy: sum values
    ));
// {a=1, b=5, c=4}
```

---

**Q279. Filter map entries based on key.**

```java
Map<String, Integer> map = Map.of("Alice", 1, "Bob", 2, "Anna", 3);
Map<String, Integer> result = map.entrySet().stream()
    .filter(e -> e.getKey().startsWith("A"))
    .collect(Collectors.toMap(Map.Entry::getKey, Map.Entry::getValue));
// {Alice=1, Anna=3}
```

---

**Q280. Filter map entries based on value.**

```java
Map<String, Integer> salaries = Map.of("Alice", 70000, "Bob", 40000, "Charlie", 90000);
Map<String, Integer> highEarners = salaries.entrySet().stream()
    .filter(e -> e.getValue() > 50000)
    .collect(Collectors.toMap(Map.Entry::getKey, Map.Entry::getValue));
// {Alice=70000, Charlie=90000}
```

---

**Q281. Convert map keys to uppercase.**

```java
Map<String, Integer> map = Map.of("alice", 1, "bob", 2);
Map<String, Integer> result = map.entrySet().stream()
    .collect(Collectors.toMap(
        e -> e.getKey().toUpperCase(),
        Map.Entry::getValue
    ));
// {ALICE=1, BOB=2}
```

---

**Q282. Convert map values to uppercase.**

```java
Map<String, String> map = Map.of("name", "alice", "city", "mumbai");
Map<String, String> result = map.entrySet().stream()
    .collect(Collectors.toMap(
        Map.Entry::getKey,
        e -> e.getValue().toUpperCase()
    ));
```

---

**Q283. Swap keys and values in a map.**

```java
Map<String, Integer> map = Map.of("Alice", 1, "Bob", 2);
Map<Integer, String> swapped = map.entrySet().stream()
    .collect(Collectors.toMap(Map.Entry::getValue, Map.Entry::getKey));
// {1=Alice, 2=Bob}
```

---

**Q284. Sort map by keys.**

```java
Map<String, Integer> map = new HashMap<>(Map.of("Charlie", 3, "Alice", 1, "Bob", 2));
Map<String, Integer> sorted = map.entrySet().stream()
    .sorted(Map.Entry.comparingByKey())
    .collect(Collectors.toMap(
        Map.Entry::getKey,
        Map.Entry::getValue,
        (e1, e2) -> e1,
        LinkedHashMap::new
    ));
```

---

**Q285. Sort map by values.**

```java
Map<String, Integer> map = Map.of("Charlie", 3, "Alice", 1, "Bob", 2);
Map<String, Integer> sorted = map.entrySet().stream()
    .sorted(Map.Entry.comparingByValue())
    .collect(Collectors.toMap(
        Map.Entry::getKey,
        Map.Entry::getValue,
        (e1, e2) -> e1,
        LinkedHashMap::new
    ));
```

---

**Q286. Find the entry with maximum value in a map.**

```java
Map<String, Integer> map = Map.of("Alice", 90, "Bob", 75, "Charlie", 85);
Map.Entry<String, Integer> maxEntry = map.entrySet().stream()
    .max(Map.Entry.comparingByValue())
    .orElseThrow();
System.out.println(maxEntry.getKey() + ": " + maxEntry.getValue()); // Alice: 90
```

---

**Q287. Find the entry with minimum value in a map.**

```java
Map<String, Integer> map = Map.of("Alice", 90, "Bob", 75, "Charlie", 85);
Map.Entry<String, Integer> minEntry = map.entrySet().stream()
    .min(Map.Entry.comparingByValue())
    .orElseThrow();
System.out.println(minEntry.getKey() + ": " + minEntry.getValue()); // Bob: 75
```

---

**Q288. Sum all values in a map.**

```java
Map<String, Integer> map = Map.of("a", 10, "b", 20, "c", 30);
int sum = map.values().stream()
             .mapToInt(Integer::intValue)
             .sum();
System.out.println(sum); // 60
```

---

**Q289. Get top N entries from a map based on values.**

```java
Map<String, Integer> scores = Map.of("Alice", 90, "Bob", 75, "Charlie", 85, "David", 95);
int n = 2;
List<Map.Entry<String, Integer>> topN = scores.entrySet().stream()
    .sorted(Map.Entry.<String, Integer>comparingByValue().reversed())
    .limit(n)
    .collect(Collectors.toList());
// [David=95, Alice=90]
```

---

### Map to List Conversions

**Q290. Convert map to list of "key=value" strings.**

```java
Map<String, Integer> map = Map.of("Alice", 90, "Bob", 75);
List<String> result = map.entrySet().stream()
    .map(e -> e.getKey() + "=" + e.getValue())
    .collect(Collectors.toList());
// [Alice=90, Bob=75]
```

---

**Q291. Convert map entries to list of custom objects.**

```java
Map<String, Double> salaryMap = Map.of("Alice", 70000.0, "Bob", 60000.0);
List<Employee> empList = salaryMap.entrySet().stream()
    .map(e -> new Employee(e.getKey(), e.getValue()))
    .collect(Collectors.toList());
```

---

**Q292. Extract all keys from map as a list.**

```java
Map<String, Integer> map = Map.of("Alice", 1, "Bob", 2, "Charlie", 3);
List<String> keys = new ArrayList<>(map.keySet());
// Or:
List<String> keyList = map.entrySet().stream()
    .map(Map.Entry::getKey)
    .collect(Collectors.toList());
```

---

**Q293. Extract all values from map as a list.**

```java
Map<String, Integer> map = Map.of("Alice", 1, "Bob", 2, "Charlie", 3);
List<Integer> values = map.values().stream()
    .collect(Collectors.toList());
```

---

**Q294. Filter map and collect to list.**

```java
Map<String, Integer> scores = Map.of("Alice", 90, "Bob", 55, "Charlie", 70);
List<String> passed = scores.entrySet().stream()
    .filter(e -> e.getValue() >= 60)
    .map(Map.Entry::getKey)
    .collect(Collectors.toList());
// [Alice, Charlie]
```

---

## 15. Array & List Conversions

### Array Operations

**Q295. Convert array to list using streams.**

```java
String[] arr = {"apple", "banana", "cherry"};
List<String> list = Arrays.stream(arr).collect(Collectors.toList());
```

---

**Q296. Convert array to set using streams.**

```java
String[] arr = {"apple", "banana", "apple", "cherry"};
Set<String> set = Arrays.stream(arr).collect(Collectors.toSet());
// {apple, banana, cherry}
```

---

**Q297. Filter array elements using streams.**

```java
int[] arr = {1, 2, 3, 4, 5, 6};
int[] evens = Arrays.stream(arr)
                    .filter(n -> n % 2 == 0)
                    .toArray();
// [2, 4, 6]
```

---

**Q298. Sort an array using streams.**

```java
int[] arr = {5, 2, 8, 1, 9};
int[] sorted = Arrays.stream(arr).sorted().toArray();
// [1, 2, 5, 8, 9]
```

---

**Q299. Find max element in an array using streams.**

```java
int[] arr = {5, 2, 8, 1, 9};
int max = Arrays.stream(arr).max().getAsInt();
System.out.println(max); // 9
```

---

**Q300. Find min element in an array using streams.**

```java
int[] arr = {5, 2, 8, 1, 9};
int min = Arrays.stream(arr).min().getAsInt();
System.out.println(min); // 1
```

---

> **Previous:** [Part 2 — Q101 to Q200](java-stream-api-questions-part2(Q101-Q200).md)
> **Next:** [Part 4 — Q301 to Q400](java-stream-api-questions-part4(Q301-Q400).md)
