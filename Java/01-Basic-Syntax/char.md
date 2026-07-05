# char

## 特点

用于保存一个字符。

例如：

```java
char c = 'A';
```

---

## 注意

char 底层保存的是 Unicode 编码。

例如：

```java
char c = 65;
```

输出：

```
A
```

---

## 转义字符

```java
'\''

'\\'

'\n'

'\t'
```

## 代码
```
/** char类型的演示 */
public class CharDemo {
    public static void main(String[] args) {
        //5.char：字符型，2字节
        char c1 = '女';//字符女
        char c2 = 'f';//字符f
        char c3 = '6';//字符6
        char c4 = ' ';//空格符
        //char c5 = 女;//编译错误，字符直接量必须放在单引号中
        //char c6 = '10';//编译错误，只能存一个字符
        //char c7 = '';//编译错误，必须有字符
        char c8 = 65;//0到65535
        System.out.println(c8);//A c8是字符型
        char c9 = '\'';//特殊符号需要通过\来转义
        System.out.println(c9);//'
        char c10 = '\\';
        System.out.println(c10);//\
    }
}

```