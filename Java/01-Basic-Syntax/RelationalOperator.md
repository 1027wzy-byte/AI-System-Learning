# 关系运算符（Relational Operators）

---

## 什么是关系运算符

关系运算符用于比较两个数据之间的关系。

比较结果只有两种：

```java
true
false
```

---

## 老师注释

```java
//2.关系运算符：>、<、>=、<=、==、!=
```

---

## 运算符一览

| 运算符 | 含义 |
|---------|------|
| > | 大于 |
| < | 小于 |
| >= | 大于等于 |
| <= | 小于等于 |
| == | 等于 |
| != | 不等于 |

---

## 老师代码

```java
int a = 5;
int b = 10;
int c = 5;

boolean b1 = a > b;
System.out.println(b1);

System.out.println(c < b);
System.out.println(a >= c);
System.out.println(a <= b);
System.out.println(a == c);
System.out.println(a != c);
```

输出：

```
false
true
true
true
true
false
```

---

## 表达式比较

老师代码：

```java
System.out.println(a % 2 == 0);
```

输出：

```
false
```

分析：

```
5 % 2

↓

1

↓

1 == 0

↓

false
```

判断：

是否为偶数。

---

老师代码：

```java
System.out.println(a + c > b);
```

输出：

```
false
```

分析：

```
5 + 5

↓

10

↓

10 > 10

↓

false
```

---

## 与 ++ 结合使用

老师代码：

```java
System.out.println(a++ > 5);
System.out.println(a++ > 5);

System.out.println(a);
```

输出：

```
false
true
7
```

分析：

第一次：

```
a = 5

↓

5 > 5

↓

false

↓

a 变成6
```

第二次：

```
a = 6

↓

6 > 5

↓

true

↓

a 变成7
```

---

## 老师强调

关系运算符的结果一定是：

```java
boolean
```

只能是：

```java
true
```

或

```java
false
```

不能得到整数。

---

## 易错点

❌

```java
if(a = b)
```

这是赋值。

不是比较。

正确：

```java
if(a == b)
```

---

## 代码

```
/** 关系运算的演示 */
public class OperDemo2 {
    public static void main(String[] args) {
        //2.关系运算符：>、<、>=、<=、==、!=
        int a=5,b=10,c=5;
        boolean b1 = a>b;
        System.out.println(b1);//false
        System.out.println(c<b);//true
        System.out.println(a>=c);//true
        System.out.println(a<=b);//true
        System.out.println(a==c);//true
        System.out.println(a!=c);//false
        System.out.println(a%2==0);//false
        System.out.println(a+c>b);//false
        System.out.println("------------------------------------");
        System.out.println(a++>5);//false-------a自增1变为6
        System.out.println(a++>5);//true--------a自增1变为7
        System.out.println(a);//7


    }
}
```

---