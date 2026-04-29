# Java Stream API Coding Interview Questions — Part 4 (Q301–Q400)

> **Series:** Part 4 of 5 | Questions 301–400
> **Topics:** Array & List Conversions (continued), Optional Operations, Partitioning, Statistical Operations, File Operations with Streams, Advanced & Complex Scenarios

---

## 15. Array & List Conversions *(continued)*

### Array Operations *(continued)*

**Q301. Convert primitive array to list.**

```java
int[] arr = {1, 2, 3, 4, 5};
// Primitive arrays can't be directly collected — use boxed()
List<Integer> list = Arrays.stream(arr)
                           .boxed()
                           .collect(Collectors.toList());
// [1, 2, 3, 4, 5]
```

---

**Q302. Convert list to primitive array.**

```java
List<Integer> list = Arrays.asList(1, 2, 3, 4, 5);
int[] arr = list.stream()
                .mapToInt(Integer::intValue)
                .toArray();
```

---

**Q303. Find sum of array elements.**

```java
int[] arr = {1, 2, 3, 4, 5};
int sum = Arrays.stream(arr).sum();
System.out.println(sum); // 15
```

---

**Q304. Find average of array elements.**

```java
int[] arr = {1, 2, 3, 4, 5};
double avg = Arrays.stream(arr).average().getAsDouble();
System.out.println(avg); // 3.0
```

---

### IntStream, LongStream, DoubleStream

**Q305. Create IntStream from range.**

```java
// rangeClosed includes both endpoints
IntStream.rangeClosed(1, 10).forEach(System.out::println); // 1..10

// range excludes end
IntStream.range(1, 10).forEach(System.out::println); // 1..9
```

---

**Q306. Use IntStream to generate numbers.**

```java
// Generate first 10 even numbers
IntStream.iterate(0, n -> n + 2)
         .limit(10)
         .forEach(System.out::println);
// 0, 2, 4, 6, 8, 10, 12, 14, 16, 18
```

---

**Q307. Convert IntStream to List.**

```java
List<Integer> list = IntStream.rangeClosed(1, 5)
                              .boxed()
                              .collect(Collectors.toList());
// [1, 2, 3, 4, 5]
```

---

**Q308. Use mapToInt for primitive operations.**

```java
List<String> words = Arrays.asList("apple", "banana", "cherry");
int totalChars = words.stream()
                      .mapToInt(String::length)
                      .sum();
System.out.println(totalChars); // 5+6+6 = 17
```

---

**Q309. Use mapToDouble for decimal operations.**

```java
List<Employee> employees = getEmployees();
double avgSalary = employees.stream()
                            .mapToDouble(Employee::getSalary)
                            .average()
                            .orElse(0.0);
```

---

**Q310. Calculate sum using IntStream.**

```java
int sum = IntStream.rangeClosed(1, 100).sum();
System.out.println(sum); // 5050
```

---

**Q311. Find max using IntStream.**

```java
int max = IntStream.of(3, 7, 1, 9, 4).max().getAsInt();
System.out.println(max); // 9
```

---

**Q312. Use summaryStatistics with IntStream.**

```java
IntSummaryStatistics stats = IntStream.of(1, 2, 3, 4, 5).summaryStatistics();
System.out.println("Count: " + stats.getCount());
System.out.println("Sum: " + stats.getSum());
System.out.println("Min: " + stats.getMin());
System.out.println("Max: " + stats.getMax());
System.out.println("Avg: " + stats.getAverage());
```

---

## 16. Optional Operations

**Q313. Use Optional.of() vs Optional.ofNullable().**

```java
// Optional.of() — throws NullPointerException if value is null
Optional<String> opt1 = Optional.of("Hello"); // OK
// Optional.of(null); // throws NPE!

// Optional.ofNullable() — safe with null
Optional<String> opt2 = Optional.ofNullable(null); // Optional.empty
Optional<String> opt3 = Optional.ofNullable("World"); // Optional[World]
```

---

**Q314. Get value from Optional or provide default.**

```java
Optional<String> opt = Optional.ofNullable(null);
String value = opt.orElse("Default Value");
System.out.println(value); // Default Value
```

---

**Q315. Use orElse() vs orElseGet().**

```java
Optional<String> opt = Optional.empty();

// orElse — evaluates the default value EAGERLY
String val1 = opt.orElse("default");

// orElseGet — evaluates the supplier LAZILY (only if empty)
String val2 = opt.orElseGet(() -> "computed default");

// Prefer orElseGet when default computation is expensive
```

---

**Q316. Use orElseThrow() to throw exception.**

```java
Optional<Employee> emp = employees.stream()
    .filter(e -> e.getId() == 999)
    .findFirst();

Employee found = emp.orElseThrow(() -> new RuntimeException("Employee not found"));
```

---

**Q317. Check if Optional is present.**

```java
Optional<String> opt = Optional.ofNullable("Hello");

if (opt.isPresent()) {
    System.out.println(opt.get()); // Hello
}

// Cleaner alternative:
opt.ifPresent(System.out::println);
```

---

**Q318. Filter Optional values.**

```java
Optional<String> opt = Optional.of("Hello World");
Optional<String> filtered = opt.filter(s -> s.contains("World"));
System.out.println(filtered.isPresent()); // true
```

---

**Q319. Map Optional values.**

```java
Optional<String> opt = Optional.of("hello");
Optional<String> upperOpt = opt.map(String::toUpperCase);
System.out.println(upperOpt.get()); // HELLO
```

---

**Q320. FlatMap with Optional.**

```java
Optional<String> opt = Optional.of("hello");
// Use flatMap when the mapping function returns Optional
Optional<String> result = opt.flatMap(s -> s.isEmpty() ? Optional.empty() : Optional.of(s.toUpperCase()));
System.out.println(result.get()); // HELLO
```

---

**Q321. Chain multiple Optional operations.**

```java
Optional<Employee> emp = findEmployeeById(101);
String city = emp.map(Employee::getAddress)
                 .map(Address::getCity)
                 .orElse("Unknown");
System.out.println(city);
```

---

**Q322. Convert null to Optional and handle gracefully.**

```java
String name = null; // could be null
String result = Optional.ofNullable(name)
                        .map(String::toUpperCase)
                        .orElse("NO NAME");
System.out.println(result); // NO NAME
```

---

## 17. Partitioning

**Q323. Partition list into two groups based on condition.**

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8);
Map<Boolean, List<Integer>> partitioned = numbers.stream()
    .collect(Collectors.partitioningBy(n -> n % 2 == 0));
// {true=[2, 4, 6, 8], false=[1, 3, 5, 7]}
```

---

**Q324. Partition employees into juniors and seniors based on age.**

```java
Map<Boolean, List<Employee>> partitioned = employees.stream()
    .collect(Collectors.partitioningBy(e -> e.getAge() >= 30));
List<Employee> seniors = partitioned.get(true);
List<Employee> juniors = partitioned.get(false);
```

---

**Q325. Partition products into expensive and cheap.**

```java
Map<Boolean, List<Product>> partitioned = products.stream()
    .collect(Collectors.partitioningBy(p -> p.getPrice() > 1000));
```

---

**Q326. Partition numbers into positive and negative.**

```java
List<Integer> numbers = Arrays.asList(-3, -1, 0, 2, 5, -7, 8);
Map<Boolean, List<Integer>> partitioned = numbers.stream()
    .collect(Collectors.partitioningBy(n -> n >= 0));
// {true=[0, 2, 5, 8], false=[-3, -1, -7]}
```

---

**Q327. Get counts of both partitions.**

```java
Map<Boolean, Long> counts = employees.stream()
    .collect(Collectors.partitioningBy(
        e -> e.getSalary() > 50000,
        Collectors.counting()
    ));
System.out.println("High earners: " + counts.get(true));
System.out.println("Others: " + counts.get(false));
```

---

**Q328. Process both partitions separately.**

```java
Map<Boolean, List<Employee>> partitioned = employees.stream()
    .collect(Collectors.partitioningBy(e -> e.getAge() >= 30));

// Process seniors
partitioned.get(true).forEach(e -> System.out.println("Senior: " + e.getName()));

// Process juniors
partitioned.get(false).forEach(e -> System.out.println("Junior: " + e.getName()));
```

---

## 18. Statistical Operations

**Q329. Get summary statistics for a list of integers.**

```java
List<Integer> numbers = Arrays.asList(3, 7, 1, 9, 4, 6);
IntSummaryStatistics stats = numbers.stream()
                                    .mapToInt(Integer::intValue)
                                    .summaryStatistics();
System.out.println(stats);
// IntSummaryStatistics{count=6, sum=30, min=1, average=5.0, max=9}
```

---

**Q330. Calculate count, sum, min, max, and average in one operation.**

```java
List<Integer> numbers = Arrays.asList(10, 20, 30, 40, 50);
IntSummaryStatistics stats = numbers.stream()
                                    .mapToInt(n -> n)
                                    .summaryStatistics();
System.out.println("Count: " + stats.getCount());
System.out.println("Sum: " + stats.getSum());
System.out.println("Min: " + stats.getMin());
System.out.println("Max: " + stats.getMax());
System.out.println("Average: " + stats.getAverage());
```

---

**Q331. Get statistics for employee salaries.**

```java
DoubleSummaryStatistics salaryStats = employees.stream()
    .mapToDouble(Employee::getSalary)
    .summaryStatistics();
System.out.println("Min Salary: " + salaryStats.getMin());
System.out.println("Max Salary: " + salaryStats.getMax());
System.out.println("Avg Salary: " + salaryStats.getAverage());
System.out.println("Total: " + salaryStats.getSum());
```

---

**Q332. Use DoubleSummaryStatistics.**

```java
List<Double> prices = Arrays.asList(10.5, 20.3, 15.8, 8.9, 30.0);
DoubleSummaryStatistics stats = prices.stream()
                                      .mapToDouble(Double::doubleValue)
                                      .summaryStatistics();
System.out.println(stats);
```

---

**Q333. Use IntSummaryStatistics.**

```java
List<Employee> employees = getEmployees();
IntSummaryStatistics ageStats = employees.stream()
                                         .mapToInt(Employee::getAge)
                                         .summaryStatistics();
System.out.println("Youngest: " + ageStats.getMin());
System.out.println("Oldest: " + ageStats.getMax());
System.out.println("Average Age: " + ageStats.getAverage());
```

---

**Q334. Use LongSummaryStatistics.**

```java
List<Long> ids = Arrays.asList(100L, 200L, 300L, 400L, 500L);
LongSummaryStatistics stats = ids.stream()
                                 .mapToLong(Long::longValue)
                                 .summaryStatistics();
System.out.println(stats);
```

---

**Q335. Get statistics per group (e.g., per department).**

```java
Map<String, DoubleSummaryStatistics> statsByDept = employees.stream()
    .collect(Collectors.groupingBy(
        Employee::getDept,
        Collectors.summarizingDouble(Employee::getSalary)
    ));

statsByDept.forEach((dept, stats) ->
    System.out.println(dept + ": avg=" + stats.getAverage() + ", max=" + stats.getMax()));
```

---

## 19. File Operations with Streams

### Reading Files

**Q336. Read all lines from a file using streams.**

```java
Path path = Paths.get("data.txt");
try (Stream<String> lines = Files.lines(path)) {
    lines.forEach(System.out::println);
}
```

---

**Q337. Count number of lines in a file.**

```java
Path path = Paths.get("data.txt");
try (Stream<String> lines = Files.lines(path)) {
    long count = lines.count();
    System.out.println("Lines: " + count);
}
```

---

**Q338. Find lines containing a specific word.**

```java
Path path = Paths.get("data.txt");
try (Stream<String> lines = Files.lines(path)) {
    List<String> matches = lines
        .filter(line -> line.contains("error"))
        .collect(Collectors.toList());
    matches.forEach(System.out::println);
}
```

---

**Q339. Count unique words in a file.**

```java
Path path = Paths.get("data.txt");
try (Stream<String> lines = Files.lines(path)) {
    long uniqueWords = lines
        .flatMap(line -> Arrays.stream(line.split("\\s+")))
        .map(String::toLowerCase)
        .distinct()
        .count();
    System.out.println("Unique words: " + uniqueWords);
}
```

---

**Q340. Find the longest line in a file.**

```java
Path path = Paths.get("data.txt");
try (Stream<String> lines = Files.lines(path)) {
    Optional<String> longest = lines
        .max(Comparator.comparingInt(String::length));
    longest.ifPresent(System.out::println);
}
```

---

**Q341. Convert file content to uppercase.**

```java
Path input = Paths.get("data.txt");
try (Stream<String> lines = Files.lines(input)) {
    List<String> upperLines = lines
        .map(String::toUpperCase)
        .collect(Collectors.toList());
    Files.write(Paths.get("upper.txt"), upperLines);
}
```

---

**Q342. Filter empty lines from a file.**

```java
Path path = Paths.get("data.txt");
try (Stream<String> lines = Files.lines(path)) {
    List<String> nonEmpty = lines
        .filter(line -> !line.isBlank())
        .collect(Collectors.toList());
}
```

---

**Q343. Count occurrences of a word in a file.**

```java
String targetWord = "java";
Path path = Paths.get("data.txt");
try (Stream<String> lines = Files.lines(path)) {
    long count = lines
        .flatMap(line -> Arrays.stream(line.split("\\s+")))
        .map(String::toLowerCase)
        .filter(w -> w.equals(targetWord))
        .count();
    System.out.println("Occurrences of '" + targetWord + "': " + count);
}
```

---

### CSV Processing

**Q344. Read and parse CSV file using streams.**

```java
Path path = Paths.get("employees.csv");
try (Stream<String> lines = Files.lines(path)) {
    List<String[]> rows = lines
        .skip(1) // skip header
        .map(line -> line.split(","))
        .collect(Collectors.toList());
    rows.forEach(row -> System.out.println(Arrays.toString(row)));
}
```

---

**Q345. Filter rows in CSV based on condition.**

```java
Path path = Paths.get("employees.csv");
try (Stream<String> lines = Files.lines(path)) {
    List<String> highSalary = lines
        .skip(1)
        .filter(line -> {
            String[] parts = line.split(",");
            return Double.parseDouble(parts[2]) > 50000;
        })
        .collect(Collectors.toList());
}
```

---

**Q346. Group CSV data by a column.**

```java
Path path = Paths.get("employees.csv");
try (Stream<String> lines = Files.lines(path)) {
    Map<String, List<String>> grouped = lines
        .skip(1)
        .collect(Collectors.groupingBy(line -> line.split(",")[1])); // group by dept (col 1)
}
```

---

**Q347. Calculate aggregate statistics from CSV.**

```java
Path path = Paths.get("employees.csv");
try (Stream<String> lines = Files.lines(path)) {
    DoubleSummaryStatistics stats = lines
        .skip(1)
        .mapToDouble(line -> Double.parseDouble(line.split(",")[2]))
        .summaryStatistics();
    System.out.println("Avg salary: " + stats.getAverage());
}
```

---

**Q348. Convert CSV to list of objects.**

```java
Path path = Paths.get("employees.csv");
try (Stream<String> lines = Files.lines(path)) {
    List<Employee> employees = lines
        .skip(1)
        .map(line -> {
            String[] parts = line.split(",");
            return new Employee(parts[0], parts[1], Double.parseDouble(parts[2]));
        })
        .collect(Collectors.toList());
}
```

---

**Q349. Extract specific columns from CSV.**

```java
Path path = Paths.get("employees.csv");
try (Stream<String> lines = Files.lines(path)) {
    List<String> names = lines
        .skip(1)
        .map(line -> line.split(",")[0]) // extract name column
        .collect(Collectors.toList());
}
```

---

## 20. Advanced & Complex Scenarios

### Complex Combinations

**Q350. Find pairs of numbers from a list that sum to a specific value.**

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9);
int target = 10;
List<String> pairs = numbers.stream()
    .flatMap(n1 -> numbers.stream()
        .filter(n2 -> n1 < n2 && n1 + n2 == target)
        .map(n2 -> "(" + n1 + ", " + n2 + ")")
    )
    .collect(Collectors.toList());
// [(1, 9), (2, 8), (3, 7), (4, 6)]
```

---

**Q351. Find all permutations using streams.**

```java
// Simple: all pairs from a list
List<Integer> list = Arrays.asList(1, 2, 3);
List<String> perms = list.stream()
    .flatMap(a -> list.stream()
        .filter(b -> !b.equals(a))
        .map(b -> a + "" + b))
    .collect(Collectors.toList());
// [12, 13, 21, 23, 31, 32]
```

---

**Q352. Find combinations of elements.**

```java
List<Integer> list = Arrays.asList(1, 2, 3, 4);
// All pairs (combinations of 2)
List<String> combos = list.stream()
    .flatMap(a -> list.stream()
        .filter(b -> a < b)
        .map(b -> "(" + a + "," + b + ")"))
    .collect(Collectors.toList());
// [(1,2), (1,3), (1,4), (2,3), (2,4), (3,4)]
```

---

**Q353. Implement custom collector.**

```java
// Custom collector that joins strings with '|' and wraps in brackets
Collector<String, StringBuilder, String> customCollector = Collector.of(
    StringBuilder::new,                          // supplier
    (sb, s) -> { if (sb.length() > 0) sb.append("|"); sb.append(s); }, // accumulator
    StringBuilder::append,                       // combiner
    sb -> "[" + sb.toString() + "]"              // finisher
);

String result = Stream.of("A", "B", "C").collect(customCollector);
System.out.println(result); // [A|B|C]
```

---

**Q354. Chain multiple stream operations.**

```java
List<String> result = employees.stream()
    .filter(e -> e.getDept().equals("IT"))
    .filter(e -> e.getSalary() > 50000)
    .map(Employee::getName)
    .map(String::toUpperCase)
    .sorted()
    .distinct()
    .collect(Collectors.toList());
```

---

**Q355. Use peek() for debugging streams.**

```java
List<Integer> result = Arrays.asList(1, 2, 3, 4, 5).stream()
    .peek(n -> System.out.println("Before filter: " + n))
    .filter(n -> n % 2 == 0)
    .peek(n -> System.out.println("After filter: " + n))
    .map(n -> n * 2)
    .peek(n -> System.out.println("After map: " + n))
    .collect(Collectors.toList());
```

---

**Q356. Limit and skip operations.**

```java
List<Integer> numbers = IntStream.rangeClosed(1, 20).boxed().collect(Collectors.toList());

// First 5 elements
List<Integer> first5 = numbers.stream().limit(5).collect(Collectors.toList());
// [1, 2, 3, 4, 5]

// Elements 6–10 (skip 5, take 5)
List<Integer> page2 = numbers.stream().skip(5).limit(5).collect(Collectors.toList());
// [6, 7, 8, 9, 10]
```

---

**Q357. Create infinite streams and control them.**

```java
// Infinite stream of natural numbers
Stream.iterate(1, n -> n + 1)
      .limit(10)
      .forEach(System.out::println);

// Infinite stream of random numbers
Stream.generate(Math::random)
      .limit(5)
      .forEach(System.out::println);
```

---

### Real-world Scenarios

**Q358. Process JSON data using streams.**

```java
// Assume a list of JSON-like maps
List<Map<String, Object>> records = getJsonData();
List<String> names = records.stream()
    .filter(r -> (Integer) r.get("age") > 25)
    .map(r -> (String) r.get("name"))
    .collect(Collectors.toList());
```

---

**Q359. Handle exceptions in stream operations.**

```java
// Wrap checked exception in unchecked
List<Integer> result = strNumbers.stream()
    .map(s -> {
        try {
            return Integer.parseInt(s);
        } catch (NumberFormatException e) {
            return 0; // default value on error
        }
    })
    .collect(Collectors.toList());
```

---

**Q360. Convert between different date formats using streams.**

```java
List<String> dates = Arrays.asList("2024-01-15", "2024-06-20", "2024-12-01");
DateTimeFormatter in = DateTimeFormatter.ofPattern("yyyy-MM-dd");
DateTimeFormatter out = DateTimeFormatter.ofPattern("dd/MM/yyyy");

List<String> formatted = dates.stream()
    .map(d -> LocalDate.parse(d, in).format(out))
    .collect(Collectors.toList());
// [15/01/2024, 20/06/2024, 01/12/2024]
```

---

**Q361. Validate data using streams.**

```java
List<String> emails = Arrays.asList("user@mail.com", "invalid", "test@test.org");
String emailRegex = "^[\\w.-]+@[\\w.-]+\\.[a-z]{2,}$";

Map<Boolean, List<String>> validated = emails.stream()
    .collect(Collectors.partitioningBy(e -> e.matches(emailRegex)));

System.out.println("Valid: " + validated.get(true));
System.out.println("Invalid: " + validated.get(false));
```

---

**Q362. Implement caching with streams.**

```java
// Build a cached lookup map from a list
Map<Integer, Employee> cache = employees.stream()
    .collect(Collectors.toMap(Employee::getId, e -> e));

// Later, look up quickly
Employee emp = cache.get(101);
```

---

**Q363. Batch process elements (e.g., process 100 at a time).**

```java
List<Integer> numbers = IntStream.rangeClosed(1, 500).boxed().collect(Collectors.toList());
int batchSize = 100;

IntStream.range(0, (numbers.size() + batchSize - 1) / batchSize)
    .forEach(i -> {
        List<Integer> batch = numbers.subList(
            i * batchSize,
            Math.min((i + 1) * batchSize, numbers.size())
        );
        System.out.println("Processing batch " + (i + 1) + ": " + batch.size() + " items");
    });
```

---

**Q364. Compare two lists and find differences.**

```java
List<String> list1 = Arrays.asList("Alice", "Bob", "Charlie", "David");
List<String> list2 = Arrays.asList("Bob", "David", "Eve");

// In list1 but not list2
List<String> onlyInList1 = list1.stream()
    .filter(s -> !list2.contains(s))
    .collect(Collectors.toList()); // [Alice, Charlie]

// In list2 but not list1
List<String> onlyInList2 = list2.stream()
    .filter(s -> !list1.contains(s))
    .collect(Collectors.toList()); // [Eve]
```

---

**Q365. Implement pagination using streams.**

```java
List<Employee> employees = getEmployees(); // large list
int page = 2;         // page number (1-based)
int pageSize = 10;

List<Employee> pageResult = employees.stream()
    .skip((long)(page - 1) * pageSize)
    .limit(pageSize)
    .collect(Collectors.toList());
```

---

### Performance & Optimization

**Q366. When to use sequential vs parallel streams.**

```java
// Use sequential for:
// - Small collections (< 10,000 elements)
// - Operations with side effects
// - Ordered output is critical
List<Integer> small = Arrays.asList(1, 2, 3, 4, 5);
int sum = small.stream().mapToInt(n -> n).sum();

// Use parallel for:
// - Large collections with CPU-heavy independent operations
List<Integer> large = IntStream.rangeClosed(1, 1_000_000).boxed().collect(Collectors.toList());
long count = large.parallelStream().filter(n -> isPrime(n)).count();
```

---

**Q367. Avoid using streams for small collections.**

```java
// Overhead not worth it for tiny lists — plain loop is faster
List<Integer> tiny = Arrays.asList(1, 2, 3);
int sum = 0;
for (int n : tiny) sum += n; // better than stream for tiny lists

// Stream is fine for readability even on small lists in non-hot paths
int streamSum = tiny.stream().mapToInt(n -> n).sum();
```

---

**Q368. Understand laziness in streams.**

```java
// Intermediate operations are lazy — they don't execute until a terminal op
Stream<Integer> lazyStream = Stream.of(1, 2, 3, 4, 5)
    .filter(n -> { System.out.println("filter: " + n); return n % 2 == 0; })
    .map(n -> { System.out.println("map: " + n); return n * 2; });

// Nothing has printed yet!
System.out.println("Before terminal");
lazyStream.findFirst(); // Now it executes — and stops after first match
```

---

**Q369. Avoid stateful operations in parallel streams.**

```java
// WRONG — stateful lambda causes race conditions in parallel
List<Integer> results = new ArrayList<>();
numbers.parallelStream().forEach(n -> results.add(n * 2)); // NOT SAFE

// CORRECT — use collect (thread-safe)
List<Integer> safeResults = numbers.parallelStream()
    .map(n -> n * 2)
    .collect(Collectors.toList());
```

---

**Q370. Profile stream performance.**

```java
List<Integer> list = IntStream.rangeClosed(1, 10_000_000).boxed().collect(Collectors.toList());

long start = System.nanoTime();
long sum = list.stream().mapToLong(n -> n).sum();
long seqNs = System.nanoTime() - start;

start = System.nanoTime();
long parSum = list.parallelStream().mapToLong(n -> n).sum();
long parNs = System.nanoTime() - start;

System.out.printf("Sequential: %.2fms%n", seqNs / 1e6);
System.out.printf("Parallel:   %.2fms%n", parNs / 1e6);
```

---

**Q371. Optimize groupingBy operations.**

```java
// Prefer downstream collectors over post-processing
// LESS efficient:
Map<String, List<Employee>> byDept = employees.stream()
    .collect(Collectors.groupingBy(Employee::getDept));
Map<String, Long> counts = new HashMap<>();
byDept.forEach((k, v) -> counts.put(k, (long) v.size()));

// MORE efficient — single pass:
Map<String, Long> efficientCounts = employees.stream()
    .collect(Collectors.groupingBy(Employee::getDept, Collectors.counting()));
```

---

**Q372. Understand cost of boxing/unboxing.**

```java
List<Integer> boxed = IntStream.rangeClosed(1, 1_000_000).boxed().collect(Collectors.toList());

// SLOW — autoboxing in stream
long slowSum = boxed.stream().reduce(0, Integer::sum);

// FAST — use primitive IntStream to avoid boxing
long fastSum = boxed.stream().mapToLong(Integer::longValue).sum();

// FASTEST — use IntStream directly from the start
long fastest = IntStream.rangeClosed(1, 1_000_000).asLongStream().sum();
```

---

### Multi-level Grouping

**Q373. Group by department and then by gender.**

```java
Map<String, Map<String, List<Employee>>> result = employees.stream()
    .collect(Collectors.groupingBy(
        Employee::getDept,
        Collectors.groupingBy(Employee::getGender)
    ));
```

---

**Q374. Group by city, then by department.**

```java
Map<String, Map<String, List<Employee>>> result = employees.stream()
    .collect(Collectors.groupingBy(
        Employee::getCity,
        Collectors.groupingBy(Employee::getDept)
    ));
```

---

**Q375. Multi-level grouping with counting.**

```java
Map<String, Map<String, Long>> result = employees.stream()
    .collect(Collectors.groupingBy(
        Employee::getDept,
        Collectors.groupingBy(Employee::getGender, Collectors.counting())
    ));
```

---

**Q376. Multi-level grouping with averaging.**

```java
Map<String, Map<String, Double>> result = employees.stream()
    .collect(Collectors.groupingBy(
        Employee::getDept,
        Collectors.groupingBy(
            Employee::getGender,
            Collectors.averagingDouble(Employee::getSalary)
        )
    ));
```

---

**Q377. Create nested maps using groupingBy.**

```java
Map<String, Map<String, Map<String, List<Employee>>>> result = employees.stream()
    .collect(Collectors.groupingBy(
        Employee::getDept,
        Collectors.groupingBy(
            Employee::getGender,
            Collectors.groupingBy(Employee::getCity)
        )
    ));
```

---

**Q378. Group employees by department, city, and gender.**

```java
// Using a composite key string
Map<String, List<Employee>> result = employees.stream()
    .collect(Collectors.groupingBy(
        e -> e.getDept() + "_" + e.getCity() + "_" + e.getGender()
    ));
```

---

### Custom Object Scenarios

**Q379. Filter products by category and price range.**

```java
List<Product> result = products.stream()
    .filter(p -> p.getCategory().equals("Electronics"))
    .filter(p -> p.getPrice() >= 500 && p.getPrice() <= 2000)
    .collect(Collectors.toList());
```

---

**Q380. Find top-selling products.**

```java
List<Product> topSelling = products.stream()
    .sorted(Comparator.comparingInt(Product::getUnitsSold).reversed())
    .limit(5)
    .collect(Collectors.toList());
```

---

**Q381. Calculate order totals.**

```java
Map<String, Double> orderTotals = orders.stream()
    .collect(Collectors.toMap(
        Order::getOrderId,
        o -> o.getItems().stream().mapToDouble(i -> i.getPrice() * i.getQty()).sum()
    ));
```

---

**Q382. Group orders by customer.**

```java
Map<String, List<Order>> ordersByCustomer = orders.stream()
    .collect(Collectors.groupingBy(Order::getCustomerId));
```

---

**Q383. Find customers with most orders.**

```java
String topCustomer = orders.stream()
    .collect(Collectors.groupingBy(Order::getCustomerId, Collectors.counting()))
    .entrySet().stream()
    .max(Map.Entry.comparingByValue())
    .map(Map.Entry::getKey)
    .orElse("None");
```

---

**Q384. Calculate customer lifetime value.**

```java
Map<String, Double> clv = orders.stream()
    .collect(Collectors.groupingBy(
        Order::getCustomerId,
        Collectors.summingDouble(Order::getTotal)
    ));
```

---

**Q385. Find students with highest marks.**

```java
Optional<Student> topper = students.stream()
    .max(Comparator.comparingDouble(Student::getMarks));
topper.ifPresent(s -> System.out.println(s.getName() + ": " + s.getMarks()));
```

---

**Q386. Group students by grade and subject.**

```java
Map<String, Map<String, List<Student>>> result = students.stream()
    .collect(Collectors.groupingBy(
        Student::getGrade,
        Collectors.groupingBy(Student::getSubject)
    ));
```

---

**Q387. Calculate class averages.**

```java
Map<String, Double> classAvg = students.stream()
    .collect(Collectors.groupingBy(
        Student::getGrade,
        Collectors.averagingDouble(Student::getMarks)
    ));
```

---

**Q388. Find students passing all subjects.**

```java
// Assuming each Student has a list of subject scores, passing = score >= 40
List<Student> passing = students.stream()
    .filter(s -> s.getSubjectScores().values().stream().allMatch(score -> score >= 40))
    .collect(Collectors.toList());
```

---

### Date & Time Operations

**Q389. Filter dates in a range.**

```java
LocalDate start = LocalDate.of(2024, 1, 1);
LocalDate end = LocalDate.of(2024, 6, 30);
List<LocalDate> result = dates.stream()
    .filter(d -> !d.isBefore(start) && !d.isAfter(end))
    .collect(Collectors.toList());
```

---

**Q390. Group events by month.**

```java
Map<Month, List<LocalDate>> byMonth = events.stream()
    .collect(Collectors.groupingBy(LocalDate::getMonth));
```

---

**Q391. Find the earliest and latest date.**

```java
Optional<LocalDate> earliest = dates.stream().min(LocalDate::compareTo);
Optional<LocalDate> latest   = dates.stream().max(LocalDate::compareTo);
```

---

**Q392. Calculate duration between dates.**

```java
List<Long> durations = datePairs.stream()
    .map(pair -> ChronoUnit.DAYS.between(pair.getStart(), pair.getEnd()))
    .collect(Collectors.toList());
```

---

**Q393. Filter weekend dates.**

```java
List<LocalDate> weekends = dates.stream()
    .filter(d -> d.getDayOfWeek() == DayOfWeek.SATURDAY
              || d.getDayOfWeek() == DayOfWeek.SUNDAY)
    .collect(Collectors.toList());
```

---

**Q394. Group transactions by day/month/year.**

```java
// By month
Map<Month, List<Transaction>> byMonth = transactions.stream()
    .collect(Collectors.groupingBy(t -> t.getDate().getMonth()));

// By year
Map<Integer, List<Transaction>> byYear = transactions.stream()
    .collect(Collectors.groupingBy(t -> t.getDate().getYear()));
```

---

### Stream of Streams

**Q395. Flatten stream of streams.**

```java
Stream<Stream<Integer>> sos = Stream.of(
    Stream.of(1, 2, 3),
    Stream.of(4, 5),
    Stream.of(6, 7, 8)
);
List<Integer> flat = sos.flatMap(s -> s).collect(Collectors.toList());
// [1, 2, 3, 4, 5, 6, 7, 8]
```

---

**Q396. Process nested collections.**

```java
List<Department> departments = getDepartments();
List<String> allNames = departments.stream()
    .flatMap(dept -> dept.getEmployees().stream())
    .map(Employee::getName)
    .collect(Collectors.toList());
```

---

**Q397. Combine multiple streams.**

```java
Stream<Integer> s1 = Stream.of(1, 2, 3);
Stream<Integer> s2 = Stream.of(4, 5, 6);
Stream<Integer> s3 = Stream.of(7, 8, 9);

List<Integer> combined = Stream.of(s1, s2, s3)
    .flatMap(s -> s)
    .collect(Collectors.toList());
```

---

**Q398. Merge and deduplicate streams.**

```java
Stream<String> s1 = Stream.of("apple", "banana", "cherry");
Stream<String> s2 = Stream.of("banana", "date", "cherry");

List<String> merged = Stream.concat(s1, s2)
    .distinct()
    .sorted()
    .collect(Collectors.toList());
// [apple, banana, cherry, date]
```

---

### Error Handling

**Q399. Handle exceptions gracefully in stream pipelines.**

```java
List<String> inputs = Arrays.asList("10", "abc", "20", "xyz", "30");
List<Integer> results = inputs.stream()
    .flatMap(s -> {
        try {
            return Stream.of(Integer.parseInt(s));
        } catch (NumberFormatException e) {
            return Stream.empty(); // skip invalid
        }
    })
    .collect(Collectors.toList());
// [10, 20, 30]
```

---

**Q400. Use try-catch inside stream operations.**

```java
List<String> urls = Arrays.asList("http://a.com", "bad_url", "http://b.com");
List<String> content = urls.stream()
    .map(url -> {
        try {
            return fetchContent(url); // may throw IOException
        } catch (IOException e) {
            return "ERROR: " + url;
        }
    })
    .collect(Collectors.toList());
```

---

> **Previous:** [Part 3 — Q201 to Q300](java-stream-api-questions-part3(Q201-Q300).md)
> **Next:** [Part 5 — Q401 to Q500](java-stream-api-questions-part5(Q401-Q500).md)
