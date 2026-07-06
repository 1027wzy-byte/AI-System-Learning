# 成绩等级判断（Grade Evaluation）

## 题目

使用 `Scanner` 接收用户输入的成绩（0~100），判断成绩等级：

- A：90~100
- B：80~89
- C：60~79
- D：0~59

若输入不合法，提示用户重新输入。

---

## 涉及知识点

- Scanner
- if...else if...else
- 逻辑运算符（&&、||）
- 数据合法性判断

---

## 解题思路

1. 使用 `Scanner` 接收用户输入。
2. 先判断成绩是否合法。
3. 按照成绩区间依次判断等级。
4. 输出对应结果。

---

## 我的收获

- 学会了使用 `Scanner` 获取用户输入。
- 掌握了多条件判断的使用方法。
- 明白了进行数据合法性校验的重要性。



## 代码

```
package day03;
import java.util.Scanner;
public class IfElseIfDemo2 {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        System.out.println("请输出成绩(0-100)：");
        double score = scan.nextDouble();
        if (score < 0 || score > 100) {
            System.out.println("成绩输入错误，请重新输入...");
        } else if(score>=90){
            System.out.println("A-等级");
        }else if(score>=80){
            System.out.println("B-等级");
        }else if(score>=60){
            System.out.println("C-等级");
        }else{
            System.out.println("D-等级");
        }

```

---