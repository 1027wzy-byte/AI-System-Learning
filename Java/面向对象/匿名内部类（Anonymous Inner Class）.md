# Day XX - 匿名内部类（Anonymous Inner Class）

---

# 一、什么是匿名内部类

匿名内部类（Anonymous Inner Class）：

> **没有名字的内部类，用来创建一个只使用一次的对象。**

它本质上：

- 创建了一个子类（或实现类）
- 立即创建对象
- 不需要单独编写新的 Java 类

因此叫：

> **匿名（没有名字）的内部类。**

---

# 二、匿名内部类的作用

老师重点：

> **如果某个派生类对象只会使用一次，就可以使用匿名内部类简化代码。**

优点：

- 不需要新建 Java 文件
- 不需要给类起名字
- 代码更加简洁

---

# 三、基本语法

## 继承类

```java
父类 引用 = new 父类(){
    // 重写方法
};
```

例如：

```java
Animal animal = new Animal(){

};
```

这里实际上：

- 创建了 Animal 的匿名子类
- 创建了该子类对象
- 用 Animal 类型引用保存对象

---

## 实现接口

```java
接口 引用 = new 接口(){

    @Override
    public void 方法(){

    }

};
```

例如：

```java
Inter inter = new Inter(){

};
```

如果接口中有抽象方法：

```java
InterInter obj = new InterInter(){

    @Override
    public void show(){
        System.out.println("show");
    }

};
```

---

# 四、匿名内部类的执行过程（老师重点）

例如：

```java
Inter obj = new Inter(){};
```

实际上发生了三件事情：

① 创建了 Inter 的一个实现类（没有名字）

↓

② 创建了该实现类对象

↓

③ 使用 Inter 类型引用保存对象

老师课堂总结：

> **new 接口(){} 本质是在创建接口实现类对象。**

同理：

```java
new 父类(){}
```

本质是在：

> **创建父类的匿名子类对象。**

---

# 五、匿名内部类的特点

- 没有类名
- 只能创建一次
- 创建后立即使用
- 常用于接口和抽象类
- 可以重写父类或接口中的方法

---

# 六、什么时候使用匿名内部类？

适用于：

- 对象只使用一次
- 不需要重复创建
- 不需要单独维护一个类

例如：

以前需要：

```
Inter
    │
    └── MyInter
             │
             └── new MyInter()
```

匿名内部类：

```
Inter obj = new Inter(){

};
```

直接完成。

---

# 七、匿名内部类与普通实现类对比

## 普通实现类

需要：

```text
Inter
   │
MyInter.java
```

然后：

```java
Inter obj = new MyInter();
```

---

## 匿名内部类

直接：

```java
Inter obj = new Inter(){

};
```

不用创建：

```
MyInter.java
```

代码更简单。

---

# 八、老师重点总结

- 匿名内部类没有类名。
- 本质是创建一个匿名的子类（或实现类）。
- 对象通常只使用一次。
- 可以重写父类或接口的方法。
- 经常用于接口和抽象类。

---

# 九、今日掌握内容

✅ 匿名内部类的概念

✅ 匿名内部类的语法

✅ 接口匿名实现

✅ 抽象类匿名继承

✅ 匿名内部类的使用场景

✅ 匿名内部类与普通实现类的区别


## 代码

```
/** 匿名内部类的演示 */
public class AnonInnerClassDemo {
    public static void main(String[] args) {
        //1)创建了Inter的一个派生类，但是没有名字
        //2)为该派生类创建了一个对象，名为o1，向上造型为Inter类型
        //  ----new Inter(){};是在创建Inter的派生类对象
        //3)大括号中的为派生类的类体
        Inter o1 = new Inter(){};

        //1)创建了Inter的一个派生类，但是没有名字
        //2)为该派生类创建了一个对象，名为o2，向上造型为Inter类型
        //    new Inter(){};是在创建Inter的派生类对象
        //3)大括号中的为派生类的类体
        Inter o2 = new Inter() {};

        //1)创建了InterInter的一个派生类，但是没有名字
        //2)为该派生类创建了一个对象，名为o3，向上造型为InterInter类型
        //    new InterInter(){};是在创建InterInter的派生类对象
        //3)大括号中的为派生类的类体
        InterInter o3 = new InterInter() {
            public void show(){
                System.out.println("showshow");
            }
        };
        o3.show();
    }
}
interface InterInter{
    void show();
}
interface Inter{

}
```
1
---