# 包装类（Wrapper Class）与 Object 类

## 一、为什么需要包装类？

Java 为了提高运行效率，保留了 **8 种基本数据类型**，但它们不是对象，无法使用面向对象的特性。

因此，Java 为每种基本数据类型都提供了对应的包装类。

| 基本类型 | 包装类 |
|----------|---------|
| byte | Byte |
| short | Short |
| int | Integer |
| long | Long |
| float | Float |
| double | Double |
| char | Character |
| boolean | Boolean |

> **记忆技巧：** 除了 `Integer` 和 `Character`，其他都是首字母大写。

---

# 二、基本类型 VS 包装类

| 基本类型 | 包装类 |
|----------|---------|
| 存储值 | 存储对象 |
| 存放在栈中（局部变量） | 对象存放在堆中 |
| 默认值为 0、false 等 | 默认值为 null |
| 运算效率高 | 功能丰富，可调用方法 |

例如：

```java
int a = 10;
Integer b = 10;
```

区别：

```java
a       // 没有任何方法

b.xxx() // 可以调用各种方法
```

---

# 三、自动装箱与自动拆箱

## 自动装箱

基本类型 → 包装类

```java
Integer a = 100;
```

编译器实际执行：

```java
Integer a = Integer.valueOf(100);
```

---

## 自动拆箱

包装类 → 基本类型

```java
Integer a = 100;
int b = a;
```

底层：

```java
int b = a.intValue();
```

---

# 四、空指针异常（NPE）

包装类默认值是 **null**。

```java
Integer score = null;

int s = score;
```

实际上执行：

```java
score.intValue();
```

由于 score 为 null，会抛出：

```text
NullPointerException
```

**开发中要注意：**

使用包装类之前，先判断是否为 null。

---

# 五、Integer 缓存（IntegerCache）

```java
Integer a = 127;
Integer b = 127;

System.out.println(a == b);
```

输出：

```text
true
```

但是：

```java
Integer a = 128;
Integer b = 128;

System.out.println(a == b);
```

输出：

```text
false
```

原因：

Java 会缓存 **-128 ~ 127** 之间的 Integer 对象。

超出范围会重新创建对象。

---

## 比较包装类

错误：

```java
Integer a = 128;
Integer b = 128;

a == b
```

比较的是地址。

正确：

```java
a.equals(b)
```

比较的是值。

> **建议：包装类之间统一使用 `equals()`。**

---

# 六、包装类常用方法

字符串转数字：

```java
int age = Integer.parseInt("18");
```

字符串转小数：

```java
double pi = Double.parseDouble("3.14");
```

字符串转布尔：

```java
boolean flag = Boolean.parseBoolean("true");
```

如果字符串不是数字：

```java
Integer.parseInt("abc");
```

会抛出：

```text
NumberFormatException
```

---

# 七、包装类与集合

基本类型不能作为泛型。

错误：

```java
ArrayList<int> list;
```

正确：

```java
ArrayList<Integer> list = new ArrayList<>();
```

这是包装类最常见的使用场景。

---

# 八、Object 类

Java 中所有类都直接或间接继承 Object。

常用方法：

## 1、toString()

默认输出：

```text
类名@地址
```

重写后：

```java
@Override
public String toString() {
    return "Drone{id=" + id + ", model='" + model + "'}";
}
```

输出更加直观。

---

## 2、equals()

默认比较：

```text
对象地址
```

重写后可以比较对象内容。

例如：

```java
d1.equals(d2)
```

比较：

- id
- model

是否相同。

---

## 3、hashCode()

返回对象哈希值。

如果重写了 equals()，

一般也要一起重写 hashCode()。

保证：

```text
equals 相等

↓

hashCode 必须相等
```

---

## 4、getClass()

获取对象真实运行类型。

```java
System.out.println(obj.getClass().getName());
```

常用于：

- 类型判断
- equals()
- 反射

---

# 九、本章总结

✔ 理解了基本类型和包装类的区别

✔ 掌握自动装箱与自动拆箱

✔ 理解 IntegerCache（-128~127）

✔ 学会使用 parseInt() 等常用方法

✔ 掌握 Object 四个常用方法：

- toString()
- equals()
- hashCode()
- getClass()

> **一句话总结：**

包装类让基本类型拥有了面向对象能力；Object 是所有类的父类，提供了对象最基本的功能。