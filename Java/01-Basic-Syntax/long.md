# long

## 特点

- 8 字节
- 64 位

---

## 注意

long 直接量必须加：

```java
L
```

例如：

```java
10000000000L
```

否则默认属于 int。

---

## 易错点

```java
1000000000 * 3 * 10L
```

可能已经发生 int 溢出。

推荐：

```java
1000000000L * 3 * 10
```

## 代码
```
/** long类型的演示 */
public class LongDemo {
    public static void main(String[] args) {
        //2.long：长整型，8个字节，-2^63到2^63-1(正负900万万亿多)
        long a = 25L;//25L为长整型直接量
        //long b = 10000000000;//编译错误，100亿默认为int类型，但是超出int取值范围了
        long c = 10000000000L;
        //long d = 3.14;//编译错误，长整型直接量中只能装整数

        long e = 1000000000*2*10L;
        System.out.println(e);//200亿L
        long f = 1000000000*3*10L;
        System.out.println(f);//不是300亿
        long g = 1000000000L*3*10;
        System.out.println(g);//300亿L

```

---