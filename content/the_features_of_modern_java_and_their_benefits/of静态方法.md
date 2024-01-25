Stream.of() 是 Java 8 中引入的一个静态方法，用于创建一个包含指定元素的流（Stream）。它接受一个或多个参数，并返回一个包含这些参数的流。

这个方法的语法如下：

```
Stream.of(element1, element2, ..., elementN)
```

其中，element1 到 elementN 是要添加到流中的元素。

以下是一个使用 Stream.of() 方法的示例：

```java
import java.util.stream.Stream;

public class Sample {

    public static void main(String[] args) {

        Stream<String> stream = Stream.of("apple", "banana", "orange");

        stream.forEach(System.out::println);

    }

} 
```

在上面的示例中，我们使用 Stream.of() 方法创建了一个包含三个字符串元素的流。然后，我们使用 forEach() 方法遍历流中的每个元素，并将其打印到控制台上。

需要注意的是，Stream.of() 方法返回的是一个顺序流（Ordered Stream），即元素的顺序与它们被添加到流中的顺序相同。如果需要并行流（Parallel Stream），可以使用 Stream.parallel() 方法将顺序流转换为并行流。

List.of() 是 Java 9 中引入的一个静态方法，用于创建一个不可变的列表（Immutable List）。它接受一个或多个参数，并返回一个包含这些参数的不可变列表。

这个方法的语法如下：

`List.of(element1, element2, ..., elementN)`

其中，element1 到 elementN 是要添加到列表中的元素。

以下是一些常用的 List.of() 方法的实例：

1. 创建一个包含整数的列表：

`List<Integer> numbers = List.of(1, 2, 3, 4, 5);`

2. 创建一个包含字符串的列表：

`List<String> names = List.of("Alice", "Bob", "Charlie");`

3. 创建一个包含自定义对象的列表：

 ```java
class Person {

    private String name;

    private int age;

    public Person(String name, int age) {

        this.name = name;

        this.age = age;

    }

    // Getters and setters...

}

List people = List.of(

    new Person("Alice", 25),

    new Person("Bob", 30),

    new Person("Charlie", 35)

);
```

需要注意的是，List.of() 方法返回的列表是不可变的，即不能添加、删除或修改其中的元素。如果尝试进行修改操作，将会抛出 UnsupportedOperationException 异常。如果需要可变的列表，可以使用 ArrayList 或其他可变列表实现类。
