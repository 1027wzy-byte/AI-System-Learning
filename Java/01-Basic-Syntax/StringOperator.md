# 字符串连接运算符（String Concatenation）

---

## 老师注释

```java
//5.字符串连接运算符：+
```

---

## 基本使用

老师代码：

```java
int age = 18;

System.out.println("age=");
System.out.println(age);

System.out.println("age="+age);
```

输出：

```
age=
18
age=18
```

---

## 字符串拼接

老师代码：

```java
String name = "张三";

System.out.println("大家好，我叫"+name+"，今年"+age+"岁了");
```

输出：

```
大家好，我叫张三，今年18岁了
```

---

继续：

```java
String addr="北京市海淀区圣熙八号";

System.out.println("大家好，我叫"+name+"，今年"+age+"岁了，家住"+addr);
```

---

## 运算顺序（老师重点）

老师代码：

```java
System.out.println(10+20+""+30);
```

输出：

```
3030
```

分析：

```
10+20

↓

30

↓

30+""

↓

"30"

↓

"30"+30

↓

3030
```

---

老师代码：

```java
System.out.println(""+10+20+30);
```

输出：

```
102030
```

分析：

第一个就是字符串。

后面全部变成字符串连接。

---

老师代码：

```java
System.out.println(10+20+30+"");
```

输出：

```
60
```

分析：

前面都是整数。

先计算：

```
10+20+30

↓

60
```

最后：

```
60+""

↓

"60"
```

---

## 老师强调

字符串参与：

```
+
```

以后。

整个表达式都会变成字符串拼接。

---

## 易错点

不要认为：

```java
10+"20"
```

等于：

```
30
```

实际上：

```
1020
```

---

## 我的总结

字符串连接遵循：

> **从左向右计算。**

只要遇到字符串。

后面的：

```
+
```

全部变成字符串拼接。

## 代码

```
/** 字符串连接运算符 */
public class OperDemo5 {
    public static void main(String[] args) {
        //5.字符串连接运算符：+
        int age = 18;
        System.out.println("age=");//age=
        System.out.println(age);//18
        System.out.println("age="+age);//age=18
        System.out.println("我今年"+age+"岁了");//我今年18岁了

        String name = "张三";
        //输出：大家好，我叫张三，今年18岁了
        System.out.println("大家好，我叫"+name+"，今年"+age+"岁了");
        String addr = "北京市海淀区圣熙八号";
        //输出：大家好，我叫张三，今年18岁了，家住北京市海淀区圣熙八号
        System.out.println("大家好，我叫"+name+"，今年"+age+"岁了，家住"+addr);

        System.out.println(10+20+""+30);//3030------------String
        System.out.println(""+10+20+30);//102030----------String
        System.out.println(10+20+30+"");//60--------------String
    }
}
```

---