
```java
import java.util.*;

public class Sample {
  public static int totalValues(List<Integer> numbers) {
    int total = 0;

    for(var number: numbers) {
      total += number;
    }

    return  total;
  }

  public static void main(String[] args) {
    var numbers = List.of(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);

    System.out.println(totalValues(numbers));
  }
}

/*
Suppose we have a collection of numbers, may be
price of stock, products, etc.

We are asked to write a method to total all values
*/


```
