# while 循环（While Loop）

## 作用

`while` 用于**先判断条件，再执行循环体**。

只要条件为 `true`，循环就会一直执行。

---

## 基本语法

```java
while (条件表达式) {

}
```

---

## 课堂笔记

- while 属于**入口循环**。
- 循环包含三个要素：
    - 循环变量初始化
    - 循环条件
    - 循环变量变化
- 条件第一次就是 `false` 时，循环一次都不会执行。

---

## 注意事项

- 必须修改循环变量，否则容易形成死循环。
- 循环条件最终必须变为 `false`。

---

## 易错点

- 忘记更新循环变量。
- 条件始终成立导致死循环。

---

## 我的总结

适用于**循环次数未知**或**依赖条件结束**的场景。

## 代码

```
/** while结构的演示 */
public class WhileDemo {
    public static void main(String[] args) {
        //输出5次"行动是成功的阶梯"
        int times = 0;//1)循环变量的初始化
        while (times < 5){//2)循环条件
            System.out.println("行动是成功的阶梯");
            times++;//3)循环变量的改变
        }
        System.out.println("继续执行...");
        /*
            执行过程：-------------------------带数
                                    times=0
                   true   输出       times=1
                   true   输出       times=2
                   true   输出       times=3
                   true   输出       times=4
                   true   输出       times=5
                   false   while循环结束
                   输出"继续执行..."
         */
```

---