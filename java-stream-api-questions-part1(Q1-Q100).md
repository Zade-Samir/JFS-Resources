# Java Stream API Coding Interview Questions — Part 1 (Q1–Q100)

> **Series:** Part 1 of 5 | Questions 1–100
> **Topics:** Basic Stream Operations, Filtering & Mapping, Sorting, Reduction & Aggregation, Collectors – Basic (Q81–Q100)

---

## 1. Basic Stream Operations

### Creating & Converting Streams

**Q1. Given a list of integers, convert it to a stream and print all elements.**

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
numbers.stream().forEach(n -> System.out.println(n));
// Or using method reference:
numbers.stream().forEach(System.out::println);
```

---

**Q2. Create a stream from an array of strings.**

```java
String[] arr = {"apple", "banana", "cherry"};
Stream<String> stream = Arrays.stream(arr);
stream.forEach(System.out::println);
```

---

**Q3. Create an infinite stream of random numbers and limit it to 10 elements.**

```java
Stream.generate(Math::random)
      .limit(10)
      .forEach(System.out::println);
```

---

**Q4. Create a stream of integers from 1 to 100.**

```java
IntStream.rangeClosed(1, 100)
         .forEach(System.out::println);
```

---

**Q5. Convert an array to a list using streams.**

```java
String[] arr = {"a", "b", "c"};
List<String> list = Arrays.stream(arr).collect(Collectors.toList());
```

---

**Q6. Create a stream from a Map's keys.**

```java
Map<String, Integer> map = Map.of("a", 1, "b", 2);
map.keySet().stream().forEach(System.out::println);
```

---

**Q7. Create a stream from a Map's values.**

```java
Map<String, Integer> map = Map.of("a", 1, "b", 2);
map.values().stream().forEach(System.out::println);
```

---

**Q8. Create a stream from a Map's entries.**

```java
Map<String, Integer> map = Map.of("a", 1, "b", 2);
map.entrySet().stream().forEach(e -> System.out.println(e.getKey() + "=" + e.getValue()));
```

---

**Q9. Create a stream of custom objects (e.g., Employee, Student).**

```java
List<Employee> employees = Arrays.asList(
    new Employee("Alice", 50000),
    new Employee("Bob", 60000)
);
employees.stream().forEach(System.out::println);
```

---

**Q10. Convert a Set to a List using streams.**

```java
Set<String> set = Set.of("x", "y", "z");
List<String> list = set.stream().collect(Collectors.toList());
```

---

### Counting & Iteration

**Q11. Count the total number of elements in a list using streams.**

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
long count = numbers.stream().count();
System.out.println(count); // 5
```

---

**Q12. Print all elements in a list using forEach.**

```java
List<String> names = Arrays.asList("Alice", "Bob", "Charlie");
names.stream().forEach(System.out::println);
```

---

**Q13. Count the number of elements greater than a certain value.**

```java
List<Integer> numbers = Arrays.asList(5, 10, 15, 20, 25);
long count = numbers.stream().filter(n -> n > 10).count();
System.out.println(count); // 3
```

---

**Q14. Count how many strings start with a specific character.**

```java
List<String> names = Arrays.asList("Alice", "Bob", "Anna", "Charlie");
long count = names.stream().filter(s -> s.startsWith("A")).count();
System.out.println(count); // 2
```

---

**Q15. Iterate over a stream and perform operations on each element.**

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
numbers.stream()
       .map(n -> n * 2)
       .forEach(System.out::println); // 2, 4, 6, 8, 10
```

---

## 2. Filtering & Mapping

### Filtering Operations

**Q16. Filter all even numbers from a list of integers.**

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6);
List<Integer> evens = numbers.stream()
                             .filter(n -> n % 2 == 0)
                             .collect(Collectors.toList());
// [2, 4, 6]
```

---

**Q17. Filter all odd numbers from a list of integers.**

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6);
List<Integer> odds = numbers.stream()
                            .filter(n -> n % 2 != 0)
                            .collect(Collectors.toList());
// [1, 3, 5]
```

---

**Q18. Filter strings that start with a specific letter.**

```java
List<String> names = Arrays.asList("Alice", "Bob", "Anna", "Charlie");
List<String> result = names.stream()
                           .filter(s -> s.startsWith("A"))
                           .collect(Collectors.toList());
// [Alice, Anna]
```

---

**Q19. Filter strings that end with a specific letter.**

```java
List<String> names = Arrays.asList("Alice", "Bob", "Charlie", "Mike");
List<String> result = names.stream()
                           .filter(s -> s.endsWith("e"))
                           .collect(Collectors.toList());
// [Alice, Charlie, Mike]
```

---

**Q20. Filter strings that contain a specific substring.**

```java
List<String> words = Arrays.asList("apple", "application", "banana", "appetite");
List<String> result = words.stream()
                           .filter(s -> s.contains("app"))
                           .collect(Collectors.toList());
// [apple, application, appetite]
```

---

**Q21. Filter numbers greater than a specific value.**

```java
List<Integer> numbers = Arrays.asList(3, 7, 12, 18, 25);
List<Integer> result = numbers.stream()
                              .filter(n -> n > 10)
                              .collect(Collectors.toList());
// [12, 18, 25]
```

---

**Q22. Filter numbers less than a specific value.**

```java
List<Integer> numbers = Arrays.asList(3, 7, 12, 18, 25);
List<Integer> result = numbers.stream()
                              .filter(n -> n < 10)
                              .collect(Collectors.toList());
// [3, 7]
```

---

**Q23. Filter numbers within a specific range (e.g., between 10 and 50).**

```java
List<Integer> numbers = Arrays.asList(5, 15, 30, 55, 70);
List<Integer> result = numbers.stream()
                              .filter(n -> n >= 10 && n <= 50)
                              .collect(Collectors.toList());
// [15, 30]
```

---

**Q24. Filter null values from a list.**

```java
List<String> names = Arrays.asList("Alice", null, "Bob", null, "Charlie");
List<String> result = names.stream()
                           .filter(s -> s != null)
                           .collect(Collectors.toList());
// [Alice, Bob, Charlie]
```

---

**Q25. Filter empty strings from a list.**

```java
List<String> words = Arrays.asList("hello", "", "world", "", "java");
List<String> result = words.stream()
                           .filter(s -> !s.isEmpty())
                           .collect(Collectors.toList());
// [hello, world, java]
```

---

**Q26. Filter blank/whitespace strings from a list.**

```java
List<String> words = Arrays.asList("hello", "  ", "world", "\t", "java");
List<String> result = words.stream()
                           .filter(s -> !s.isBlank())
                           .collect(Collectors.toList());
// [hello, world, java]
```

---

**Q27. Filter elements based on multiple conditions.**

```java
List<Integer> numbers = Arrays.asList(1, 4, 9, 12, 15, 20);
List<Integer> result = numbers.stream()
                              .filter(n -> n > 5 && n % 2 == 0)
                              .collect(Collectors.toList());
// [12, 20]
```

---

**Q28. Filter numbers divisible by both 3 and 5.**

```java
List<Integer> numbers = Arrays.asList(5, 10, 15, 20, 30, 45);
List<Integer> result = numbers.stream()
                              .filter(n -> n % 3 == 0 && n % 5 == 0)
                              .collect(Collectors.toList());
// [15, 30, 45]
```

---

**Q29. Filter strings with length greater than 5.**

```java
List<String> words = Arrays.asList("hi", "hello", "stream", "java", "programming");
List<String> result = words.stream()
                           .filter(s -> s.length() > 5)
                           .collect(Collectors.toList());
// [stream, programming]
```

---

**Q30. Filter strings with length equal to a specific value.**

```java
List<String> words = Arrays.asList("hi", "hey", "hello", "java", "bee");
List<String> result = words.stream()
                           .filter(s -> s.length() == 3)
                           .collect(Collectors.toList());
// [hey, bee]
```

---

### Mapping Operations

**Q31. Convert all strings to uppercase using map.**

```java
List<String> names = Arrays.asList("alice", "bob", "charlie");
List<String> result = names.stream()
                           .map(s -> s.toUpperCase())
                           .collect(Collectors.toList());
// [ALICE, BOB, CHARLIE]
```

---

**Q32. Convert all strings to lowercase using map.**

```java
List<String> names = Arrays.asList("ALICE", "BOB", "CHARLIE");
List<String> result = names.stream()
                           .map(s -> s.toLowerCase())
                           .collect(Collectors.toList());
// [alice, bob, charlie]
```

---

**Q33. Extract the length of each string in a list.**

```java
List<String> words = Arrays.asList("apple", "hi", "stream");
List<Integer> lengths = words.stream()
                             .map(s -> s.length())
                             .collect(Collectors.toList());
// [5, 2, 6]
```

---

**Q34. Square all numbers in a list.**

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
List<Integer> squares = numbers.stream()
                               .map(n -> n * n)
                               .collect(Collectors.toList());
// [1, 4, 9, 16, 25]
```

---

**Q35. Multiply all numbers by a specific value.**

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
List<Integer> result = numbers.stream()
                              .map(n -> n * 3)
                              .collect(Collectors.toList());
// [3, 6, 9, 12, 15]
```

---

**Q36. Extract specific fields from a list of objects (e.g., get all employee names).**

```java
List<Employee> employees = Arrays.asList(
    new Employee("Alice", "IT", 60000),
    new Employee("Bob", "HR", 50000)
);
List<String> names = employees.stream()
                              .map(e -> e.getName())
                              .collect(Collectors.toList());
// [Alice, Bob]
```

---

**Q37. Convert a list of strings to a list of their lengths.**

```java
List<String> words = Arrays.asList("apple", "mango", "banana");
List<Integer> lengths = words.stream()
                             .map(String::length)
                             .collect(Collectors.toList());
// [5, 5, 6]
```

---

**Q38. Convert a list of integers to a list of their squares.**

```java
List<Integer> numbers = Arrays.asList(2, 3, 4);
List<Integer> squares = numbers.stream()
                               .map(n -> n * n)
                               .collect(Collectors.toList());
// [4, 9, 16]
```

---

**Q39. Add a prefix to all strings in a list.**

```java
List<String> names = Arrays.asList("Alice", "Bob");
List<String> result = names.stream()
                           .map(s -> "Mr. " + s)
                           .collect(Collectors.toList());
// [Mr. Alice, Mr. Bob]
```

---

**Q40. Add a suffix to all strings in a list.**

```java
List<String> names = Arrays.asList("Alice", "Bob");
List<String> result = names.stream()
                           .map(s -> s + " Jr.")
                           .collect(Collectors.toList());
// [Alice Jr., Bob Jr.]
```

---

**Q41. Extract first character from each string.**

```java
List<String> words = Arrays.asList("apple", "banana", "cherry");
List<Character> result = words.stream()
                              .map(s -> s.charAt(0))
                              .collect(Collectors.toList());
// [a, b, c]
```

---

**Q42. Extract last character from each string.**

```java
List<String> words = Arrays.asList("apple", "banana", "cherry");
List<Character> result = words.stream()
                              .map(s -> s.charAt(s.length() - 1))
                              .collect(Collectors.toList());
// [e, a, y]
```

---

**Q43. Map integers to their corresponding strings.**

```java
List<Integer> numbers = Arrays.asList(1, 2, 3);
List<String> result = numbers.stream()
                             .map(n -> String.valueOf(n))
                             .collect(Collectors.toList());
// ["1", "2", "3"]
```

---

**Q44. Map objects to a different type (e.g., Employee to EmployeeDTO).**

```java
List<Employee> employees = Arrays.asList(new Employee("Alice", "IT", 60000));
List<EmployeeDTO> dtos = employees.stream()
                                  .map(e -> new EmployeeDTO(e.getName(), e.getDept()))
                                  .collect(Collectors.toList());
```

---

**Q45. Convert a list of strings to integers.**

```java
List<String> strNums = Arrays.asList("1", "2", "3", "4");
List<Integer> nums = strNums.stream()
                            .map(s -> Integer.parseInt(s))
                            .collect(Collectors.toList());
// [1, 2, 3, 4]
```

---

## 3. Sorting

### Basic Sorting

**Q46. Sort a list of integers in ascending order.**

```java
List<Integer> numbers = Arrays.asList(5, 2, 8, 1, 9);
List<Integer> sorted = numbers.stream()
                              .sorted()
                              .collect(Collectors.toList());
// [1, 2, 5, 8, 9]
```

---

**Q47. Sort a list of integers in descending order.**

```java
List<Integer> numbers = Arrays.asList(5, 2, 8, 1, 9);
List<Integer> sorted = numbers.stream()
                              .sorted((a, b) -> b - a)
                              .collect(Collectors.toList());
// [9, 8, 5, 2, 1]
```

---

**Q48. Sort a list of strings in alphabetical order.**

```java
List<String> names = Arrays.asList("Charlie", "Alice", "Bob");
List<String> sorted = names.stream()
                           .sorted()
                           .collect(Collectors.toList());
// [Alice, Bob, Charlie]
```

---

**Q49. Sort a list of strings in reverse alphabetical order.**

```java
List<String> names = Arrays.asList("Charlie", "Alice", "Bob");
List<String> sorted = names.stream()
                           .sorted((a, b) -> b.compareTo(a))
                           .collect(Collectors.toList());
// [Charlie, Bob, Alice]
```

---

**Q50. Sort a list of strings by their length (ascending).**

```java
List<String> words = Arrays.asList("banana", "hi", "apple", "stream");
List<String> sorted = words.stream()
                           .sorted((a, b) -> a.length() - b.length())
                           .collect(Collectors.toList());
// [hi, apple, banana, stream]
```

---

**Q51. Sort a list of strings by their length (descending).**

```java
List<String> words = Arrays.asList("banana", "hi", "apple", "stream");
List<String> sorted = words.stream()
                           .sorted((a, b) -> b.length() - a.length())
                           .collect(Collectors.toList());
// [banana, stream, apple, hi]
```

---

**Q52. Sort a list ignoring case sensitivity.**

```java
List<String> names = Arrays.asList("charlie", "Alice", "bob");
List<String> sorted = names.stream()
                           .sorted((a, b) -> a.compareToIgnoreCase(b))
                           .collect(Collectors.toList());
// [Alice, bob, charlie]
```

---

**Q53. Sort a list with custom comparator.**

```java
List<String> words = Arrays.asList("banana", "apple", "cherry");
List<String> sorted = words.stream()
                           .sorted(Comparator.comparing(s -> s.charAt(s.length() - 1)))
                           .collect(Collectors.toList());
// Sorted by last character
```

---

### Object Sorting

**Q54. Sort a list of Employee objects by salary in ascending order.**

```java
List<Employee> sorted = employees.stream()
                                 .sorted((a, b) -> Double.compare(a.getSalary(), b.getSalary()))
                                 .collect(Collectors.toList());
```

---

**Q55. Sort a list of Employee objects by salary in descending order.**

```java
List<Employee> sorted = employees.stream()
                                 .sorted((a, b) -> Double.compare(b.getSalary(), a.getSalary()))
                                 .collect(Collectors.toList());
```

---

**Q56. Sort a list of Employee objects by name.**

```java
List<Employee> sorted = employees.stream()
                                 .sorted((a, b) -> a.getName().compareTo(b.getName()))
                                 .collect(Collectors.toList());
```

---

**Q57. Sort a list of Employee objects by age.**

```java
List<Employee> sorted = employees.stream()
                                 .sorted((a, b) -> a.getAge() - b.getAge())
                                 .collect(Collectors.toList());
```

---

**Q58. Sort a list of Employee objects by multiple fields (e.g., department then salary).**

```java
List<Employee> sorted = employees.stream()
                                 .sorted(Comparator.comparing(Employee::getDept)
                                         .thenComparing(Employee::getSalary))
                                 .collect(Collectors.toList());
```

---

**Q59. Sort a list of Employee objects by joining date.**

```java
List<Employee> sorted = employees.stream()
                                 .sorted((a, b) -> a.getJoiningDate().compareTo(b.getJoiningDate()))
                                 .collect(Collectors.toList());
```

---

**Q60. Sort and then reverse the order.**

```java
List<Employee> sorted = employees.stream()
                                 .sorted(Comparator.comparing(Employee::getName).reversed())
                                 .collect(Collectors.toList());
```

---

## 4. Reduction & Aggregation

### Sum, Min, Max, Average

**Q61. Find the sum of all integers in a list.**

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
int sum = numbers.stream()
                 .mapToInt(n -> n)
                 .sum();
System.out.println(sum); // 15
```

---

**Q62. Find the sum of all even numbers in a list.**

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6);
int sum = numbers.stream()
                 .filter(n -> n % 2 == 0)
                 .mapToInt(n -> n)
                 .sum();
System.out.println(sum); // 12
```

---

**Q63. Find the sum of all odd numbers in a list.**

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6);
int sum = numbers.stream()
                 .filter(n -> n % 2 != 0)
                 .mapToInt(n -> n)
                 .sum();
System.out.println(sum); // 9
```

---

**Q64. Find the product of all numbers in a list.**

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
int product = numbers.stream()
                     .reduce(1, (a, b) -> a * b);
System.out.println(product); // 120
```

---

**Q65. Find the minimum number in a list.**

```java
List<Integer> numbers = Arrays.asList(5, 2, 8, 1, 9);
int min = numbers.stream()
                 .mapToInt(n -> n)
                 .min()
                 .getAsInt();
System.out.println(min); // 1
```

---

**Q66. Find the maximum number in a list.**

```java
List<Integer> numbers = Arrays.asList(5, 2, 8, 1, 9);
int max = numbers.stream()
                 .mapToInt(n -> n)
                 .max()
                 .getAsInt();
System.out.println(max); // 9
```

---

**Q67. Find the average of all numbers in a list.**

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
double avg = numbers.stream()
                    .mapToInt(n -> n)
                    .average()
                    .getAsDouble();
System.out.println(avg); // 3.0
```

---

**Q68. Find the sum of squares of all numbers.**

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4);
int sumOfSquares = numbers.stream()
                          .mapToInt(n -> n * n)
                          .sum();
System.out.println(sumOfSquares); // 30
```

---

**Q69. Find the sum of squares of all even numbers.**

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6);
int result = numbers.stream()
                    .filter(n -> n % 2 == 0)
                    .mapToInt(n -> n * n)
                    .sum();
System.out.println(result); // 56 (4+16+36)
```

---

**Q70. Calculate the total salary of all employees.**

```java
double totalSalary = employees.stream()
                              .mapToDouble(e -> e.getSalary())
                              .sum();
System.out.println(totalSalary);
```

---

### Reduce Operations

**Q71. Concatenate all strings in a list using reduce.**

```java
List<String> words = Arrays.asList("Hello", " ", "World");
String result = words.stream()
                     .reduce("", (a, b) -> a + b);
System.out.println(result); // "Hello World"
```

---

**Q72. Find the longest string using reduce.**

```java
List<String> words = Arrays.asList("apple", "banana", "kiwi", "strawberry");
String longest = words.stream()
                      .reduce("", (a, b) -> a.length() >= b.length() ? a : b);
System.out.println(longest); // strawberry
```

---

**Q73. Find the shortest string using reduce.**

```java
List<String> words = Arrays.asList("apple", "banana", "kiwi", "strawberry");
String shortest = words.stream()
                       .reduce(words.get(0), (a, b) -> a.length() <= b.length() ? a : b);
System.out.println(shortest); // kiwi
```

---

**Q74. Multiply all numbers in a list using reduce.**

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
int product = numbers.stream()
                     .reduce(1, (a, b) -> a * b);
System.out.println(product); // 120
```

---

**Q75. Find the maximum number using reduce.**

```java
List<Integer> numbers = Arrays.asList(3, 7, 2, 9, 4);
int max = numbers.stream()
                 .reduce(Integer.MIN_VALUE, (a, b) -> a > b ? a : b);
System.out.println(max); // 9
```

---

**Q76. Find the minimum number using reduce.**

```java
List<Integer> numbers = Arrays.asList(3, 7, 2, 9, 4);
int min = numbers.stream()
                 .reduce(Integer.MAX_VALUE, (a, b) -> a < b ? a : b);
System.out.println(min); // 2
```

---

**Q77. Join all strings with a delimiter using reduce.**

```java
List<String> words = Arrays.asList("Java", "Stream", "API");
String result = words.stream()
                     .reduce((a, b) -> a + ", " + b)
                     .orElse("");
System.out.println(result); // Java, Stream, API
```

---

**Q78. Calculate factorial using reduce.**

```java
int n = 5;
int factorial = IntStream.rangeClosed(1, n)
                         .reduce(1, (a, b) -> a * b);
System.out.println(factorial); // 120
```

---

**Q79. Implement custom reduction logic.**

```java
// Sum of squares of even numbers
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
int result = numbers.stream()
                    .filter(n -> n % 2 == 0)
                    .map(n -> n * n)
                    .reduce(0, (a, b) -> a + b);
System.out.println(result); // 20
```

---

**Q80. Reduce with initial value vs without initial value.**

```java
List<Integer> numbers = Arrays.asList(1, 2, 3);

// With identity (always returns int)
int withIdentity = numbers.stream().reduce(0, (a, b) -> a + b);

// Without identity (returns Optional)
Optional<Integer> withoutIdentity = numbers.stream().reduce((a, b) -> a + b);

System.out.println(withIdentity);          // 6
System.out.println(withoutIdentity.get()); // 6
```

---

## 5. Collectors — Basic

### toList, toSet, toMap

**Q81. Collect stream elements to a List.**

```java
List<String> names = Arrays.asList("Alice", "Bob", "Charlie");
List<String> result = names.stream()
                           .filter(s -> s.length() > 3)
                           .collect(Collectors.toList());
// [Alice, Charlie]
```

---

**Q82. Collect stream elements to a Set.**

```java
List<Integer> numbers = Arrays.asList(1, 2, 2, 3, 3, 4);
Set<Integer> result = numbers.stream()
                             .collect(Collectors.toSet());
// {1, 2, 3, 4}
```

---

**Q83. Collect stream elements to a specific collection (e.g., TreeSet, LinkedList).**

```java
List<String> names = Arrays.asList("Charlie", "Alice", "Bob");

// TreeSet (sorted)
TreeSet<String> treeSet = names.stream()
                               .collect(Collectors.toCollection(TreeSet::new));

// LinkedList
LinkedList<String> linkedList = names.stream()
                                     .collect(Collectors.toCollection(LinkedList::new));
```

---

**Q84. Convert a list to a Map with index as key.**

```java
List<String> names = Arrays.asList("Alice", "Bob", "Charlie");
Map<Integer, String> map = IntStream.range(0, names.size())
                                    .boxed()
                                    .collect(Collectors.toMap(i -> i, i -> names.get(i)));
// {0=Alice, 1=Bob, 2=Charlie}
```

---

**Q85. Convert a list of objects to a Map (e.g., Employee ID as key, Employee as value).**

```java
Map<Integer, Employee> empMap = employees.stream()
                                         .collect(Collectors.toMap(e -> e.getId(), e -> e));
```

---

**Q86. Convert a list to a Map handling duplicate keys.**

```java
List<String> names = Arrays.asList("Alice", "Bob", "Alice");
Map<String, Integer> nameLength = names.stream()
                                       .collect(Collectors.toMap(
                                           s -> s,
                                           s -> s.length(),
                                           (existing, replacement) -> existing // keep first
                                       ));
```

---

**Q87. Collect to an unmodifiable list.**

```java
List<String> names = Arrays.asList("Alice", "Bob");
List<String> unmodifiable = names.stream()
                                 .collect(Collectors.toUnmodifiableList());
```

---

**Q88. Collect to an unmodifiable set.**

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 2);
Set<Integer> unmodifiable = numbers.stream()
                                   .collect(Collectors.toUnmodifiableSet());
```

---

**Q89. Collect to an unmodifiable map.**

```java
Map<String, Integer> unmodifiable = employees.stream()
                                             .collect(Collectors.toUnmodifiableMap(
                                                 e -> e.getName(),
                                                 e -> e.getSalary()
                                             ));
```

---

**Q90. Convert stream to array.**

```java
List<String> names = Arrays.asList("Alice", "Bob", "Charlie");
String[] arr = names.stream().toArray(String[]::new);
```

---

### Joining Operations

**Q91. Join all strings in a list with comma separator.**

```java
List<String> names = Arrays.asList("Alice", "Bob", "Charlie");
String result = names.stream()
                     .collect(Collectors.joining(", "));
System.out.println(result); // Alice, Bob, Charlie
```

---

**Q92. Join all strings with a custom delimiter.**

```java
List<String> words = Arrays.asList("Java", "Stream", "API");
String result = words.stream()
                     .collect(Collectors.joining(" | "));
System.out.println(result); // Java | Stream | API
```

---

**Q93. Join strings with prefix and suffix.**

```java
List<String> names = Arrays.asList("Alice", "Bob", "Charlie");
String result = names.stream()
                     .collect(Collectors.joining(", ", "[", "]"));
System.out.println(result); // [Alice, Bob, Charlie]
```

---

**Q94. Join strings with space separator.**

```java
List<String> words = Arrays.asList("Hello", "World", "Java");
String result = words.stream()
                     .collect(Collectors.joining(" "));
System.out.println(result); // Hello World Java
```

---

**Q95. Concatenate all strings without separator.**

```java
List<String> parts = Arrays.asList("Java", "Stream", "API");
String result = parts.stream()
                     .collect(Collectors.joining());
System.out.println(result); // JavaStreamAPI
```

---

## 6. Collectors — GroupingBy

### Basic Grouping

**Q96. Group strings by their length.**

```java
List<String> words = Arrays.asList("hi", "hello", "hey", "stream", "java");
Map<Integer, List<String>> grouped = words.stream()
                                          .collect(Collectors.groupingBy(s -> s.length()));
// {2=[hi], 3=[hey], 4=[java], 5=[hello], 6=[stream]}
```

---

**Q97. Group numbers by even/odd.**

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6);
Map<String, List<Integer>> grouped = numbers.stream()
                                            .collect(Collectors.groupingBy(
                                                n -> n % 2 == 0 ? "Even" : "Odd"
                                            ));
// {Even=[2, 4, 6], Odd=[1, 3, 5]}
```

---

**Q98. Group employees by department.**

```java
Map<String, List<Employee>> grouped = employees.stream()
                                               .collect(Collectors.groupingBy(e -> e.getDept()));
```

---

**Q99. Group employees by gender.**

```java
Map<String, List<Employee>> grouped = employees.stream()
                                               .collect(Collectors.groupingBy(e -> e.getGender()));
```

---

**Q100. Group employees by age.**

```java
Map<Integer, List<Employee>> grouped = employees.stream()
                                                .collect(Collectors.groupingBy(e -> e.getAge()));
```

---

> **Next:** [Part 2 — Q101 to Q200](java-stream-api-questions-part2(Q101-Q200).md)
