List.of 是 Java 9 中引入的一种创建不可变列表的便捷方法。这个方法接受一系列参数，并返回一个包含这些参数的不可变列表。不可变意味着你不能向列表中添加或删除元素。  
例如，以下代码创建了一个包含三个元素的列表：
`List<String> list = List.of("A", "B", "C");`
这个列表不能被修改，尝试添加或删除元素将抛出 UnsupportedOperationException。

```
list.add("D");  // 抛出 UnsupportedOperationException
list.remove("A");  // 抛出 UnsupportedOperationException
```

这种语法的主要优点是它提供了一种简洁、易读的方式来创建不可变列表，而不需要创建一个可变列表然后再将其转换为不可变列表。
类似的语法还有哪些

Java 9 除了引入 List.of 之外，还引入了类似的方法来创建不可变的集合和映射。以下是一些例子：  
1. Set.of(E... elements)：创建一个包含给定元素的不可变集合。例如：
`Set<String> set = Set.of("A", "B", "C");`
2. Map.of(K k1, V v1, K k2, V v2, ...)：创建一个包含给定键值对的不可变映射。例如：
`Map<String, Integer> map = Map.of("A", 1, "B", 2, "C", 3);`
3. Map.ofEntries(Map.Entry<? extends K, ? extends V>... entries)：创建一个包含给定映射条目的不可变映射。例如：

Map<String, Integer> map = Map.ofEntries(
    Map.entry("A", 1),
    Map.entry("B", 2),
    Map.entry("C", 3)
);
这些方法都返回不可变的集合，尝试修改这些集合（例如添加或删除元素）将抛出 UnsupportedOperationException。
还有呢

除了 List.of(), Set.of(), Map.of(), Map.ofEntries() 这些方法，Java 9 还引入了一些其他的工厂方法来创建不可变集合，这些方法主要用于处理较大的集合。  
1. List.copyOf(Collection<? extends E> coll)：创建一个包含给定集合中所有元素的不可变列表。  
2. Set.copyOf(Collection<? extends E> coll)：创建一个包含给定集合中所有元素的不可变集合。  
3. Map.copyOf(Map<? extends K, ? extends V> map)：创建一个包含给定映射中所有键值对的不可变映射。  
这些方法的主要用途是创建一个给定集合的不可变副本。例如，如果你有一个可变的列表，并且你想创建一个这个列表的不可变副本，你可以使用 List.copyOf() 方法：
List<String> mutableList = new ArrayList<>();
mutableList.add("A");
mutableList.add("B");
mutableList.add("C");
List<String> immutableList = List.copyOf(mutableList);
这个 immutableList 是不可变的，尝试修改它将抛出 UnsupportedOperationException。
stream.of
USED
Rerun without context
Java语法.java
Current file
Stream.of 是 Java 8 引入的一种创建流的方法。这个方法接受一系列参数，并返回一个包含这些参数的流。  
例如，以下代码创建了一个包含三个元素的流：
Stream<String> stream = Stream.of("A", "B", "C");
你可以在这个流上执行各种操作，例如过滤、映射、归约等。例如，以下代码将流中的每个元素转换为其大写形式，然后将结果收集到一个列表中：
List<String> list = stream.map(String::toUpperCase).collect(Collectors.toList());
Stream.of 的主要优点是它提供了一种简洁、易读的方式来创建流，而不需要创建一个集合然后再将其转换为流。
类似的有哪些
USED
Rerun without context
Java语法.java
Current file
Java 8 引入了 Stream API，除了 Stream.of，还有其他一些方法可以用来创建流：  
1. Arrays.stream(array)：从数组创建一个流。例如：
int[] numbers = {1, 2, 3, 4, 5};
IntStream stream = Arrays.stream(numbers);
2. Collection.stream()：从集合创建一个流。例如：
List<String> list = Arrays.asList("A", "B", "C");
Stream<String> stream = list.stream();
3. Stream.generate(Supplier s)：使用 Supplier 函数生成一个无限流。例如：
Stream<String> stream = Stream.generate(() -> "Hello").limit(10);
4. Stream.iterate(seed, UnaryOperator f)：使用初始元素 seed 和函数 f 生成一个无限流。例如：
Stream<Integer> stream = Stream.iterate(0, n -> n + 2).limit(10);
5. IntStream.range(start, end) 或 IntStream.rangeClosed(start, end)：生成一个整数范围的流。例如：
IntStream stream = IntStream.range(1, 5);  // 生成 1, 2, 3, 4
这些方法提供了多种创建流的方式，可以根据具体的需求选择合适的方法。