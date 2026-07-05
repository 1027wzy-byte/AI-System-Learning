# 逻辑运算符（Logical Operators）

---

## 什么是逻辑运算符

逻辑运算符用于连接多个条件。

Java 中共有三种：

| 运算符 | 含义 |
|---------|------|
| && | 与（AND） |
| \|\| | 或（OR） |
| ! | 非（NOT） |

---

## 老师注释

```java
//3.逻辑运算符：&&、||、!
```

---

# 一、&&（逻辑与）

只有：

两个条件都成立。

结果才为：

```
true
```

否则：

```
false
```

---

老师代码：

```java
boolean b1 = b>=a && b<c;
```

分析：

```
10>=5

↓

true

5<5

↓

false

↓

true && false

↓

false
```

---

老师代码：

```java
System.out.println(b!=c && a<b);
```

输出：

```
true
```

分析：

```
10!=5

↓

true

5<10

↓

true

↓

true&&true

↓

true
```

---

老师案例：

```java
int age = 18;

System.out.println(age>=18 && age<=50);
```

表示：

年龄是否在：

```
18~50
```

之间。

---

# 二、||（逻辑或）

只要：

有一个条件成立。

整个结果就是：

```
true
```

---

老师代码：

```java
System.out.println(b>=a || b<c);
```

分析：

```
true || false

↓

true
```

---

老师案例：

```java
int score = 90;

System.out.println(score<0 || score>100);
```

表示：

成绩是否合法。

如果：

```
<0

或者

>100
```

说明成绩非法。

---

# 三、!（逻辑非）

作用：

取反。

老师代码：

```java
boolean b2 = !(a<b);
```

分析：

```
a<b

↓

true

↓

!

↓

false
```

---

# 四、短路运算（重点）

老师代码：

```java
boolean b3 = a>b && c++>2;

System.out.println(c);
```

输出：

```
5
```

分析：

```
a>b

↓

false
```

由于：

```
&&
```

左边已经是 false。

所以：

右边：

```
c++
```

不会执行。

因此：

```
c

仍然等于5
```

这种现象叫：

> **短路运算（Short-circuit Evaluation）**

---

老师继续演示：

```java
boolean b4 = a<b || c++>2;

System.out.println(c);
```

输出：

```
5
```

分析：

```
a<b

↓

true
```

因为：

```
||

```

左边已经成立。

所以：

右边不会执行。

---

# 老师强调

短路规则：

对于：

```
&&
```

左边 false。

右边不执行。

---

对于：

```
||
```

左边 true。

右边不执行。

---

# 易错点

不要写：

```java
if(a>0 & b>0)
```

应该：

```java
if(a>0 && b>0)
```

开发中绝大多数情况使用：

```
&&

||

```

而不是：

```
&

|
```

---

## 代码

```
/** 逻辑运算符的演示 */
public class OperDemo3 {
    public static void main(String[] args) {
        //3.逻辑运算符：&&、||、!
        int a=5,b=10,c=5;
        boolean b1= b>=a && b<c;
        System.out.println(b1);//true&&false=false
        System.out.println(b<=c&&b>a);//false&&true=false
        System.out.println(a==b&&c>b);//false&&false=false
        System.out.println(b!=c&&a<b);//true&&true=true
        int age = 18;
        System.out.println(age>=18 && age<=50);//年龄在18到50岁之间
        System.out.println("-----------------------------------");

        System.out.println(b>=a||b<c);//true||false=true
        System.out.println(b<=c||b>a);//false||true=true
        System.out.println(b!=c||a<b);//true||true=true
        System.out.println(a==b||b<c);//false||false=false
        int score = 90;
        System.out.println(score<0||score>100);//成绩不合法(不在0到100之间)
        System.out.println("----------------------");

        boolean b2 = !(a<b);
        System.out.println(b2);//!true=false
        System.out.println(!(a>b));//!false=true
        System.out.println("-----------------------");

        // int a=5,b=10,c=5;
        boolean b3 = a>b && c++>2;
        System.out.println(b3);//false&&true=false
        System.out.println(c);//5,发生短路了

        boolean b4=a<b || c++>2;
        System.out.println(b4);//true||true=true
        System.out.println(c);//5,发生短路
    }
}
```

---