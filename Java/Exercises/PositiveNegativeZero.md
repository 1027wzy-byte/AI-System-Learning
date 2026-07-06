# 判断正数、负数和零（Positive / Negative / Zero）

## 题目

判断一个整数是：

- 正数
- 负数
- 0

并输出对应结果。

---

## 涉及知识点

- if...else if...else
- 数值比较

---

## 解题思路

1. 判断是否大于 0。
2. 判断是否小于 0。
3. 否则说明等于 0。

---

## 我的收获

- 熟悉了多分支判断的执行顺序。
- 理解了 `else` 用于处理剩余情况。

## 代码

```
package day03;

public class IfElseIfDemo3 {
    public static void main(String[] args) {
        int num = 0;
        if(num>0){
            System.out.println(num+"是正数");
        }else if(num<0){
            System.out.println(num+"是负数");
        }else{
            System.out.println(num+"是0");
        }
    }
}

```

---