在Java 10中，var 是一种新的关键字，用于声明局部变量。它可以根据变量的初始化值自动推断出变量的类型。这样可以简化代码并提高可读性。  
  
在你提供的代码示例中，var 关键字被用于声明多个变量。例如，在 main 方法中，var numberOfCores = Runtime.getRuntime().availableProcessors(); 声明了一个整数变量 numberOfCores，它的类型会根据 availableProcessors() 方法的返回值自动推断出来。  
  
var 关键字还可以用于增强 for 循环中的迭代变量。例如，for(var name: names) 中的 var 关键字会根据 names 集合的元素类型自动推断出迭代变量 name 的类型。  
  
此外，var 关键字还可以与 try-with-resources 语句一起使用，用于自动关闭资源。例如，try(var reader = new java.io.FileReader("Sample.java")) 中的 var 关键字会根据 FileReader 类型自动推断出 reader 的类型，并在代码块执行完毕后自动关闭 reader。  
  
需要注意的是，var 关键字只能用于局部变量的声明，不能用于字段或方法参数的声明。

```java
import java.util.*;

public class Sample {  
  //var max = 1000; //not for fields
  
  //public void process(var count) // not for parameters
  
  public static void main(String[] args) throws java.io.IOException {
    var numberOfCores = Runtime.getRuntime().availableProcessors();
    
    System.out.println(numberOfCores);
    
    var names = List.of("Tom", "Jerry");
    
    for(var name: names) {
      System.out.println(name);
    }
    
    try(var reader = new java.io.FileReader("Sample.java")) {
      System.out.println("reading...");
    }
  }
}
```