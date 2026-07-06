# if...else 语句（If...Else Statement）

## 作用

`if...else` 用于处理两种互斥的情况。

当条件成立时执行 `if` 中的代码，否则执行 `else` 中的代码。

---

## 基本语法

```java
if (条件表达式) {

} else {

}
```

---

## 课堂笔记

- if 表示"满足条件时执行"。
- else 表示"条件不满足时执行"。
- 两个代码块只能执行其中一个。
- 常用于两种结果的判断，例如：是否及格、是否合法、比较大小等。

---

## 注意事项

- `else` 不需要写条件。
- `else` 必须紧跟在 `if` 后面。
- `if` 和 `else` 只能执行其中一个代码块。

---

## 易错点

### ① else 不能单独使用

❌

```java
else {

}
```

必须和 `if` 配合使用。

---

### ② 不要漏写大括号

建议始终保留 `{}`，提高代码可读性，避免逻辑错误。

---

## 我的总结

当程序只有两种结果时，优先使用 `if...else`。

例如：

- 是否满足优惠
- 是否及格
- 是否合法
- 比较两个数大小

---

## 代码

```
/** if...else结构的演示 */
public class IfElseDemo {
    public static void main(String[] args) {
        //满500打八折，不满500打9折
        double price = 300;
        if(price>=500){
            price *= 0.8;
        }else{
            price *= 0.9;
        }
        System.out.println("最终结算金额为:"+price);

        //练习：判断成绩(score)是否合法(0-100)
        //如果合法则输出(score+是合法成绩)，否则输出(score+是不合法成绩)
        double score = 90;
        if(score>=0 && score<=100){
            System.out.println(score+"是合法成绩");
        }else{
            System.out.println(score+"是不合法成绩");
        }

        //练习：定义两个整型变量a和b，判断这两个变量的大小，用if else实现
        //     如果a大，输出最大值为a的值
        //     如果b大，输出最大值为b的值
        int a = 55,b = 8;
        if(a>b){
            System.out.println("最大值为:"+a);
        }else{
            System.out.println("最大值为:"+b);
        }

    }
}
```

---