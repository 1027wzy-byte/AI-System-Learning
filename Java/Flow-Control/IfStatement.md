# if 语句（If Statement）

## 作用

`if` 用于条件判断。

当条件成立时执行代码块，否则跳过。

---

## 基本语法

```java
if (条件表达式) {

}
```

---

## 老师重点

- if 只判断一次条件。
- 条件必须是 boolean 类型。
- 条件成立执行代码块，不成立直接跳过。
- if 可以单独使用，不一定需要 else。

---

## 注意事项

- 条件表达式必须返回 boolean。
- 建议始终保留 `{}`。
- if 执行结束后，程序继续向下运行。

---

## 易错点

❌

```java
if(score = 60)
```

应该写成：

```java
if(score == 60)
```

---

## 我的总结

if 适用于**单条件判断**。

当只有"满足条件才执行"这一种情况时，优先使用 if。

---

## 代码

```
/** if结构的演示 */
public class IfDemo {
public static void main(String[] args) {
//满500打八折
double price = 500;//消费金额
if(price>=500){//满500
price *= 0.8;//打八折 相当于price=(double)(price*0.8)
}
System.out.println("最终结算金额为:"+price);

        System.out.println("---------演示满299减100------------");
        //练习：定义一个总价变量名为money，演示当总价满299时，减100
        double money = 200;//消费金额
        if(money>=299){//满299
            money -= 100;
        }
        System.out.println("最终结算金额为:"+money);

        //判断成绩(score)是否合法，若合法则输出(score+为合法成绩)----0到100之间为合法成绩
        double score = 95.5;
        if (score>=0&&score<=100){//0到100之间为合法成绩
            System.out.println(score+"是合法成绩");
        }
        System.out.println("继续执行...");
    }
}
```

---