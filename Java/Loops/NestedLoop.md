# 嵌套循环（Nested Loop）

## 作用

循环中再包含循环，用于处理二维结构或重复输出。

---

## 基本语法

```java
for(...){

    for(...){

    }

}
```

---

## 课堂笔记

- 外层循环控制行。
- 内层循环控制列。
- 九九乘法表是典型应用。

---

## 注意事项

- 内层循环执行完一次，外层循环才继续。
- 内外层循环变量不要重名。

---

## 我的总结

掌握嵌套循环后，可以实现九九乘法表、矩阵输出等功能。


## 代码

```
package day04;
/** 九九乘法表 */
public class MultiTable {
    public static void main(String[] args) {
        for (int i=1;i<=9;i++){
            for(int num=1;num<=i;num++){
                System.out.print(num+"*"+i+"="+num*i+"\t");//\t的作用是用来补齐8位
            }
            System.out.println();//换行
        }
        /*
            执行过程：
             i=1
               num=1  1*1=1
               num=2  false
               换行
             i=2
               num=1  1*2=2
               num=2  2*2=4
               num=3  false
               换行
             i=3
               num=1  1*3=3
               num=2  2*3=6
               num=3  3*3=9
               num=4  false
               换行
             i=4
         */
    }
}

```

---