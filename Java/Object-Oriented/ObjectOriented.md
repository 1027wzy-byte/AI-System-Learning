# 面向对象基础（Object-Oriented Programming）

## 作用

面向对象（OOP）是一种编程思想，通过"对象"描述现实世界中的事物。

对象由**属性**和**行为**组成。

---

## 类与对象

### 类（Class）

类是对象的模板。

用于描述对象共同具有的属性和行为。

### 对象（Object）

对象是类创建出来的实例。

通过 `new` 创建对象。

---

## 成员变量

成员变量用于描述对象的属性。

例如：

- 品牌
- 颜色
- 价格
- 座位数

---

## 成员方法

成员方法用于描述对象的行为。

例如：

- 启动
- 行驶
- 停止

---

## 构造方法

构造方法用于创建对象时初始化成员变量。

特点：

- 方法名与类名相同。
- 没有返回值类型。
- 创建对象时自动调用。

Java 可以提供：

- 无参构造
- 有参构造

---

## this 关键字

`this` 表示当前对象。

通常用于区分成员变量和局部变量。

例如：

```java
this.name = name;
```

---

## 继承（extends）

继承用于建立类之间的关系。

```java
class Student extends Person
```

表示：

Student 继承 Person。

---

## 课堂笔记

继承后：

子类可以直接使用父类中的：

- 成员变量
- 成员方法

子类可以新增自己的属性和方法。

例如：

Student

新增：

- className
- stuId
- study()

Teacher

新增：

- salary
- teach()

Doctor

新增：

- title
- cut()

---

## 注意事项

- Java 只支持单继承。
- 子类不能继承父类构造方法。
- 创建对象时优先执行构造方法。

---

## 易错点

### 父类不能访问子类成员

❌

```java
Person p = new Person();

p.study();
```

编译错误。

---

### 子类可以访问父类成员

✔

```java
Student stu = new Student();

stu.eat();
stu.sleep();
```

---

### 创建对象必须使用 new

```java
Car car = new Car();
```

---

## 我的总结

今天正式进入面向对象编程。

掌握了：

- 类
- 对象
- 成员变量
- 成员方法
- 构造方法
- this
- 继承

这些内容是后续学习 Java 面向对象开发的基础。

## 代码

```
package ooday01;

import java.util.Scanner;

/** 汽车类 */
public class Car {//自己创造的一种数据类型
    //成员变量------------描述对象的属性
    String brand;
    String color;
    double price;
    int capacity;
    Car(){
    }
    Car(String brand,String color,double price,int capacity){
        this.brand = brand;
        this.color = color;
        this.price = price;
        this.capacity = capacity;
    }

    //方法--------------描述对象的行为
    void start(){
        System.out.println(brand+"牌子的"+color+"色的"+capacity+"座的"+price+"块钱的车启动了...");
    }
    void run(){
        System.out.println(brand+"牌子的"+color+"色的"+capacity+"座的"+price+"块钱的车跑起来了...");
    }
    void stop(){
        System.out.println(brand+"牌子的"+color+"色的"+capacity+"座的"+price+"块钱的车停止了...");
    }
}

/** Car类的测试类 */
public class CarTest {
    public static void main(String[] args) {
        //创建一个汽车对象
        Car bm = new Car();
        //访问成员变量
        bm.brand = "宝马";
        bm.color = "白";
        bm.price = 600000;
        bm.capacity = 5;
        //调用方法
        bm.start();
        bm.run();
        bm.stop();

        //创建一个引用为ad的汽车对象，设置为 奥迪 银  500000  5  分别调用 启动 运行 暂停方法
        Car ad = new Car();
        ad.brand = "奥迪";
        ad.color = "银";
        ad.price = 500000;
        ad.capacity = 5;
        ad.start();
        ad.run();
        ad.stop();

        //1)创建一个汽车对象
        //2)给所有成员变量赋默认值
        Car bc = new Car();
        bc.start();
        bc.run();
        bc.stop();

    }
}
/** 构造方法的测试类 */
public class ConsTest {
    public static void main(String[] args) {
        Car bm = new Car();
        bm.brand = "宝马";
        bm.color = "白";
        bm.price = 600000;
        bm.capacity = 5;
        bm.start();

        Car ad = new Car("奥迪","银",500000,5);
        ad.start();

        Car bc = new Car("奔驰","黑",900000,6);
        bc.start();
    }
}
```

---