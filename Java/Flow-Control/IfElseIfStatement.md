# if...else if...else 语句（If...Else If Statement）

## 作用

`if...else if...else` 用于处理**多个条件**的判断。

程序会从上往下依次判断，遇到第一个满足条件的代码块后立即执行，其余条件将不再判断。

---

## 基本语法

```java
if (条件1) {

} else if (条件2) {

} else if (条件3) {

} else {

}
```

---

## 课堂笔记

- 适用于三个及以上结果的判断。
- 条件按顺序依次判断。
- 满足一个条件后，后面的条件不会再执行。
- `else` 用于处理前面所有条件都不满足的情况。
- 条件范围应从大到小（或从小到大）排列，避免逻辑错误。

---

## 注意事项

- `else if` 可以有多个。
- `else` 可以省略，但建议保留，用于处理其他情况。
- 条件之间不要出现重复或包含关系，否则可能导致后面的条件永远不会执行。

---

## 易错点

### ① 判断顺序错误

❌

```java
if(score >= 60){

}else if(score >= 90){

}
```

当成绩为 95 时，会先满足 `score >= 60`，后面的 `score >= 90` 永远不会执行。

应改为：

```java
if(score >= 90){

}else if(score >= 60){

}
```

---

### ② 忘记处理其他情况

例如输入非法数据：

```java
score = -10
```

如果没有 `else`，程序可能不会输出任何结果。

---

## 我的总结

`if...else if...else` 适用于**多条件、多结果**的判断。

例如：

- 商品折扣
- 成绩等级
- 年龄分组
- 会员等级
- 风险等级

使用时应特别注意**条件的先后顺序**。

---

## 代码

```
/** if...else if结构的演示 */
public class IfElseIfDemo {
    public static void main(String[] args) {
        //满2000打5折，满1000不满2000打7折，满500不满1000打8折，不满500打9折
        double price = 800;
        if(price>=2000){
            price *= 0.5;
        }else if(price>=1000){
            price *= 0.7;
        }else if(price>=500){
            price *= 0.8;
        }else{
            price *= 0.9;
        }
        System.out.println("最终结算金额为:"+price);
```

---