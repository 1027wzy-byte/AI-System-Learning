# final

## 什么是 final

final 表示"最终、不可改变"。

可以修饰：

- 变量
- 方法
- 类

---

# final 修饰变量

变量不能再次赋值。

```java
final int a = 10;
```

特点：

- 必须初始化
- 初始化后不可修改

---

# final 修饰方法

方法不能被重写（Override）。

```java
final void show(){

}
```

---

# final 修饰类

类不能被继承。

```java
final class Demo{

}
```

---

# 使用场景

变量：

- 常量

方法：

- 不希望子类修改实现

类：

- 不允许继承

---

# 学习总结

final 用于保证数据或行为不可修改，提高程序安全性。


## 代码

```
/** final的演示 */
public class FinalDemo {
}

//演示final修饰变量
class Eoo{
    final int a = 5;
    int b = 6;
    void test(){
        //a = 55;//编译错误，final修饰的变量不能被改变
        b = 66;
        final int c = 8;
        //c = 88;//编译错误，final修饰的变量不能被改变
    }
}

//演示final修饰方法
class Foo{
    final void show(){}
    void test(){}
}

class Goo extends Foo{
    //void show(){}//编译错误，final修饰的方法不能被重写
    void test(){}
}
//演示final修饰类
final class Hoo{}
//class Ioo extends Hoo{}//编译错误，final修饰的类不能被继承
class Joo{}
final class Koo extends Joo{}//正确，不能当爸，但是能当儿子

```

---