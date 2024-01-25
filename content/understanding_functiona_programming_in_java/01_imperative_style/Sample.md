```java
import java.util.*;
public class Sample {
  public static void main(String[] args) {
    List<String> names = List.of("Dory", "Gill", "Bruce", "Nemo", "Darla", "Marlin", "Jacques");
    //find if Nemo is there.
    //imperative style: we tell what to do and also how to do it
    boolean found = false;
    //for(int i = 0; i < names.size(); i++...) //how
    for(String name: names) { //how
      //if(name == "Nemo") //how
      if (name.equals("Nemo")) {
        found = true;
	break; //how
      }
    }
    if(found) {
      System.out.println("Nemo found");
    } else {
      System.out.println("Nemo not found");
    }
  }
}
```

"Imperative style"（命令式风格）和"Declarative style"（声明式风格）是两种不同的编程范式，用于描述程序的编写方式。它们在代码结构、可读性和表达方式上有所不同。

Imperative style (命令式风格):
命令式风格是一种以编写详细的指令和操作步骤为主的编程方式。在命令式风格中，程序员会直接描述程序执行的步骤和顺序，告诉计算机如何执行任务。典型的命令式语言如C、C++、Java等。以下是命令式风格的特点：

强调具体的计算步骤和流程控制。
代码通常按照顺序执行，从上到下。
可能会使用循环、条件语句等来实现控制流程。
需要显式地操作变量状态。
Declarative style (声明式风格):
声明式风格是一种更注重描述任务的目标和逻辑，而不是详细的执行步骤的编程方式。在声明式风格中，程序员描述了所需的结果，由计算机根据描述来生成结果。典型的声明式语言如SQL、HTML、CSS、函数式编程语言（如Haskell、Clojure）等。以下是声明式风格的特点：

强调问题的本质和目标，而不是具体的执行步骤。
更加抽象和高层次，减少了繁琐的细节。
可以利用函数式编程、查询语言等来实现任务。
不需要显式地操作变量状态，通常通过函数或规则来描述逻辑。
举例比较：

比如，假设我们要从一个整数数组中找出所有大于10的元素，然后将它们加倍。下面分别用命令式风格和声明式风格的伪代码示例来说明：

命令式风格：

python

```python
imperative_result = []
for num in integer_array:
    if num > 10:
        doubled_num = num * 2
        imperative_result.append(doubled_num)
```

声明式风格：


```python
declarative_result = integer_array.filter(num => num > 10).map(num => num * 2)
```

在命令式风格中，我们直接描述了每个步骤的具体操作，使用循环和条件语句来控制流程。而在声明式风格中，我们通过函数式方法链式地表示了任务的目标，而不需要显式地指定步骤。

选择使用哪种风格取决于任务的性质、编程语言的特性以及代码的可维护性和可读性等因素。有些任务更适合命令式风格，而另一些任务则更适合声明式风格。