
```java
import java.util.*;

public class Sample {
  public static String gradeForScore(int score) {
    String grade = "";

    if(score > 90) {
      grade = "A";
    } else {
      if(score > 80) {
        grade = "B";
      } else {
        if(score > 70) {
          grade = "C";
	} else {
          if(score > 60) {
            grade = "D";
	  } else {
	    grade = "F";
	  }
	}
      }
    }

    return "Grade for score %d is %s".formatted(score, grade);
  }

  public static void main(String[] args) {
    List.of(59, 65, 78, 83, 89, 93).stream()
      .map(Sample::gradeForScore)
      .forEach(System.out::println);
  }
}

//verbose
//high complexity
//hard to maintain
//hard to reason
//hard to understand


```

方法2
```java
import java.util.*;
import java.math.*;

public class Sample {
  public static String gradeForScore(int score) {
    String grade = "";

    switch(Math.min(score / 10, 10)) {
      case 9:
        grade = "A";
	break;
      case 8:
        grade = "B";
	break;
      case 7:
        grade = "C";
	break;
      case 6:
        grade = "D";
	break;
      default:
        grade = "F";
    }

    return "Grade for score %d is %s".formatted(score, grade);
  }

  public static void main(String[] args) {
    List.of(59, 65, 78, 83, 89, 93).stream()
      .map(Sample::gradeForScore)
      .forEach(System.out::println);
  }
}

//concise, but
//error prone
//a statement that mutates variables

```

## 方法3

```java

import java.util.*;
import java.math.*;

public class Sample {
  public static String gradeForScore(int score) {
    final String grade = switch(Math.min(score / 10, 10)) {
      case 9 -> "A";
      case 8 -> "B";
      case 7 -> "C";
      case 6 -> "D";
      default -> "F";
    };

    return "Grade for score %d is %s".formatted(score, grade);
  }

  public static void main(String[] args) {
    List.of(59, 65, 78, 83, 89, 93).stream()
      .map(Sample::gradeForScore)
      .forEach(System.out::println);
  }
}

//no break
//no mutation
//concise


```


