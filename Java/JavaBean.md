# JavaBean

## 什么是 JavaBean

JavaBean 是 Java 中一种标准的数据封装规范。

主要作用：

- 封装对象数据
- 隐藏成员变量
- 对外提供统一访问方式

很多 Java 框架（Spring、MyBatis、JSP 等）都依赖 JavaBean。

---

# JavaBean 规范

一个标准 JavaBean 需要满足：

## 1. 成员变量必须 private

```java
private int x;
private int y;
```

目的：

- 隐藏数据
- 防止外部直接修改成员变量

---

## 2. 提供 Getter / Setter 方法

Getter：获取数据

```java
public int getX(){
    return x;
}
```

Setter：修改数据

```java
public void setX(int x){
    this.x = x;
}
```

作用：

- 控制数据访问
- 提高封装性

---

## 3. 提供 public 无参构造方法

```java
public Point(){

}
```

很多框架创建对象时都会先调用无参构造。

---

# JavaBean 示例

```java
private int x;

public int getX(){
    return x;
}

public void setX(int x){
    this.x = x;
}
```

---

# 学习总结

今天第一次接触 JavaBean。

它本质上就是一种对象封装规范，后续开发中几乎所有实体类都会按照这种方式编写。


## 代码

```
/**
 * 标准JavaBean的规范
 * 1、成员变量私有，同时提供对应的公开的getter/setter
 * 2、包含公开的无参构造方法
 */
public class Point {//点
    private int x;
    private int y;
    //以下内容alt+insert生成
    public Point(){

    }
    public int getX(){//getter获取
        return x;
    }
    public void setX(int x){//setter设置
        this.x = x;
    }
    public int getY(){
        return y;
    }
    public void setY(int y){
        this.y = y;
    }

}
```

---