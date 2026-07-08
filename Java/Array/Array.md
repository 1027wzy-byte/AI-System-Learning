# 数组（Array）

## 作用

数组用于**存储多个相同数据类型的元素**。

一个数组中的所有元素类型必须一致，并且长度固定。

---

## 数组定义

### 基本语法

```java
数据类型[] 数组名 = new 数据类型[长度];
```

例如：

```java
int[] arr = new int[5];
```

---

## 数组初始化

Java 提供两种常见初始化方式：

### 动态初始化

```java
int[] arr = new int[3];
```

系统自动赋默认值：

| 数据类型 | 默认值 |
| -------- | ------ |
| byte、short、int、long | 0 |
| float、double | 0.0 |
| char | '\u0000' |
| boolean | false |
| 引用类型 | null |

---

### 静态初始化

```java
int[] arr = {2,5,8};
```

或

```java
int[] arr = new int[]{2,5,8};
```

---

## 数组访问

通过下标（索引）访问元素：

```java
arr[0]
arr[1]
```

数组下标从 **0** 开始。

最后一个元素：

```java
arr[arr.length-1]
```

数组长度：

```java
arr.length
```

---

## 数组遍历

通常使用 `for` 循环遍历数组。

```java
for(int i=0;i<arr.length;i++){

}
```

课堂中结合 `Math.random()` 为数组生成随机数。

---

## 数组复制

使用：

```java
Arrays.copyOf()
```

基本语法：

```java
Arrays.copyOf(源数组, 新长度)
```

特点：

- 长度变大，新增元素使用默认值。
- 长度变小，超出的元素被截断。
- 常用于数组扩容。

---

## 课堂笔记

- 数组长度创建后不能修改。
- 数组下标从 0 开始。
- 使用 `arr.length` 获取数组长度。
- 遍历数组推荐使用 `for` 循环。
- `Arrays.copyOf()` 可以实现数组复制和扩容。

---

## 注意事项

- 下标不能越界。
- 数组只能存放同一种数据类型。
- 动态初始化会自动赋默认值。
- 静态初始化必须在声明时完成，不能写成：

```java
int[] arr;
arr = {1,2,3}; // ❌
```

---

## 易错点

### 数组下标越界

```java
arr[3];
```

如果数组长度为 3，则最大下标只能是：

```java
arr[2]
```

否则会发生：

```
ArrayIndexOutOfBoundsException
```

---

### 静态初始化写法错误

错误：

```java
int[] arr;

arr = {1,2,3};
```

正确：

```java
arr = new int[]{1,2,3};
```

---

## 我的总结

数组适用于**存储固定数量、相同类型的数据**。

掌握数组的定义、初始化、访问、遍历和复制，是后续学习排序、查找、集合等内容的基础。


## 代码

```
/** 数组定义的演示 */
public class ArrayDemo01 {
    public static void main(String[] args) {
        //声明整型数组a，包含5个元素，每个元素都是int类型，默认值为0
        int[] a = new int[5];
        //声明浮点型数组d，包含10个元素，每个元素都是double类型，默认值为0.0
        double[] d = new double[10];
        //声明布尔型数组b，包含26个元素，每个元素都是boolean类型，默认值为false
        boolean[] b = new boolean[26];

        //数组的初始化
        int[] arr1 = new int[3];//0,0,0
        int[] arr2 = {2,5,8};//2,5,8
        int[] arr3 = new int[]{2,5,8};
        int[] arr4;
        //arr4 = {2,5,8};//编译错误，此方式只能用于声明的同时初始化
        arr4 = new int[]{2,5,8};//正确


    }
}


/** 数组访问的演示 */
public class ArrayDemo02 {
    public static void main(String[] args) {
        int[] arr = new int[3];//0,0,0
        System.out.println("数组的长度:"+arr.length);//3,长度即元素的个数
        System.out.println("数组第1个元素的值："+arr[0]);//0
        arr[0] = 100;//给第一个元素赋值为100
        arr[1] = 200;//给第二个元素赋值为200
        arr[2] = 300;//给第三个元素赋值为300
        System.out.println(arr[0]);//100
        //arr[3] = 400;//运行时异常，发生的是数组下标越界异常
        System.out.println(arr[2]);//300,输出最后一个元素的值
        System.out.println(arr[arr.length-1]);//300,输出最后一个元素的值



    }
}


p/** 数组遍历的演示 */
public class ArrayDemo03 {
    public static void main(String[] args) {

        int[] arr = new int[10];
        for(int i=0;i<arr.length;i++){//遍历arr数组
            arr[i] = (int) (Math.random()*100);//给每个元素赋值为0到99的随机数
            System.out.println(arr[i]);//输出每个元素的值
        }

        //创建MaxOfArray类，复写一遍上面代码



    }
}

/** 数组赋值的演示 */
public class ArrayDemo04 {
    public static void main(String[] args) {
        int[] a = {10,20,30,40,50};
        //a:源数组
        //b:目标数组
        //6:目标数组的长度
        //  --若目标数组长度>源数组的长度，则末尾补默认值
        //  --若目标数组长度<源数组的长度，则将末尾的截掉
        int[] b = Arrays.copyOf(a,6);
        for (int i=0;i<b.length;i++){
            System.out.println(b[i]);
        }

        System.out.println("-------------------------");
        //数组的扩容(创建了一个更大的新的数组，并将数据复制进去了)
        a = Arrays.copyOf(a,a.length+1);
        for(int i=0;i<a.length;i++){
            System.out.println(a[i]);
        }

    }
}

```

---