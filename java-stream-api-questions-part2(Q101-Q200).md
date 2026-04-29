# Java Stream API Coding Interview Questions — Part 2 (Q101–Q200)

> **Series:** Part 2 of 5 | Questions 101–200
> **Topics:** Collectors – GroupingBy (continued), Collectors – Advanced, FlatMap Operations, String Manipulation, Finding & Matching, Distinct & Unique Elements

---

## 6. Collectors — GroupingBy *(continued)*

### Basic Grouping *(continued)*

**Q101. Group employees by salary range.**

```java
Map<String, List<Employee>> grouped = employees.stream()
    .collect(Collectors.groupingBy(e -> {
        if (e.getSalary() < 30000) return "Low";
        else if (e.getSalary() < 70000) return "Mid";
        else return "High";
    }));
```

---

**Q102. Group strings by their first character.**

```java
List<String> words = Arrays.asList("apple", "banana", "avocado", "blueberry", "cherry");
Map<Character, List<String>> grouped = words.stream()
                                            .collect(Collectors.groupingBy(s -> s.charAt(0)));
// {a=[apple, avocado], b=[banana, blueberry], c=[cherry]}
```

---

**Q103. Group numbers by their remainder when divided by a number.**

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9);
Map<Integer, List<Integer>> grouped = numbers.stream()
                                             .collect(Collectors.groupingBy(n -> n % 3));
// {0=[3, 6, 9], 1=[1, 4, 7], 2=[2, 5, 8]}
```

---

**Q104. Group employees by city.**

```java
Map<String, List<Employee>> grouped = employees.stream()
                                               .collect(Collectors.groupingBy(e -> e.getCity()));
```

---

**Q105. Group employees by joining year.**

```java
Map<Integer, List<Employee>> grouped = employees.stream()
                                                .collect(Collectors.groupingBy(
                                                    e -> e.getJoiningDate().getYear()
                                                ));
```

---

### Counting with GroupingBy

**Q106. Count employees in each department.**

```java
Map<String, Long> countByDept = employees.stream()
                                          .collect(Collectors.groupingBy(
                                              e -> e.getDept(),
                                              Collectors.counting()
                                          ));
```

---

**Q107. Count strings of each length.**

```java
List<String> words = Arrays.asList("hi", "hey", "hello", "java", "bee");
Map<Integer, Long> countByLength = words.stream()
                                        .collect(Collectors.groupingBy(
                                            s -> s.length(),
                                            Collectors.counting()
                                        ));
```

---

**Q108. Count even and odd numbers.**

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6);
Map<String, Long> count = numbers.stream()
                                 .collect(Collectors.groupingBy(
                                     n -> n % 2 == 0 ? "Even" : "Odd",
                                     Collectors.counting()
                                 ));
// {Even=3, Odd=3}
```

---

**Q109. Count male and female employees.**

```java
Map<String, Long> count = employees.stream()
                                   .collect(Collectors.groupingBy(
                                       e -> e.getGender(),
                                       Collectors.counting()
                                   ));
```

---

**Q110. Find department with maximum number of employees.**

```java
Map<String, Long> countByDept = employees.stream()
    .collect(Collectors.groupingBy(e -> e.getDept(), Collectors.counting()));

String maxDept = countByDept.entrySet().stream()
    .max((a, b) -> Long.compare(a.getValue(), b.getValue()))
    .map(e -> e.getKey())
    .orElse("None");

System.out.println(maxDept);
```

---

**Q111. Find the frequency of each character in a string.**

```java
String str = "programming";
Map<Character, Long> freq = str.chars()
                               .mapToObj(c -> (char) c)
                               .collect(Collectors.groupingBy(c -> c, Collectors.counting()));
```

---

**Q112. Count occurrences of each element in a list.**

```java
List<String> names = Arrays.asList("Alice", "Bob", "Alice", "Charlie", "Bob", "Alice");
Map<String, Long> freq = names.stream()
                              .collect(Collectors.groupingBy(s -> s, Collectors.counting()));
// {Alice=3, Bob=2, Charlie=1}
```

---

**Q113. Find the most frequent element in a list.**

```java
List<String> names = Arrays.asList("Alice", "Bob", "Alice", "Charlie", "Bob", "Alice");
String mostFrequent = names.stream()
    .collect(Collectors.groupingBy(s -> s, Collectors.counting()))
    .entrySet().stream()
    .max((a, b) -> Long.compare(a.getValue(), b.getValue()))
    .map(e -> e.getKey())
    .orElse("None");

System.out.println(mostFrequent); // Alice
```

---

### Downstream Collectors with GroupingBy

**Q114. Group employees by department and collect their names.**

```java
Map<String, List<String>> namesByDept = employees.stream()
    .collect(Collectors.groupingBy(
        e -> e.getDept(),
        Collectors.mapping(e -> e.getName(), Collectors.toList())
    ));
```

---

**Q115. Group employees by department and find average salary.**

```java
Map<String, Double> avgSalaryByDept = employees.stream()
    .collect(Collectors.groupingBy(
        e -> e.getDept(),
        Collectors.averagingDouble(e -> e.getSalary())
    ));
```

---

**Q116. Group employees by department and find total salary.**

```java
Map<String, Double> totalSalaryByDept = employees.stream()
    .collect(Collectors.groupingBy(
        e -> e.getDept(),
        Collectors.summingDouble(e -> e.getSalary())
    ));
```

---

**Q117. Group employees by department and find maximum salary.**

```java
Map<String, Optional<Employee>> maxSalaryByDept = employees.stream()
    .collect(Collectors.groupingBy(
        e -> e.getDept(),
        Collectors.maxBy((a, b) -> Double.compare(a.getSalary(), b.getSalary()))
    ));
```

---

**Q118. Group employees by department and find minimum salary.**

```java
Map<String, Optional<Employee>> minSalaryByDept = employees.stream()
    .collect(Collectors.groupingBy(
        e -> e.getDept(),
        Collectors.minBy((a, b) -> Double.compare(a.getSalary(), b.getSalary()))
    ));
```

---

**Q119. Group employees by department and count them.**

```java
Map<String, Long> countByDept = employees.stream()
    .collect(Collectors.groupingBy(e -> e.getDept(), Collectors.counting()));
```

---

**Q120. Group employees by department and find the highest paid employee.**

```java
Map<String, Optional<Employee>> highestPaidByDept = employees.stream()
    .collect(Collectors.groupingBy(
        e -> e.getDept(),
        Collectors.maxBy(Comparator.comparingDouble(Employee::getSalary))
    ));
```

---

**Q121. Group employees by department and sort by salary.**

```java
Map<String, List<Employee>> sortedByDept = employees.stream()
    .collect(Collectors.groupingBy(
        e -> e.getDept(),
        Collectors.collectingAndThen(
            Collectors.toList(),
            list -> list.stream()
                        .sorted((a, b) -> Double.compare(a.getSalary(), b.getSalary()))
                        .collect(Collectors.toList())
        )
    ));
```

---

**Q122. Group students by grade and find average marks.**

```java
Map<String, Double> avgMarksByGrade = students.stream()
    .collect(Collectors.groupingBy(
        s -> s.getGrade(),
        Collectors.averagingDouble(s -> s.getMarks())
    ));
```

---

**Q123. Group employees by department and collect to Set.**

```java
Map<String, Set<Employee>> setByDept = employees.stream()
    .collect(Collectors.groupingBy(e -> e.getDept(), Collectors.toSet()));
```

---

**Q124. Group by multiple levels (nested grouping).**

```java
// Group by department, then by gender
Map<String, Map<String, List<Employee>>> nested = employees.stream()
    .collect(Collectors.groupingBy(
        e -> e.getDept(),
        Collectors.groupingBy(e -> e.getGender())
    ));
```

---

## 7. Collectors — Advanced

### PartitioningBy

**Q125. Partition numbers into even and odd using partitioningBy.**

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6);
Map<Boolean, List<Integer>> partitioned = numbers.stream()
    .collect(Collectors.partitioningBy(n -> n % 2 == 0));
// {true=[2, 4, 6], false=[1, 3, 5]}
```

---

**Q126. Partition employees into high earners (>50000) and others.**

```java
Map<Boolean, List<Employee>> partitioned = employees.stream()
    .collect(Collectors.partitioningBy(e -> e.getSalary() > 50000));
// true = high earners, false = others
```

---

**Q127. Partition strings into palindromes and non-palindromes.**

```java
List<String> words = Arrays.asList("madam", "java", "level", "stream", "racecar");
Map<Boolean, List<String>> partitioned = words.stream()
    .collect(Collectors.partitioningBy(
        s -> s.equals(new StringBuilder(s).reverse().toString())
    ));
```

---

**Q128. Partition employees by age (above 30 and below 30).**

```java
Map<Boolean, List<Employee>> partitioned = employees.stream()
    .collect(Collectors.partitioningBy(e -> e.getAge() > 30));
```

---

**Q129. Partition products by availability (in stock or out of stock).**

```java
Map<Boolean, List<Product>> partitioned = products.stream()
    .collect(Collectors.partitioningBy(p -> p.getStock() > 0));
```

---

### Mapping Collector

**Q130. Group employees by department and map to their names.**

```java
Map<String, List<String>> namesByDept = employees.stream()
    .collect(Collectors.groupingBy(
        e -> e.getDept(),
        Collectors.mapping(Employee::getName, Collectors.toList())
    ));
```

---

**Q131. Group employees by department and map to their salaries.**

```java
Map<String, List<Double>> salariesByDept = employees.stream()
    .collect(Collectors.groupingBy(
        e -> e.getDept(),
        Collectors.mapping(Employee::getSalary, Collectors.toList())
    ));
```

---

**Q132. Group strings by length and convert to uppercase.**

```java
Map<Integer, List<String>> result = words.stream()
    .collect(Collectors.groupingBy(
        String::length,
        Collectors.mapping(String::toUpperCase, Collectors.toList())
    ));
```

---

**Q133. Use mapping collector to transform data after grouping.**

```java
// Group by dept, get CSV of names
Map<String, String> csvNamesByDept = employees.stream()
    .collect(Collectors.groupingBy(
        Employee::getDept,
        Collectors.mapping(Employee::getName, Collectors.joining(", "))
    ));
```

---

### FlatMapping Collector

**Q134. Group employees by department and flatten their skills.**

```java
// Assuming Employee has List<String> getSkills()
Map<String, List<String>> skillsByDept = employees.stream()
    .collect(Collectors.groupingBy(
        Employee::getDept,
        Collectors.flatMapping(e -> e.getSkills().stream(), Collectors.toList())
    ));
```

---

**Q135. Flatten nested lists after grouping.**

```java
Map<String, List<String>> result = data.stream()
    .collect(Collectors.groupingBy(
        Item::getCategory,
        Collectors.flatMapping(item -> item.getTags().stream(), Collectors.toList())
    ));
```

---

**Q136. Group orders by customer and flatten line items.**

```java
Map<String, List<String>> itemsByCustomer = orders.stream()
    .collect(Collectors.groupingBy(
        Order::getCustomer,
        Collectors.flatMapping(o -> o.getItems().stream(), Collectors.toList())
    ));
```

---

**Q137. Use flatMapping with groupingBy.**

```java
Map<String, Set<String>> result = employees.stream()
    .collect(Collectors.groupingBy(
        Employee::getDept,
        Collectors.flatMapping(e -> e.getSkills().stream(), Collectors.toSet())
    ));
```

---

### CollectingAndThen

**Q138. Group employees by department and get unmodifiable lists.**

```java
Map<String, List<Employee>> result = employees.stream()
    .collect(Collectors.groupingBy(
        Employee::getDept,
        Collectors.collectingAndThen(Collectors.toList(), Collections::unmodifiableList)
    ));
```

---

**Q139. Find max element and wrap in custom object using collectingAndThen.**

```java
String longestName = employees.stream()
    .collect(Collectors.collectingAndThen(
        Collectors.maxBy(Comparator.comparingInt(e -> e.getName().length())),
        opt -> opt.map(Employee::getName).orElse("N/A")
    ));
```

---

**Q140. Calculate average and format result using collectingAndThen.**

```java
String formatted = employees.stream()
    .collect(Collectors.collectingAndThen(
        Collectors.averagingDouble(Employee::getSalary),
        avg -> String.format("Average Salary: %.2f", avg)
    ));
```

---

**Q141. Sort after collecting using collectingAndThen.**

```java
List<Employee> sortedList = employees.stream()
    .collect(Collectors.collectingAndThen(
        Collectors.toList(),
        list -> { list.sort(Comparator.comparing(Employee::getName)); return list; }
    ));
```

---

**Q142. Find second highest salary in each department.**

```java
Map<String, Optional<Double>> result = employees.stream()
    .collect(Collectors.groupingBy(
        Employee::getDept,
        Collectors.collectingAndThen(
            Collectors.mapping(Employee::getSalary,
                Collectors.collectingAndThen(
                    Collectors.toList(),
                    list -> list.stream().distinct().sorted(Collections.reverseOrder()).skip(1).findFirst()
                )),
            opt -> opt
        )
    ));
```

---

### Filtering Collector

**Q143. Group employees by department and filter those earning >50000.**

```java
Map<String, List<Employee>> result = employees.stream()
    .collect(Collectors.groupingBy(
        Employee::getDept,
        Collectors.filtering(e -> e.getSalary() > 50000, Collectors.toList())
    ));
```

---

**Q144. Use filtering collector with groupingBy to exclude elements.**

```java
Map<String, Long> countHighEarners = employees.stream()
    .collect(Collectors.groupingBy(
        Employee::getDept,
        Collectors.filtering(e -> e.getSalary() > 60000, Collectors.counting())
    ));
```

---

**Q145. Filter and group in a single operation.**

```java
// Get names of employees earning > 50000 grouped by dept
Map<String, List<String>> result = employees.stream()
    .collect(Collectors.groupingBy(
        Employee::getDept,
        Collectors.filtering(
            e -> e.getSalary() > 50000,
            Collectors.mapping(Employee::getName, Collectors.toList())
        )
    ));
```

---

## 8. FlatMap Operations

### Basic FlatMap

**Q146. Flatten a list of lists into a single list.**

```java
List<List<Integer>> nested = Arrays.asList(
    Arrays.asList(1, 2, 3),
    Arrays.asList(4, 5),
    Arrays.asList(6, 7, 8)
);
List<Integer> flat = nested.stream()
                           .flatMap(list -> list.stream())
                           .collect(Collectors.toList());
// [1, 2, 3, 4, 5, 6, 7, 8]
```

---

**Q147. Flatten a list of arrays into a single list.**

```java
List<String[]> arrays = Arrays.asList(
    new String[]{"a", "b"},
    new String[]{"c", "d"}
);
List<String> flat = arrays.stream()
                          .flatMap(arr -> Arrays.stream(arr))
                          .collect(Collectors.toList());
// [a, b, c, d]
```

---

**Q148. Convert a list of strings to a stream of characters.**

```java
List<String> words = Arrays.asList("Java", "Stream");
List<Character> chars = words.stream()
                             .flatMap(s -> s.chars().mapToObj(c -> (char) c))
                             .collect(Collectors.toList());
// [J, a, v, a, S, t, r, e, a, m]
```

---

**Q149. Split strings and flatten the results.**

```java
List<String> sentences = Arrays.asList("hello world", "java stream api");
List<String> words = sentences.stream()
                              .flatMap(s -> Arrays.stream(s.split(" ")))
                              .collect(Collectors.toList());
// [hello, world, java, stream, api]
```

---

**Q150. Flatten a list of sets into a single list.**

```java
List<Set<String>> sets = Arrays.asList(
    new HashSet<>(Arrays.asList("a", "b")),
    new HashSet<>(Arrays.asList("c", "d"))
);
List<String> flat = sets.stream()
                        .flatMap(set -> set.stream())
                        .collect(Collectors.toList());
```

---

**Q151. Flatten Optional values.**

```java
List<Optional<String>> optionals = Arrays.asList(
    Optional.of("apple"),
    Optional.empty(),
    Optional.of("banana")
);
List<String> result = optionals.stream()
                               .flatMap(opt -> opt.stream())
                               .collect(Collectors.toList());
// [apple, banana]
```

---

**Q152. Flatten nested collections.**

```java
List<List<List<Integer>>> nested = Arrays.asList(
    Arrays.asList(Arrays.asList(1, 2), Arrays.asList(3, 4)),
    Arrays.asList(Arrays.asList(5, 6))
);
List<Integer> flat = nested.stream()
                           .flatMap(l -> l.stream())
                           .flatMap(l -> l.stream())
                           .collect(Collectors.toList());
// [1, 2, 3, 4, 5, 6]
```

---

### Complex FlatMap Scenarios

**Q153. Flatten a list of Employee lists (from multiple departments).**

```java
List<List<Employee>> departments = Arrays.asList(itDept, hrDept, financeDept);
List<Employee> allEmployees = departments.stream()
                                         .flatMap(dept -> dept.stream())
                                         .collect(Collectors.toList());
```

---

**Q154. Split sentences into words and flatten.**

```java
List<String> sentences = Arrays.asList("I love Java", "Stream API is powerful");
List<String> words = sentences.stream()
                              .flatMap(s -> Arrays.stream(s.split(" ")))
                              .collect(Collectors.toList());
```

---

**Q155. Extract all unique characters from a list of strings.**

```java
List<String> words = Arrays.asList("hello", "world", "java");
Set<Character> uniqueChars = words.stream()
                                  .flatMap(s -> s.chars().mapToObj(c -> (char) c))
                                  .collect(Collectors.toSet());
```

---

**Q156. Flatten a list of lists and filter results.**

```java
List<List<Integer>> nested = Arrays.asList(
    Arrays.asList(1, 2, 3, 4),
    Arrays.asList(5, 6, 7, 8)
);
List<Integer> evenNumbers = nested.stream()
                                  .flatMap(list -> list.stream())
                                  .filter(n -> n % 2 == 0)
                                  .collect(Collectors.toList());
// [2, 4, 6, 8]
```

---

**Q157. Flatten and map in combination.**

```java
List<String> words = Arrays.asList("hello", "world");
List<String> upperChars = words.stream()
                               .flatMap(s -> s.chars().mapToObj(c -> String.valueOf((char) c)))
                               .map(String::toUpperCase)
                               .collect(Collectors.toList());
```

---

**Q158. Flatten a stream of streams.**

```java
Stream<Stream<Integer>> streamOfStreams = Stream.of(
    Stream.of(1, 2, 3),
    Stream.of(4, 5, 6)
);
List<Integer> flat = streamOfStreams.flatMap(s -> s)
                                    .collect(Collectors.toList());
// [1, 2, 3, 4, 5, 6]
```

---

**Q159. Get all unique words from a list of sentences.**

```java
List<String> sentences = Arrays.asList("I love Java", "Java is great", "I love streams");
Set<String> uniqueWords = sentences.stream()
                                   .flatMap(s -> Arrays.stream(s.split(" ")))
                                   .collect(Collectors.toSet());
```

---

**Q160. Flatten map values into a single list.**

```java
Map<String, List<String>> map = Map.of(
    "fruits", Arrays.asList("apple", "banana"),
    "veggies", Arrays.asList("carrot", "pea")
);
List<String> allValues = map.values().stream()
                            .flatMap(list -> list.stream())
                            .collect(Collectors.toList());
```

---

## 9. String Manipulation

### Character Operations

**Q161. Find the first non-repeated character in a string.**

```java
String str = "programming";
char result = str.chars()
                 .mapToObj(c -> (char) c)
                 .collect(Collectors.groupingBy(c -> c, LinkedHashMap::new, Collectors.counting()))
                 .entrySet().stream()
                 .filter(e -> e.getValue() == 1)
                 .map(e -> e.getKey())
                 .findFirst()
                 .orElse('\0');
System.out.println(result); // 'p'... wait: actually 'o' — first non-repeated
```

---

**Q162. Find all duplicate characters in a string.**

```java
String str = "programming";
Set<Character> duplicates = str.chars()
    .mapToObj(c -> (char) c)
    .collect(Collectors.groupingBy(c -> c, Collectors.counting()))
    .entrySet().stream()
    .filter(e -> e.getValue() > 1)
    .map(e -> e.getKey())
    .collect(Collectors.toSet());
// [r, g, m]
```

---

**Q163. Count the frequency of each character in a string.**

```java
String str = "hello";
Map<Character, Long> freq = str.chars()
                               .mapToObj(c -> (char) c)
                               .collect(Collectors.groupingBy(c -> c, Collectors.counting()));
// {h=1, e=1, l=2, o=1}
```

---

**Q164. Find the most frequent character in a string.**

```java
String str = "programming";
char mostFrequent = str.chars()
    .mapToObj(c -> (char) c)
    .collect(Collectors.groupingBy(c -> c, Collectors.counting()))
    .entrySet().stream()
    .max((a, b) -> Long.compare(a.getValue(), b.getValue()))
    .map(e -> e.getKey())
    .orElse('\0');
```

---

**Q165. Remove duplicate characters from a string.**

```java
String str = "programming";
String result = str.chars()
                   .distinct()
                   .collect(StringBuilder::new, StringBuilder::appendCodePoint, StringBuilder::append)
                   .toString();
System.out.println(result); // "progamin"
```

---

**Q166. Check if two strings are anagrams.**

```java
String s1 = "listen";
String s2 = "silent";
boolean isAnagram = s1.chars().sorted().boxed().collect(Collectors.toList())
                      .equals(s2.chars().sorted().boxed().collect(Collectors.toList()));
System.out.println(isAnagram); // true
```

---

**Q167. Reverse each word in a sentence.**

```java
String sentence = "Hello World Java";
String result = Arrays.stream(sentence.split(" "))
                      .map(w -> new StringBuilder(w).reverse().toString())
                      .collect(Collectors.joining(" "));
System.out.println(result); // olleH dlroW avaJ
```

---

**Q168. Reverse a string using streams.**

```java
String str = "Hello";
String reversed = str.chars()
                     .mapToObj(c -> String.valueOf((char) c))
                     .reduce("", (a, b) -> b + a);
System.out.println(reversed); // olleH
```

---

**Q169. Check if a string is a palindrome using streams.**

```java
String str = "racecar";
boolean isPalindrome = IntStream.range(0, str.length() / 2)
                                .allMatch(i -> str.charAt(i) == str.charAt(str.length() - 1 - i));
System.out.println(isPalindrome); // true
```

---

### Word Operations

**Q170. Find the longest word in a sentence.**

```java
String sentence = "I love Java stream programming";
String longest = Arrays.stream(sentence.split(" "))
                       .max(Comparator.comparingInt(String::length))
                       .orElse("");
System.out.println(longest); // programming
```

---

**Q171. Find the shortest word in a sentence.**

```java
String sentence = "I love Java stream programming";
String shortest = Arrays.stream(sentence.split(" "))
                        .min(Comparator.comparingInt(String::length))
                        .orElse("");
System.out.println(shortest); // I
```

---

**Q172. Count the number of words in a sentence.**

```java
String sentence = "Java Stream API is powerful";
long count = Arrays.stream(sentence.split(" "))
                   .filter(w -> !w.isEmpty())
                   .count();
System.out.println(count); // 5
```

---

**Q173. Count vowels in a string.**

```java
String str = "programming";
long count = str.chars()
                .filter(c -> "aeiouAEIOU".indexOf(c) != -1)
                .count();
System.out.println(count); // 3
```

---

**Q174. Count consonants in a string.**

```java
String str = "programming";
long count = str.chars()
                .filter(Character::isLetter)
                .filter(c -> "aeiouAEIOU".indexOf(c) == -1)
                .count();
System.out.println(count); // 8
```

---

**Q175. Find all palindromic words in a sentence.**

```java
String sentence = "madam went to the racecar level";
List<String> palindromes = Arrays.stream(sentence.split(" "))
    .filter(w -> w.equals(new StringBuilder(w).reverse().toString()))
    .collect(Collectors.toList());
// [madam, racecar, level]
```

---

**Q176. Capitalize the first letter of each word.**

```java
String sentence = "hello world java";
String result = Arrays.stream(sentence.split(" "))
                      .map(w -> Character.toUpperCase(w.charAt(0)) + w.substring(1))
                      .collect(Collectors.joining(" "));
System.out.println(result); // Hello World Java
```

---

**Q177. Convert string to title case.**

```java
String sentence = "the quick brown fox";
String titleCase = Arrays.stream(sentence.split(" "))
    .map(w -> w.isEmpty() ? w : Character.toUpperCase(w.charAt(0)) + w.substring(1).toLowerCase())
    .collect(Collectors.joining(" "));
System.out.println(titleCase); // The Quick Brown Fox
```

---

**Q178. Remove all whitespace from a string.**

```java
String str = "Hello World Java Stream";
String result = str.chars()
                   .filter(c -> !Character.isWhitespace(c))
                   .collect(StringBuilder::new, StringBuilder::appendCodePoint, StringBuilder::append)
                   .toString();
System.out.println(result); // HelloWorldJavaStream
```

---

**Q179. Find words with a specific length.**

```java
String sentence = "I love Java stream programming";
int targetLength = 4;
List<String> result = Arrays.stream(sentence.split(" "))
                            .filter(w -> w.length() == targetLength)
                            .collect(Collectors.toList());
// [love, Java]
```

---

**Q180. Find words starting with a vowel.**

```java
String sentence = "apple and orange banana";
List<String> result = Arrays.stream(sentence.split(" "))
                            .filter(w -> "aeiouAEIOU".indexOf(w.charAt(0)) != -1)
                            .collect(Collectors.toList());
// [apple, and, orange]
```

---

## 10. Finding & Matching

### Find Operations

**Q181. Find the first element in a stream.**

```java
List<Integer> numbers = Arrays.asList(5, 3, 8, 1, 4);
Optional<Integer> first = numbers.stream().findFirst();
System.out.println(first.get()); // 5
```

---

**Q182. Find any element in a parallel stream.**

```java
List<Integer> numbers = Arrays.asList(5, 3, 8, 1, 4);
Optional<Integer> any = numbers.parallelStream().findAny();
System.out.println(any.get()); // any element (non-deterministic)
```

---

**Q183. Find the first even number in a list.**

```java
List<Integer> numbers = Arrays.asList(1, 3, 5, 4, 6, 8);
Optional<Integer> firstEven = numbers.stream()
                                     .filter(n -> n % 2 == 0)
                                     .findFirst();
System.out.println(firstEven.get()); // 4
```

---

**Q184. Find the first string starting with 'A'.**

```java
List<String> names = Arrays.asList("Bob", "Alice", "Anna", "Charlie");
Optional<String> first = names.stream()
                              .filter(s -> s.startsWith("A"))
                              .findFirst();
System.out.println(first.get()); // Alice
```

---

**Q185. Find the first employee with salary > 50000.**

```java
Optional<Employee> emp = employees.stream()
                                  .filter(e -> e.getSalary() > 50000)
                                  .findFirst();
emp.ifPresent(e -> System.out.println(e.getName()));
```

---

**Q186. Find the first element greater than 100.**

```java
List<Integer> numbers = Arrays.asList(50, 80, 120, 200);
Optional<Integer> result = numbers.stream()
                                  .filter(n -> n > 100)
                                  .findFirst();
System.out.println(result.get()); // 120
```

---

**Q187. Find the last element in a stream.**

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
Optional<Integer> last = numbers.stream()
                                .reduce((a, b) -> b);
System.out.println(last.get()); // 5
```

---

**Q188. Find the nth element in a stream.**

```java
List<Integer> numbers = Arrays.asList(10, 20, 30, 40, 50);
int n = 3; // 3rd element (1-based)
Optional<Integer> nth = numbers.stream()
                               .skip(n - 1)
                               .findFirst();
System.out.println(nth.get()); // 30
```

---

### Matching Operations

**Q189. Check if any element matches a condition (anyMatch).**

```java
List<Integer> numbers = Arrays.asList(1, 3, 5, 8, 9);
boolean hasEven = numbers.stream().anyMatch(n -> n % 2 == 0);
System.out.println(hasEven); // true
```

---

**Q190. Check if all elements match a condition (allMatch).**

```java
List<Integer> numbers = Arrays.asList(2, 4, 6, 8);
boolean allEven = numbers.stream().allMatch(n -> n % 2 == 0);
System.out.println(allEven); // true
```

---

**Q191. Check if no element matches a condition (noneMatch).**

```java
List<Integer> numbers = Arrays.asList(1, 3, 5, 7);
boolean noEven = numbers.stream().noneMatch(n -> n % 2 == 0);
System.out.println(noEven); // true
```

---

**Q192. Check if any string contains a specific substring.**

```java
List<String> words = Arrays.asList("apple", "banana", "cherry");
boolean result = words.stream().anyMatch(s -> s.contains("nan"));
System.out.println(result); // true
```

---

**Q193. Check if all numbers are positive.**

```java
List<Integer> numbers = Arrays.asList(3, 5, 7, 9);
boolean allPositive = numbers.stream().allMatch(n -> n > 0);
System.out.println(allPositive); // true
```

---

**Q194. Check if all strings are non-empty.**

```java
List<String> words = Arrays.asList("hello", "world", "java");
boolean allNonEmpty = words.stream().allMatch(s -> !s.isEmpty());
System.out.println(allNonEmpty); // true
```

---

**Q195. Check if any employee salary is above 100000.**

```java
boolean hasHighEarner = employees.stream()
                                 .anyMatch(e -> e.getSalary() > 100000);
System.out.println(hasHighEarner);
```

---

**Q196. Check if all employees are adults (age >= 18).**

```java
boolean allAdults = employees.stream()
                             .allMatch(e -> e.getAge() >= 18);
System.out.println(allAdults);
```

---

**Q197. Check if no employee has zero salary.**

```java
boolean noZeroSalary = employees.stream()
                                .noneMatch(e -> e.getSalary() == 0);
System.out.println(noZeroSalary);
```

---

**Q198. Check if any number is prime.**

```java
List<Integer> numbers = Arrays.asList(4, 6, 8, 7, 10);
boolean hasPrime = numbers.stream()
    .anyMatch(n -> n > 1 && IntStream.rangeClosed(2, (int) Math.sqrt(n)).allMatch(i -> n % i != 0));
System.out.println(hasPrime); // true (7 is prime)
```

---

## 11. Distinct & Unique Elements

### Distinct Operations

**Q199. Remove duplicate elements from a list.**

```java
List<Integer> numbers = Arrays.asList(1, 2, 2, 3, 3, 4, 1);
List<Integer> distinct = numbers.stream()
                                .distinct()
                                .collect(Collectors.toList());
// [1, 2, 3, 4]
```

---

**Q200. Get distinct numbers from a list.**

```java
List<Integer> numbers = Arrays.asList(5, 3, 5, 2, 8, 3, 1);
List<Integer> distinct = numbers.stream()
                                .distinct()
                                .sorted()
                                .collect(Collectors.toList());
// [1, 2, 3, 5, 8]
```

---

> **Previous:** [Part 1 — Q1 to Q100](java-stream-api-questions-part1(Q1-Q100).md)
> **Next:** [Part 3 — Q201 to Q300](java-stream-api-questions-part3(Q201-Q300).md)
