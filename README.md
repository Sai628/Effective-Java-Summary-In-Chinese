
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

**_覆盖 equals 方法时, 需实现了等价关系:_**

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
提供好的 _toString_ 实现可以使类用起来更加舒适.

在实际应用中, _toString_ 方法应该返回对象中包含的所有值得关注的信息.

无论你是否决定指定格式, 都应该在文档中明确地表明你的意图.

无论是否指定格式, 都为 _toString_ 返回值中包含的所有信息, 提供一种编程式的访问途径, 使得对象的使用者不需要自己去解析这些字符串. 例如: _PhoneNumber_ 类应该包含针对 _areaCode_, _prefix_ 和 _lineNumber_ 的访问方法.

<br/>

## 11. 谨慎地覆盖 _clone_
_Cloneable_ 接口并没有包含任何方法. 如果一个类实现了 _Cloneable_ 接口, _Object_ 的 _clone_ 方法就会返回该对象的逐域拷贝, 否则就会抛出 _CloneNotSupportedException_ 异常.

如果你覆盖了非 _final_ 类中的 _clone_ 方法, 则应该返回一个通过调用 _super.clone_ 而得到的对象. 对于实现了 _Cloneable_ 的类, 我们总是期望它也提供一个功能适当的公有的 _clone_ 方法.

<br/>

如果对象中 **没有包含** 可变对象的域, 可以使用简单的 _clone_ 的实现:

```java
@Override
public PhoneNumber clone() {
    try {
        // PhoneNumber.clone must cast the result of super.clone() before returning it.
        return (PhoneNumber)super.clone();
    } catch (CloneNotSupportedException e) {
        throw new AssertionError();  // Can't happen
    }
}
```

<br/>

但如果对象中 **包含了** 可变对象的域, 我们就需要另一种解决方案了. 因为可变域会指向内存中相同的对象, 原始的实例与被克隆的实例将会共享这些对象.

_clone_ 方法就是另一个构造器, 你必须确保它不会伤害到原始的对象, 并确保正确地创建被克隆对象中的约束条件.

在可变域对象上递归地调用 _clone_ 是最容易的做法:

```java
@Override
public Stack clone() {
    try {
        Stack result = (Stack)super.clone();
        // From Java 1.5, don't need casting when cloning arrays.
        result.elements = elements.clone();
        return result;
    } catch (CloneNotSupportedException e) {
        throw new AssertionError();
    }
}
```

<br/>

_clone_ 架构与引用可变对象的 _final_ 域的正常用法是不相兼容的, 除非在原始对象和克隆之间可以安全地共享此可变对象.

对于更复杂的对象的克隆, 有时递归地调用 _clone_ 是不够的, 还需要一些特别的方法.  
例如:

* 对于被克隆对象中的对象数组域, 很可能需要进行"深度拷贝". 对于容易导致栈溢出的调用, 可以在 _deepCopy_ 中用迭代代替递归.

* 使用另一种方式去完成克隆操作: 先调用 _super.clone_, 然后把结果对象中的所有域都设置成它们的空白状态, 然后调用高层的方法来重新产生对象的状态.

<br/>

如同构造器一样, _clone_ 方法不应该在构造的过程中, 调用新对象中任何非 _final_ 的方法.

_Object_ 的 _clone_ 方法被声明为可抛出 _CloneNotSupportedException_ 异常, 但是, 覆盖版本的 _clone_ 方法可能会忽略这个声明.  
公有的 _clone_ 方法应该省略这个声明.

如果专门为了继承而设计的类覆盖了 _clone_ 方法, 覆盖版本的 _clone_ 方法就应该模拟 _Object.clone_ 的行为:

* 它应该被声明为 _protected_;
* 它应该被声明为抛出 _CloneNotSupportedException_ 异常;
* 它 **不应该** 实现 _Cloneable_ 接口.

这样可使得子类具有实现或不实现 _Cloneable_ 接口的自由, 就仿佛它们直接扩展了 _Object_ 一样.

<br/>

值得注意的是:

> 如果你决定用线程安全的类实现 _Cloneable_ 接口, 要记得它的 _clone_ 方法必须得到很好的同步.

简而言之, 实现了 _Cloneable_ 接口的类, 都应该像以下步骤这样创建一个方法:

* 用一个公有的方法覆盖 _clone_;
* 返回的对象类型是当前的类;
* 首先调用 _super.clone_ 方法;
* 然后修改任何需要修正的域.

<br/>

最好提供某些其它的途径来代替对象拷贝, 或者干脆不提供这样的功能.

**_拷贝构造器_**

```java
public Yum(Yum yum);
```

**_拷贝工厂_**

```java
public static Yum newInstance(Yum yum);
```

拷贝构造器的做法, 及其静态工厂方法的变形, 都比 _Cloneable/clone_ 的方式具有更多的优势:

* 不依赖于某一种很有风险的, 语言之外的对象创建机制;
* 不要求遵守尚未制定好文档的规范;
* 不会与 _final_ 域的正常使用发生冲突;
* 不会抛出不必要的受检异常;
* 不需要进行类型转换.

除此之外, 基于接口的拷贝构造器和拷贝工厂(更准确的应叫 "转换构造器" 和 "转换工厂"), 允许客户选择拷贝的实现类型

```java
public HashSet(Set set) -> TreeSet;
```

<br/>

## 12. 考虑实现 _Comparable_ 接口
_Comparable_ 是一个接口, 它并没有在 _Object_ 中声明.

为实现 _Comparable_ 接口的对象数组进行排序可以简单地使用: _Arrays.sort(a);_

一旦类实现了 _Comparable_ 接口, 它就可以跟许多泛型算法以及依赖于该接口的集合实现进行协作. 你付出很小的努力就可以获得非常强大的功能.

_compareTo_ 方法需遵循以下的约定(自反性, 对称性, 传递性)

* if a > b then b < a;  if a == b then b == a;  if a < b then b > a;

* if a > b and b > c then a > c;

* if a == b and b == c then a == c;

* 强烈建议: (x.compareTo(y) == 0) == (x.equals(y))

<br/>

比较整数型基本类型的域, 可以使用关系操作符 < 和 >. 对于浮点域, 需使用 _Double.compare_ 或者 _Float.compare_. 对于数组域, 则要把这些指导原则应用到每个元素上.

如果一个类有多个关键域, 那么, 按什么样的顺序来比较这些域是非常关键的. 你必须从最关键的域开始, 逐步进行到所有的重要域.

```java
public int compareTo(PhoneNumber pn) {
    // Compare area codes
    if (areaCode < pn.areaCode) {
        return -1;
    }
    if (areaCode > pn.areaCode) {
        return 1;
    }

    // Area codes are equal, compare prefixes
    if (prefix < pn.prefix) {
        return -1;
    }
    if (prefix > pn.prefix) {
        return 1;
    }

    // Area codes and prefixes are equal, compare line numbers
    if (lineNumber < pn.lineNumber) {
        return -1;
    }
    if (lineNumber > pn.lineNumber) {
        return 1;
    }

    return 0;  // All fields are equal
}
```

<br/>

# 四. 类和接口
## 13. 使类和成员的可访问性最小化
__封装:__

* 设计良好的模块会隐藏所有的实现细节.

* 模块之间只通过它们的API进行通信, 一个模块不需要知道其它模块的内部工作情况.

* 解除组成系统的各模块之间的耦合关系, 使得这些模块可以独立地:
    - 开发(可以并行的进行)
    - 测试(即使整个系统无法通过测试, 独立的模块也可能测试成功)
    - 优化与修改(不会影响到其它的模块)
    - 理解(不需要被其它的模块理解)
    - 重用

<br/>

__尽可能地使每个类或者成员不被外界访问__

如果一个包级私有的顶层类(或者接口), 只是在某一个类的内部被使用, 就应该考虑使它成为唯一使用它的那个类的私有嵌套类.

为了测试而将一个公有类的私有成员变成包级私有的, 这还可以接受, 但是要将访问级别提高到超过它, 这就无法接受了.
> 不能为了测试, 而将类/接口或者成员变量变成包的导出API的一部分.

<br/>

_实例域决不能是公有的._ 包含公有可变域的类并不是线程安全的.

对于静态域, 如果这些域包含基本类型的值, 或者是包含指向不可变对象的引用, 那么可以通过公有的静态 _final_ 域来暴露这些常量. 如果 _final_ 域包含可变对象的引用, 它便具有非 _final_ 域的所有缺点.

<br/>

长度非零的数组总是可变的. 所有, __类具有公有的静态final数组域, 或者返回这种域的访问方法, 这几乎总是错误的.__

```java
// 存在的安全漏洞!
public static final Thing[] VALUES = { ... };
```

解决方案:
```java
private static final Thing[] PRIVATE_VALUES = { ... };

public static final List<Thing> VALUES = Collections.unmodifiableList(Arrays.asList(PRIVATE_VALUES));
```

或者:
```java
private static final Thing[] PRIVATE_VALUES = { ... };

public static final Thing[] values() {
    return PRIVATE_VALUES;
}
```

<br/>

## 14. 在公有类中使用访问方法而非公有域
退化类(_Degenerate classes_)不应该是公有的

```java
class Point {
    public double x;
    public double y;
}
```

因为这些类:

* 没有提供封装的功能;
* 如果不改变API, 就无法改变它的数据表示法;
* 无法强加任何约束条件;
* 当域被访问的时候, 无法采取任何辅助的行动.

<br/>

对于可变的类来说, 应该用包含私有域和公有设值方式(_setter_)的类代替:

```java
class Point {
    private double x;
    private double y;

    public Point(double x, double y) {
        this.x = x;
        this.y = y;
    }

    public double getX() {
        return x;
    }

    public double getY() {
        return y;
    }

    public void setX(double x) {
        this.x = x;
    }

    public void setY(double y) {
        this.y = y;
    }
}
```

<br/>

* 如果类可以在它所在的包的外部进行访问, 就提供访问方法.

* 如果类是包级私有的, 或者是私有的嵌套类, 直接暴露它的数据域并没有本质的错误.

* 公有类永远都不应该暴露可变的域. 虽然还是有问题, 但是让公有类暴露不可变的域其危害比较小.

```java
// Public class with exposed immutable fields - questionable
public final class Time {
    private static final int HOURS_PER_DAY = 24;
    private static final int MINUTES_PER_HOUR = 60;

    public final int hour;
    public final int minute;

    public Time(int hour, int minute) {
        if (hour < 0 || hour >= HOURS_PER_DAY) {
            throw new IllegalArgumentException("Hour: " + hour);
        }
        if (minute < 0 || minute >= MINUTES_PER_HOUR) {
            throw new IllegalArgumentException("Min: " + minute);
        }
        this.hour = hour;
        this.minute = minute;
    }

    ... // Remainder omitted
}
```

<br/>

## 15. 使可变性最小化
不可变类只是其实例不能被修改的类. 每个实例中包含的所有信息都必须在创建该实例的时候就提供, 并在对象的整个生命周期内固定不变.  
不可变的类比可变类更加易于设计、实现和使用. 它们不容易出错, 且更加安全.

<br/>

__为了使类成为不可变, 要遵循下面5条规则:__

* 不要提供任何会修改对象状态的方法

* 保证类不会被扩展

* 使所有的域都是 _final_ 的

* 使所有的域都成为私有的

* 确保对于任何可变组件的互斥访问

<br/>

```java
public final class Complex {
    private final double re;
    private final double im;

    public Complex(double re, double im) {
        this.re = re;
        this.im = im;
    }

    // Accessors with no corresponding mutators
    public double realPart() {
        return re;
    }

    public double imaginaryPart() {
        return im;
    }

    public Complex add(Complex c) {
        return new Complex(re + c.re, im + c.im);
    }

    public Complex subtract(Complex c) {
        return new Complex(re - c.re, im - c.im);
    }

    ...

    @Override
    public boolean equals(Object o) {
        ...
    }
}
```

这些算术运算创建并返回新的 _Complex_ 实例. (函数的做法)

<br/>

不可变对象比较简单, 它们在整个生命周期内只有一种状态.

不可变对象本质上是线程安全的, 它们不要求同步. 它们可以被自由地共享, 并且可以重用现有的实例.

```java
public static final Complex ZERO = new Complex(0, 0);
public static final Complex ONE = new Complex(1, 0);
public static final Complex I = new Complex(0, 1);
```

不可变的类可以提供一些静态工厂, 它们把频繁被请求的实例缓存起来, 从而当现在实例可以符合请求的时候, 就不必创建新的实例.

<br/>

不仅可以共享不可变对象, 甚至也可以共享它们的内部信息.

不可变对象为其它对象提供了大量的构件(_building blocks_).

不可变类真正唯一的缺点是, 对于每个不同的值都需要一个单独的对象. 在某些情况下, 这会带来性能的问题.

<br/>

__如何禁止不可变对象子类化__
* 使类成为 _final_ 的
* 让类的所有构造器都变成私有的或者包级私有的, 并添加公有的静态工厂来代替公有的构造器

```java
// Immutable class with static factories instead of constructors
public class Complex {
    private final double re;
    private final double im;

    private Complex(double re, double im) {
        this.re = re;
        this.im = im;
    }

    public static Complex valueOf(double re, double im) {
        return new Complex(re, im);
    }

    ... // Remainder unchanged
}
```

除了允许多个实现类的灵活性之外, 这种方法还使得有可能通过改善静态工厂的对象缓存能力, 在后续的发行版本中改进该类的性能. 并且允许创建更多的工厂方法, 其名字就可以阐明其功能.

<br/>

__总结__

* 除非有很好的理由要让类成为可变的类, 否则就应该是不可变的

* 如果类不能被做成是不可变的, 仍然应该尽可能地限制它的可变性

* 除非有令人信服的理由要使域变成是非 _final_ 的, 否则要使每个域都是 _final_ 的

* 可以减轻一些规则以提高性能(缓存, 延迟初始化...)

<br/>

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
