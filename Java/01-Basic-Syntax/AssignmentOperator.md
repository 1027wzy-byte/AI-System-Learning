# 赋值运算符（Assignment Operators）

---

## 什么是赋值运算符

赋值运算符用于**给变量赋值**。

最基本的是：

```java
=
```

除此之外，还有复合赋值运算符。

---

## 老师注释

```java
//4.赋值运算符：=、+=、-=、*=、/=、%=
```

---

## 运算符一览

| 运算符 | 含义 |
|---------|------|
| = | 赋值 |
| += | 加后赋值 |
| -= | 减后赋值 |
| *= | 乘后赋值 |
| /= | 除后赋值 |
| %= | 取余后赋值 |

---

## 老师代码

```java
int a = 5;

a += 10;
System.out.println(a);

a *= 2;
System.out.println(a);

a /= 6;
System.out.println(a);

a %= 2;
System.out.println(a);

a -= 1;
System.out.println(a);
```

输出：

```
15
30
5
1
0
```

---

## 等价关系

老师强调：

```java
a += 10;
```

等价于：

```java
a = (int)(a + 10);
```

同理：

```java
a -= 5;
```

等价于：

```java
a = (int)(a - 5);
```

其它几个运算符也是一样。

---

## 面试题（老师重点）

老师代码：

```java
short s = 5;

// s = s + 10;   // 编译错误

s += 10;

System.out.println(s);
```

输出：

```
15
```

---

### 为什么？

因为：

```java
s + 10
```

结果已经提升为了：

```
int
```

所以：

```java
s = s + 10;
```

需要：

```java
s = (short)(s + 10);
```

而：

```java
s += 10;
```

Java 会自动完成强制转换。

---

## byte 同样如此

老师代码：

```java
byte b = 5;

// b = b + 10;    // 编译错误

b += 10;
```

原因完全相同。

---

## 老师强调

复合赋值运算符：

Java 会自动进行类型转换。

因此：

```java
+=
-=

*=

/=
%=
```

比普通赋值更方便。

---

## 易错点

❌

```java
short s = 5;

s = s + 1;
```

编译失败。

---

✅

```java
s += 1;
```

或者：

```java
s = (short)(s + 1);
```

---

## 我的总结

赋值运算符最大的特点：

> **复合赋值运算符会自动进行一次隐式强制类型转换。**

这是 Java 面试中经常考察的知识点。
## 代码

```
/** 赋值运算符的演示 */
public class OperDemo4 {
    public static void main(String[] args) {
        //4.赋值运算符：=、+=、-=、*=、/=、%=
        int a = 5;
        a += 10;//相当于a=(int)(a+10)
        System.out.println(a);//15
        a *= 2;//相当于a=(int)(a*2)
        System.out.println(a);//30
        a /= 6;//相当于a=(int)(a/6)
        System.out.println(a);//5
        a %= 2;//相当于a=(int)(a%2)
        System.out.println(a);//1
        a -= 1;//相当于a=(int)(a-1)
        System.out.println(a);//0

        //面试题
        short s = 5;
        //s = s + 10;//编译错误，需要强转，改为：s=(short)(s+10)
        s += 10;//相当于s=(short)(s+10)
        System.out.println(s);//15

        byte b = 5;
        //b = b + 10;//编译错误，需要强转
        b += 10;
    }
}

```

---