# Day XX - Java 集合框架（Collection Framework）

> 学习日期：2026-07-17

---

# 今日目标

学习 Java Collection 集合框架，掌握：

- Collection 整体结构
- List、Set、Queue 三大体系
- ArrayList 与 LinkedList
- Queue、Deque、PriorityQueue
- HashSet 去重原理
- Iterator 迭代器
- ConcurrentModificationException
- 集合选型原则

---

# 一、为什么需要集合？

数组存在三个明显缺陷：

- 长度固定，无法自动扩容
- 插入、删除元素效率低
- 无法自动去重

Collection 提供了统一的数据容器，可以自动扩容、增删元素，并提供丰富 API。

---

# 二、Collection 家族

```
Collection
│
├── List（有序，可重复）
│     ├── ArrayList
│     └── LinkedList
│
├── Set（无序，不重复）
│     ├── HashSet
│     ├── LinkedHashSet
│     └── TreeSet
│
└── Queue（先进先出）
      ├── LinkedList
      ├── ArrayDeque
      └── PriorityQueue
```

Collection 常用方法：

```java
add()
remove()
size()
clear()
contains()
```

---

# 三、List

特点：

- 有序
- 可以重复
- 可以使用索引

---

## ArrayList

底层：

```
Object[]
```

特点：

✅ 查询快

```java
list.get(index);
```

时间复杂度：

```
O(1)
```

缺点：

中间插入删除需要移动大量元素。

自动扩容：

```
原容量 × 1.5
```

适合：

> 读多写少

---

### 常用 API

```java
add()

add(index,e)

get(index)

set(index,e)

remove(index)

contains()

clear()

size()
```

课堂代码：

```java
List<String> list=new ArrayList<>();

list.add("Apple");
list.add("Banana");
list.add("Cherry");

System.out.println(list.get(0));

list.remove(0);

list.clear();
```

---

## LinkedList

底层：

```
双向链表
```

每个节点：

```
prev ← node → next
```

特点：

查询：

```
O(n)
```

插入删除：

```
O(1)
```

适合：

> 写多读少

---

常用 API

```java
addFirst()

addLast()

pollFirst()

peekFirst()

removeFirst()

getFirst()
```

课堂代码：

```java
LinkedList<String> list=new LinkedList<>();

list.addFirst("A");

list.addLast("B");

System.out.println(list.peekFirst());

list.pollFirst();
```

---

# ArrayList VS LinkedList

|特点|ArrayList|LinkedList|
|------|------|------|
|底层|数组|双向链表|
|查询|★★★★★|★★|
|插入|★★|★★★★★|
|删除|★★|★★★★★|
|内存|较少|较大|

开发原则：

> 90% 场景直接使用 ArrayList。

---

# 四、Queue（队列）

特点：

```
FIFO
First In First Out
```

先进先出。

推荐方法：

```java
offer()

poll()

peek()
```

不要使用：

```java
add()

remove()

element()
```

因为这些方法可能直接抛异常。

---

## LinkedList 实现 Queue

```java
Deque<Integer> queue=new LinkedList<>();

queue.offer(1);

queue.offer(2);

queue.peek();

queue.poll();
```

---

## ArrayDeque

高性能双端队列。

支持：

```java
offerFirst()

offerLast()

pollFirst()

pollLast()

peekFirst()

peekLast()
```

也是官方推荐替代 Stack 的实现。

---

# 五、PriorityQueue（优先队列）

普通队列：

```
先来先服务
```

PriorityQueue：

```
按优先级出队
```

默认：

数字越小

优先级越高。

例如：

```java
PriorityQueue<Integer> queue=new PriorityQueue<>();

queue.offer(5);
queue.offer(1);
queue.offer(2);

System.out.println(queue.poll());
```

输出：

```
1
2
5
```

---

## 自定义对象排序

对象需要：

```java
implements Comparable
```

实现：

```java
compareTo()
```

例如：

```java
@Override
public int compareTo(Pilot o){
    return this.level.compareTo(o.level);
}
```

返回值：

```
<0
当前对象优先

=0
相同

>0
当前对象靠后
```

---

# 六、Set

特点：

- 不允许重复
- 无索引

实现类：

```
HashSet

LinkedHashSet

TreeSet
```

---

## HashSet

底层：

```
HashMap
```

去重流程：

```
hashCode()

↓

equals()
```

只有：

```
hashCode 相同

并且

equals 为 true
```

才认为重复。

所以：

自定义对象必须重写：

```java
hashCode()

equals()
```

否则无法正常去重。

---

## LinkedHashSet

特点：

```
去重

+

保持插入顺序
```

课堂练习：

字符串去重：

```java
MMNNAABBCCDDEEFF
```

输出：

```
MNABCDEF
```

核心代码：

```java
Set<Character> set=new LinkedHashSet<>();
```

---

# 七、Iterator

统一遍历集合。

基本写法：

```java
Iterator<String> it=list.iterator();

while(it.hasNext()){

    String str=it.next();

    System.out.println(str);

}
```

增强 for：

```java
for(String str:list){

}
```

底层其实也是 Iterator。

---

# 八、ConcurrentModificationException

错误示例：

```java
for(String s:list){

    list.remove(s);

}
```

运行：

```
ConcurrentModificationException
```

原因：

遍历时修改集合。

正确做法：

```java
Iterator<String> it=list.iterator();

while(it.hasNext()){

    String s=it.next();

    if(s.equals("Go")){

        it.remove();

    }

}
```

删除元素必须使用：

```java
iterator.remove();
```

---

# 今日重点

## Collection

- List
- Set
- Queue

---

## List

ArrayList

读快。

LinkedList

写快。

---

## Queue

推荐：

```java
offer()

poll()

peek()
```

---

## PriorityQueue

依据：

```java
Comparable
```

决定优先级。

---

## HashSet

去重依赖：

```
hashCode()

+

equals()
```

---

## Iterator

遍历删除元素：

```java
iterator.remove()
```

不要：

```java
list.remove()
```

否则会抛：

```
ConcurrentModificationException
```

---

# 今日总结

- 熟悉 Collection 整体框架。
- 掌握 List、Set、Queue 三大体系。
- 理解 ArrayList 与 LinkedList 的使用场景。
- 掌握 Queue、Deque、PriorityQueue 的基本操作。
- 理解 HashSet 去重机制（hashCode + equals）。
- 学会使用 Iterator 安全遍历集合。
- 理解 ConcurrentModificationException 的原因及解决方案。

---

# 学习收获

今天正式进入 Java 集合框架学习。

集合相比数组最大的优势是：

- 自动扩容
- 丰富 API
- 更高开发效率

后续 Spring、Spring Boot、MyBatis 等框架都会大量使用 Collection，因此这一章节属于 Java 基础中的核心内容。