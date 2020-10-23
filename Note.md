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

