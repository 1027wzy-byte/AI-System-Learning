# 猜数字小游戏（while）

## 题目

使用 `while` 循环实现猜数字游戏。

---

## 涉及知识点

- while
- if...else
- break
- Scanner
- Math.random()

---

## 解题思路

1. 随机生成答案。
2. 不断接收用户输入。
3. 判断大小。
4. 猜中后使用 `break` 结束循环。

---

## 我的收获

- 学会使用死循环配合 `break` 控制程序结束。
- 熟悉随机数和用户输入的结合使用。


## 代码

```
package day04;
/** 猜数字小游戏 */
import java.util.Scanner;
public class GuessingWhile {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        int num = (int)(Math.random()*1000+1);//答案
        System.out.println(num);//作弊
        while(true){//自造死循环
            System.out.println("猜吧!");
            int guess = scan.nextInt();
            if(guess>num){
                System.out.println("太大了！");
            }else if(guess<num){
                System.out.println("太小了！");
            }else{
                System.out.println("猜对了！");
                break;
            }
        }



/** do...while版本的猜数字小游戏 */
import java.util.Scanner;
public class GuessingDoWhile {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        int num = (int)(Math.random()*1000+1);//答案
        System.out.println(num);//作弊
        int guess;
        do{
            System.out.println("猜吧!");
            guess = scan.nextInt();
            if(guess>num){
                System.out.println("猜大了...");
            }else if(guess<num){
                System.out.println("猜小了...");
            }
        }while(guess != num);
        System.out.println("恭喜你，猜对了");


    }
}
```

---