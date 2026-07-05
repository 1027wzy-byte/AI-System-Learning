# double

## 特点

Java 默认的小数类型。

例如：

```java
3.14
```

---

## 注意

float 必须写：

```java
3.14F
```

---

## 易错点

存在精度误差。

例如：

```java
3.0 - 2.9
```

结果：

```
0.10000000000000009
```

开发中不要直接比较两个浮点数是否相等。

## 代码
```
/** double类型的演示 */
public class DoubleDemo {
    public static void main(String[] args) {
        //3.double:双精度浮点型，8字节
        double a = 3.14;//3.14为小数直接量，默认为double类型
        float b = 3.14F;//3.14F为float类型直接量

        double c=3.0,d=2.9;
        System.out.println(c-d);//0.10000000000000009 ,发生舍入误差
        double e=6.0,f=4.9;
        System.out.println(e-f);//1.0999999999999996 ,发生舍入误差
        double g=6.0,h=1.9;
        System.out.println(g-h);//4.1，没有发生舍入误差


    }
}
```

---