记录（record）是Java 14中引入的一种新的类类型。它是一种用于表示不可变数据的简洁方式。记录类似于传统的Java类，但具有一些特殊的语法和行为。  
  
记录使用record关键字来声明，后面跟着类的名称和成员变量的列表。在记录中，成员变量被称为组件（component），它们的值在创建记录对象时被初始化，并且不能被修改。  
  
记录还自动提供了一些方法，如equals()、hashCode()和toString()，这些方法根据记录的组件生成相应的实现。此外，记录还提供了一种简洁的方式来定义构造函数。  

```java
import java.util.*;

record Location(double lat, double lon) {
  public Location {
    if(Math.abs(lat) > 180 || Math.abs(lon) > 180) {
      throw new RuntimeException("Invalid values for lat or lon");
    }
  }
}

public class Sample {  
  public static void main(String[] args) {
    var location1 = new Location(121.35, -84.23);
    var location2 = new Location(121.35, -84.23);
    var location3 = new Location(141.35, -84.23);
    
    System.out.println(location1);
    System.out.println(location1.lat());
    System.out.println(location1.lon());
    
    System.out.println(location1.equals(location2));
    System.out.println(location1.equals(location3));
    
    try {
      new Location(190.1, 200);
    } catch(Exception ex) {
      System.out.println(ex);
    }
  }
}
```
  
在给定的代码示例中，Location是一个记录类，它有两个组件lat和lon，分别表示纬度和经度。构造函数使用了一个条件语句来验证lat和lon的有效性。记录还提供了默认的equals()、hashCode()和toString()方法的实现。  
  
在Sample类的main()方法中，我们可以看到如何创建和使用Location记录对象。我们还可以看到如何使用记录对象的组件和equals()方法来比较记录对象的相等性。  
  
总而言之，记录是一种用于表示不可变数据的简洁方式，它提供了自动生成的方法和简化的构造函数定义。

