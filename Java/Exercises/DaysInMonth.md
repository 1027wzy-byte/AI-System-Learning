# 判断月份天数（Days In Month）

## 题目

输入年份和月份，输出该月的天数。

要求：

- 31 天的月份直接输出。
- 30 天的月份直接输出。
- 2 月需要判断是否为闰年。
- 输入非法月份时提示错误。

---

## 涉及知识点

- Scanner
- switch...case
- if...else
- 闰年判断
- 逻辑运算符

---
。
## 解题思路

1. 使用 `Scanner` 获取年份和月份。
2. 使用 `switch` 判断月份。
3. 如果是 2 月，再使用 `if` 判断是否为闰年。
4. 输出对应天数；若月份不合法，则提示错误。

---

## 我的收获

- 学会了 `switch` 与 `if` 结合使用。
- 掌握了闰年的判断公式。
- 理解了流程控制语句在实际场景中的综合应用。


## 代码

```
package day03;
import java.util.Scanner;
public class SwitchCaseDemo2 {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        System.out.println("请输入年份:");
        int year = scan.nextInt();
        System.out.println("请输入月份:");
        int month = scan.nextInt();
        switch (month){
            case 1,3,5,7,8,10,12:
                System.out.println(year+"年"+month+"月有31天");
                break;
            case 4,6,9,11:
                System.out.println(year+"年"+month+"月有30天");
                break;
            case 2:
                if((year%4==0&&year%100!=0)||year%400==0){
                    System.out.println(year+"年"+month+"月有29天");
                }else{
                    System.out.println(year+"年"+month+"月有28天");
                }
                break;
            default:
                System.out.println("输入的月份有误，请重新输入...");
        }

    }
}
```

---