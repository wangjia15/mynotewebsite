# 多态与pattern一起使用
```java
import java.util.*;

interface Trade {}
record Buy(String ticker, int quantity) implements Trade {}
record Sell(String ticker, int quantity) implements Trade {}

public class Sample {
  public static boolean processBuy(Buy buy) {
    System.out.println("processing a buy for " + buy);
    return true;
  }

  public static boolean processSell(Sell sell) {
    System.out.println("processing a sell for " + sell);
    return true;
  }

  public static boolean process(Trade trade) {
    return switch(trade) {
      case Buy buy -> processBuy(buy);
      case Sell sell -> processSell(sell);
      default -> {
        System.out.println("No clue what this is");
        yield false;
      }
    };
  }

  public static void main(String[] args) {
    System.out.println(process(new Buy("GOOG", 200)));
    System.out.println(process(new Sell("AMZN", 300)));
  }
}

```

```java
import java.util.*;

interface Trade {}
record Buy(String ticker, int quantity) implements Trade {}
record Sell(String ticker, int quantity) implements Trade {}

public class Sample {
  public static boolean processBuy(Buy buy) {
    System.out.println("processing a buy for " + buy);
    return true;
  }

  public static boolean processSell(Sell sell) {
    System.out.println("processing a sell for " + sell);
    return true;
  }

  public static boolean process(Trade trade) {
    return switch(trade) {
      case Buy buy when buy.quantity() >= 5000 -> {
        System.out.println("call audit routine");
        yield processBuy(buy);
      }
      case Buy buy -> processBuy(buy);
      case Sell sell -> processSell(sell);
      default -> {
        System.out.println("No clue what this is");
        yield false;
      }
    };
  }

  public static void main(String[] args) {
    System.out.println(process(new Buy("GOOG", 5000)));
    System.out.println(process(new Buy("GOOG", 200)));
    System.out.println(process(new Sell("AMZN", 300)));
  }
}
```

switch语句是一种在编程中用于根据不同的条件执行不同代码块的结构。switch语句中的case语句用于匹配不同的条件，并在匹配成功时执行相应的代码块。  
  
在Java 14及更高版本中，switch语句引入了新的when关键字，用于在case语句中添加更复杂的条件。when关键字允许我们在case语句中使用布尔表达式，以便更灵活地匹配条件。  
  
在给定的代码示例中，switch语句使用when关键字来匹配不同的Trade对象，并根据条件执行相应的代码块。例如，当Buy对象的quantity大于等于5000时，会调用processBuy方法，并在调用完成后返回结果。对于其他情况，会执行相应的处理逻辑。

## error
```java
  public static boolean process(Trade trade) {
    return switch(trade) {
      //case Buy buy -> processBuy(buy); //ERROR if this appears here due to dominance over the next case
      case Buy buy when buy.quantity() >= 5000 -> {
        System.out.println("call audit routine");
        yield processBuy(buy);
      }
      case Buy buy -> processBuy(buy);
      case Sell sell -> processSell(sell);
      default -> {
        System.out.println("No clue what this is");
        yield false;
      }
    };
  }
```