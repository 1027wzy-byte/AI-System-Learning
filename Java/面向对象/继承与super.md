# Day XX - 继承（Inheritance）、super、方法重写

---

# 一、继承（extends）

## 什么是继承

继承是面向对象三大特性之一，用于让子类拥有父类的属性和方法，提高代码复用性。

语法：

```java
class 子类 extends 父类{
}
```

例如：

```java
class Student extends Person{
}

class Teacher extends Person{
}

class Doctor extends Person{
}
```

继承后：

- 子类可以直接使用父类的成员变量
- 子类可以直接调用父类的方法
- 子类还能扩展自己的属性和行为

---

# 二、super关键字

super 表示当前对象的父类对象。

主要有三种用途。

---

## 1、访问父类成员变量

```java
super.name;
```

作用：

访问父类中的成员变量。

老师强调：

> 如果父类和子类成员变量同名：
>
> - this 表示当前类
> - super 表示父类

如果没有重名：

```java
this.name;
```

和

```java
super.name;
```

效果一致。

---

## 2、调用父类方法

```java
super.eat();
```

作用：

调用父类的方法。

通常用于：

子类想保留父类功能，再增加自己的逻辑。

---

## 3、调用父类构造方法

```java
super();
```

或

```java
super(name, age, color);
```

作用：

调用父类构造器。

例如：

```java
Dog(String name,int age,String color){
    super(name,age,color);
}
```

---

# 三、老师重点

Java规定：

> 创建子类对象之前，必须先创建父类对象。

因此：

如果没有写

```java
super(...)
```

Java 会自动补：

```java
super();
```

也就是默认调用父类无参构造。

如果自己写了：

```java
super(name,age,color);
```

Java 就不会再自动补。

---

## 注意

super() 必须写在构造方法第一行。

例如：

```java
Dog(String name,int age,String color){
    super(name,age,color);
}
```

不能写成：

```java
Dog(...){
    System.out.println("...");
    super(...);   // 错误
}
```

---

# 四、方法重写（Override）

## 什么是重写

子类重新实现父类的方法。

要求：

- 方法名相同
- 参数列表相同

例如：

Animal：

```java
void eat(){
}
```

Dog：

```java
void eat(){
    System.out.println("狗吃骨头");
}
```

Fish：

```java
void eat(){
    System.out.println("鱼吃小虾");
}
```

Chick：

```java
void eat(){
    System.out.println("鸡吃小米");
}
```

---

## 重写特点

老师重点：

> 方法调用看对象。

例如：

```java
Animal animal = new Dog();
animal.eat();
```

最终执行：

```java
Dog.eat()
```

不是 Animal.eat()。

也就是：

**new 谁，调用谁的方法。**

---

# 五、继承带来的好处

以 Person 为例：

父类：

- name
- age
- address
- eat()
- sleep()
- sayHi()

子类：

Student：

新增：

- className
- stuId
- study()

Teacher：

新增：

- salary
- teach()

Doctor：

新增：

- title
- cut()

公共代码全部复用，只需扩展自己的功能。

---

# 六、老师强调

- extends 表示继承
- 子类自动拥有父类成员
- super 表示父类对象
- super() 必须放构造器第一行
- 方法重写发生在父子类之间
- 重写时方法名、参数必须完全一致
- **方法调用遵循："new 谁调谁"**

---

# 七、今日掌握内容

✅ extends

✅ super

✅ 构造方法调用

✅ 方法重写 Override

✅ Person 家族继承关系

✅ Animal 家族继承关系



## 代码

```
/** super关键字的演示 */
public class SuperDemo {
    public static void main(String[] args) {
        Boo o = new Boo();
    }
}
//1)在派生类的构造方法中若没有调用超类的构造方法，则默认super()调用超类的无参构造方法
class Aoo{
    Aoo(){
        System.out.println("超类的无参构造方法");
    }
}
class Boo extends Aoo{
    Boo(){
        super();//默认的，调用超类的无参构造方法
        System.out.println("派生类的无参构造方法");
    }
}
//2)在派生类的构造方法中若自己调用了超类的构造方法，则不在默认提供
class Coo{
    Coo(int a){
    }
}
class Doo extends Coo{
    Doo(){
        super(5);//调用超类的有参构造
    }

    //如下代码是默认提供的
//    Doo(){
//        super();
//    }
}
```

---