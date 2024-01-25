```java
import java.util.*;

record Location(double lat, double lon) {}
record PairOfLocation(Location loc1, Location loc2) {}

public class Sample {
  public static String process(Object input) {
    return switch(input) {
      case String str -> str.toUpperCase();

      case Location(double latitude, double longitude) ->
        "The location is " + latitude + ", " + longitude;

      case PairOfLocation(Location(double lat1, double lon1), Location(double lat2, double lon2)) ->
        "The pair has " + lat1 + " and " + lat2;
      default -> "whatever";
    };
  }

  public static void main(String[] args) {
    System.out.println(process("hello"));

    System.out.println(process(new Location(145.23, -84.23)));
    System.out.println(process(new Location(123.23, -73.23)));
    System.out.println(process(new Location(115.23, -62.23)));
    
    System.out.println(process(new PairOfLocation(
      new Location(115.23, -62.23), new Location(121.32, -76.23))));
  }
}

```