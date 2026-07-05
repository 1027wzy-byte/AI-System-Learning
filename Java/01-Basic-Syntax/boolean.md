# boolean

## 特点

只有两个值：

- true
- false

主要用于条件判断。

---

## 注意

不能写：

```java
boolean a = 1;
```

也不能写：

```java
boolean a = "true";
```

## 代码
```
/** boolean类型的演示 */
public class BooleanDemo {
    public static void main(String[] args) {
        //4.boolean:布尔型，1字节
        boolean a = true;//true为布尔型直接量
        boolean b = false;//false为布尔型直接量
        //boolean c = 250;//编译错误，布尔型变量中只能存true或者false
        System.out.println(a);//true
        System.out.println(b);//false


    }
}

```
