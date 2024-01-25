
```
import java.util.*;

public class Sample {
  //functional style == declarative style + higher-order function
  //higher-order function?

  //functions in general
  //We can pass objects to functions
  //we can return object from functions
  //we can create objects in functions

  //higher-order functions
  //We can pass functions to functions
  //we can return functions from functions
  //we can create functions in functions

  //We can treat functions like we treat data or objects.
  //code as data

  public static void main(String[] args) {
  }
}
```

"Functional style"（函数式风格）和"Declarative style"（声明式风格）都是不同的编程范式，尽管它们在一些方面有重叠，但也有一些区别。以下是两者的比较：

**1. 关注点：**

- **函数式风格：** 强调函数的使用，将计算视为数学函数的组合，侧重于操作数据的转换和处理。函数被认为是一等公民，可以作为参数传递、返回值返回。
- **声明式风格：** 强调描述问题的目标，而不是详细的执行步骤。关注于"做什么"而不是"怎么做"。

**2. 可变性：**

- **函数式风格：** 强调不可变性，数据一旦创建就不能被修改。这有助于避免并发问题和副作用。
- **声明式风格：** 声明式编程更倾向于不修改现有数据，但并不像函数式编程那么强调不可变性。

**3. 纯度：**

- **函数式风格：** 强调纯函数，即函数的输出只由输入决定，没有副作用。
- **声明式风格：** 声明式编程也强调纯函数，但并不是如此强调。

**4. 数据流：**

- **函数式风格：** 关注于显式的数据流，将数据从一个函数传递到另一个函数。
- **声明式风格：** 也关注数据流，但更注重于表达问题的目标和逻辑。

**5. 抽象和组合：**

- **函数式风格：** 强调函数的组合，可以通过高阶函数将函数组合成更复杂的功能。
- **声明式风格：** 也支持抽象和组合，但不像函数式编程那样强调函数的高阶特性。

**6. 适用语言：**

- **函数式风格：** 主要在函数式编程语言中受到支持，如Haskell、Scala、Clojure等。但也可以在其他编程语言中应用函数式编程思想。
- **声明式风格：** 在许多编程语言中都可以应用，包括命令式编程语言。

**7. 适用场景：**

- **函数式风格：** 适用于处理复杂的数据转换和处理，以及并发编程。
- **声明式风格：** 适用于描述问题的目标、界面设计、查询语言等。

虽然函数式风格和声明式风格有一些区别，但它们并不是互斥的。在实际编程中，可以根据任务的性质选择适当的编程范式，甚至可以将两种风格结合使



