
```java
import java.util.*;

enum Pip { ONE, TWO, THREE, FOUR, FIVE, SIX };

public class Sample {
  public static int scoreFor(Pip pip) {
    return switch(pip) {
      case ONE -> 100;
      case TWO -> 2;
      case THREE, FOUR -> 3;
      case FIVE -> 5;
      case SIX -> 50;
        //if you don't have to, do not write the default.
      //The runtime will result in a failure if a new enum were added later.
      //Of course, we will also get a compilation error if the code in question
      //were to be compiled after the addition of the new enum value.
    };
  }

  public static void main(String[] args) {
    var result = List.of(Pip.ONE, Pip.THREE, Pip.FOUR, Pip.THREE, Pip.TWO, Pip.SIX).stream()
      .mapToInt(Sample::scoreFor)
      .sum();


    System.out.println(result);
  }
}


```

使用switch语句与enum一起使用有以下几个好处：  
  
1. 类型安全：enum提供了一组有限的取值，使用switch语句可以确保只处理这些特定的取值，避免了使用其他类型的值导致的错误。  
  
2. 可读性：enum提供了一种更加可读和可理解的方式来表示一组相关的常量。switch语句可以根据不同的enum值执行不同的逻辑，使代码更加清晰和易于理解。  
  
3. 扩展性：当需要添加新的常量时，只需在enum中添加新的取值，并在switch语句中处理新的情况即可。这样可以方便地扩展代码，而不需要修改大量的条件语句。  
  
4. 编译时检查：使用switch语句处理enum值时，编译器可以检查是否处理了所有可能的情况。如果遗漏了某个情况，编译器会发出警告，帮助开发人员避免潜在的错误。