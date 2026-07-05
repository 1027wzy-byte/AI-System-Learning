# Scanner（用户输入）

---

## 什么是 Scanner

Scanner 是 Java 提供的输入工具。

作用：

**从键盘读取用户输入的数据。**

---

## 导入 Scanner

老师代码：

```java
import java.util.Scanner;
```

老师注释：

```java
//1、导入扫描仪
```

只有导入之后，程序才能使用 Scanner。

---

## 创建 Scanner 对象

老师代码：

```java
Scanner scan = new Scanner(System.in);
```

老师注释：

```java
//2、新建一个扫描仪，叫 scan
```

说明：

- `Scanner`：类名
- `scan`：对象名
- `System.in`：标准输入（键盘）

---

## 读取整数

老师代码：

```java
System.out.println("请输入年龄...");

int age = scan.nextInt();

System.out.println(age);
```

老师注释：

```java
//3、扫描一个整数并赋值给 age
```

执行过程：

```
程序等待输入

↓

输入整数

↓

按 Enter

↓

程序继续执行
```

---

## 读取小数

老师代码：

```java
System.out.println("请输入商品价格...");

double price = scan.nextDouble();

System.out.println(price);
```

说明：

`nextDouble()` 用于读取 double 类型数据。

---

## 读取字符串

老师代码：

```java
System.out.println("请输入姓名...");

String name = scan.next();

System.out.println(name);
```

说明：

`next()` 用于读取一个字符串（遇到空格结束）。

---

## Scanner 常用方法

| 方法 | 作用 |
|------|------|
| nextInt() | 读取整数 |
| nextDouble() | 读取小数 |
| next() | 读取字符串（单个单词） |
| nextLine() | 读取整行字符串（后续课程会学习） |

---

## 老师强调

使用 Scanner 的三个步骤：

1. 导入包

```java
import java.util.Scanner;
```

2. 创建对象

```java
Scanner scan = new Scanner(System.in);
```

3. 调用方法读取数据

```java
scan.nextInt();
```

---

## 易错点

❌ 忘记导入：

```java
import java.util.Scanner;
```

程序无法编译。

---

❌ 输入类型与读取方法不一致。

例如：

```java
int age = scan.nextInt();
```

如果输入：

```
18.5
```

程序会报错。

---

## 我的总结

Scanner 是 Java 中最常用的输入工具。

基本流程固定：

```
导包

↓

创建对象

↓

读取数据

↓

保存到变量
```

以后几乎所有控制台程序都会使用 Scanner 获取用户输入。


## 代码

```
import java.util.Scanner;//1、导入扫描仪
/** Scanner的演示 */
public class ScannerDemo {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);//2.新建一个扫描仪，叫scan
        System.out.println("请输入年龄...");
        int age = scan.nextInt();//3.扫描一个整数并赋值给age
        System.out.println(age);

        System.out.println("请输入商品价格...");
        double price = scan.nextDouble();//扫描一个小数赋值给price
        System.out.println(price);

        System.out.println("请输入姓名...");
        String name = scan.next();
        System.out.println(name);
    }
}
```

---