```java
import java.util.*;
import java.util.function.*;
public class Sample {
  public static void print(int number, String msg,
    Function<Integer, Integer> func) {
    System.out.println(number + " " + msg + ": " + func.apply(number));
  }
  public static void main(String[] args) {
    Function<Integer, Integer> inc = e -> e + 1; 
    Function<Integer, Integer> doubled = e -> e * 2;
    print(5, "increment", inc);
    print(6, "increment", inc);
    print(5, "doubled", doubled);
    print(6, "doubled", doubled);
    Function<Integer, Integer> incrementAndDouble =
      inc.andThen(doubled);
    print(5, "incremeted and doubled", incrementAndDouble);
    /*
         -----> |  inc  | ---->
         -----> |  doubled  | ---->
	               incrementAndDouble
         -----> ||----> |  inc | ---> | doubled |---> || --->
    */
  }
}
```

"Functional style"（函数式风格）是一种编程范式，强调使用函数来构建软件，将计算视为数学函数的组合，而不是通过修改变量的状态来实现。函数式编程强调不可变性、函数的纯粹性（函数的输出仅由输入决定）、高阶函数和避免副作用等特性。

以下是函数式编程风格的一些特点：

不可变性（Immutability）： 函数式编程中的数据一旦创建就不能被修改，任何修改都会创建新的数据。这样可以避免在多线程环境中的竞态条件和副作用。

纯函数（Pure Functions）： 纯函数是指输出仅由输入决定的函数，没有副作用（不会修改外部状态）。相同的输入永远会得到相同的输出。

高阶函数（Higher-Order Functions）： 函数可以作为参数传递给其他函数，也可以作为函数的返回值。这种能力支持了函数的组合和抽象。

函数组合（Function Composition）： 可以将多个函数组合成一个更复杂的函数，通过将一个函数的输出作为另一个函数的输入，以此来构建功能。

递归（Recursion）： 函数式编程中常常使用递归来解决问题，因为不可变性和纯函数的特性使得递归更易于实现和理解。

显式的数据流（Explicit Data Flow）： 函数式编程强调将数据从一个函数传递到另一个函数，从而形成明确的数据流。这有助于理解程序的执行路径。

模块化（Modularity）： 函数式编程鼓励将程序分解为小的、可复用的函数，使代码更易于管理和测试。

函数式编程在一些编程语言中有更强烈的支持，如Haskell、Clojure、Scala等。而在其他编程语言中，如Java、Python、JavaScript等，也可以采用函数式编程的一些思想和技巧。

示例（在JavaScript中的函数式风格）：


```javascript

const numbers = [1, 2, 3, 4, 5];

// 使用函数式编程风格计算数组中大于2的元素的平方和
const result = numbers
  .filter(num => num > 2) // 过滤出大于2的元素
  .map(num => num * num)   // 对元素进行平方
  .reduce((acc, curr) => acc + curr, 0); // 求和

console.log(result); // 输出：29
```

函数式编程强调代码的可读性、可维护性和抽象能力，适合处理复杂的问题和处理大量数据的情况。
