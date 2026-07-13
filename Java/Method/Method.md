# 方法（Method）

## 作用

方法用于**封装一段具有特定功能的代码**，实现代码复用，提高程序的可读性和维护性。

---

## 方法分类

Java 中的方法可以按照参数和返回值分为四种：

| 类型 | 参数 | 返回值 |
|------|------|--------|
| 无参无返回值 | ❌ | ❌ |
| 有参无返回值 | ✅ | ❌ |
| 无参有返回值 | ❌ | ✅ |
| 有参有返回值 | ✅ | ✅ |

---

## 基本语法

### 无参无返回值

```java
public static void 方法名(){

}
```

### 有参无返回值

```java
public static void 方法名(数据类型 参数){

}
```

### 有参有返回值

```java
public static 返回值类型 方法名(参数){

    return 返回值;
}
```

---

## 课堂笔记

### 方法参数

- 形参：方法定义时声明的参数。
- 实参：调用方法时传入的数据。
- 实参与形参类型、数量、顺序必须一致。

### return

- 返回方法执行结果。
- 可以提前结束方法执行。
- `void` 方法可以直接使用 `return;` 提前结束。

### 方法重载（Overload）

同一个类中：

- 方法名相同
- 参数列表不同（数量、类型、顺序）

即可构成方法重载。

返回值类型和参数名称不能作为重载依据。

---

## 注意事项

- 调用方法时必须传入正确参数。
- 有返回值的方法建议接收返回结果。
- 一个方法可以调用另一个方法。

---

## 易错点

### 返回值不能作为重载依据

❌

```java
int sum()
double sum()
```

---

### 参数名称不同不是重载

❌

```java
say(String name)

say(String address)
```

---

### return 后不能再写代码

```java
return;

// 后面的代码不会执行
```

---

## 我的总结

方法就是把重复代码封装起来，提高代码复用率。

开发过程中，应尽量做到"一个方法完成一个功能"。


## 代码

```
/** 方法参数的演示 */
public class MethodDemo1 {
    public static void main(String[] args) {
//        say();
//        //sayHi();//编译错误，有参必须传参
//        //sayHi(250);//编译错误，参数类型不匹配
//        sayHi("zhangsan");//String name="zhangsan"-----------实参
//        sayHi("lisi");//String name="lisi"-------------------实参
//        System.out.println("-----------------------------");
//        sayHello("wangwu",25);//---------------------------实参
//        sayHello("zhaoliu",65);//--------------------------实参

//        a();//111,333,222,444
//        System.out.println(444);

        say();//自动绑定无参say
        say("zhangsan");//自动绑定String参的say
        say("lisi",25);//自动绑定String+int参的say
        //say(3.14);//编译错误，没有double参的say


    }
    //无参无返回值
    public static void say(){
        System.out.println("大家好，我叫张三，今年18岁了");
    }
    //有参无返回值
    public static void say(String name){//--------------------形式
        System.out.println("大家好，我叫"+name+"，今年18岁了");
    }
    //有参无返回值
    public static void say(String name,int age){//-----------形参
        if(age>=60){//在某种特定条件下，提前结束方法
            return;//结束方法
        }
        System.out.println("大家好，我叫"+name+",今年"+age+"岁了");
    }

    public static void say(int age){}//正确的重载
    public static void say(int age,String name){}//正确的重载
    //public static int say(){return 1;}//编译错误，重载与返回值无关
    //public static void say(String address){}//编译错误，重载与参数名称无关


    public static void a(){
        System.out.println(111);
        b();//嵌套调用
        System.out.println(222);
    }

    public static void b(){
        System.out.println(333);
    }
}

import java.util.Random;

//方法返回值的演示
public class MethodDemo2 {
    public static void main(String[] args) {

        int a = sum(5,6);//sum(5,6)的值就是return后的那个数
        System.out.println(a);//11-----模拟对返回值的后续操作
        System.out.println(sum(7,8));
        int m=5,n=6;
        int b = sum(m,n);//传的是m和n里面的数
        System.out.println(b);//11------模拟对返回值的后续操作
        System.out.println("----------------------");

        int[] c = generateArray(5,10);//模拟第1个人的访问
        System.out.println("数组的长度为:"+c.length);//----模拟对返回值的后续操作
        for(int i=0;i<c.length;i++){//-----模拟对返回值的后续操作
            System.out.println(c[i]);
        }
        System.out.println("----------------------------");
        int[] d = generateArray(10,30);//-----模拟第2个人的访问
        System.out.println("第1个元素的值："+d[0]);
        for (int i=0;i<d.length;i++){//------模拟对返回值的后续操作
            System.out.println(d[i]);
        }

    }
    //生成一个整型数组，填充随机数据并返回
    public static int[] generateArray(int len,int max){
        Random rand = new Random();//创建随机数对象
        int[] arr = new int[len];
        for(int i=0;i<arr.length;i++){
            arr[i] = rand.nextInt(max+1);//包含max
        }
        return arr;
    }


    //有参有返回值
    public static int sum(int num1,int num2){
        int num = num1+num2;
        return num;//返回的是num里面的那个数
//        return num1+num2;//返回的是num1与num2的和
    }

}
```

---