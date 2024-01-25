在给定的代码中，核心语法是Java中的try-with-resources语句。  
  
在Java 7和8中，try-with-resources语句通过自动关闭实现AutoCloseable接口的资源，实现了自动资源管理。它通过消除显式资源清理的需要，简化了代码。  
  
在给定的代码中，Resource类实现了AutoCloseable接口。try-with-resources语句在use方法中用于创建一个新的Resource实例，并在try语句内的代码块执行后自动关闭它。  
  
然而，在Java 7和8中，try-with-resources语句要求在try语句本身内声明和初始化资源。这意味着资源不能在try语句外部声明并在块内重用。  
  
从Java 9开始，语法被增强，允许在try-with-resources语句中使用有效的最终变量作为资源。这意味着资源可以在try语句外部声明和初始化，并在其中使用。  
  
在给定的代码中，try-with-resources语句与resource变量一起使用，该变量在try语句外部声明和初始化。这种语法在Java 7和8中是不可能的，但在Java 9和后续版本中是允许的。

```java
import java.io.*;

public class Example {
    public static void main(String[] args) {
        try (BufferedReader reader = new BufferedReader(new FileReader("file.txt"))) {
            String line;
            while ((line = reader.readLine()) != null) {
                System.out.println(line);
            }
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

## 自定义实现
```java
import java.util.*;

class Resource implements AutoCloseable {
  public Resource() { System.out.println("Created..."); }
  public void op1() { System.out.println("op1"); }
  public void op2() { System.out.println("op2"); }
  public void close() { System.out.println("clean up external resources"); }
}

public class Sample {  
  public static void use(Resource resource) {
    
    //try(Resource resource = new Resource()) Java 7 and 8 allowed this
    
    try(resource) { //Was not possible in Java 7 and 8
      resource.op1();
      resource.op2();
    }
  }
  
  public static void main(String[] args) {
    use(new Resource());
  }
}
```