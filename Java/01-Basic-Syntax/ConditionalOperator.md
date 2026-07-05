# 条件运算符（三元运算符）

---

## 什么是条件运算符

条件运算符（Conditional Operator）又称**三元运算符**。

它可以根据条件返回不同的结果，是 Java 中最简洁的条件判断方式。

---

## 老师注释

```java
//6.条件运算符：boolean ? 表达式1 : 表达式2
```

---

## 基本语法

```java
条件 ? 表达式1 : 表达式2
```

执行流程：

```
条件成立（true）

↓

执行表达式1

否则

↓

执行表达式2
```

---

## 老师代码

```java
int num = 5;

int a = num > 0 ? 1 : -1;

System.out.println(a);
```

输出：

```
1
```

分析：

```
num > 0

↓

true

↓

返回1
```

---

## 返回值必须类型一致

例如：

```java
double d1 = 99 > 9.0 ? 99 : 9.0;
```

输出：

```
99.0
```

分析：

```
99

↓

自动转换为

99.0
```

最终返回：

```
double
```

---

## 嵌套使用

老师代码：

```java
int number = 0;

String str = number > 0
        ? "是正数"
        : (number == 0 ? "是0" : "是负数");

System.out.println(number + str);
```

输出：

```
0是0
```

分析：

首先判断：

```
number > 0
```

如果不成立：

继续判断：

```
number == 0
```

最终得到：

```
是0
```

---

## 老师强调

三元运算符适用于：

- 简单条件判断
- 返回一个值

如果逻辑比较复杂，应使用：

```java
if...else
```

代码会更加清晰。

---

## 易错点

❌

```java
num > 0 ? 1;
```

错误。

三元运算符必须同时具有：

- 条件
- 真值
- 假值

正确写法：

```java
num > 0 ? 1 : -1;
```

---

## 我的总结

三元运算符可以代替简单的 if...else。

特点：

- 代码简洁
- 必须返回一个值
- 两个结果类型应保持一致或可自动转换

## 代码

```
/** 条件运算符的演示 */
public class OperDemo6 {
    public static void main(String[] args) {
        //6.条件运算符： boolean ? 表达式1 : 表达式2
        int num = 5;
        int a = num>0 ? 1 : -1;
        System.out.println(a);//1

        /*
           练习：
            创建类：OperDemo6Test
            接收用户输入的两个数字，用条件运算符判断，输出两个数字中的最大值
         */

        //面试题：
        double d1 = 99>9.0?99:9.0;
        System.out.println(99>9.0?99:9.0);//99.0

        /*
           练习：
            int number = ?
            用条件运算符判断，如果number是正数，输出number+"是正数"
                            如果number是负数，输出number+"是负数"
                            如果number是0，输出number+"是0"
         */


        int number = 0;
        String str = number>0?"是正数":(number==0?"是0":"是负数");
        System.out.println(number+str);
    }
}
```

---