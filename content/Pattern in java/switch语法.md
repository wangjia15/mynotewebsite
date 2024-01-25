## 多个标签类型
```java
import java.util.*;

public class Sample {
  public static int scoreFor(int pip) {
    return switch(pip) {
      case 1 -> 100;
      case 2 -> 2;
      case 3, 4 -> 3;
      case 5 -> 5;
      case 6 -> 50;
      default -> 0;
    };
  }

  public static void main(String[] args) {
    var result = List.of(3, 4, 3, 2, 6).stream()
      .mapToInt(Sample::scoreFor)
      .sum();

    System.out.println(result);
  }
}

```

## 多行逻辑代码
```java
import java.util.*;

public class Sample {
  public static int scoreFor(int pip) {
    return switch(pip) {
      case 1 -> {
        System.out.println("log this value for monitoring...");
        yield 100;
      }
      case 2 -> 2;
      case 3, 4 -> 3;
      case 5 -> 5;
      case 6 -> 50;
      default -> {
        System.out.println("check how this happened? value is " + pip);
        yield 0;
      }
    };
  }

  public static void main(String[] args) {
    var result = List.of(1, 3, 0, 4, 3, 2, 6).stream()
      .mapToInt(Sample::scoreFor)
      .sum();


    System.out.println(result);
  }
}


```
yield 是在 Java 14 中引入的新的关键字，用于在 switch 表达式中返回一个值。它的作用类似于 return 语句，但是可以在 switch 表达式中使用。  
  
在给定的代码片段中，yield 关键字用于返回 switch 表达式的值并终止 switch 块。根据不同的情况，它返回不同的值。在默认情况下，它打印一条消息并返回值 0。  
  
需要注意的是，yield 语句只能在 switch 表达式中使用，用于返回一个值并结束 switch 块的执行。

## 常见错误
```java
public class Sample {
  public static int scoreFor(int pip) {
    return switch(pip) {
      case 1 -> 100;
      case 2 -> 2;
      case 3, 4 -> 3;
      case 5 -> 5;
      case 6 -> 50;
      //ERROR because default is not provided, all possible values not covered
    };
  }

```