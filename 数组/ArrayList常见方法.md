ArrayList类是一个可以进行动态修改的数组，与普通的数组区别是没有固定大小的限制。

ArrayList继承了AbstractList，实现了List接口

![img](https://www.runoob.com/wp-content/uploads/2020/06/ArrayList-1-768x406-1.png)

ArrayList使用时需要导入java.util包

```java
import java.util.ArrayList; // 引入 ArrayList 类

ArrayList<E> objectName =new ArrayList<>();　 // 初始化

```

>E: 泛型数据类型，用于设置 objectName 的数据类型，只能为引用数据类型。
>objectName: 对象名。

如果我们要存储其他类型，而 <E> 只能为引用数据类型，这时我们就需要使用到基本类型的包装类。

基本类型对应的包装类表如下：

| 基本类型 | 引用类型  |
| :------- | :-------- |
| boolean  | Boolean   |
| byte     | Byte      |
| short    | Short     |
| int      | Integer   |
| long     | Long      |
| float    | Float     |
| double   | Double    |
| char     | Character |

此外，BigInteger、BigDecimal 用于高精度的运算，BigInteger 支持任意精度的整数，也是引用类型，但它们没有相对应的基本类型。

```java
ArrayList<Integer> li=new Arraylist<>();     // 存放整数元素
ArrayList<Character> li=new Arraylist<>();   // 存放字符元素
```

- ### 常见的使用方法

  添加单个元素 list.add(val);

  添加结合中的所有元素 newList.addAll(list);

  访问元素 list.get(i);

  修改元素 list.set(i,val);

  删除元素 list.remove(i);

  计算数组长度 list.size();

  迭代数组列表

  for(int i =0;i<list.size();i++){

  ​	list.get(i);

  }

  for(E i:list){

  ​	stdout(i);

  }

  对数组排序：Collections.sort(list);
  
  











https://www.runoob.com/java/java-arraylist.html