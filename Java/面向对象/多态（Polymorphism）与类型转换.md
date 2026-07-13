# Day XX - 多态（Polymorphism）与类型转换

---

# 一、多态（Polymorphism）

## 什么是多态

多态（Polymorphism）指：

> **同一个父类引用，可以指向不同的子类对象。**

例如：

```java
Animal animal = new Dog();
Animal animal = new Fish();
Animal animal = new Chick();
```

这里：

- 引用类型：Animal
- 实际对象：Dog、Fish、Chick

这就是多态。

---

# 二、向上转型（Upcasting）

## 什么是向上转型

向上转型就是：

> **父类引用指向子类对象。**

例如：

```java
Animal animal = new Dog();
```

或者：

```java
Swim swim = new Dog();
```

Java 会自动完成转换，因此也称：

- 自动类型转换
- 向上造型

---

## 向上转型特点（老师重点）

能够访问什么成员：

**由引用类型决定。**

例如：

```java
Animal animal = new Dog();
```

可以访问：

```java
animal.eat();
animal.drink();
animal.name;
```

不能访问：

```java
animal.lookHome();
animal.swim();
```

因为：

这些方法不是 Animal 中定义的。

老师强调：

> **能点出来什么，看引用的类型。**

这是 Java 的规定。

---

# 三、多态的动态绑定

虽然：

```java
Animal animal = new Dog();
```

引用类型是 Animal。

但是：

```java
animal.eat();
```

真正执行的是：

Dog 中重写后的 eat()。

老师重点：

> **重写方法调用时，看对象的实际类型（new 谁就调用谁）。**

例如：

```java
Animal animal = new Dog();
animal.eat();
```

执行：

```
Dog.eat()
```

而不是：

```
Animal.eat()
```

---

# 四、向下转型（Downcasting）

## 什么是向下转型

当父类引用需要调用子类特有的方法时，需要进行强制类型转换。

例如：

```java
Animal animal = new Dog();

Dog dog = (Dog) animal;
dog.lookHome();
```

这就是向下转型。

---

# 五、向下转型成功的条件（老师重点）

只有以下两种情况可以成功：

### ① 引用所指向的对象就是该类型

例如：

```java
Animal animal = new Dog();

Dog dog = (Dog) animal;
```

成功。

---

### ② 引用对象实现了该接口

例如：

```java
Animal animal = new Dog();

Swim swim = (Swim) animal;
```

因为：

Dog 实现了 Swim 接口。

所以转换成功。

---

# 六、转换失败

如果对象本身不是该类型：

例如：

```java
Animal animal = new Dog();

Fish fish = (Fish) animal;
```

运行时会出现：

```text
ClassCastException
```

即：

**类型转换异常。**

---

# 七、instanceof

为了避免强制转换异常：

老师建议：

先使用：

```java
instanceof
```

判断对象类型。

例如：

```java
if(animal instanceof Dog){
    Dog dog = (Dog) animal;
}
```

只有返回：

```java
true
```

时：

才可以安全转换。

---

## instanceof 返回值

返回：

```java
boolean
```

即：

- true
- false

例如：

```java
animal instanceof Dog
```

表示：

animal 是否引用的是 Dog 对象。

---

## 老师重点

> **instanceof 为 true 的条件，就是强转成功的条件。**

因此：

建议：

> **强转之前先判断 instanceof。**

---

# 八、多态的实际应用

## ① 统一管理不同对象

例如：

动物数组：

```java
Animal[] animals;
```

里面可以存放：

- Dog
- Fish
- Chick

遍历时：

统一调用：

```java
eat();
drink();
```

实现：

> **代码复用。**

---

## ② 扩大方法适用范围

例如：

```java
feed(Animal animal)
```

参数类型使用：

Animal。

那么：

Dog、Fish、Chick

都可以传入。

实现：

> **代码复用。**

---

# 九、什么时候需要向下转型？

如果：

父类中没有的方法，

而子类有。

例如：

```java
lookHome();
```

或者：

```java
layEggs();
```

就需要：

```java
(Dog)
```

或

```java
(Chick)
```

进行强制转换。

---

# 十、多态总结

## 优点

- 提高代码复用性
- 扩大方法适用范围
- 统一管理不同对象
- 降低代码耦合

---

## 使用流程

① 向上转型

```java
Animal animal = new Dog();
```

↓

② 调用公共方法

```java
animal.eat();
animal.drink();
```

↓

③ 需要子类功能时

先判断：

```java
instanceof
```

↓

④ 向下转型

```java
Dog dog = (Dog) animal;
dog.lookHome();
```

---

# 十一、老师重点总结

- 多态：父类引用指向子类对象。
- 向上转型是自动完成的。
- **能访问什么成员，看引用类型。**
- **调用重写方法，看对象类型（new 谁调谁）。**
- 向下转型需要强制转换。
- 强转失败会发生 **ClassCastException**。
- 建议强转前使用 **instanceof** 判断。
- instanceof 返回 true，就是可以安全强转。
- 多态可以统一管理对象，实现代码复用。

---

# 十二、今日掌握内容

✅ 多态（Polymorphism）

✅ 向上转型（Upcasting）

✅ 向下转型（Downcasting）

✅ instanceof

✅ ClassCastException

✅ 多态在数组中的应用

✅ 多态在方法参数中的应用


## 代码

```
/** 多态的演示 */
public class PolymorphicDemo {
    public static void main(String[] args) {

//        //演示向上造型的语法：
//        Dog o1 = new Dog("小黑",2,"黑");//狗是狗
//        //o1.name/age/color/eat()/lookHome()/swim()/drink()
//        Animal o2 = new Dog("小黑",2,"黑");//狗是动物-----向上造型
//        //o2.name/age/color/eat()/drink()
//        Swim o3 = new Dog("小黑",2,"黑");//狗会游泳------向上造型
//        //o3.swim();
1
        //演示向上造型(多态)的第1点应用
        Master master = new Master();
        Dog dog = new Dog("小黑",2,"黑");
        Chick chick = new Chick("小花",3,"花");
        Fish fish = new Fish("小金",1,"金");
        master.feed(dog);//在传参的同时，系统自动做了向上造型  Animal animal = dog;
        master.feed(chick);
        master.feed(fish);

        System.out.println("----------------------------------------");
        //演示向上造型(多态)第2点应用
        //Animal o = new Animal() ;//编译错误，抽象类不能被实例化
        Animal[] animals = new Animal[5];
        animals[0] = new Dog("小黑",2,"黑");//向上造型
        animals[1] = new Dog("小白",1,"白");
        animals[2] = new Fish("小金",1,"金");
        animals[3] = new Fish("大金",2,"金");
        animals[4] = new Chick("小灰",3,"灰");
        for(int i=0;i<animals.length;i++){//遍历所有动物
            System.out.println(animals[i].name);//输出每个动物的名字
            animals[i].eat();//每个动物吃饭
            animals[i].drink();//每个动物喝水
            //调用lookHome()\layEggs()\swim()
            if(animals[i] instanceof Dog){
                Dog dog1 = (Dog) animals[i];
                dog1.lookHome();
            }
            if(animals[i] instanceof Chick){
                Chick chick1 = (Chick) animals[i];
                chick1.layEggs();
            }
            if(animals[i] instanceof Swim){//适用于所有实现Swim接口的(会游泳的)
                Swim swims = (Swim) animals[i];
                swims.swim();
            }
        }


        //演示强转成功的条件:
        Animal o = new Dog("小黑",2,"黑");//向上造型
        Dog g = (Dog) o;//引用o指向的对象，就是Dog类型
        Swim s = (Swim) o;//引用o所指向而定对象，实现了Swim接口
        //Fish f = (Fish) o;//运行时会发生ClassCastException类型转换异常

        System.out.println(o instanceof Dog);//true
        System.out.println(o instanceof Swim);//true
        System.out.println(o instanceof Fish);//false
        if (o instanceof Fish){//false
            Fish f = (Fish) o;
        }
    }
}



/** 引用类型数组的演示 */
public class RefArrayDemo {
    public static void main(String[] args) {

//        //声明Dog型数组dogs，包含3个元素，每个元素都是Dog型，默认值为null
//        Dog[] dogs = new Dog[3];
//        //声明Chick型数组chicks，包含3个元素，每个元素都是Chick型，默认值为null
//        Chick[] chicks = new Chick[3];
//        //声明Fish型数组fishs，包含2个元素，每个元素都是Fish型，默认值为null
//        Fish[] fishs = new Fish[2];


        Dog[] dogs = new Dog[3];
        dogs[0] = new Dog("小黑",2,"黑");
        dogs[1] = new Dog("小白",1,"白");
        dogs[2] = new Dog("小灰",3,"灰");
        System.out.println(dogs[0].name);//输出第1只狗的名字
        dogs[1].age = 4;//修改第2只狗的年龄为4岁
        dogs[2].swim();//第3只狗在游泳
        System.out.println("------------------------");
        for (int i=0;i<dogs.length;i++){//遍历dogs数组
            System.out.println(dogs[i].name);//输出每只狗的名字
            dogs[i].eat();//每只狗吃饭
        }
        //创建包含2个元素的小鸡数组，
        //                 第一个小鸡为 小花 1 花
        //                 第二个小鸡为 大花 2 花
        //输出每个小鸡的名字，让每个小鸡下蛋
        Chick[] chicks = new Chick[2];
        chicks[0] = new Chick("小花",1,"花");
        chicks[1] = new Chick("大花",2,"花");
        for (int i=0;i<chicks.length;i++){//遍历chicks数组
            System.out.println(chicks[i].name);
            chicks[i].layEggs();
        }

        //创建包含4个元素的小鱼数组，
        //          第一个小鱼为 小金 1  金
        //          第二个小鱼为 大金 4  白
        //          第三个小鱼为 小绿 1  绿
        //          第四个小鱼为 小红 3  红
        //输出每个小鱼的颜色，让每条鱼游泳
        Fish[] fishs = new Fish[4];
        fishs[0] = new Fish("小金",1,"金");
        fishs[1] = new Fish("大金",4,"白");
        fishs[2] = new Fish("小绿",1,"绿");
        fishs[3] = new Fish("小红",3,"红");
        for (int i=0;i<fishs.length;i++){//遍历fishs数组
            System.out.println(fishs[i].color);
            fishs[i].swim();
        }
    }
}
```

---