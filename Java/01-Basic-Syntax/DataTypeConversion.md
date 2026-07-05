# 数据类型转换（Data Type Conversion）

---

## 什么是数据类型转换

不同数据类型之间可以相互转换。

Java 中共有两种类型转换：

1. 自动类型转换（Implicit Conversion）
2. 强制类型转换（Explicit Conversion）

---

# 一、自动类型转换（Automatic Type Conversion）

## 老师代码

```java
int a = 5;

long b = a;      // 自动类型转换

long d = 5;      // 自动类型转换

double e = 5;    // 自动类型转换
```

---

## 老师注释

```java
// 两种方式：自动类型转换、强制类型转换
```

---

## 什么情况下发生？

当：

**小类型 → 大类型**

Java 会自动完成转换。

转换方向：

```
byte
   ↓
short
   ↓
int
   ↓
long
   ↓
float
   ↓
double
```

例如：

```java
int age = 18;

long money = age;

double score = age;
```

无需任何操作。

---

## 老师强调

自动类型转换：

- 不会丢失数据。
- 不需要程序员手动干预。

---

# 二、强制类型转换（Cast）

## 老师代码

```java
long b = 5;

int c = (int)b;
```

老师注释：

```java
// 强制类型转换
```

---

## 语法

```java
目标类型 变量 = (目标类型)原变量;
```

例如：

```java
double d = 3.14;

int i = (int)d;
```

输出：

```
3
```

---

# 三、强制转换可能出现的问题

老师重点演示了两种情况。

---

## ① 数据溢出（Overflow）

老师代码：

```java
long f = 10000000000L;

int g = (int)f;

System.out.println(g);
```

输出：

```
1410065408
```

### 原因

int 无法保存这么大的数字。

因此：

发生了数据溢出。

---

## ② 精度丢失

老师代码：

```java
double h = 25.987;

int i = (int)h;

System.out.println(i);
```

输出：

```
25
```

原因：

int 只能保存整数。

因此：

小数部分会被直接舍弃。

不是四舍五入。

---

# 四、运算规则

老师代码：

```java
byte b1 = 5;

byte b2 = 6;

byte b3 = (byte)(b1 + b2);
```

老师注释：

```java
// 两点规则
```

---

## 规则一

只要参与运算：

```
byte
short
char
```

都会先提升为：

```
int
```

因此：

```java
b1+b2
```

结果实际上已经变成：

```
int
```

所以需要：

```java
(byte)
```

进行强制转换。

---

## 规则二

字符参与运算时：

会自动转换为 Unicode 编码。

老师代码：

```java
System.out.println(2 + '2');
```

输出：

```
52
```

因为：

```
'2'
```

对应编码：

```
50
```

所以：

```
2+50=52
```

老师继续演示：

```java
System.out.println('2'+'2');
```

输出：

```
100
```

而：

```java
System.out.println('2');
```

输出：

```
2
```

因为：

没有参与运算。

所以输出的是字符本身。

---

# 五、float 特殊情况

老师代码：

```java
float fl = (float)3.14;
```

原因：

```
3.14
```

默认属于：

```
double
```

所以：

必须：

```java
(float)
```

或者：

```java
3.14F
```

---

# 易错点

❌

```java
int a = 3.14;
```

错误。

---

❌

```java
byte b = b1 + b2;
```

错误。

---

❌

```java
int i = 10000000000L;
```

错误。

---

# 我的总结

今天主要学习了 Java 数据类型转换。

重点需要记住：

- 自动类型转换：小类型 → 大类型。
- 强制类型转换：大类型 → 小类型。
- 强制转换可能导致：
    - 数据溢出（Overflow）
    - 精度丢失
- byte、short、char 参与运算时会自动提升为 int。
- 字符参与运算时使用的是 Unicode 编码，而不是字符本身。
---
## 代码

```

/** 类型间转换的演示 */
public class DataTypeDemo {
    public static void main(String[] args) {
        //两种方式：自动类型转换、强制类型转换
        int a = 5;
        long b = a;//自动类型转换
        int c = (int) b;//强制类型转换

        long d = 5;//自动类型转换
        double e = 5;//自动类型转换
        System.out.println(e);//5.0,默认保留一位小数

        long f = 10000000000L;
        int g = (int) f;
        System.out.println(g);//1410065408，强转有可能发生溢出
        double h = 25.987;
        int i = (int) h;
        System.out.println(i);//25,强转有可能造成精度的丢失


        //两点规则
        byte b1 = 5;
        byte b2 = 6;
        byte b3 = (byte) (b1 +b2);
        System.out.println(b3);

        //byte b4 = 128;//编译错误，超出byte取值范围了
        System.out.println(2+2);//4
        System.out.println(2+'2');//52  ，'2'参与运算转为int的50
        System.out.println('2'+'2');//100 '2'参与运算转为int的50
        System.out.println('2');//2,因为没有运算，所以输出的是字符2

        float fl = (float) 3.14;//3.14默认为double类型

    }
}

```

---