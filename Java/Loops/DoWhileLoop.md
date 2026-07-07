# do...while 循环（Do...While Loop）

## 作用

`do...while` 会**先执行一次循环体，再判断条件**。

因此循环体至少执行一次。

---

## 基本语法

```java
do{

}while(条件表达式);
```

---

## 课堂笔记

- 属于**出口循环**。
- 无论条件是否成立，都会先执行一次。

---

## 注意事项

- `while` 后必须加分号 `;`
- 与 `while` 最大区别：至少执行一次。

---

## 易错点

- 忘记最后的分号。
- 与 `while` 的执行顺序混淆。

---

## 我的总结

适用于**至少需要执行一次**的业务场景。


## 代码

```
package day04;
/** do...while的结构演示 */
public class DoWhileDemo {
    public static void main(String[] args) {

        int num = 1;
        while(num>1){//第一次就是false
            System.out.println(num);
        }
        System.out.println("继续执行...");


        System.out.println("-----do while的循环------");
        do{
            System.out.println(num);//最少会执行一次
        }while(num<1);//第一次就是false


    }
}
1
```

---