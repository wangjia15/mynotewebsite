```java
import java.util.*;
import java.util.function.Function;
public class Sample {
  public static void print(int number, 
    String message,
    Function<Integer, Integer> func) {
    System.out.println(number + " " + 
      message + ": " + func.apply(number));
  }
  public static void main(String[] args) {
    Function<Integer, Integer> inc = value -> value + 1;
    Function<Integer, Integer> doubled = value -> value * 2;
    print(5, "incremented" , inc);
    print(5, "doubled" , doubled);
    print(5, "incremented and doubled" , 
      inc.andThen(doubled));
    /*
      inc ---->|inc|---->
      doubled ---->|doubled|---->
      combined
      ---->|---->|inc|--->|doubled|---->|---->
    */
  }
}
/*
Functions are composable.
*/
```

将函数组合在Java中允许您通过将现有函数组合在一起来创建新函数。这是通过Java util.function包中的Function接口提供的andThen方法实现的。
当您组合两个函数时，第一个函数的输出成为第二个函数的输入。andThen方法先应用第一个函数，然后将结果应用于第二个函数。
在给定的代码示例中，inc函数将给定的值增加1，doubled函数将给定的值乘以2。这两个函数使用andThen方法组合在一起，创建一个先增加值，然后将其加倍的新函数。
组合的函数然后作为参数传递给print方法，该方法将函数应用于给定的数字并打印结果。
代码注释中的图示说明了函数的组合：
这显示了组合函数首先应用inc函数，然后将结果应用于doubled函数。
通过组合函数，您可以通过在现有函数的基础上构建更复杂和可重用的代码来创建更高级的代码。这有助于代码的模块化和提高代码的可读性。
有关在Java中组合函数的更多信息，您可以参考Java官方文档中关于Function接口的说明。