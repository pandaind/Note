~~~java
import java.util.*;
import java.util.stream.*;

public class Main {
  public static void main(String[] args) {
    List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);

    // filter
    List<Integer> evenNumbers = numbers.stream()
        .filter(n -> n % 2 == 0)
        .collect(Collectors.toList());
    System.out.println("Even Numbers: " + evenNumbers);

    // map
    List<Integer> squaredNumbers = numbers.stream()
        .map(n -> n * n)
        .collect(Collectors.toList());
    System.out.println("Squared Numbers: " + squaredNumbers);

    // flatMap
    List<Integer> flatMappedNumbers = numbers.stream()
        .flatMap(n -> Stream.of(n, n + 1))
        .collect(Collectors.toList());
    System.out.println("FlatMapped Numbers: " + flatMappedNumbers);

    // distinct
    List<Integer> distinctNumbers = flatMappedNumbers.stream()
        .distinct()
        .collect(Collectors.toList());
    System.out.println("Distinct Numbers: " + distinctNumbers);

    // sorted
    List<Integer> sortedNumbers = numbers.stream()
        .sorted(Comparator.comparingInt(a -> a))
        .collect(Collectors.toList());
    System.out.println("Sorted Numbers: " + sortedNumbers);

    // peek
    List<Integer> peekedNumbers = numbers.stream()
        .peek(n -> System.out.println("Peeked: " + n))
        .collect(Collectors.toList());

    // limit
    List<Integer> limitedNumbers = numbers.stream()
        .limit(5)
        .toList();
    System.out.println("Limited Numbers: " + limitedNumbers);

    // skip
    List<Integer> skippedNumbers = numbers.stream()
        .skip(5)
        .toList();
    System.out.println("Skipped Numbers: " + skippedNumbers);

    // forEach
    System.out.print("ForEach: ");
    numbers.forEach(n -> System.out.print(n + " "));
    System.out.println();

    // collect
    Set<Integer> collectedSet = numbers.stream().collect(Collectors.toSet());
    System.out.println("Collected Set: " + collectedSet);

    // reduce
    int sum = numbers.stream()
        .reduce(1, (a,b)-> a*b);
    System.out.println("Sum: " + sum);

    // count
    long count = numbers.stream()
        .count();
    System.out.println("Count: " + count);

    // anyMatch
    boolean anyMatch = numbers.stream()
        .anyMatch(n -> n > 5);
    System.out.println("Any Match > 5: " + anyMatch);

    // allMatch
    boolean allMatch = numbers.stream()
        .allMatch(n -> n > 0);
    System.out.println("All Match > 0: " + allMatch);

    // noneMatch
    boolean noneMatch = numbers.stream()
        .noneMatch(n -> n < 0);
    System.out.println("None Match < 0: " + noneMatch);

    // findFirst
    Optional<Integer> first = numbers.stream()
        .findFirst();
    System.out.println("First: " + first.orElse(-1));

    // findAny
    Optional<Integer> any = numbers.stream()
        .findAny();
    System.out.println("Any: " + any.orElse(-1));

    // max
    Optional<Integer> max = numbers.stream()
        .max(Integer::compareTo);
    System.out.println("Max: " + max.orElse(-1));

    // min
    Optional<Integer> min = numbers.stream()
        .min(Integer::compareTo);
    System.out.println("Min: " + min.orElse(-1));

    // Create HashMap from List of integers
    Map<Integer, Integer> numberSquareMap = numbers.stream()
        .collect(Collectors.toMap(n -> n+1, n -> n*n));
    System.out.println("Number-Square Map: " + numberSquareMap);

    // Create HashMap from array of strings
    String[] words = {"apple", "banana", "cherry", "apple"};
    Map<String, Integer> wordLengthMap = Arrays.stream(words)
        .collect(Collectors.toMap(w -> w, w -> w.length(), (any1, any2) -> any1));
    System.out.println("Word-Length Map: " + wordLengthMap);

    // Create HashMap from Set of characters
    Set<Character> characters = new HashSet<>(Arrays.asList('a', 'b', 'c'));
    Map<Character, Integer> charAsciiMap = characters.stream()
        .collect(Collectors.toMap(ch -> ch, ch -> (int) ch));
    System.out.println("Char-ASCII Map: " + charAsciiMap);


    // takeWhile
    List<Integer> takenWhile = numbers.stream()
        .takeWhile(n -> n < 5)
        .collect(Collectors.toList());
    System.out.println("Taken While < 5: " + takenWhile);

    // dropWhile
    List<Integer> droppedWhile = numbers.stream()
        .dropWhile(n -> n < 5)
        .collect(Collectors.toList());
    System.out.println("Dropped While < 5: " + droppedWhile);

    // iterate
    List<Integer> iteratedNumbers = Stream.iterate(1, n -> n + 1)
        .limit(10)
        .collect(Collectors.toList());
    System.out.println("Iterated Numbers: " + iteratedNumbers);

    // generate
    List<Double> generatedNumbers = Stream.generate(Math::random)
        .limit(5)
        .collect(Collectors.toList());
    System.out.println("Generated Numbers: " + generatedNumbers);

    // boxed
    List<Integer> boxedNumbers = IntStream.range(1, 11) // IntStream of 1 to 10
        .boxed() // Convert IntStream to Stream<Integer>
        .collect(Collectors.toList());
    System.out.println("Boxed Numbers: " + boxedNumbers);

    List<String> strings = Arrays.asList("apple", "banana", "cherry", "date");

    // forEach
    System.out.print("forEach: ");
    strings.parallelStream().forEach(word -> System.out.print(word + " "));
    System.out.println();

    // forEachOrdered
    System.out.print("forEachOrdered: ");
    strings.parallelStream().forEachOrdered(word -> System.out.print(word + " "));
    System.out.println();


    // Create a HashMap
    HashMap<String, Integer> map = new HashMap<>();
    map.put("apple", 1);
    map.put("banana", 2);
    map.put("cherry", 3);
    map.put("date", 4);

    // Iterate over the map using streams
    map.entrySet().stream()
        .forEach(entry -> System.out.println("Key: " + entry.getKey() + ", Value: " + entry.getValue()));
  }
}
~~~

~~~bash
Even Numbers: [2, 4, 6, 8, 10]
Squared Numbers: [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
FlatMapped Numbers: [1, 2, 2, 3, 3, 4, 4, 5, 5, 6, 6, 7, 7, 8, 8, 9, 9, 10, 10, 11]
Distinct Numbers: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11]
Sorted Numbers: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
Peeked: 1
Peeked: 2
Peeked: 3
Peeked: 4
Peeked: 5
Peeked: 6
Peeked: 7
Peeked: 8
Peeked: 9
Peeked: 10
Limited Numbers: [1, 2, 3, 4, 5]
Skipped Numbers: [6, 7, 8, 9, 10]
ForEach: 1 2 3 4 5 6 7 8 9 10 
Collected Set: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
Sum: 3628800
Count: 10
Any Match > 5: true
All Match > 0: true
None Match < 0: true
First: 1
Any: 1
Max: 10
Min: 1
Number-Square Map: {2=1, 3=4, 4=9, 5=16, 6=25, 7=36, 8=49, 9=64, 10=81, 11=100}
Word-Length Map: {banana=6, cherry=6, apple=5}
Char-ASCII Map: {a=97, b=98, c=99}
Taken While < 5: [1, 2, 3, 4]
Dropped While < 5: [5, 6, 7, 8, 9, 10]
Iterated Numbers: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
Generated Numbers: [0.9016335751314905, 0.1810844673937697, 0.26219990265255666, 0.7199147604612719, 0.8207664381491393]
Boxed Numbers: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
forEach: cherry date apple banana 
forEachOrdered: apple banana cherry date 
Key: banana, Value: 2
Key: date, Value: 4
Key: apple, Value: 1
Key: cherry, Value: 3
~~~
