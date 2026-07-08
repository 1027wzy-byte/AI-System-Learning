# 求数组最大值（Max Of Array）

## 题目

随机生成一个长度为 10 的整数数组，求其中的最大值。

---

## 涉及知识点

- 数组
- for 循环
- if 条件判断
- Math.random()

---

## 解题思路

1. 创建数组并生成随机数。
2. 假设第一个元素为最大值。
3. 遍历剩余元素。
4. 如果当前元素更大，则更新最大值。
5. 输出最终结果。

---

## 我的收获

- 学会遍历数组。
- 掌握了"假设最大值，再逐个比较"的思想。
- 理解了数组与循环、条件判断结合使用的方法。


## 代码

```
/** 求数组元素的最大值 */
public class MaxOfArray {
    public static void main(String[] args) {
        int[] arr = new int[10];
        for(int i=0;i<arr.length;i++){//遍历arr数组
            arr[i] = (int) (Math.random()*100);//给每个元素赋值为0到99的随机数
            System.out.println(arr[i]);//输出每个元素的值
        }

        //                  0   1  2 3
        //假设：int[] arr = {12,56,89,8};
        //假设:第一个数最大 max=arr[0]
        //max=12/56/89
        int max = arr[0];//假设第一个元素为最大值
        for(int i=1;i<arr.length;i++){//遍历数组中的剩余元素
            if(arr[i]>max){//若剩余元素大于max
                max = arr[i];//将max值修改为较大的
            }
        }
        System.out.println("最大值为:"+max);
    }
}
```

---