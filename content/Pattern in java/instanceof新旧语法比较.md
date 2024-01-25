```java
import java.util.*;

public class Sample {
  public static void process(CharSequence input) {
    if(input instanceof String) {
      String str = (String) input;
      System.out.println(str.isBlank());
    }
    //Do you work for the compiler or does the compiler work for you?
  }

  public static void main(String[] args) {
    process("hello");
  }
}

```

```java
import java.util.*;

public class Sample {
  public static void process(CharSequence input) {
    if(input instanceof String str) {
      System.out.println(str.isBlank());
      //here String str is the same reference as CharSequence input
      //CharSequence input --> MEM <-  String str
    } //scope of str ends here
  }

  public static void main(String[] args) {
    process("hello");
  }
}
```

```java
    return input instanceof String str && !str.isBlank() ? "yes, " + str : "no";
    //in the "no" part, str is not visible.
```