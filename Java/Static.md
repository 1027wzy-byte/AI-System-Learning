# static

## 什么是 static

static 表示"属于类"。

被 static 修饰的成员，不属于某个对象，而属于整个类。

---

# 静态变量（static 变量）

特点：

- 属于类
- 所有对象共享一份数据
- 推荐使用 类名.变量 访问

例如：

```java
StaticVar.b
```

适用场景：

多个对象共享的数据。

---

# 静态方法（static 方法）

特点：

- 属于类
- 可以直接通过类名调用
- 没有 this

例如：

```java
StaticMethod.plus(3,5);
```

注意：

静态方法不能直接访问：

- 实例变量
- 实例方法

因为没有对象。

适用场景：

方法与对象状态无关，只完成某种计算。

---

# 静态代码块（static Block）

特点：

- 类加载时执行
- 一个类只执行一次

作用：

- 初始化静态资源
- 初始化静态变量

---

# static final 常量

特点：

- 必须声明同时初始化
- 不可修改
- 推荐全部大写

例如：

```java
public static final double PI = 3.14159;
```

命名规范：

```text
MAX_SIZE
PI
COUNT
DEFAULT_PORT
```

适用场景：

程序运行过程中永远不会变化的数据。

---

# static 使用总结

| 类型 | 属于 | 是否共享 |
|------|------|----------|
| 实例变量 | 对象 | 否 |
| static变量 | 类 | 是 |
| static方法 | 类 | 是 |
| static常量 | 类 | 是 |


## 代码

```
/** 静态变量的演示 */
public class StaticVar {
    int a;//实例变量
    static int b;//静态变量
    StaticVar(){
        a++;
        b++;
    }
    void show(){
        System.out.println("a="+a+",b="+b);
    }
}
/** 静态块 */
public class StaticBlock {
    static {
        System.out.println("静态块");
    }

    StaticBlock(){
        System.out.println("构造方法");
    }
}
public class StaticMethod {
    int a;//实例变量(对象来访问)-------------------属于对象的
    static int b;//静态变量(类名来访问)-------------属于类的

    void show(){//有隐式this
        System.out.println(this.a);
        System.out.println(StaticMethod.b);
    }
    static void test(){//没有隐式this
        //静态方法中没有隐式this传递
        //没有this就意味着没有对象
        //而实例变量a必须通过对象来访问
        //所以如下语句发生编译错误
        //System.out.println(a);//编译错误，静态方法中不能直接访问实例变量
        System.out.println(StaticMethod.b);
    }

    //静态方法何时用：方法的操作与对象无关(不需要访问对象的属性/行为)
    //在say()中需要访问对象的属性a，所以认为say()的操作与对象有关，不适合设计为静态方法
    void say(){
        System.out.println(a);
    }
    //在plus()中不需要访问对象的属性/行为,所以认为plus()的操作与对象无关，可以设计为静态方法
    static int plus(int num1,int num2){
        int num = num1+num2;
        return num;
    }
/** static final常量的演示 */
public class StaticFinalDemo {
    public static void main(String[] args) {
        System.out.println(Loo.PI);//常常通过类名点来访问
        //Loo.PI = 3.1415926;//编译错误，常量不能被改变

        //1)加载Loo.class到方法区中
        //2)静态变量num一并存储到方法区中
        //3)到方法区中获取num的值并输出
        System.out.println(Loo.num);

        //编译器在编译时会将常量替换为具体的值，效率高
        //相当于System.out.println(5);
        System.out.println(Loo.COUNT);
    }
}
class Loo{
    public static final double PI = 3.14159;
    //public static final int NUM;//编译错误，变量必须声明同时初始化
    public static int num = 5;//静态变量
    public static final int COUNT = 5;//常量(静态常量)
}1
```

---