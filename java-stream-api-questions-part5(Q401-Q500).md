# Java Stream API Coding Interview Questions — Part 5 (Q401–Q500)

> **Series:** Part 5 of 5 | Questions 401–500
> **Topics:** Error Handling (continued), Stream Best Practices, Tricky Scenarios, Additional Challenge Questions — Mixed, String, Number, Collection Challenges, Advanced Employee Questions, Stream Internals, Real Interview Scenarios, Edge Cases

---

## 20. Advanced & Complex Scenarios *(continued)*

### Error Handling *(continued)*

**Q401. Filter out elements that cause exceptions.**

```java
List<String> inputs = Arrays.asList("5", "hello", "10", null, "20");
List<Integer> safe = inputs.stream()
    .filter(s -> s != null)
    .flatMap(s -> {
        try {
            return Stream.of(Integer.parseInt(s));
        } catch (NumberFormatException e) {
            return Stream.empty();
        }
    })
    .collect(Collectors.toList());
// [5, 10, 20]
```

---

**Q402. Wrap checked exceptions in unchecked exceptions.**

```java
// Helper method to wrap checked exception
static <T, R> Function<T, R> wrap(CheckedFunction<T, R> fn) {
    return t -> {
        try {
            return fn.apply(t);
        } catch (Exception e) {
            throw new RuntimeException(e);
        }
    };
}

// Usage in stream:
List<String> lines = filePaths.stream()
    .map(wrap(path -> Files.readString(Paths.get(path))))
    .collect(Collectors.toList());
```

---

### Stream Best Practices

**Q403. Avoid modifying source during stream operations.**

```java
List<Integer> numbers = new ArrayList<>(Arrays.asList(1, 2, 3, 4, 5));

// WRONG — modifying source during stream is undefined behavior:
// numbers.stream().forEach(n -> numbers.remove(n)); // ConcurrentModificationException!

// CORRECT — collect to a new list, then reassign:
List<Integer> evens = numbers.stream()
    .filter(n -> n % 2 == 0)
    .collect(Collectors.toList());
```

---

**Q404. Understand terminal vs intermediate operations.**

```java
// Intermediate (lazy, return Stream):
// filter(), map(), flatMap(), distinct(), sorted(), peek(), limit(), skip()

// Terminal (eager, trigger execution, return non-Stream):
// forEach(), collect(), reduce(), count(), findFirst(), findAny(),
// anyMatch(), allMatch(), noneMatch(), min(), max(), toArray()

Stream<Integer> stream = Stream.of(1, 2, 3, 4, 5)
    .filter(n -> n > 2)   // intermediate (lazy)
    .map(n -> n * 2);     // intermediate (lazy)

List<Integer> result = stream.collect(Collectors.toList()); // terminal (triggers execution)
```

---

**Q405. Know when streams can be reused (they can't).**

```java
Stream<String> stream = Stream.of("a", "b", "c");
stream.forEach(System.out::println); // first use

// stream.forEach(System.out::println); // IllegalStateException: stream already operated upon

// Solution: recreate the stream each time
Supplier<Stream<String>> supplier = () -> Stream.of("a", "b", "c");
supplier.get().forEach(System.out::println);
supplier.get().filter(s -> !s.equals("b")).forEach(System.out::println);
```

---

**Q406. Use method references where possible.**

```java
List<String> names = Arrays.asList("alice", "bob", "charlie");

// Lambda
List<String> upper1 = names.stream().map(s -> s.toUpperCase()).collect(Collectors.toList());

// Method reference (cleaner)
List<String> upper2 = names.stream().map(String::toUpperCase).collect(Collectors.toList());

// Method reference with instance method
names.stream().forEach(System.out::println);
```

---

**Q407. Prefer collection over reduce when appropriate.**

```java
// reduce is for single value aggregation
int sum = numbers.stream().reduce(0, Integer::sum);

// collect is for building data structures
List<Integer> list = numbers.stream().filter(n -> n > 2).collect(Collectors.toList());
Map<Boolean, List<Integer>> map = numbers.stream().collect(Collectors.partitioningBy(n -> n % 2 == 0));

// Don't misuse reduce to build collections — it's inefficient due to copying
```

---

**Q408. Use specialized streams (IntStream) for primitives.**

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);

// Using boxed Stream (boxing overhead):
int sum1 = numbers.stream().reduce(0, Integer::sum);

// Using IntStream (no boxing — faster):
int sum2 = numbers.stream().mapToInt(Integer::intValue).sum();

// Even better — use IntStream directly:
int sum3 = IntStream.of(1, 2, 3, 4, 5).sum();
```

---

**Q409. Avoid forEach for non-side-effect operations.**

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);

// WRONG — using forEach to build a collection:
List<Integer> squares = new ArrayList<>();
numbers.stream().forEach(n -> squares.add(n * n)); // side effect

// CORRECT — use map + collect:
List<Integer> correctSquares = numbers.stream()
    .map(n -> n * n)
    .collect(Collectors.toList());
```

---

**Q410. Understand short-circuiting operations.**

```java
// Short-circuit terminal ops — stop early when result is known:
// anyMatch, allMatch, noneMatch, findFirst, findAny, limit

boolean found = Stream.of(1, 2, 3, 4, 5)
    .peek(n -> System.out.print(n + " "))
    .anyMatch(n -> n == 3);
// Prints: 1 2 3 — stops at 3

Optional<Integer> first = Stream.of(1, 2, 3, 4, 5)
    .filter(n -> n % 2 == 0)
    .peek(n -> System.out.print("found: " + n))
    .findFirst();
// Prints: found: 2 — stops immediately
```

---

### Tricky Scenarios

**Q411. Handle null elements in streams.**

```java
List<String> names = Arrays.asList("Alice", null, "Bob", null, "Charlie");

// Filter nulls before processing
List<String> result = names.stream()
    .filter(Objects::nonNull)
    .map(String::toUpperCase)
    .collect(Collectors.toList());
// [ALICE, BOB, CHARLIE]
```

---

**Q412. Work with empty streams.**

```java
// Empty stream — all terminal ops behave safely
Stream<Integer> empty = Stream.empty();

long count = empty.count(); // 0
Optional<Integer> opt = Stream.<Integer>empty().findFirst(); // Optional.empty
int sum = Stream.<Integer>empty().mapToInt(n -> n).sum(); // 0
```

---

**Q413. Difference between findFirst() and findAny().**

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);

// findFirst — always returns the first element in encounter order
Optional<Integer> first = numbers.stream().filter(n -> n > 2).findFirst();
System.out.println(first.get()); // 3 (always)

// findAny — may return any element (non-deterministic in parallel)
Optional<Integer> any = numbers.parallelStream().filter(n -> n > 2).findAny();
System.out.println(any.get()); // 3, 4, or 5 (not guaranteed)
```

---

**Q414. Understanding of lazy evaluation.**

```java
// Stream operations are lazy — nothing executes until a terminal op
long count = Stream.of("hello", "world", "java", "stream")
    .filter(s -> {
        System.out.println("Filtering: " + s); // will only run as needed
        return s.startsWith("j");
    })
    .count();
// Prints filtering for all elements (count needs to process all)
// But with findFirst() it would stop early
```

---

**Q415. Side effects in stream operations.**

```java
// Side effects (changing external state) are discouraged inside stream ops
// Use forEach only for genuine side effects like printing/logging

// BAD — side effect inside map:
List<Integer> sideEffectList = new ArrayList<>();
numbers.stream().map(n -> { sideEffectList.add(n); return n * 2; }).count();

// GOOD — use peek for debug side effects:
numbers.stream()
    .peek(n -> System.out.println("Processing: " + n))
    .map(n -> n * 2)
    .collect(Collectors.toList());
```

---

**Q416. Stateless vs stateful operations.**

```java
// Stateless — each element processed independently (filter, map)
List<Integer> stateless = numbers.stream()
    .filter(n -> n > 2)   // stateless
    .map(n -> n * 2)      // stateless
    .collect(Collectors.toList());

// Stateful — need to see other elements (sorted, distinct, limit)
List<Integer> stateful = numbers.stream()
    .distinct()           // stateful — must track seen elements
    .sorted()             // stateful — must see all elements
    .limit(5)             // stateful — tracks count
    .collect(Collectors.toList());
```

---

**Q417. Order of operations matters.**

```java
// filter BEFORE map — fewer elements go through map
List<String> efficient = employees.stream()
    .filter(e -> e.getSalary() > 50000)  // reduces elements first
    .map(Employee::getName)              // only maps filtered employees
    .collect(Collectors.toList());

// filter AFTER map — all elements mapped, then filtered (less efficient)
List<String> less = employees.stream()
    .map(Employee::getName)              // maps all employees
    .filter(n -> n.startsWith("A"))     // then filters
    .collect(Collectors.toList());
```

---

**Q418. When distinct() should be used.**

```java
// Use distinct() to remove duplicates — uses equals() and hashCode()
List<Integer> numbers = Arrays.asList(1, 2, 2, 3, 3, 4, 1);
List<Integer> unique = numbers.stream().distinct().collect(Collectors.toList());
// [1, 2, 3, 4]

// For objects, ensure equals/hashCode are overridden:
List<Employee> uniqueByName = employees.stream()
    .collect(Collectors.collectingAndThen(
        Collectors.toMap(Employee::getName, e -> e, (e1, e2) -> e1),
        m -> new ArrayList<>(m.values())
    ));
```

---

**Q419. Performance implications of sorted().**

```java
// sorted() is an O(n log n) stateful operation — must buffer all elements
// Avoid if possible, or push it to the end of the pipeline

// Avoid sorting before filter — filter first to reduce elements:
List<Employee> result = employees.stream()
    .filter(e -> e.getSalary() > 50000)  // filter first
    .sorted(Comparator.comparing(Employee::getName))  // sort the smaller set
    .collect(Collectors.toList());
```

---

**Q420. Understanding collectors composition.**

```java
// Compose collectors to build complex downstream processing in one pass
Map<String, String> result = employees.stream()
    .collect(Collectors.groupingBy(
        Employee::getDept,
        Collectors.collectingAndThen(
            Collectors.mapping(Employee::getName, Collectors.joining(", ")),
            names -> "[" + names + "]"
        )
    ));
// {IT=[Alice, Bob], HR=[Charlie]}
```

---

## Additional Challenge Questions

### Mixed Operations

**Q421. Find employees with second highest salary per department.**

```java
Map<String, Optional<Double>> result = employees.stream()
    .collect(Collectors.groupingBy(
        Employee::getDept,
        Collectors.collectingAndThen(
            Collectors.toList(),
            list -> list.stream()
                .map(Employee::getSalary)
                .distinct()
                .sorted(Collections.reverseOrder())
                .skip(1)
                .findFirst()
        )
    ));
```

---

**Q422. Find the nth element without using skip.**

```java
List<Integer> numbers = Arrays.asList(10, 20, 30, 40, 50);
int n = 3; // 1-based index
int[] index = {0};
Optional<Integer> nth = numbers.stream()
    .filter(num -> ++index[0] == n)
    .findFirst();
System.out.println(nth.orElse(-1)); // 30
```

---

**Q423. Implement running sum using streams.**

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
int[] runningSum = {0};
List<Integer> result = numbers.stream()
    .map(n -> runningSum[0] += n)
    .collect(Collectors.toList());
System.out.println(result); // [1, 3, 6, 10, 15]
```

---

**Q424. Find missing numbers in a sequence.**

```java
List<Integer> numbers = Arrays.asList(1, 2, 4, 6, 7, 9, 10);
int max = numbers.stream().max(Integer::compareTo).orElse(0);

List<Integer> missing = IntStream.rangeClosed(1, max)
    .filter(n -> !numbers.contains(n))
    .boxed()
    .collect(Collectors.toList());
// [3, 5, 8]
```

---

**Q425. Rotate a list using streams.**

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
int k = 2; // rotate right by 2
int size = numbers.size();

List<Integer> rotated = Stream.concat(
    numbers.stream().skip(size - k),
    numbers.stream().limit(size - k)
).collect(Collectors.toList());
// [4, 5, 1, 2, 3]
```

---

**Q426. Implement custom sorting logic.**

```java
// Sort employees: IT dept first, then by salary descending
List<Employee> sorted = employees.stream()
    .sorted(Comparator
        .comparing((Employee e) -> e.getDept().equals("IT") ? 0 : 1)
        .thenComparing(Comparator.comparingDouble(Employee::getSalary).reversed()))
    .collect(Collectors.toList());
```

---

**Q427. Find elements at even indices.**

```java
List<String> names = Arrays.asList("A", "B", "C", "D", "E");
List<String> evenIndexElements = IntStream.range(0, names.size())
    .filter(i -> i % 2 == 0)
    .mapToObj(names::get)
    .collect(Collectors.toList());
// [A, C, E]  (indices 0, 2, 4)
```

---

**Q428. Find elements at odd indices.**

```java
List<String> names = Arrays.asList("A", "B", "C", "D", "E");
List<String> oddIndexElements = IntStream.range(0, names.size())
    .filter(i -> i % 2 != 0)
    .mapToObj(names::get)
    .collect(Collectors.toList());
// [B, D]  (indices 1, 3)
```

---

**Q429. Chunk a list into sublists of size N.**

```java
List<Integer> numbers = IntStream.rangeClosed(1, 10).boxed().collect(Collectors.toList());
int chunkSize = 3;

List<List<Integer>> chunks = IntStream.range(0, (numbers.size() + chunkSize - 1) / chunkSize)
    .mapToObj(i -> numbers.subList(
        i * chunkSize,
        Math.min((i + 1) * chunkSize, numbers.size())
    ))
    .collect(Collectors.toList());
// [[1,2,3], [4,5,6], [7,8,9], [10]]
```

---

**Q430. Implement zip operation (combine two lists).**

```java
List<String> names = Arrays.asList("Alice", "Bob", "Charlie");
List<Integer> ages  = Arrays.asList(30, 25, 35);

List<String> zipped = IntStream.range(0, Math.min(names.size(), ages.size()))
    .mapToObj(i -> names.get(i) + " -> " + ages.get(i))
    .collect(Collectors.toList());
// [Alice -> 30, Bob -> 25, Charlie -> 35]
```

---

### String Challenges

**Q431. Remove all special characters from strings.**

```java
List<String> inputs = Arrays.asList("hello!", "world@#", "java$stream");
List<String> cleaned = inputs.stream()
    .map(s -> s.replaceAll("[^a-zA-Z0-9]", ""))
    .collect(Collectors.toList());
// [hello, world, javastream]
```

---

**Q432. Find the longest common prefix.**

```java
List<String> words = Arrays.asList("flower", "flow", "flight");
String prefix = words.stream()
    .reduce((a, b) -> {
        int i = 0;
        while (i < a.length() && i < b.length() && a.charAt(i) == b.charAt(i)) i++;
        return a.substring(0, i);
    })
    .orElse("");
System.out.println(prefix); // "fl"
```

---

**Q433. Group anagrams together.**

```java
List<String> words = Arrays.asList("eat", "tea", "tan", "ate", "nat", "bat");
Map<String, List<String>> anagrams = words.stream()
    .collect(Collectors.groupingBy(
        s -> s.chars().sorted()
               .collect(StringBuilder::new, StringBuilder::appendCodePoint, StringBuilder::append)
               .toString()
    ));
// {aet=[eat, tea, ate], ant=[tan, nat], abt=[bat]}
```

---

**Q434. Sort strings by number of vowels.**

```java
List<String> words = Arrays.asList("apple", "bee", "stream", "io", "java");
List<String> sorted = words.stream()
    .sorted(Comparator.comparingLong(s ->
        s.chars().filter(c -> "aeiouAEIOU".indexOf(c) != -1).count()))
    .collect(Collectors.toList());
```

---

**Q435. Find strings with unique characters only.**

```java
List<String> words = Arrays.asList("abcde", "hello", "stream", "java");
List<String> unique = words.stream()
    .filter(s -> s.chars().distinct().count() == s.length())
    .collect(Collectors.toList());
// [abcde, stream]
```

---

**Q436. Implement string compression.**

```java
// Compress "aaabbbcc" -> "a3b3c2"
String input = "aaabbbcc";
String compressed = input.chars()
    .mapToObj(c -> (char) c)
    .collect(Collectors.groupingBy(c -> c, LinkedHashMap::new, Collectors.counting()))
    .entrySet().stream()
    .map(e -> e.getKey() + "" + e.getValue())
    .collect(Collectors.joining());
System.out.println(compressed); // a3b3c2
```

---

**Q437. Check if strings are rotations of each other.**

```java
String s1 = "abcde";
String s2 = "cdeab";
boolean isRotation = s1.length() == s2.length() && (s1 + s1).contains(s2);
System.out.println(isRotation); // true
```

---

**Q438. Find all substrings of a string.**

```java
String str = "abc";
List<String> substrings = IntStream.range(0, str.length())
    .boxed()
    .flatMap(i -> IntStream.rangeClosed(i + 1, str.length())
        .mapToObj(j -> str.substring(i, j)))
    .collect(Collectors.toList());
// [a, ab, abc, b, bc, c]
```

---

### Number Challenges

**Q439. Find prime numbers in a range.**

```java
List<Integer> primes = IntStream.rangeClosed(2, 50)
    .filter(n -> IntStream.rangeClosed(2, (int) Math.sqrt(n)).allMatch(i -> n % i != 0))
    .boxed()
    .collect(Collectors.toList());
// [2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37, 41, 43, 47]
```

---

**Q440. Generate Fibonacci sequence using streams.**

```java
Stream.iterate(new long[]{0, 1}, f -> new long[]{f[1], f[0] + f[1]})
      .limit(10)
      .map(f -> f[0])
      .forEach(System.out::println);
// 0, 1, 1, 2, 3, 5, 8, 13, 21, 34
```

---

**Q441. Find Armstrong numbers.**

```java
// Armstrong: 153 = 1^3 + 5^3 + 3^3
List<Integer> armstrongs = IntStream.rangeClosed(1, 999)
    .filter(n -> {
        int digits = String.valueOf(n).length();
        int sum = String.valueOf(n).chars()
                       .map(c -> (int) Math.pow(c - '0', digits))
                       .sum();
        return sum == n;
    })
    .boxed()
    .collect(Collectors.toList());
// [1, 2, 3, 4, 5, 6, 7, 8, 9, 153, 370, 371, 407]
```

---

**Q442. Check if a number is perfect number.**

```java
int n = 28;
boolean isPerfect = IntStream.rangeClosed(1, n / 2)
    .filter(i -> n % i == 0)
    .sum() == n;
System.out.println(isPerfect); // true (28 = 1+2+4+7+14)
```

---

**Q443. Find GCD of numbers in a list.**

```java
List<Integer> numbers = Arrays.asList(12, 18, 24, 36);
int gcd = numbers.stream()
    .reduce((a, b) -> {
        while (b != 0) { int t = b; b = a % b; a = t; }
        return a;
    })
    .orElse(0);
System.out.println(gcd); // 6
```

---

**Q444. Find LCM of numbers in a list.**

```java
List<Integer> numbers = Arrays.asList(4, 6, 8);
int lcm = numbers.stream()
    .reduce(1, (a, b) -> {
        int g = a;
        int temp = b;
        while (temp != 0) { int t = temp; temp = g % temp; g = t; }
        return a / g * b; // LCM = a*b/gcd
    });
System.out.println(lcm); // 24
```

---

**Q445. Convert decimal to binary using streams.**

```java
int decimal = 13;
String binary = IntStream.iterate(decimal, n -> n > 0, n -> n / 2)
    .map(n -> n % 2)
    .mapToObj(Integer::toString)
    .collect(Collectors.joining());
String reversed = new StringBuilder(binary).reverse().toString();
System.out.println(reversed); // 1101
```

---

**Q446. Find factors of a number.**

```java
int n = 36;
List<Integer> factors = IntStream.rangeClosed(1, n)
    .filter(i -> n % i == 0)
    .boxed()
    .collect(Collectors.toList());
// [1, 2, 3, 4, 6, 9, 12, 18, 36]
```

---

**Q447. Check if numbers form an arithmetic sequence.**

```java
List<Integer> numbers = Arrays.asList(2, 5, 8, 11, 14);
int diff = numbers.get(1) - numbers.get(0);
boolean isArithmetic = IntStream.range(1, numbers.size())
    .allMatch(i -> numbers.get(i) - numbers.get(i - 1) == diff);
System.out.println(isArithmetic); // true
```

---

**Q448. Check if numbers form a geometric sequence.**

```java
List<Integer> numbers = Arrays.asList(2, 6, 18, 54);
double ratio = (double) numbers.get(1) / numbers.get(0);
boolean isGeometric = IntStream.range(1, numbers.size())
    .allMatch(i -> (double) numbers.get(i) / numbers.get(i - 1) == ratio);
System.out.println(isGeometric); // true (ratio = 3)
```

---

### Collection Challenges

**Q449. Rotate elements in a list by K positions.**

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6, 7);
int k = 3;
int size = numbers.size();
k = k % size;

List<Integer> rotated = Stream.concat(
    numbers.stream().skip(size - k),
    numbers.stream().limit(size - k)
).collect(Collectors.toList());
// [5, 6, 7, 1, 2, 3, 4]
```

---

**Q450. Find the kth largest element.**

```java
List<Integer> numbers = Arrays.asList(3, 1, 7, 4, 9, 2, 6);
int k = 2;
Optional<Integer> kthLargest = numbers.stream()
    .distinct()
    .sorted(Collections.reverseOrder())
    .skip(k - 1)
    .findFirst();
System.out.println(kthLargest.get()); // 7
```

---

**Q451. Find the kth smallest element.**

```java
List<Integer> numbers = Arrays.asList(3, 1, 7, 4, 9, 2, 6);
int k = 3;
Optional<Integer> kthSmallest = numbers.stream()
    .distinct()
    .sorted()
    .skip(k - 1)
    .findFirst();
System.out.println(kthSmallest.get()); // 4
```

---

**Q452. Implement sliding window operations.**

```java
List<Integer> numbers = Arrays.asList(1, 3, 5, 7, 9, 11);
int windowSize = 3;

List<Integer> slidingWindowSums = IntStream.rangeClosed(0, numbers.size() - windowSize)
    .mapToObj(i -> numbers.subList(i, i + windowSize))
    .map(window -> window.stream().mapToInt(n -> n).sum())
    .collect(Collectors.toList());
// [9, 15, 21, 27]
```

---

**Q453. Find majority element (appearing > n/2 times).**

```java
List<Integer> numbers = Arrays.asList(3, 3, 4, 2, 3, 3, 3);
int n = numbers.size();
Optional<Integer> majority = numbers.stream()
    .collect(Collectors.groupingBy(i -> i, Collectors.counting()))
    .entrySet().stream()
    .filter(e -> e.getValue() > n / 2)
    .map(Map.Entry::getKey)
    .findFirst();
System.out.println(majority.orElse(-1)); // 3
```

---

**Q454. Find all triplets that sum to zero.**

```java
List<Integer> numbers = Arrays.asList(-4, -1, -1, 0, 1, 2);
List<String> triplets = numbers.stream()
    .flatMap(a -> numbers.stream()
        .filter(b -> b > a)
        .flatMap(b -> numbers.stream()
            .filter(c -> c > b && a + b + c == 0)
            .map(c -> "(" + a + "," + b + "," + c + ")")
        ))
    .collect(Collectors.toList());
// [(-1,-1,2), (-1,0,1)]
```

---

**Q455. Implement custom partitioning logic.**

```java
// Partition into 3 groups: low (<30), mid (30-60), high (>60)
Map<String, List<Integer>> partitioned = numbers.stream()
    .collect(Collectors.groupingBy(n -> {
        if (n < 30) return "Low";
        else if (n <= 60) return "Mid";
        else return "High";
    }));
```

---

**Q456. Find longest consecutive sequence.**

```java
List<Integer> numbers = Arrays.asList(100, 4, 200, 1, 3, 2);
Set<Integer> set = new HashSet<>(numbers);
int longest = numbers.stream()
    .filter(n -> !set.contains(n - 1)) // only start of sequences
    .mapToInt(start -> {
        int len = 0;
        while (set.contains(start + len)) len++;
        return len;
    })
    .max()
    .orElse(0);
System.out.println(longest); // 4 (sequence: 1,2,3,4)
```

---

**Q457. Implement LRU cache operations using streams.**

```java
// Build a frequency map — most recently used (simulate with LinkedHashMap ordering)
int capacity = 3;
List<Integer> accessOrder = Arrays.asList(1, 2, 3, 1, 4, 2, 5);

// Simulate LRU: last 'capacity' distinct accesses
Set<Integer> lruCache = accessOrder.stream()
    .collect(Collectors.toCollection(LinkedHashSet::new)) // maintain insertion order + dedupe
    .stream()
    .skip(Math.max(0, (long)(new LinkedHashSet<>(accessOrder).size()) - capacity))
    .collect(Collectors.toCollection(LinkedHashSet::new));
System.out.println(lruCache);
```

---

**Q458. Find equilibrium index of an array.**

```java
// Index where sum of elements to the left equals sum to the right
int[] arr = {1, 7, 3, 6, 5, 6};
int total = IntStream.of(arr).sum();
int[] leftSum = {0};

OptionalInt equilIndex = IntStream.range(0, arr.length)
    .filter(i -> {
        int right = total - leftSum[0] - arr[i];
        boolean eq = leftSum[0] == right;
        leftSum[0] += arr[i];
        return eq;
    })
    .findFirst();

System.out.println(equilIndex.orElse(-1)); // 3 (leftSum=11, rightSum=11)
```

---

### Advanced Employee Questions

**Q459. Find employees with duplicate names.**

```java
Map<String, Long> nameFreq = employees.stream()
    .collect(Collectors.groupingBy(Employee::getName, Collectors.counting()));

List<Employee> duplicates = employees.stream()
    .filter(e -> nameFreq.get(e.getName()) > 1)
    .collect(Collectors.toList());
```

---

**Q460. Find department with highest average salary.**

```java
String topDept = employees.stream()
    .collect(Collectors.groupingBy(Employee::getDept,
             Collectors.averagingDouble(Employee::getSalary)))
    .entrySet().stream()
    .max(Map.Entry.comparingByValue())
    .map(Map.Entry::getKey)
    .orElse("None");
```

---

**Q461. Find employees earning more than their department average.**

```java
Map<String, Double> avgByDept = employees.stream()
    .collect(Collectors.groupingBy(Employee::getDept,
             Collectors.averagingDouble(Employee::getSalary)));

List<Employee> aboveAvg = employees.stream()
    .filter(e -> e.getSalary() > avgByDept.get(e.getDept()))
    .collect(Collectors.toList());
```

---

**Q462. Find employees earning less than their department average.**

```java
Map<String, Double> avgByDept = employees.stream()
    .collect(Collectors.groupingBy(Employee::getDept,
             Collectors.averagingDouble(Employee::getSalary)));

List<Employee> belowAvg = employees.stream()
    .filter(e -> e.getSalary() < avgByDept.get(e.getDept()))
    .collect(Collectors.toList());
```

---

**Q463. Calculate salary percentile for each employee.**

```java
List<Double> sortedSalaries = employees.stream()
    .map(Employee::getSalary)
    .sorted()
    .collect(Collectors.toList());

Map<Employee, Double> percentiles = employees.stream()
    .collect(Collectors.toMap(
        e -> e,
        e -> (double) sortedSalaries.indexOf(e.getSalary()) / sortedSalaries.size() * 100
    ));
```

---

**Q464. Find employees with same salary in different departments.**

```java
Map<Double, List<Employee>> bySalary = employees.stream()
    .collect(Collectors.groupingBy(Employee::getSalary));

List<Employee> result = bySalary.values().stream()
    .filter(list -> list.stream().map(Employee::getDept).distinct().count() > 1)
    .flatMap(List::stream)
    .collect(Collectors.toList());
```

---

**Q465. Get a map of salary ranges and employee counts.**

```java
Map<String, Long> salaryRanges = employees.stream()
    .collect(Collectors.groupingBy(e -> {
        double s = e.getSalary();
        if (s < 30000) return "< 30K";
        else if (s < 60000) return "30K–60K";
        else if (s < 100000) return "60K–100K";
        else return "100K+";
    }, Collectors.counting()));
```

---

**Q466. Find employees who are in top 25% salary bracket.**

```java
DoubleSummaryStatistics stats = employees.stream()
    .mapToDouble(Employee::getSalary).summaryStatistics();
double q3 = stats.getMin() + 0.75 * (stats.getMax() - stats.getMin());

List<Employee> top25 = employees.stream()
    .filter(e -> e.getSalary() >= q3)
    .collect(Collectors.toList());
```

---

**Q467. Create a report of department-wise gender distribution.**

```java
Map<String, Map<String, Long>> report = employees.stream()
    .collect(Collectors.groupingBy(
        Employee::getDept,
        Collectors.groupingBy(Employee::getGender, Collectors.counting())
    ));

report.forEach((dept, genderMap) ->
    System.out.println(dept + ": " + genderMap));
```

---

**Q468. Find correlation between age and salary.**

```java
// Simple correlation check: group by age bracket and average salary
Map<String, Double> avgSalaryByAgeBracket = employees.stream()
    .collect(Collectors.groupingBy(
        e -> e.getAge() < 30 ? "Young" : e.getAge() < 45 ? "Mid" : "Senior",
        Collectors.averagingDouble(Employee::getSalary)
    ));
avgSalaryByAgeBracket.forEach((bracket, avg) ->
    System.out.println(bracket + " avg salary: " + avg));
```

---

**Q469. Identify salary outliers.**

```java
DoubleSummaryStatistics stats = employees.stream()
    .mapToDouble(Employee::getSalary).summaryStatistics();
double mean = stats.getAverage();
double range = stats.getMax() - stats.getMin();
double threshold = mean + 1.5 * (range / 4); // simple outlier bound

List<Employee> outliers = employees.stream()
    .filter(e -> e.getSalary() > threshold)
    .collect(Collectors.toList());
```

---

**Q470. Find employees with longest tenure.**

```java
LocalDate today = LocalDate.now();
Optional<Employee> longestTenure = employees.stream()
    .min(Comparator.comparing(e -> ChronoUnit.DAYS.between(e.getJoiningDate(), today)));
// min because earliest joining date = longest tenure

longestTenure.ifPresent(e ->
    System.out.println(e.getName() + " joined " + e.getJoiningDate()));
```

---

### Stream Internals & Theory

**Q471. Explain how peek() works vs forEach().**

```java
// peek() is intermediate — passes element through unchanged, for side effects (e.g., debug)
List<Integer> result = Stream.of(1, 2, 3, 4, 5)
    .peek(n -> System.out.println("Before: " + n))
    .filter(n -> n % 2 == 0)
    .peek(n -> System.out.println("After: " + n))
    .collect(Collectors.toList());

// forEach() is terminal — consumes the stream
Stream.of(1, 2, 3).forEach(System.out::println);
// peek leaves stream open; forEach closes it
```

---

**Q472. Why can't streams be reused?**

```java
Stream<String> stream = Stream.of("a", "b", "c");
stream.forEach(System.out::println); // OK

try {
    stream.forEach(System.out::println); // IllegalStateException
} catch (IllegalStateException e) {
    System.out.println("Stream already consumed: " + e.getMessage());
}

// Solution: use a Supplier
Supplier<Stream<String>> supplier = () -> Stream.of("a", "b", "c");
supplier.get().forEach(System.out::println);
supplier.get().forEach(System.out::println); // OK — creates fresh streams
```

---

**Q473. Difference between Collection.stream() and Arrays.stream().**

```java
// Collection.stream() — works on any Collection (List, Set, etc.)
List<String> list = Arrays.asList("a", "b", "c");
Stream<String> s1 = list.stream();

// Arrays.stream() — works on arrays, supports primitive types directly
String[] arr = {"a", "b", "c"};
Stream<String> s2 = Arrays.stream(arr);

int[] intArr = {1, 2, 3};
IntStream s3 = Arrays.stream(intArr); // returns IntStream, not Stream<Integer>
```

---

**Q474. How does parallel stream split the work?**

```java
// Parallel streams use ForkJoinPool.commonPool() by default
// They split data using Spliterator into chunks and process concurrently

List<Integer> numbers = IntStream.rangeClosed(1, 8).boxed().collect(Collectors.toList());
numbers.parallelStream()
    .map(n -> {
        System.out.println(Thread.currentThread().getName() + ": " + n);
        return n * 2;
    })
    .collect(Collectors.toList());
// Output shows different threads processing different elements
```

---

**Q475. What is spliterator and how does it work?**

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6);
Spliterator<Integer> spliterator = numbers.spliterator();

System.out.println("Est. size: " + spliterator.estimateSize()); // 6

// Split into two — used by parallel streams
Spliterator<Integer> half = spliterator.trySplit();
half.forEachRemaining(n -> System.out.print("Half1: " + n + " "));
spliterator.forEachRemaining(n -> System.out.print("Half2: " + n + " "));
```

---

**Q476. Explain the stream pipeline execution.**

```java
// A stream pipeline has 3 parts:
// 1. Source — data source (list, array, generator)
// 2. Intermediate operations — lazy, return Stream
// 3. Terminal operation — eager, triggers execution

// Execution is driven by the terminal operation
// Elements are pulled through the pipeline one by one (vertical processing)

long result = Stream.of(1, 2, 3, 4, 5)   // source
    .filter(n -> n % 2 == 0)             // intermediate (lazy)
    .map(n -> n * n)                     // intermediate (lazy)
    .count();                            // terminal — triggers all operations
// Elements processed: 2 (filtered) -> 4 (mapped), then 4 (filtered) -> 16 (mapped)
```

---

**Q477. What are characteristics of a collector?**

```java
// A Collector has 5 components:
// 1. supplier()     — creates the mutable result container
// 2. accumulator()  — adds a single element to container
// 3. combiner()     — merges two containers (used in parallel)
// 4. finisher()     — transforms container to final result
// 5. characteristics() — CONCURRENT, UNORDERED, IDENTITY_FINISH

// Example — recreating Collectors.toList():
Collector<String, List<String>, List<String>> toListCollector = Collector.of(
    ArrayList::new,                 // supplier
    List::add,                      // accumulator
    (l1, l2) -> { l1.addAll(l2); return l1; }, // combiner
    Collector.Characteristics.IDENTITY_FINISH   // finisher is identity
);
```

---

**Q478. How does groupingBy work internally?**

```java
// groupingBy is essentially:
// 1. Create a HashMap
// 2. For each element, apply classifier to get key
// 3. Add element to the list for that key
// 4. Apply downstream collector to each group's list

// Simplified equivalent:
Map<String, List<Employee>> manual = new HashMap<>();
for (Employee e : employees) {
    manual.computeIfAbsent(e.getDept(), k -> new ArrayList<>()).add(e);
}
// Stream version:
Map<String, List<Employee>> stream = employees.stream()
    .collect(Collectors.groupingBy(Employee::getDept));
```

---

**Q479. Explain combiner function in reduce.**

```java
// The 3-arg reduce() is for parallel streams
// combiner merges partial results from different threads

int sum = Stream.of(1, 2, 3, 4, 5)
    .parallel()
    .reduce(
        0,                          // identity
        (a, b) -> a + b,           // accumulator
        (partialSum1, partialSum2) -> partialSum1 + partialSum2 // combiner
    );
System.out.println(sum); // 15
```

---

**Q480. What is the difference between reduce and collect?**

```java
// reduce — produces a single immutable value; each step creates new value
int sum = Stream.of(1, 2, 3, 4, 5).reduce(0, Integer::sum);

// collect — uses a mutable container (no new object per step — efficient for containers)
List<Integer> list = Stream.of(1, 2, 3, 4, 5)
    .collect(Collectors.toList()); // accumulates into ArrayList

// Use reduce for: sum, product, max, min, concatenation
// Use collect for: building List, Set, Map, joining strings
```

---

### Real Interview Scenarios

**Q481. Given a sentence, find all words with length > 5 and convert to uppercase.**

```java
String sentence = "Java Stream API is very powerful and flexible";
List<String> result = Arrays.stream(sentence.split(" "))
    .filter(w -> w.length() > 5)
    .map(String::toUpperCase)
    .collect(Collectors.toList());
// [STREAM, POWERFUL, FLEXIBLE]
```

---

**Q482. From a list of transactions, find total amount per category.**

```java
Map<String, Double> totalByCategory = transactions.stream()
    .collect(Collectors.groupingBy(
        Transaction::getCategory,
        Collectors.summingDouble(Transaction::getAmount)
    ));
```

---

**Q483. Find the 3 most expensive products.**

```java
List<Product> top3 = products.stream()
    .sorted(Comparator.comparingDouble(Product::getPrice).reversed())
    .limit(3)
    .collect(Collectors.toList());
```

---

**Q484. Calculate moving average of stock prices.**

```java
List<Double> prices = Arrays.asList(100.0, 102.0, 104.0, 103.0, 105.0, 107.0);
int window = 3;

List<Double> movingAvg = IntStream.rangeClosed(window - 1, prices.size() - 1)
    .mapToObj(i -> prices.subList(i - window + 1, i + 1))
    .map(sub -> sub.stream().mapToDouble(Double::doubleValue).average().orElse(0))
    .collect(Collectors.toList());
// [102.0, 103.0, 104.0, 105.0]
```

---

**Q485. Find employees who report to the same manager.**

```java
Map<Integer, List<Employee>> byManager = employees.stream()
    .filter(e -> e.getManagerId() != null)
    .collect(Collectors.groupingBy(Employee::getManagerId));
```

---

**Q486. Implement a simple recommendation system using streams.**

```java
// Recommend products that the user hasn't bought but similar users have
Set<String> userPurchases = Set.of("apple", "banana");
Map<String, Set<String>> allUserPurchases = getSimilarUserPurchases();

List<String> recommendations = allUserPurchases.values().stream()
    .flatMap(Set::stream)
    .filter(item -> !userPurchases.contains(item))
    .distinct()
    .limit(5)
    .collect(Collectors.toList());
```

---

**Q487. Process and aggregate sensor data.**

```java
// Average temperature per sensor per hour
Map<String, Map<Integer, Double>> avgTempBySensorAndHour = sensorReadings.stream()
    .collect(Collectors.groupingBy(
        SensorData::getSensorId,
        Collectors.groupingBy(
            r -> r.getTimestamp().getHour(),
            Collectors.averagingDouble(SensorData::getTemperature)
        )
    ));
```

---

**Q488. Find peak hours from timestamp data.**

```java
Map<Integer, Long> requestsPerHour = requests.stream()
    .collect(Collectors.groupingBy(
        r -> r.getTimestamp().getHour(),
        Collectors.counting()
    ));

int peakHour = requestsPerHour.entrySet().stream()
    .max(Map.Entry.comparingByValue())
    .map(Map.Entry::getKey)
    .orElse(-1);
System.out.println("Peak hour: " + peakHour + ":00");
```

---

**Q489. Analyze log files for error patterns.**

```java
try (Stream<String> lines = Files.lines(Paths.get("app.log"))) {
    Map<String, Long> errorFrequency = lines
        .filter(line -> line.contains("ERROR"))
        .map(line -> line.replaceAll(".*ERROR\\s+", "").split(":")[0]) // extract error type
        .collect(Collectors.groupingBy(e -> e, Collectors.counting()));

    errorFrequency.entrySet().stream()
        .sorted(Map.Entry.<String, Long>comparingByValue().reversed())
        .forEach(e -> System.out.println(e.getKey() + ": " + e.getValue()));
}
```

---

**Q490. Calculate customer churn rate.**

```java
long totalCustomers = customers.stream().count();
long churned = customers.stream()
    .filter(c -> c.getLastOrderDate().isBefore(LocalDate.now().minusMonths(6)))
    .count();

double churnRate = (double) churned / totalCustomers * 100;
System.out.printf("Churn rate: %.2f%%%n", churnRate);
```

---

### Edge Cases & Corner Cases

**Q491. Handle empty collections.**

```java
List<Integer> empty = Collections.emptyList();

// All safe — return default values or Optional.empty()
long count  = empty.stream().count();                              // 0
Optional<Integer> max = empty.stream().max(Integer::compareTo);   // Optional.empty
int sum     = empty.stream().mapToInt(n -> n).sum();              // 0
List<Integer> list = empty.stream().collect(Collectors.toList()); // []
```

---

**Q492. Handle single-element collections.**

```java
List<Integer> single = Collections.singletonList(42);

int max  = single.stream().mapToInt(n -> n).max().getAsInt(); // 42
int min  = single.stream().mapToInt(n -> n).min().getAsInt(); // 42
double avg = single.stream().mapToInt(n -> n).average().getAsDouble(); // 42.0
```

---

**Q493. Handle very large collections.**

```java
// Use parallel streams for CPU-bound operations on large data
long primeCount = LongStream.rangeClosed(2, 10_000_000L)
    .parallel()
    .filter(n -> LongStream.rangeClosed(2, (long) Math.sqrt(n)).allMatch(i -> n % i != 0))
    .count();
System.out.println("Primes up to 10M: " + primeCount);
```

---

**Q494. Deal with null elements in streams.**

```java
List<String> names = Arrays.asList("Alice", null, "Bob", null);

// Option 1: filter out nulls
List<String> noNulls = names.stream()
    .filter(Objects::nonNull)
    .collect(Collectors.toList());

// Option 2: replace nulls with default
List<String> withDefault = names.stream()
    .map(n -> n != null ? n : "Unknown")
    .collect(Collectors.toList());
```

---

**Q495. Handle concurrent modifications.**

```java
// Never modify the source collection during streaming
List<Integer> numbers = new ArrayList<>(Arrays.asList(1, 2, 3, 4, 5));

// WRONG:
// numbers.stream().forEach(n -> { if (n % 2 == 0) numbers.remove(n); }); // throws CME

// CORRECT — removeIf (thread-safe):
numbers.removeIf(n -> n % 2 == 0);
// Or collect a new list:
List<Integer> odds = numbers.stream().filter(n -> n % 2 != 0).collect(Collectors.toList());
```

---

**Q496. Process infinite streams safely.**

```java
// Always use limit() or short-circuiting terminal ops on infinite streams
Stream<Integer> infinite = Stream.iterate(1, n -> n + 1);

// SAFE — limit terminates the stream
List<Integer> first10 = infinite.limit(10).collect(Collectors.toList());

// SAFE — findFirst terminates early
Optional<Integer> firstOver100 = Stream.iterate(1, n -> n + 1)
    .filter(n -> n > 100)
    .findFirst();
System.out.println(firstOver100.get()); // 101

// DANGEROUS — never call count(), forEach() etc. on infinite streams without limit
```

---

**Q497. Handle streams with all identical elements.**

```java
List<Integer> allSame = Arrays.asList(5, 5, 5, 5, 5);

long distinctCount = allSame.stream().distinct().count(); // 1
int sum   = allSame.stream().mapToInt(n -> n).sum();     // 25
int max   = allSame.stream().mapToInt(n -> n).max().getAsInt(); // 5
int min   = allSame.stream().mapToInt(n -> n).min().getAsInt(); // 5
```

---

**Q498. Work with streams containing only nulls.**

```java
List<String> allNulls = Arrays.asList(null, null, null);

// Safe — filter nulls first
long count = allNulls.stream().filter(Objects::nonNull).count(); // 0

// Risky — map/reduce on nulls will throw NPE
// allNulls.stream().map(String::toUpperCase)... // NullPointerException!

List<String> safe = allNulls.stream()
    .filter(Objects::nonNull)
    .collect(Collectors.toList()); // []
```

---

**Q499. Process interleaved data streams.**

```java
// Merge two streams maintaining order interleaving
Stream<Integer> odds  = Stream.of(1, 3, 5, 7, 9);
Stream<Integer> evens = Stream.of(2, 4, 6, 8, 10);

// Simple concat + sort:
List<Integer> merged = Stream.concat(odds, evens)
    .sorted()
    .collect(Collectors.toList());
// [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```

---

**Q500. Handle streams with irregular data patterns.**

```java
// Mixed type data — safely convert and handle irregularities
List<Object> mixedData = Arrays.asList(1, "two", 3.0, "four", 5, null);

// Extract only integers safely
List<Integer> integers = mixedData.stream()
    .filter(o -> o instanceof Integer)
    .map(o -> (Integer) o)
    .collect(Collectors.toList());
// [1, 5]

// Extract only strings safely
List<String> strings = mixedData.stream()
    .filter(o -> o instanceof String)
    .map(o -> (String) o)
    .collect(Collectors.toList());
// [two, four]
```

---

> **Previous:** [Part 4 — Q301 to Q400](java-stream-api-questions-part4(Q301-Q400).md)

---

## Quick Reference — Stream API Cheat Sheet

| Operation | Type | Description | Example |
|---|---|---|---|
| `filter(pred)` | Intermediate | Keep matching elements | `.filter(n -> n > 0)` |
| `map(fn)` | Intermediate | Transform each element | `.map(String::toUpperCase)` |
| `flatMap(fn)` | Intermediate | Flatten nested streams | `.flatMap(List::stream)` |
| `distinct()` | Intermediate | Remove duplicates | `.distinct()` |
| `sorted()` | Intermediate | Sort elements | `.sorted(Comparator.naturalOrder())` |
| `limit(n)` | Intermediate | Take first N elements | `.limit(10)` |
| `skip(n)` | Intermediate | Skip first N elements | `.skip(5)` |
| `peek(fn)` | Intermediate | Debug side-effect | `.peek(System.out::println)` |
| `collect(c)` | Terminal | Gather into collection | `.collect(Collectors.toList())` |
| `forEach(fn)` | Terminal | Consume each element | `.forEach(System.out::println)` |
| `count()` | Terminal | Count elements | `.count()` |
| `reduce(id,fn)` | Terminal | Aggregate to single value | `.reduce(0, Integer::sum)` |
| `findFirst()` | Terminal | First element (Optional) | `.findFirst()` |
| `anyMatch(p)` | Terminal | Any match? (boolean) | `.anyMatch(n -> n > 0)` |
| `allMatch(p)` | Terminal | All match? (boolean) | `.allMatch(n -> n > 0)` |
| `noneMatch(p)` | Terminal | None match? (boolean) | `.noneMatch(Objects::isNull)` |
| `min(cmp)` | Terminal | Minimum element | `.min(Comparator.naturalOrder())` |
| `max(cmp)` | Terminal | Maximum element | `.max(Comparator.naturalOrder())` |
| `toArray()` | Terminal | Convert to array | `.toArray(String[]::new)` |

**Good luck with your Java Stream API interviews!**
