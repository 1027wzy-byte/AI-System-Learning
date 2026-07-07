# break 与 continue

## break

### 作用

立即结束当前循环。

---

### 基本语法

```java
break;
```

---

### 课堂笔记

- 可用于 `for`
- 可用于 `while`
- 可用于 `do...while`
- 也可用于 `switch`

---

## continue

### 作用

跳过本次循环剩余代码，直接进入下一次循环。

---

### 基本语法

```java
continue;
```

---

## 注意事项

- `break`：结束整个循环。
- `continue`：结束本次循环。

---

## 我的总结

- `break` = 提前结束
- `continue` = 跳过一次

## 代码

```
package day04;
/** break关键字的演示 */
public class BreakDemo {
    public static void main(String[] args) {

        for(int num=1;num<=9;num++){
            if(num == 4){
                break;
            }
            System.out.println(num+"*9="+num*9);
        }
        System.out.println("循环结束...");
        /*
            执行过程：
            num=1    1*9=9
            num=2    2*9=18
            num=3    3*9=27
            num=4    if条件为true，执行break
            输出"循环结束..."
         */
    }
}

/** continue关键字的演示 */
public class ContinueDemo {
    public static void main(String[] args) {
        //输出9的乘法表，跳过能被3整除的
        for(int num=1;num<=9;num++){
            if(num%3==0){
                continue;//跳过循环体中剩余语句而进入下一次循环
            }
            System.out.println(num+"*9="+num*9);
        }
        System.out.println("循环结束...");

        System.out.println("---------输出9的乘法表，只要不能被3整除的---------");
        //输出9的乘法表，只要不能被3整除的
        for(int num=1;num<=9;num++){
            if(num%3!=0){
                System.out.println(num+"*9="+num*9);
            }
        }

        /*
            执行过程：
            num=1   1*9=9
            num=2   2*9=18
            num=3
            num=4   4*9=36
            num=5   5*9=45
            num=6
            num=7   7*9=63
            num=8   8*9=72
            num=9
            num=10  for循环结束，输出"循环结束"
         */
    }
}

```

---