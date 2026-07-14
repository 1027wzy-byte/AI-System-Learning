# package、import 与访问控制修饰符

# package

## 作用

用于声明包（Package）。

主要目的：

- 避免类名冲突
- 分类管理 Java 文件

例如：

```java
package ooday04;
```

建议：

- 包名全部小写
- 多级目录使用点号分隔

---

# import

## 作用

导入其他包中的类。

```java
import java.util.Scanner;
```

特点：

- 同包类可直接使用
- 不同包需要 import 或使用完整类名

---

# 访问控制修饰符

用于控制成员的访问权限，实现封装。

| 修饰符 | 本类 | 同包 | 子类 | 其他类 |
|------|------|------|------|------|
| private | ✅ | ❌ | ❌ | ❌ |
| 默认(default) | ✅ | ✅ | ❌ | ❌ |
| protected | ✅ | ✅ | ✅ | ❌ |
| public | ✅ | ✅ | ✅ | ✅ |

权限大小：

```text
private
    ↓
default
    ↓
protected
    ↓
public
```

---

# 使用原则

一般开发中：

- 成员变量使用 private
- 对外提供 getter / setter
- 类通常使用 public

## 代码

```
/** 演示访问控制修饰符 */
public class Aoo {
    public int a;//任何类
    protected int b;//本类、子类、同包类
    int c;//本类、同包类
    private int d;//本类
    void show(){
        a = 1;
        b = 2;
        c = 3;
        d = 4;
    }
}
class Boo{//----------------------演示private
    void show(){
        Aoo o = new Aoo();
        o.a = 1;
        o.b = 2;
        o.c = 3;
        //o.d = 4;//编译错误
    }
}
```

---
