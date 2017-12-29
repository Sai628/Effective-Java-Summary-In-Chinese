
# 1. 目录
- [1. 目录](1-目录)
- [2. 创建和销毁对象](#2-创建和销毁对象)
    - [1. 考虑用静态工厂方法代替构造器](#1-考虑用静态工厂方法代替构造器)
    - [2. 遇到多个构造器参数时要考虑用构建器](#2-遇到多个构造器参数时要考虑用构建器)
    - [3. 用私有构造器或者枚举类型强化 _Singleton_ 属性](#3-用私有构造器或者枚举类型强化-singleton-属性)
    - [4. 通过私有构造器强化不可实例化的能力](#4-通过私有构造器强化不可实例化的能力)
    - [5. 避免创建不必要的对象](#5-避免创建不必要的对象)
    - [6. 消除过期的对象引用](#6-消除过期的对象引用)
    - [7. 避免使用终结方法](#7-避免使用终结方法)
- [3. 对于所有对象都通用的方法](#3-对于所有对象都通用的方法)
    - [8. 覆盖 _equals_ 时请遵守通用约定](#8-覆盖-equals-时请遵守通用约定)
    - [9. 覆盖 _equals_ 时总要覆盖 _hashCode_](#9-覆盖-equals-时总要覆盖-hashcode)
    - [10. 始终要覆盖 _toString_](#10-始终要覆盖-tostring)
    - [11. 谨慎地覆盖 _clone_](#11-谨慎地覆盖-clone)
    - [12. 考虑实现 _Comparable_ 接口](#12-考虑实现-comparable-接口)
- [4. 类和接口](#4-类和接口)
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
- [5. 泛型](#5-泛型)
    - [23. 请不要在新代码中使用原生态类型](#23-请不要在新代码中使用原生态类型)
    - [24. 消除非受检警告](#24-消除非受检警告)
    - [25. 列表优先于数组](#25-列表优先于数组)
    - [26. 优先考虑泛型](#26-优先考虑泛型)
    - [27. 优先考虑泛型方法](#27-优先考虑泛型方法)
    - [28. 利用有限制通配符来提升API的灵活性](#28-利用有限制通配符来提升api的灵活性)
    - [29. 优先考虑类型安全的异构容器](#29-优先考虑类型安全的异构容器)
- [6. 枚举和注解](#6-枚举和注解)
    - [30. 用 _enum_ 代替 _int_ 常量](#30-用-enum-代替-int-常量)
    - [31. 用实例域代替序数](#31-用实例域代替序数)
    - [32. 用 _EnumSet_ 代替位域](#32-用-enumset-代替位域)
    - [33. 用 _EnumMap_ 代替序数索引](#33-用-enummap-代替序数索引)
    - [34. 用接口模拟可伸缩的枚举](#34-用接口模拟可伸缩的枚举)
    - [35. 注解优先于命名模式](#35-注解优先于命名模式)
    - [36. 坚持使用 _Override_ 注解](#36-坚持使用-override-注解)
    - [37. 用标记接口定义类型](#37-用标记接口定义类型)
- [7. 方法](#7-方法)
    - [38. 检查参数的有效性](#38-检查参数的有效性)
    - [39. 必要时进行保护性拷贝](#39-必要时进行保护性拷贝)
    - [40. 谨慎设计方法签名](#40-谨慎设计方法签名)
    - [41. 慎用重载](#41-慎用重载)
    - [42. 慎用可变参数](#42-慎用可变参数)
    - [43. 返回零长度的数组或者集合, 而不是 _null_](#43-返回零长度的数组或者集合-而不是-null)
    - [44. 为所有导出的API元素编写文档注释](#44-为所有导出的api元素编写文档注释)
- [8. 通用程序设计](#8-通用程序设计)
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
- [9. 异常](#9-异常)
    - [57. 只针对异常的情况下才使用异常](#57-只针对异常的情况下才使用异常)
    - [58. 对可恢复的情况使用受检异常, 对编程错误使用运行时异常](#58-对可恢复的情况使用受检异常-对编程错误使用运行时异常)
    - [59. 避免不必要地使用受检的异常](#59-避免不必要地使用受检的异常)
    - [60. 优先使用标准的异常](#60-优先使用标准的异常)
    - [61. 抛出与抽象相对应的异常](#61-抛出与抽象相对应的异常)
    - [62. 每个方法抛出的异常都要有文档](#62-每个方法抛出的异常都要有文档)
    - [63. 在细节消息中包含能捕获失败的信息](#63-在细节消息中包含能捕获失败的信息)
    - [64. 努力使失败保持原子性](#64-努力使失败保持原子性)
    - [65. 不要忽略异常](#65-不要忽略异常)
- [10. 并发](#10-并发)
    - [66. 同步访问共享的可变数据](#66-同步访问共享的可变数据)
    - [67. 避免过度同步](#67-避免过度同步)
    - [68. _executor_ 和 _task_ 优先于线程](#68-executor-和-task-优先于线程)
    - [69. 并发工具优先于 _wait_ 和 _notify_](#69-并发工具优先于-wait-和-notify)
    - [70. 线程安全性的文档化](#70-线程安全性的文档化)
    - [71. 慎用延迟初始化](#71-慎用延迟初始化)
    - [72. 不要依赖于线程调度器](#72-不要依赖于线程调度器)
    - [73. 避免使用线程组](#73-避免使用线程组)
- [11. 序列化](#11-序列化)
    - [74. 谨慎地实现 _Serializable_ 接口](#74-谨慎地实现-serializable-接口)
    - [75. 考虑使用自定义的序列化形式](#75-考虑使用自定义的序列化形式)
    - [76. 保护性地编写 _readObject_ 方法](#76-保护性地编写-readobject-方法)
    - [77. 对于实例控制, 枚举类型优先于 _readResolve_](#77-对于实例控制-枚举类型优先于-readresolve)
    - [78. 考虑用序列化代理代替序列化实例](#78-考虑用序列化代理代替序列化实例)

<br/>

# 2. 创建和销毁对象
## 1. 考虑用静态工厂方法代替构造器
**_优点_**

静态工厂方法与构造器不同的优势在于:
* 它们有名称
* 不必在每次调用它们的时候都创建一个新对象
* 它们可以返回原返回类型的任何子类型的对象

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

* **_序列化一个Singleton_**

为了维护并保证 _Singleton_, 除了在声明中加上 "_implements Serializable_", 还必须声明所有实例域都是瞬时(_transient_)的, 并提供一个 _readResolve_ 方法.

```java
private Object readResolve() {
    // Return the one true Elvis and let the garbage collector take care of the Elvis impersonator
    return INSTANCE;
}
```

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

* **_使用静态工厂方法要优于构造器_**

比如: Boolean.valueOf(String) 几乎总是优先于构造器 Boolean(String)

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

* **_对象池一般来说不是一个好的做法_**

除非池中的对象是非常重量级的, 比如像: 数据库连接池.

## 6. 消除过期的对象引用

## 7. 避免使用终结方法

<br/>

# 3. 对于所有对象都通用的方法
## 8. 覆盖 _equals_ 时请遵守通用约定

## 9. 覆盖 _equals_ 时总要覆盖 _hashCode_

## 10. 始终要覆盖 _toString_

## 11. 谨慎地覆盖 _clone_

## 12. 考虑实现 _Comparable_ 接口

<br/>

# 4. 类和接口
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

# 5. 泛型
## 23. 请不要在新代码中使用原生态类型

## 24. 消除非受检警告

## 25. 列表优先于数组

## 26. 优先考虑泛型

## 27. 优先考虑泛型方法

## 28. 利用有限制通配符来提升API的灵活性

## 29. 优先考虑类型安全的异构容器

<br/>

# 6. 枚举和注解
## 30. 用 _enum_ 代替 _int_ 常量
## 31. 用实例域代替序数

## 32. 用 _EnumSet_ 代替位域

## 33. 用 _EnumMap_ 代替序数索引

## 34. 用接口模拟可伸缩的枚举

## 35. 注解优先于命名模式

## 36. 坚持使用 _Override_ 注解

## 37. 用标记接口定义类型

<br/>

# 7. 方法
## 38. 检查参数的有效性

## 39. 必要时进行保护性拷贝

## 40. 谨慎设计方法签名

## 41. 慎用重载

## 42. 慎用可变参数

## 43. 返回零长度的数组或者集合, 而不是 _null_

## 44. 为所有导出的API元素编写文档注释

<br/>

# 8. 通用程序设计
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

# 9. 异常
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

# 10. 并发
## 66. 同步访问共享的可变数据

## 67. 避免过度同步

## 68. _executor_ 和 _task_ 优先于线程

## 69. 并发工具优先于 _wait_ 和 _notify_

## 70. 线程安全性的文档化

## 71. 慎用延迟初始化

## 72. 不要依赖于线程调度器

## 73. 避免使用线程组

<br/>

# 11. 序列化
## 74. 谨慎地实现 _Serializable_ 接口

## 75. 考虑使用自定义的序列化形式

## 76. 保护性地编写 _readObject_ 方法

## 77. 对于实例控制, 枚举类型优先于 _readResolve_

## 78. 考虑用序列化代理代替序列化实例
