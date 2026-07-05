# 算术运算符（Arithmetic Operators）

---

## 什么是算术运算符

算术运算符用于进行数学计算。

Java 中常见的算术运算符有：

| 运算符 | 作用 |
|--------|------|
| + | 加法 |
| - | 减法 |
| * | 乘法 |
| / | 除法 |
| % | 取余（求余数） |
| ++ | 自增 |
| -- | 自减 |

---

# 一、基本运算

老师注释：

```java
//1.算术运算符：+、-、*、/、++、--、%
```

例如：

```java
System.out.println(5 + 2); //7
System.out.println(5 - 2); //3
System.out.println(5 * 2); //10
System.out.println(5 / 2); //2
System.out.println(5 % 2); //1
```

---

## 整数除法

老师之前已经演示：

```java
System.out.println(5 / 2);
```

输出：

```
2
```

原因：

两个整数相除，结果仍然是整数。

小数部分直接舍弃。

例如：

```java
System.out.println(2 / 5);
```

输出：

```
0
```

---

## 取余（%）

老师代码：

```java
System.out.println(5 % 2);
System.out.println(2 % 5);
System.out.println(8 % 2);
```

输出：

```
1
2
0
```

说明：

```
5 ÷ 2
```

商：

```
2
```

余：

```
1
```

因此：

```
5 % 2 = 1
```

当余数为 0 时：

表示能够整除。

例如：

```java
8 % 2 == 0
```

说明：

8 能被 2 整除。

---

# 二、自增运算符（++）

老师分别演示了：

```java
a++
```

和

```java
++a
```

---

## 单独使用

老师代码：

```java
int a = 5;
int b = 5;

a++;
++b;

System.out.println(a);
System.out.println(b);
```

输出：

```
6
6
```

老师强调：

单独使用时：

```
a++
```

和

```
++a
```

没有区别。

都会让变量增加 1。

---

## 参与表达式

老师代码：

```java
int c = 5;
int d = 5;

int e = c++;
int f = ++d;
```

输出：

```
c = 6
d = 6
e = 5
f = 6
```

区别：

### 后置++

```java
c++
```

先使用。

再加一。

可以理解为：

```
先赋值

↓

再+1
```

---

### 前置++

```java
++d
```

先加一。

再使用。

可以理解为：

```
先+1

↓

再赋值
```

---

## 老师重点案例

老师代码：

```java
int m = 3;

System.out.println(m++);
System.out.println(m);

System.out.println(++m);
System.out.println(m);
```

输出：

```
3
4
5
5
```

分析：

第一次：

```
m++
```

先输出：

```
3
```

然后：

```
m = 4
```

第二次：

```
++m
```

先变成：

```
5
```

然后输出：

```
5
```

---

## 综合案例

老师代码：

```java
int n = 3;

int p = n++ * 2 + ++n * 3;
```

计算过程：

```
开始：

n = 3

↓

n++ * 2

=3*2

=6

↓

n 变成4

↓

++n

先变成5

↓

5*3

=15

↓

6+15

=21
```

最终：

```
n = 5

p = 21
```

---

# 三、自减运算符（--）

老师代码：

```java
int a = 5;
int b = 5;

a--;
--b;
```

输出：

```
4
4
```

---

## 单独使用

```
a--
```

和

```
--a
```

效果相同。

变量减少 1。

---

## 参与表达式

老师代码：

```java
int c = 5;
int d = 5;

int e = c--;
int f = --d;
```

输出：

```
c = 4
d = 4
e = 5
f = 4
```

规律：

后置：

```
先使用

↓

后减一
```

前置：

```
先减一

↓

再使用
```

---

# 老师强调

记住一句话：

> **前置先变，后置后变。**

即：

```
++a

先+1
```

```
a++

后+1
```

```
--a

先-1
```

```
a--

后-1
```

---

# 易错点

❌ 认为：

```java
a++
```

和

```java
++a
```

完全一样。

实际上：

只有单独使用时一样。

参与表达式时：

结果不同。

---

❌ 写复杂表达式：

```java
a++ + ++a
```

虽然语法正确。

但是：

可读性很差。

开发中尽量避免。

---

## 代码

```


import java.sql.SQLOutput;

/** 算术运算符的演示 */
public class OperDemo1 {
    public static void main(String[] args) {
        //1.算术运算符：+、-、*、\、++、--、%

        //演示--单独用
        int a=5,b=5;
        a--;//相当于a=a-1
        --b;//相当于b=b-1
        System.out.println(a);//4
        System.out.println(b);//4
        System.out.println("----------------------");
        //演示--被使用     c--的值为c   --c的值为c-1
        int c=5,d=5;
        int e=c--;//将c--的值5赋值给e,同时c自减1变为4
        int f=--d;//将--d的值4赋值给f,同时d自减1变为4
        System.out.println(c);//4
        System.out.println(d);//4
        System.out.println(e);//5
        System.out.println(f);//4


        System.out.println("-------------------------");
        int m=3;
        System.out.println(m++);//3
        System.out.println(m);//4
        System.out.println(++m);//5
        System.out.println(m);//5

        System.out.println("--------------------");
        int n=3;
        //      3  * 2 +  5  * 3
        int p= n++ * 2 + ++n * 3;
        System.out.println(n);//5
        System.out.println(p);//21

        /*
        System.out.println(5%2);//1,商2余1
        System.out.println(2%5);//2,商0余2
        System.out.println(8%2);//0,商4余0-----整除
        System.out.println("--------------------------------");

        //演示++单独用
        int a=5,b=5;
        a++;//相当于a=a+1
        ++b;//相当于b=b+1
        System.out.println(a);//6
        System.out.println(b);//6
        System.out.println("-----------------------------------");
        //演示++被使用：a++的值是a   ++a的值为a+1
        int c=5,d=5;
        int e=c++;//将c++的值5赋值给e,同时c自增1变为6
        int f=++d;//将++d的值6赋值给f,同时d自增1变为6
        System.out.println(c);//6
        System.out.println(d);//6
        System.out.println(e);//5
        System.out.println(f);//6

         */
    }
}
```

---