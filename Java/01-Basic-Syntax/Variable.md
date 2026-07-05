# Variable（变量）

## 定义

变量用于保存数据。

---

## 生命周期

① 声明

↓

② 初始化

↓

③ 使用

↓

④ 修改

---

## 老师代码

```java
/** 变量的演示 */
public class VarDemo {
    public static void main(String[] args) {
        //1、变量的声明：------相当于在银行开了个账户
        int a;//声明一个整型的变量，名为a
        int b,c,d;//声明三个整型的变量，名为b,c,d
        //int a;//编译错误，变量不能同名


        //2、变量的初始化：------相当于给账户存钱
        int e = 250;//声明整型变量e，并赋值为250-------开户的同时存钱
        int f;//声明整型变量f------先开户
        f = 250;//给f赋值为250 -------后存钱
        f = 360;//修改变量f的值为360
        int g=5,h=6,i=10;//声明三个整型变量，名为g，h，i，分别赋值为5,6,10


        //3、变量的访问--------使用的是账户里面的钱
        int j = 5;//声明整型变量j赋值为5
        int k = j + 10;//取出j的值5加上10在赋值给整型变量k
        System.out.println(k);//输出变量k的值15
        System.out.println("k");//输出k，双引号中原样输出
        j = j + 10;//取出j的值5加上10再赋值给j
        System.out.println(j);//15

        int balance = 5000;//账户余额
        balance = balance - 1000;//花了1000
        System.out.println(balance);//余额剩下4000

        //System.out.println(m);//编译错误，m未声明
        int m;
        //System.out.println(m);//编译错误，m未初始化

        //4、变量的命名：-------相当于给账户起名字
        int a1,a_5$,_3c,$5b;
        //int a*b;//编译错误，不能包含*等特殊字符
        //int 1a;//编译错误，不能以数字开头
        int aa = 5;
        //System.out.println(Aa);//编译错误，严格区分大小写
        //int class;//编译错误，不能使用关键字

        int 年龄 = 18;//正确，但是不建议
        System.out.println(年龄);
        int nianling = 18;//正确，但是要杜绝
        int age = 18;//建议"英文的见名知意"
        int score,myScore,myJavaScore;//建议"小驼峰命名法"----变量
        //大驼峰命名法-帕斯卡命名法
        //Score,MyScore,MyJavaScore----类的命名方式
```

---

## 命名规范

推荐：

```java
studentAge
javaScore
myScore
```

类：

```java
HelloWorld
LongDemo
```

---

## 注意

- 局部变量必须初始化。
- 变量名称采用小驼峰。