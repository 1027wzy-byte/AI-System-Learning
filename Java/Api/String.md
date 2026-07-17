# Day XX - String 字符串（String、StringBuilder、StringBuffer）

## 一、String 概述

`String` 是 Java 中最常用的引用数据类型，用于表示字符串。

特点：

- String 是一个类，不是基本数据类型
- 位于 `java.lang` 包，无需导包
- String 对象不可变（Immutable）

---

## 二、String 不可变（Immutable）

String 源码：

```java
public final class String {
    private final char[] value;
}
```

### 为什么不可变？

两把锁：

① String 类使用 final 修饰

```java
public final class String
```

不能被继承。

② 保存数据的数组也是 final

```java
private final char[] value;
```

创建以后不能修改引用。

---

例如：

```java
String s = "Java";
s = s + "17";
```

很多人认为：

```
Java
↓

Java17
```

实际上是：

```
"Java"       （旧对象）

↓

创建新对象

↓

"Java17"

↓

s 指向新对象
```

原来的 `"Java"` 没有发生任何变化。

---

## 三、字符串常量池（String Pool）

Java 为了节省内存，维护了一块：

```
String Pool（字符串常量池）
```

专门保存字符串字面量。

---

### 1、字面量创建

```java
String s1 = "Hello";
String s2 = "Hello";
```

流程：

```
常量池没有

↓

创建

↓

两个变量共同指向它
```

所以：

```java
System.out.println(s1 == s2);
```

结果：

```java
true
```

---

### 2、new 创建

```java
String s3 = new String("Hello");
String s4 = new String("Hello");
```

每次都会：

```
new

↓

堆中创建新的对象
```

所以：

```java
System.out.println(s3 == s4);
```

结果：

```java
false
```

---

### 一个经典面试题

```java
String s = new String("abc");
```

可能创建：

### 情况一

常量池没有 abc

创建：

```
常量池 abc

+

堆对象 abc
```

共：

```
2 个对象
```

---

### 情况二

常量池已经有 abc

只创建：

```
堆对象
```

共：

```
1 个对象
```

---

## 四、== 与 equals()

### ==

比较：

```
对象地址
```

例如：

```java
String s1 = "abc";
String s2 = "abc";

System.out.println(s1 == s2);
```

true

---

```java
String s3 = new String("abc");
String s4 = new String("abc");

System.out.println(s3 == s4);
```

false

---

### equals()

比较：

```
字符串内容
```

例如：

```java
System.out.println(s3.equals(s4));
```

结果：

```
true
```

---

### 黄金法则

字符串比较：

永远使用：

```java
equals()
```

不要使用：

```java
==
```

---

## 五、字符串拼接

### +

例如：

```java
String s = "Java";

s += "17";
```

实际上会创建：

```
新的 String 对象
```

旧对象不会修改。

---

### 编译期优化

例如：

```java
String s = "AB" + "CD";
```

编译器直接优化成：

```java
"ABCD"
```

所以：

```java
String s1 = "ABCD";
String s2 = "AB" + "CD";

System.out.println(s1 == s2);
```

true

---

但是：

```java
String a = "AB";
String b = "CD";

String c = a + b;
```

不会优化。

因为变量值只有运行时才能知道。

所以：

```java
String s = "ABCD";

System.out.println(s == c);
```

false

---

## 六、StringBuilder

为什么出现？

因为：

```
String 不可变
```

每次拼接：

```
创建新对象
```

例如：

```java
String result = "";

for (...) {
    result += i;
}
```

实际上会产生：

```
大量临时 String 对象
```

效率很低。

---

### 正确写法

```java
StringBuilder sb = new StringBuilder();

for (...) {
    sb.append(i);
}

String result = sb.toString();
```

特点：

- 可变字符序列
- 不会一直创建新的 String
- 拼接效率高

---

### 常用方法

创建：

```java
StringBuilder sb = new StringBuilder();
```

追加：

```java
sb.append("Java");
```

删除：

```java
sb.deleteCharAt(3);
```

长度：

```java
sb.length();
```

转换成 String：

```java
sb.toString();
```

---

## 七、StringBuffer

和 StringBuilder 基本一样。

区别：

### StringBuilder

线程不安全

但是：

```
速度最快
```

推荐：

```
单线程开发
```

---

### StringBuffer

线程安全

因为内部加了锁：

```
synchronized
```

速度稍慢。

推荐：

```
多线程环境
```

---

## 八、String.format()

用于字符串格式化。

例如：

```java
String name = "张三";

double money = 888.88;

int id = 12;
```

```java
String result = String.format(
        "用户：%s，余额：%.2f，编号：%05d",
        name,
        money,
        id
);
```

输出：

```
用户：张三，余额：888.88，编号：00012
```

---

### 常用占位符

字符串：

```java
%s
```

整数：

```java
%d
```

补零：

```java
%05d
```

小数：

```java
%f
```

保留两位：

```java
%.2f
```

---

## 九、String 常用 API

### 去除空格

```java
trim()
```

---

### 截取字符串

```java
substring(begin,end)
```

特点：

```
左闭右开
```

---

### 判断是否包含

```java
contains()
```

---

### 替换

```java
replace()
```

---

### 获取长度

```java
length()
```

---

### 比较内容

```java
equals()
```

---

## 十、本节重点

### 必须掌握

✅ String 不可变

✅ 字符串常量池

✅ == 与 equals()

✅ StringBuilder

✅ StringBuffer

✅ String.format()

---

## 十一、开发规范

字符串比较：

```java
equals()
```

循环拼接：

```java
StringBuilder
```

普通拼接：

```java
+
```

多线程拼接：

```java
StringBuffer
```

---

## 十二、本节总结

### String

- 不可变
- 存放字符串
- 有字符串常量池

### StringBuilder

- 可变
- 拼接效率高
- 单线程推荐

### StringBuffer

- 可变
- 线程安全
- 多线程推荐

### 判等

对象地址：

```java
==
```

字符串内容：

```java
equals()
```

### 一句话记忆

> String 不可变，比较用 equals；循环拼接 Builder，线程安全 Buffer；字面量进常量池，new 一定建新对象。