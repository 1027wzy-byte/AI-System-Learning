# int

## 特点

- 4 字节
- 32 位
- 范围：

```
-2147483648 ~ 2147483647
```

---


## 重点

### 整数除法

```java
5 / 2
```

结果：

```
2
```

---

### 溢出

超过最大值：

```
2147483647
```

继续加：

```
-2147483648
```

发生 Overflow。

## 重点
```
/** int类型的演示 */
public class IntDemo {
    public static void main(String[] args) {
        //1、int：整型，4字节，-2^31到2^31-1(正负21亿多)
        int a = 25;//25为整数直接量，默认为int类型
        //int b = 10000000000;//编译错误，100亿默认为int类型，但是超出范围了
        //int c = 3.14;//编译错误，整型变量中只能存放整数

        System.out.println(5/2);//2
        System.out.println(2/5);//0
        System.out.println(999/1000);//0
        System.out.println(5/2.0);//2.5

        int d = 2147483647;//int的最大值
        d = d + 1;
        System.out.println(d);//-2147483648 int最小值，发生溢出了，需要避免
        int e = -2147483648;
        e = e - 1;
        System.out.println(e);//2147483647 int最大值，发生溢出了，需要避免

```

---