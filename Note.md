**ArrayList** 中获取数组长度的方法是 **res.size();**

获取指定下标的元素 **list.get(i);**

```java
List<Integer> res = new ArrayList<>();

...

int len = res.size();
```

**当频繁的访问元素的时候，可以将链表转换为线性表，利用线性表随机访问的特性。**

lc-143 ;234

```java
//链表转换为线性表
List<ListNode> list = new ArrayList<>();
ListNode node = head;
while(node != null){
    list.add(node);
    node = node.next;
}

//获取指定位置i的元素
list.get(i);
//转换位置
list.get(i).next = list.get(j);
```

---

获取**数组A[]的长度**的方法： **A.length;**   **数组长度没有括号！！！**

---

下面是 System.arrayCopy的源代码声明 : **实现数组之间的复制**

```java
public static void arraycopy(Object src, int srcPos, Object dest, int destPos, int length)
代码解释:
　　Object src : 原数组
   int srcPos : 从元数据的起始位置开始
　　Object dest : 目标数组
　　int destPos : 目标数组的开始起始位置
　　int length  : 要copy的数组的长度
```

