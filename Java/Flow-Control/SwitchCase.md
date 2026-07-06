# switch...case 语句（Switch...Case Statement）

## 作用

`switch...case` 用于根据**一个变量的不同取值**执行不同的代码。

适用于**多个固定值**的判断。

---

## 基本语法

```java
switch (表达式) {
    case 值1:
        // 代码
        break;

    case 值2:
        // 代码
        break;

    default:
        // 默认代码
}
```

---

## 课堂笔记

- `switch` 根据表达式的值匹配对应的 `case`。
- 每个 `case` 后通常都要加 `break`。
- `default` 表示所有 `case` 都不匹配时执行，可省略。
- 一个 `switch` 只能判断同一个变量。

老师强调：

```java
switch 支持的数据类型：

byte
short
char
int
String
enum（枚举）
```

---

## 注意事项

- `case` 后面的值必须是常量，不能是变量。
- 每个 `case` 的值不能重复。
- `break` 用于结束当前 `switch`，避免继续执行下面的 `case`。
- `default` 建议保留，提高程序健壮性。

---

## 易错点

### ① 忘记写 break

❌

```java
case 1:
    System.out.println(111);

case 2:
    System.out.println(222);
```

程序会继续执行 `case 2`，这种现象称为**case 穿透**。

---

### ② case 值重复

❌

```java
case 1:
case 1:
```

编译错误。

---

### ③ case 后不能写变量

❌

```java
int a = 1;

case a:
```

`case` 后必须是常量。

---

## switch 与 if...else if 的区别

| switch | if...else if |
|---------|--------------|
| 判断固定值 | 判断条件表达式 |
| 代码结构清晰 | 更灵活 |
| 适合菜单、月份、星期等 | 适合范围判断、复杂条件 |

---

## 我的总结

当需要根据**一个变量的固定值**进行多个分支判断时，优先使用 `switch`。

如果涉及**大小比较、区间判断或多个条件组合**，则应使用 `if...else if...else`。

---

## 代码

```
/** switch...case结构的演示 */
public class SwitchCaseDemo {
    public static void main(String[] args) {
        int num = 3;
        switch(num){//byte，short，char，int，String，枚举
            case 1://类似if(num==1)
                System.out.println(111);
                break;
            case 2://以此为入口
                System.out.println(222);
                break;
            case 3:
                System.out.println(333);
                break;
            case 4:
                System.out.println(444);
                break;
            default://所有case都未匹配时执行
                System.out.println(666);
        }
    }
}
```

---