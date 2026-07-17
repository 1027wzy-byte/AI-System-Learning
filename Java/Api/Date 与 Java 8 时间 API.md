# Date 与 Java 8 时间 API

## 一、旧版 Date

Java 早期使用 `Date` 类处理日期时间。

```java
Date date = new Date();
System.out.println(date);
```

创建指定日期：

```java
Date date = new Date(2026,6,1);
```

> **注意：**
>
> Date 的旧构造方法已经过时（Deprecated），存在年份、月份计算等问题，不推荐继续使用。

---

# 二、Java 8 时间 API

Java 8 引入了新的日期时间 API，推荐在项目开发中使用。

主要包括：

| 类 | 作用 |
|----|------|
| LocalDate | 日期（年月日） |
| LocalTime | 时间（时分秒） |
| LocalDateTime | 日期 + 时间 |
| Instant | 时间戳 |
| Duration | 计算时间间隔 |
| Period | 计算日期间隔 |
| DateTimeFormatter | 日期格式化 |

---

# 三、创建日期对象

获取当前时间：

```java
LocalDate date = LocalDate.now();
LocalTime time = LocalTime.now();
LocalDateTime dateTime = LocalDateTime.now();
```

创建指定日期：

```java
LocalDate date = LocalDate.of(2028,7,12);
```

输出：

```text
2028-07-12
```

相比旧版 Date，更加直观。

---

# 四、日期运算

Java 8 日期对象是**不可变对象（Immutable）**。

例如：

```java
LocalDate date = LocalDate.of(2028,7,12);

LocalDate newDate = date.plusDays(5);
```

结果：

```text
date      -> 2028-07-12

newDate   -> 2028-07-17
```

原对象不会发生改变。

常用方法：

```java
plusDays()

plusMonths()

plusYears()

minusDays()

minusMonths()

minusYears()
```

---

# 五、Duration（计算时间差）

适用于：

- 程序运行时间
- 接口耗时
- 秒、毫秒计算

例如：

```java
Instant start = Instant.now();

// 执行代码

Instant end = Instant.now();

Duration duration = Duration.between(start,end);

System.out.println(duration.toMillis());
```

输出：

```text
代码耗时：25ms
```

---

# 六、Period（计算日期差）

适用于：

- 年龄计算
- 相隔多少年、多少月、多少天

例如：

```java
LocalDate birthday = LocalDate.of(2000,5,20);

Period period = Period.between(birthday,LocalDate.now());
```

获取：

```java
period.getYears();

period.getMonths();

period.getDays();
```

---

# 七、DateTimeFormatter

用于：

- 日期 → 字符串
- 字符串 → 日期

创建格式：

```java
DateTimeFormatter formatter =
        DateTimeFormatter.ofPattern("yyyy-MM-dd HH:mm:ss");
```

---

## 日期转字符串

```java
String str = dateTime.format(formatter);
```

结果：

```text
2026-07-15 18:30:00
```

---

## 字符串转日期

```java
LocalDateTime dateTime =
    LocalDateTime.parse(
        "2026-12-25 08:30:00",
        formatter
    );
```

---

# 八、为什么推荐 Java 8 时间 API？

相比旧版 Date：

✅ API 更直观

✅ 不需要减 1900

✅ 月份不用减 1

✅ 不可变对象，更安全

✅ 线程安全

因此企业开发基本都使用 Java 8 时间 API。

---

# 九、本章总结

✔ 掌握 LocalDate、LocalTime、LocalDateTime

✔ 会创建和修改日期

✔ 学会 Duration 计算耗时

✔ 学会 Period 计算日期间隔

✔ 掌握 DateTimeFormatter 格式化与解析日期

✔ 理解为什么 Java 8 时间 API 替代旧版 Date

> **一句话总结：**

Java 8 时间 API 功能更完善、使用更简单、线程安全，是现代 Java 开发处理日期时间的首选方案。