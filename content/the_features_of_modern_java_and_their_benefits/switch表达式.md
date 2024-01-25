在这段代码中，使用了Java 12中的新特性，即Switch表达式。Switch表达式允许我们在一个表达式中使用多个分支，并根据条件返回不同的结果。  


```java
import java.time.*;
import java.util.stream.*;

public class Sample {
  public static String activity(DayOfWeek dayOfWeek) {
    return switch(dayOfWeek) {
      case SATURDAY, SUNDAY -> "take it easy";
      case MONDAY, WEDNESDAY -> "Music lesson";
      case TUESDAY, THURSDAY -> {
        var sport = dayOfWeek == DayOfWeek.TUESDAY ? "Tennis" : "Soccer";
        
        yield "Play " + sport;
      }
      case FRIDAY -> "Theater";
    };
  }
  
  public static void main(String[] args) {
    Stream.of(DayOfWeek.values())
      .forEach(dayOfWeek -> System.out.println(dayOfWeek + ": " + activity(dayOfWeek)));
  }
}
```

  
在这个例子中，我们定义了一个名为activity的静态方法，它接受一个DayOfWeek枚举类型的参数，并返回一个字符串。在方法体内部，我们使用了Switch表达式来根据不同的dayOfWeek值返回不同的活动。  
  
Switch表达式的语法如下：


```java
return switch(dayOfWeek) {

  case 值1 -> 结果1;

  case 值2 -> 结果2;

  ...

  default -> 默认结果;

};

```

  
在这个例子中，我们使用了不同的case语句来匹配不同的dayOfWeek值，并返回相应的活动。例如，如果dayOfWeek是SATURDAY或SUNDAY，则返回"take it easy"；如果是MONDAY或WEDNESDAY，则返回"Music lesson"；如果是TUESDAY或THURSDAY，则根据具体的dayOfWeek值返回不同的字符串；如果是FRIDAY，则返回"Theater"。  
  
在TUESDAY或THURSDAY的情况下，我们使用了一个代码块来定义一个局部变量sport，并根据dayOfWeek的值来赋予不同的值。然后使用yield关键字返回最终的结果。  
  
在main方法中，我们使用了Stream.of(DayOfWeek.values())来创建一个包含所有DayOfWeek枚举值的流。然后使用forEach方法遍历流中的每个元素，并调用activity方法打印出相应的活动。  
  
最后，代码块结束，程序执行结束。