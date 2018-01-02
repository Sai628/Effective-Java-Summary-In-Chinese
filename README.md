
# 一. 目录
- [一. 目录](#一-目录)
- [二. 创建和销毁对象](#二-创建和销毁对象)
    - [1. 考虑用静态工厂方法代替构造器](#1-考虑用静态工厂方法代替构造器)
    - [2. 遇到多个构造器参数时要考虑用构建器](#2-遇到多个构造器参数时要考虑用构建器)
    - [3. 用私有构造器或者枚举类型强化 _Singleton_ 属性](#3-用私有构造器或者枚举类型强化-singleton-属性)
    - [4. 通过私有构造器强化不可实例化的能力](#4-通过私有构造器强化不可实例化的能力)
    - [5. 避免创建不必要的对象](#5-避免创建不必要的对象)
    - [6. 消除过期的对象引用](#6-消除过期的对象引用)
    - [7. 避免使用终结方法](#7-避免使用终结方法)
- [三. 对于所有对象都通用的方法](#三-对于所有对象都通用的方法)
    - [8. 覆盖 _equals_ 时请遵守通用约定](#8-覆盖-equals-时请遵守通用约定)
    - [9. 覆盖 _equals_ 时总要覆盖 _hashCode_](#9-覆盖-equals-时总要覆盖-hashcode)
    - [10. 始终要覆盖 _toString_](#10-始终要覆盖-tostring)
    - [11. 谨慎地覆盖 _clone_](#11-谨慎地覆盖-clone)
    - [12. 考虑实现 _Comparable_ 接口](#12-考虑实现-comparable-接口)
- [四. 类和接口](#四-类和接口)
    - [13. 使类和成员的可访问性最小化](#13-使类和成员的可访问性最小化)
    - [14. 在公有类中使用访问方法而非公有域](#14-在公有类中使用访问方法而非公有域)
    - [15. 使可变性最小化](#15-使可变性最小化)
    - [16. 复合优于继承](#16-复合优于继承)
    - [17. 要么为继承而设计, 并提供文档说明, 要么就禁止继承](#17-要么为继承而设计-并提供文档说明-要么就禁止继承)
    - [18. 接口优于抽象类](#18-接口优于抽象类)
    - [19. 接口只用于定义类型](#19-接口只用于定义类型)
    - [20. 类层次优于标签类](#20-类层次优于标签类)
    - [21. 用函数对象表示策略](#21-用函数对象表示策略)
    - [22. 优先考虑静态成员类](#22-优先考虑静态成员类)
- [五. 泛型](#五-泛型)
    - [23. 请不要在新代码中使用原生态类型](#23-请不要在新代码中使用原生态类型)
    - [24. 消除非受检警告](#24-消除非受检警告)
    - [25. 列表优先于数组](#25-列表优先于数组)
    - [26. 优先考虑泛型](#26-优先考虑泛型)
    - [27. 优先考虑泛型方法](#27-优先考虑泛型方法)
    - [28. 利用有限制通配符来提升API的灵活性](#28-利用有限制通配符来提升api的灵活性)
    - [29. 优先考虑类型安全的异构容器](#29-优先考虑类型安全的异构容器)
- [六. 枚举和注解](#六-枚举和注解)
    - [30. 用 _enum_ 代替 _int_ 常量](#30-用-enum-代替-int-常量)
    - [31. 用实例域代替序数](#31-用实例域代替序数)
    - [32. 用 _EnumSet_ 代替位域](#32-用-enumset-代替位域)
    - [33. 用 _EnumMap_ 代替序数索引](#33-用-enummap-代替序数索引)
    - [34. 用接口模拟可伸缩的枚举](#34-用接口模拟可伸缩的枚举)
    - [35. 注解优先于命名模式](#35-注解优先于命名模式)
    - [36. 坚持使用 _Override_ 注解](#36-坚持使用-override-注解)
    - [37. 用标记接口定义类型](#37-用标记接口定义类型)
- [七. 方法](#七-方法)
    - [38. 检查参数的有效性](#38-检查参数的有效性)
    - [39. 必要时进行保护性拷贝](#39-必要时进行保护性拷贝)
    - [40. 谨慎设计方法签名](#40-谨慎设计方法签名)
    - [41. 慎用重载](#41-慎用重载)
    - [42. 慎用可变参数](#42-慎用可变参数)
    - [43. 返回零长度的数组或者集合, 而不是 _null_](#43-返回零长度的数组或者集合-而不是-null)
    - [44. 为所有导出的API元素编写文档注释](#44-为所有导出的api元素编写文档注释)
- [八. 通用程序设计](#八-通用程序设计)
    - [45. 将局部变量的作用域最小化](#45-将局部变量的作用域最小化)
    - [46. _for-each_ 循环优先于传统的 _for_ 循环](#46-for-each-循环优先于传统的-for-循环)
    - [47. 了解和使用类库](#47-了解和使用类库)
    - [48. 如果需要精确的答案, 请避免使用 _float_ 和 _double_](#48-如果需要精确的答案-请避免使用-float-和-double)
    - [49. 基本类型优先于装箱基本类型](#49-基本类型优先于装箱基本类型)
    - [50. 如果其它类型更适合, 则尽量避免使用字符串](#50-如果其它类型更适合-则尽量避免使用字符串)
    - [51. 当心字符串连接的性能](#51-当心字符串连接的性能)
    - [52. 通过接口引用对象](#52-通过接口引用对象)
    - [53. 接口优先于反射机制](#53-接口优先于反射机制)
    - [54. 谨慎地使用本地方法](#54-谨慎地使用本地方法)
    - [55. 谨慎地进行优化](#55-谨慎地进行优化)
    - [56. 遵守普遍接受的命令惯例](#56-遵守普遍接受的命令惯例)
- [九. 异常](#九-异常)
    - [57. 只针对异常的情况下才使用异常](#57-只针对异常的情况下才使用异常)
    - [58. 对可恢复的情况使用受检异常, 对编程错误使用运行时异常](#58-对可恢复的情况使用受检异常-对编程错误使用运行时异常)
    - [59. 避免不必要地使用受检的异常](#59-避免不必要地使用受检的异常)
    - [60. 优先使用标准的异常](#60-优先使用标准的异常)
    - [61. 抛出与抽象相对应的异常](#61-抛出与抽象相对应的异常)
    - [62. 每个方法抛出的异常都要有文档](#62-每个方法抛出的异常都要有文档)
    - [63. 在细节消息中包含能捕获失败的信息](#63-在细节消息中包含能捕获失败的信息)
    - [64. 努力使失败保持原子性](#64-努力使失败保持原子性)
    - [65. 不要忽略异常](#65-不要忽略异常)
- [十. 并发](#十-并发)
    - [66. 同步访问共享的可变数据](#66-同步访问共享的可变数据)
    - [67. 避免过度同步](#67-避免过度同步)
    - [68. _executor_ 和 _task_ 优先于线程](#68-executor-和-task-优先于线程)
    - [69. 并发工具优先于 _wait_ 和 _notify_](#69-并发工具优先于-wait-和-notify)
    - [70. 线程安全性的文档化](#70-线程安全性的文档化)
    - [71. 慎用延迟初始化](#71-慎用延迟初始化)
    - [72. 不要依赖于线程调度器](#72-不要依赖于线程调度器)
    - [73. 避免使用线程组](#73-避免使用线程组)
- [十一. 序列化](#十一-序列化)
    - [74. 谨慎地实现 _Serializable_ 接口](#74-谨慎地实现-serializable-接口)
    - [75. 考虑使用自定义的序列化形式](#75-考虑使用自定义的序列化形式)
    - [76. 保护性地编写 _readObject_ 方法](#76-保护性地编写-readobject-方法)
    - [77. 对于实例控制, 枚举类型优先于 _readResolve_](#77-对于实例控制-枚举类型优先于-readresolve)
    - [78. 考虑用序列化代理代替序列化实例](#78-考虑用序列化代理代替序列化实例)

<br/>

# 二. 创建和销毁对象
## 1. 考虑用静态工厂方法代替构造器
**_优点_**

静态工厂方法与构造器不同的优势在于:
* 它们有名称
* 不必在每次调用它们的时候都创建一个新对象
* 它们可以返回原返回类型的任何子类型的对象

<br/>

**_缺点_**

但是, 静态工厂方法也有缺点, 主要在于:
* 类如果不含公有的或者受保护的构造器, 就不能被子类化.(鼓励使用复合, 而不是继承)
* 它们与其它的静态方法实际上没有任何区别.  
(静态工厂方法的一些惯用名称: valueOf, of, getInstance, newInstance, getType 以及 newType)

```java
public static Boolean valueOf(boolean b) {
    return b ? Boolean.TRUE : Boolean.FALSE;
}
```

<br/>

## 2. 遇到多个构造器参数时要考虑用构建器
如果类的构造器或者静态工厂方法中具有多个参数, 设计这种类时, Builder模式就是种不错的选择.

Builder模式模拟了具名的可选参数, 就像Ada和Python中的一样.

```java
public static NutritionFacts {
    private final int servingSize;
    private final int servings;
    private final int calories;
    private final int fat;
    private final int sodium;
    private final int carbohydrate;

    public static class Builder {
        // Required paramters
        private final int servingSize;
        private final int servings;

        // Optional paramters - initialized to default values
        private int calories = 0;
        private int fat = 0;
        private int sodium = 0;
        private int carbohydrate = 0;

        public Builder(int servingSize, int servings) {
            this.servingSize = servingSize;
            this.servings = servings;
        }

        public Builder calories(int val) {
            calories = val;
            return this;
        }

        public Builder fat(int val) {
            fat = val;
            return this;
        }

        public Builder sodium(int val) {
            sodium = val;
            return this;
        }

        public Builder carbohydrate(int val) {
            carbohydrate = val;
            return this;
        }

        public NutritionFacts build() {
            return new NutritionFacts(this);
        }
    }

    private NutritionFacts(Builder builder) {
        servingSize = builder.servingSize;
        servings = builder.servings;
        calories = builder.calories;
        fat = builder.fat;
        sodium = builder.sodium;
        carbohydrate = builder.carbohydrate;
    }
}
```

**_调用builder_**

```java
NutritionFacts cocaCola = new NutritionFacts.Builder(240, 8)
    .calories(100).sodium(35).carbohydrate(27).build();
```

<br/>

## 3. 用私有构造器或者枚举类型强化 _Singleton_ 属性
创建单例有多种的方法:

* **_公有静态成员是个final域_**

```java
public class Elvis {
    public static final Elvis INSTANCE = new Elvis();

    private Elvis() { ... }
    ...
    public void singASong() { ... }
}
```

有一点要提醒的是: 享有特权的客户端可以借助 _AccessibleObject.setAccessible_ 方法, 通过反射机制调用私有构造器.  
如果需要抵御这种攻击, 可以修改构造器, 让它在被要求创建第二个实例的时候抛出异常.

<br/>

* **_公有的成员是个静态工厂方法_**

```java
public class Elvis {
    private static final Elvis INSTANCE = new Elvis();
    private Elvis() { ... }

    public static Elvis getInstance() {
        return INSTANCE;
    }

    public void singASong() { ... }
}
```

工厂方法的优势之一在于, 它提供了灵活性: 在不改变其中API的前提下, 我们可以改变该类是否应该为 _Singleton_ 的想法.

<br/>

* **_序列化一个Singleton_**

为了维护并保证 _Singleton_, 除了在声明中加上 "_implements Serializable_", 还必须声明所有实例域都是瞬时(_transient_)的, 并提供一个 _readResolve_ 方法.

```java
private Object readResolve() {
    // Return the one true Elvis and let the garbage collector take care of the Elvis impersonator
    return INSTANCE;
}
```

<br/>

* **_单元素的枚举类型, 最好的实现方式_**(Java 1.5)

```java
public enum Elvis() {
    INSTANCE;
    ...
    public void singASong() { ... }
}
```

这种方法在功能上与公有域方法相近, 但是它更加简洁, 无偿地提供了序列化机制, 绝对防止多次实例化, 即使是在面对复杂的序列化或者反射攻击的时候.

单元素的枚举类型已经成为实现 _Singleton_ 的最佳方法.

<br/>

## 4. 通过私有构造器强化不可实例化的能力
用于只包含静态方法和静态域的类.

例如用于:

* 把基本类型的值或者数组类型上的相关方法组织起来. (比如: _java.lang.Math_ 或者 _java.util.Arrays_)
* 把实现特定接口的对象上的静态方法(包括工厂方法)组织起来. (比如: _java.util.Collections_)
* 把 _final_ 类上的方法组织起来, 以取代扩展该类的做法.

**_包含私有构造器_**

```java
public class UtilityClass {
    // Suppress default constructor for noninstantiability
    private UtilityClass() {
        throw new AssertionError();
    }

    ... // Remainder omitted
}
```

<br/>

## 5. 避免创建不必要的对象
* **_重用不可变的对象_**

**_不要这样做:_**

```java
String s = new String("stringette");
```

该语句每次被执行的时候都创建一个新的 _String_ 实例. 参数 "_stringette_" 本身就是一个 _String_ 实例, 如果这种用法是在一个循环中, 或者是在一个被频繁调用的方法中, 就会创建出成千上万不必要的 _String_ 实例.

**_应该这样做:_**

```java
String s = "stringette";
```

这个版本只用了一个 _String_ 实例, 而不是每次执行的时候都创建一个新的实例.

<br/>

* **_使用静态工厂方法要优于构造器_**

比如: Boolean.valueOf(String) 几乎总是优先于构造器 Boolean(String)

<br/>

* **_重用那些已知不会被修改的可变对象_**

**_不要这样做:_**

```java
public class Person {
    private final Date birthDate;
    ...

    public boolean isBabyBoomer() {
        // Unnecessary allocation of expensive object
        Calendar gmtCal = Calendar.getInstance(TimeZone.getTimeZone("GMT"));
        gmtCal.set(1946, Calendar.JANUARY, 1, 0, 0, 0);
        Date boomStart = gmtCal.getTime();
        gmtCal.set(1965, Calendar.JANUARY, 1, 0, 0, 0);
        Date boomEnd = gmtCal.getTime();
        return birthDate.compareTo(boomStart) >= 0 && birthDate.compareTo(boomEnd) < 0;
    }
}
```

_isBabyBoomer_ 每次被调用的时候, 都会新建一个 _Calendar_, 一个 _TimeZone_ 和两个 _Date_ 实例, 这是不必要的.

**_应该这样做:_**

```java
public class Person() {
    private final Date birthDate;
    ...
    private static final Date BOOM_START;
    private static final Date BOOM_END;

    static {
        Calendar gmtCal = Calendar.getInstance(TimeZone.getTimeZone("GMT"));
        gmtCal.set(1946, Calendar.JANUARY, 1, 0, 0, 0);
        BOOM_START = gmtCal.getTime();
        gmtCal.set(1965, Calendar.JANUARY, 1, 0, 0, 0);
        BOOM_END = gmtCal.getTime();
    }

    public boolean isBabyBoomer() {
        return birthDate.compareTo(BOOM_START) >= 0 && birthDate.compareTo(BOOM_END) < 0;
    }
}
```

<br/>

* **_要优先使用基本类型而不是装箱基本类型, 要当心无意识的自动装箱_**

**_不要这样做:_**

```java
// Slow program. Where is the object creation?
public static void main(String[] args) {
    Long sum = 0L;
    for (long i = 0; i < Integer.MAX_VALUE; i++) {
        sum += i;
    }

    System.out.println(sum);
}
```

变量 _sum_ 被声明成 _Long_ 而不是 _long_, 意味着程序构造了大约 2<sup>31</sup> 个多余的 _Long_ 实例.

<br/>

* **_对象池一般来说不是一个好的做法_**

除非池中的对象是非常重量级的, 比如像: 数据库连接池.

<br/>

## 6. 消除过期的对象引用
**_你能找到其中的"内存泄漏"吗?_**

```java
public class Stack {
    private Object[] elements;
    private int size = 0;
    private static final int DEFAULT_ININTIAL_CAPACITY = 16;

    public Stack() {
        elements = new Object[DEFAULT_ININTIAL_CAPACITY];
    }

    public void push(Object e) {
        ensureCapacity();
        elements[size++] = e;
    }

    public Object pop() {
        if (size == 0) {
            throw new EmptyStackException();
        }
        return elements[--size];
    }

    private void ensureCapacity() {
        if (elements.length == size) {
            elements = Arrays.copyOf(elements, 2 * size + 1);
        }
    }
}
```

如果一个栈先是增长, 然后再收缩, 从栈中弹出来的对象将不会被当作垃圾回收. 因为栈内部维护着这些对象的过期引用(指的是永远都不会被解除的引用).

* **_清空对象引用_**

```java
    public pop() {
        if (size == 0) {
            throw new EmptyStackException();
        }

        Object result = elements[--size];
        elements[size] = null;  // Eliminate obsolete reference.
        return result;
    }
```

清空对象引用应该是一种例外, 而不是一种规范行为. 不要过度的去清空每一个对象的引用, 这样做既没必要, 也不是我们所期望的.

只有类是自己管理内存的, 才应该去清空对象引用.

<br/>

* **_缓存中的内存泄漏_**

解决缓存的内存泄漏有几种可能的方案:

使用 _WeakHashMap_. 记住只有当所要缓存项的生命周期, 是由该键的外部引用而不是由值决定时, _WeakHashMap_ 才有用处.

一个更为常见的做法是, 缓存应该时不时地清除掉没用的项. 这项工作可以使用一个后台线程来完成, 或者也可以在给缓存添加新条目的时候顺便进行清理. _LinkedHashMap_ 类利用它的 _removeEldestEntry_ 方法可以很容易地实现后一种方案.

<br/>

* **_监听器和回调中的内存泄漏_**

若客户端注册了回调, 但却没有显式地取消注册, 就很可能会发生内存泄漏.

解决这个问题的方法是, 只保存它们的弱引用(_weak reference_). 例如, 只将它们保存成 _WeakHashMap_ 中的键.

<br/>

* **_时不时的使用 Heap Profiler 工具去发现不可见的内存泄漏问题_**

<br/>

## 7. 避免使用终结方法
终结方法通常是不可预测的, 也是很危险的, 一般情况下是不必要的.

* **_注重时间的任务不应该由终结方法来完成_**

    > 不能保证终结方法会被及时地执行.

* **_不应该依赖终结方法来更新重要的持久状态_**

    > _Java_ 语言规范不仅不保证终结方法会被及时执行, 而且根本就不保证它们会被执行.

* 如果异常发生在终结方法之中, 甚至连警告都不会打印出来.

* 使用终结方法会有非常严重的性能损失.

<br/>

**_解决方案_**:

提供一个显式的终止方法, 比如像: _InputStream_, _OutputStream_ 和 _java.sql.Connection_ 上的 _close_ 方法.

显式的终止方法通常与 _try-finally_ 结构结合起来使用, 以确保及时终止.

```java
Foo foo = new Foo(...);
try {
    // Do what must be done with foo
    ...
} finally {
    foo.terminate();  // Explicit termination method
}
```

<br/>

**终结方法有两个合理的用途:**

* 当对象的所有者忘记调用前面建议的显式终止方法时, 终结方法可以充当"安全网".  
(如果你正考虑编写这样的安全网终结方法, 就要认真考虑清楚, 这种额外的保护是否值得你付出这份额外的代价)

* 在本地对等体(_native peer_)中使用, 因为垃圾回收器不会知道它们.  
(在本地对等体并不拥有关键资源的前提下, 终结方法正是执行这项任务最合适的工具. 如果本地对等体拥有必须被及时终止的资源, 那么该类就应该具有一个显式的终止方法)

在以上很少见的情况下, 既然使用了终结方法, 就要记住调用 _super.finalize_

<br/>

# 三. 对于所有对象都通用的方法
## 8. 覆盖 _equals_ 时请遵守通用约定
**_以下情况时不要覆盖_**:

* 类的每个实例本质上是唯一的. 例如: _Thread_

* 不关心类是否提供了"逻辑相等"的测试功能. 例如: _java.util.Random_

* 超类已经覆盖了 _equals_, 从超类继承过来的行为对于子类也是合适的. 例如: _Set_, _List_, _Map_

* 类是私有的或者是包级私有的, 可以确定它的 _equals_ 方法永远不会被调用.

<br/>

**_以下情况时, 应该覆盖 equals:_**

如果类具有自己特有的"逻辑相等"概念(不同于对象等同的概念), 而且超类还没有覆盖 _equals_ 以实现期望的行为.

<br/>

**_覆盖 equals 方法时, 需实现了等价关系_**

* 自反性: _x.equals(x)==true_
* 对称性: _x.equals(y)==y.equals(x)_
* 传递性: _x.equals(y)==y.equals(z)==z.equals(x)_
* 一致性: _x.equals(y)==x.equals(y)==x.equals(y)=..._
* 非空性: _x.equals(null)->false_

<br/>

**_实现高质量 equals 方法的决窍:_**

1. 使用 _==_ 操作符, 检查"参数是否为这个对象的引用". (这是为了性能的优化)

2. 使用 _instanceof_ 操作符, 检查"参数是否为正确的类型".

3. 把参数转换成正确的类型.

4. 对于该类中的每个"关键(_significant_)"域, 检查参数中的域是否与该对象中对应的域相匹配.

5. 当你编写完成了 _equals_ 方法之后, 应该问自己三个问题: 它是否是对称的, 传递的, 一致的? (自反性和非空性通常上会自动满足)

```java
@Override
public boolean equals(Object o) {
    if (o == this) {
        return true;
    }

    if (!(o instanceof PhoneNumber)) {
        return false;
    }

    PhoneNumber pn = (PhoneNumber)o;
    return pn.lineNumber == lineNumber
        && pn.prefix == prefix
        && pn.areaCode == areaCode;
}
```

<br/>

**_最后的一些告诫:_**

* 覆盖 _equals_ 时总要覆盖 _hashCode_

* 不要企图让 _equals_ 方法过于智能(简单才是你的朋友)

* 不是将 _equals_ 声明中的 _Object_ 对象替换为其它的类型

<br/>

## 9. 覆盖 _equals_ 时总要覆盖 _hashCode_
**_hashCode 的通用约定:_**

* 在应用程序的执行期间, 只要对象的 _equals_ 方法的比较操作所用到的信息没有被修改, 那么对这同一个对象调用多次, _hashCode_ 方法都必须始终如一地返回同一个整数. 在同一个应用程序的多次执行过程中, 每次执行所返回的整数可以不一致.

* 如果两个对象根据 _equals(Object)_ 方法比较是相等的, 那么调用这两个对象中任意一个对象的 _hashCode_ 方法都必须产生同样的整数结果.

* 如果两个对象根据 _equals(Object)_ 方法比较是不相等的, 那么调用这两个对象中任意一个对象的 _hashCode_ 方法, 则不一定要产生不同的整数结果. 但是程序员应该知道, 给不相等的对象产生截然不同的整数结果, 有可能提高散列表(_hash table_)的性能.

<br/>

**_覆盖 hashCode 方法的决窍:_**

1. 把某个非零的常数值, 比如: 17, 保存在一个名为 _result_ 的 _int_ 类型的变量中.

2. 对于对象中每个关键域 _f_ (指 _equals_ 方法中涉及的每个域), 完成以下步骤:

    a. 为该域计算 _int_ 类型的散列码 _c_:

        i. boolean 类型: (f ? 1 : 0)

        ii. byte, char, short 或者 int 类型: (int)f

        iii. long 类型: (int)(f ^ (f >>> 32))

        iv. float 类型: Float.floatToIntBits(f)

        v. double 类型: Double.doubleToLongBits(f), 然后按照步骤 2.a.iii, 为得到的 long 类型值计算散列值

        vi. 对象引用: 如果该类的 equals 方法通过递归地调用 equals 的方式来比较这个域, 则同样为这个域递归地调用 hashCode.  
        如果这个域的值为 null, 则返回 0(或者其它某个常数, 但通常为 0)

        vii. array 类型: 把每一个元素当做单独的域来处理. 递归地应用上述规则, 对每个重要的元素计算一个散列码, 
        然后根据步骤 2.b 中的做法把这些散列值组合起来.  
        如果数组域中的每个元素都很重要, 可以利用 Java 1.5 中新增的 Arrays.hashCode 方法.

    b. 按照下面的公式, 把步骤 2.a 中计算得到的散列码 _c_ 合并到 _result_ 中:

        result = 31 * result + c;

3. 返回 _result_.

4. 问问自己 "相等的实例是否都具有相等的散列码?".

```java
// Lazily initialized, cached hashCode
private volatile int hashCode;

@Override
public int hashCode() {
    int result = hashCode;
    if (result == 0) {
        result = 17;
        result = 31 * result + areaCode;
        result = 31 * result + prefix;
        result = 31 * result + lineNumber;
    }
    return result;
}
```

<br/>

**_需要注意的是:_**

* 在散列码的计算过程中, 可以把冗余域排除在外. (必须排除 _equals_ 比较计算中没有用到的任何域)

* 不要试图从散列码计算中排除掉一个对象的关键部分来提高性能.

<br/>

## 10. 始终要覆盖 _toString_

## 11. 谨慎地覆盖 _clone_

## 12. 考虑实现 _Comparable_ 接口

<br/>

# 四. 类和接口
## 13. 使类和成员的可访问性最小化

## 14. 在公有类中使用访问方法而非公有域

## 15. 使可变性最小化

## 16. 复合优于继承

## 17. 要么为继承而设计, 并提供文档说明, 要么就禁止继承

## 18. 接口优于抽象类

## 19. 接口只用于定义类型

## 20. 类层次优于标签类

## 21. 用函数对象表示策略

## 22. 优先考虑静态成员类

<br/>

# 五. 泛型
## 23. 请不要在新代码中使用原生态类型

## 24. 消除非受检警告

## 25. 列表优先于数组

## 26. 优先考虑泛型

## 27. 优先考虑泛型方法

## 28. 利用有限制通配符来提升API的灵活性

## 29. 优先考虑类型安全的异构容器

<br/>

# 六. 枚举和注解
## 30. 用 _enum_ 代替 _int_ 常量
## 31. 用实例域代替序数

## 32. 用 _EnumSet_ 代替位域

## 33. 用 _EnumMap_ 代替序数索引

## 34. 用接口模拟可伸缩的枚举

## 35. 注解优先于命名模式

## 36. 坚持使用 _Override_ 注解

## 37. 用标记接口定义类型

<br/>

# 七. 方法
## 38. 检查参数的有效性

## 39. 必要时进行保护性拷贝

## 40. 谨慎设计方法签名

## 41. 慎用重载

## 42. 慎用可变参数

## 43. 返回零长度的数组或者集合, 而不是 _null_

## 44. 为所有导出的API元素编写文档注释

<br/>

# 八. 通用程序设计
## 45. 将局部变量的作用域最小化

## 46. _for-each_ 循环优先于传统的 _for_ 循环

## 47. 了解和使用类库

## 48. 如果需要精确的答案, 请避免使用 _float_ 和 _double_

## 49. 基本类型优先于装箱基本类型

## 50. 如果其它类型更适合, 则尽量避免使用字符串

## 51. 当心字符串连接的性能

## 52. 通过接口引用对象

## 53. 接口优先于反射机制

## 54. 谨慎地使用本地方法

## 55. 谨慎地进行优化

## 56. 遵守普遍接受的命令惯例

<br/>

# 九. 异常
## 57. 只针对异常的情况下才使用异常

## 58. 对可恢复的情况使用受检异常, 对编程错误使用运行时异常

## 59. 避免不必要地使用受检的异常

## 60. 优先使用标准的异常

## 61. 抛出与抽象相对应的异常

## 62. 每个方法抛出的异常都要有文档

## 63. 在细节消息中包含能捕获失败的信息

## 64. 努力使失败保持原子性

## 65. 不要忽略异常

<br/>

# 十. 并发
## 66. 同步访问共享的可变数据

## 67. 避免过度同步

## 68. _executor_ 和 _task_ 优先于线程

## 69. 并发工具优先于 _wait_ 和 _notify_

## 70. 线程安全性的文档化

## 71. 慎用延迟初始化

## 72. 不要依赖于线程调度器

## 73. 避免使用线程组

<br/>

# 十一. 序列化
## 74. 谨慎地实现 _Serializable_ 接口

## 75. 考虑使用自定义的序列化形式

## 76. 保护性地编写 _readObject_ 方法

## 77. 对于实例控制, 枚举类型优先于 _readResolve_

## 78. 考虑用序列化代理代替序列化实例
