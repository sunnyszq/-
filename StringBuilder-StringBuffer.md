#### String、StringBuilder 和 StringBuffer常见用法



当对字符串进行修改的时候，需要使用 StringBuffer 和 StringBuilder 类。

和 String 类不同的是，**StringBuffer 和 StringBuilder 类的对象能够被多次的修改，并且不产生新的未使用对象**。

StringBuilder 类在 Java 5 中被提出，它和 StringBuffer 之间的最大不同在于 StringBuilder 的方法不是线程安全的（不能同步访问）。

由于 **StringBuilder 相较于 StringBuffer 有速度优势**，所以多数情况下**建议使用 StringBuilder** 类。然而在应用程序要求线程安全的情况下，则必须使用 StringBuffer 类。

一、String类的常用方法

```java
1.获取：
        1）获取字符串str长度
                int i = str.length();
        2)根据位置（index)获取字符
                char  c = str.charAt(index);
        3)获取字符在字符串中的位置
                int i =str.indexOf(char ch);  //获取的是第一次出现的位置
                int i =str.indexOf(char ch ,int index);  //从位置index后获取ch出现的第一次的位置
                int  i =str.indexOf(str1) ;// 获取str1 在str 第一次出现的位置
                int i=str.indexOf(str1, index0);//获取从index位置后str第一次出现的位置
                int i = str.lastIndexOf(ch或者 str1)  //获取ch或者str1最后出现的位置
 
2.判断
        1)判断是否以指定字符串str1开头、结尾
                boolean b = str.startWith(str1)  //开头
                boolean b = str.endsWith(str1) //结尾
        2)判断是否包含某一子串
                boolean b = str.contains(str1)
        3)判断字符串是否有内容
                boolean b = str.isEmpty();
        4)忽略大小写判断字符串是否相同
                boolean b = str.equalsIgnoreCase(str1);
 
3.转换
        1)将字符数组 -char[] ch- 转化成字符串
            i.  String str =new String(ch); //将整个数组变成字符串
            ii. String str =new String(ch,offset,count)
    //将字符数组中的offset位置之后的count个元素转换成字符串  
            1. String str =String.valueOf(ch);
            2. String str =String.copyValueOf(ch,offset,count);
            3. String str =String.copyValueOf(ch);
        2)将字符串转化为字符数组
            char[] ch = str.toCharAarray();
        3)将字节数组转换为字符串
            同上1) 传入类型变为Byte[];
        4)将字符串转换为字节数组
            Byte[] b = str.toByteArray();
        5)将基本数据类型装换成字符串
            String str = String.valueOf(基本数据类型数据)；
            若是整形数据可以用 字符串连接符 + "" 
            eg :  String  str = 5+"";
            得到字符串 “5”   
 
4.替换   replace();
        str.replace(oldchar,newchar)//将str里oldchar变为newchar
        str.replace(str1,str2)//将str中str1，变为str2
 
5.切割   split();
        String[]  str1 = str.split(","); //将str用 ","分割成String数组
 
6.子串
        String s = str.substring(begin);
        // s 为 str 从begin位置到最后的字符串
        String s = str.substring(begin,end)
        //s 是 str 从begin 位置到end 位置的字符串
 
7.转换大小写：
        String s1 = str. toUpperCase(); //将str变成大写字母
        String s2 = str. toLowerCase(); //将str变成小写字母
    除去空格：
        String s =str.trim();
    比较：
        int i = str.compareTo(str1);


```

二、 StringBuffer常用方法   **（StringBuffer)是线程安全的**

```java
    /***StringBuffer        是一个容器，长度可变，可以直接操作字符串，用toString方法变为字符串 **/
1.存储
        1)append(); //将指定数据加在容器末尾,返回值也是StringBuffer
        eg:
        StringBuffer sb = new StringBuffer();//可以加(str);
        StringBuffer sb1=ab.append(数据） //数据可以任何基本数据类型
    注：此时sb == sb1他们是同一对象，意思是可以不用新建sb1直接 sb.append(数据) 使用时之后接使用sb
		2)insert();// 插入
   		 sb.insert(index ,数据);
3.获取
    char c = sb.charAt(index);//获取index上的字符
    int i = sb.indexOf(char)://获取char字符出现的第一次位置
    //与 String 中的获取方法一致参考前面
 
4.修改 String类中无次操作方法
    sb =sb.replace(start,end,string)//将从start开始到end的字符串替换为string；
    sb.setCharAr(index ,char);//将index位置的字符变为新的char
 
5.反转     sb.reverse();//将sb倒序
6. getChars(int srcBegin,int srcEnd,char[] ch,int chBegin)
//将StringBuffer缓冲区中的指定数据存储到指定数组中
```

三、StringBuilder 
**StringBuilder 和 StringBuffer 方法和功能完全一致**只是一个是早期版本（StringBuffer)是线程安全的，由于发现利用多线程堆同一String数据操作的情况是很少的，为了提高效率idk1.5以后有StringBuilder 类。意思是多线程操作同一字符串的时候用StringBuffer 安全，现在一般用StringBuilder

---

深入理解

**String类是被final修饰的**

1）String类是**final类**，也即意味着String类**不能被继承**，**并且它的成员方法都默认为final方法**。在Java中，被final修饰的类是不允许被继承的，并且该类中的成员方法都默认为final方法。在早期的JVM实现版本中，被final修饰的方法会被转为内嵌调用以提升执行效率。而从Java SE5/6开始，就渐渐摈弃这种方式了。因此在现在的Java SE版本中，不需要考虑用final去提升方法调用效率。只有在确定不想让该方法被覆盖时，才将方法设置为final。

**切记：“对String对象的任何改变都不影响到原对象，相关的任何change操作都会生成新的对象”**

1.String str="hello world"和String str=new String("hello world")的区别

```java
public class Main {
         
    public static void main(String[] args) {
        String str1 = "hello world";
        String str2 = new String("hello world");
        String str3 = "hello world";
        String str4 = new String("hello world");
         
        System.out.println(str1==str2);      //false
        System.out.println(str1==str3);		//true
        System.out.println(str2==str4);		//false
    }
}
```

通过**new关键字**来生成对象是在**堆区**进行的，而在**堆区进行对象生成的过程是不会去检测该对象是否已经存在的**。因此通过new来创建对象，**创建出的一定是不同的对象**，即使字符串的内容是相同的。

String str1 = "hello world";和String str3 = "hello world"; 都在编译期间生成了 字面常量和符号引用，**运行期间字面常量"hello world"被存储在运行时常量池**（当然只保存了一份）。通过这种方式来将String对象跟引用绑定的话，**JVM执行引擎会先在运行时常量池查找是否存在相同的字面常量**，**如果存在，则直接将引用指向已经存在的字面常量；**否则在运行时常量池开辟一个空间来存储该字面常量，并将引用指向该字面常量。

----

## 常见的关于String、StringBuffer的面试题

下面是一些常见的关于String、StringBuffer的一些面试笔试题，若有不正之处，请谅解和批评指正。

1.下面这段代码的输出结果是什么？

　　String a = "hello2"; 　　String b = "hello" + 2; 　　System.out.println((a == b));

　　输出结果为：true。原因很简单，"hello"+2在编译期间就已经被优化成"hello2"，因此在运行期间，变量a和变量b指向的是同一个对象。

2.下面这段代码的输出结果是什么？

　　String a = "hello2"; 　 String b = "hello";    String c = b + 2;    System.out.println((a == c));

　　输出结果为:false。由于有符号引用的存在，所以 String c = b + 2;不会在编译期间被优化，不会把b+2当做字面常量来处理的，因此这种方式生成的对象事实上是保存在堆上的。因此a和c指向的并不是同一个对象。javap -c得到的内容：

　　![img](https://images0.cnblogs.com/i/288799/201406/091527127176464.jpg)

3.下面这段代码的输出结果是什么？

　　String a = "hello2";  　 final String b = "hello";    String c = b + 2;    System.out.println((a == c));

　　输出结果为：true。对于被final修饰的变量，会在class文件常量池中保存一个副本，也就是说不会通过连接而进行访问，对final变量的访问在编译期间都会直接被替代为真实的值。那么String c = b + 2;在编译期间就会被优化成：String c = "hello" + 2; 下图是javap -c的内容：

　　![img](https://images0.cnblogs.com/i/288799/201406/091529124671347.jpg)

4.下面这段代码输出结果为：

```
public` `class` `Main {``  ``public` `static` `void` `main(String[] args) {``    ``String a = ``"hello2"``;``    ``final` `String b = getHello();``    ``String c = b + ``2``;``    ``System.out.println((a == c));``  ``}``  ` `  ``public` `static` `String getHello() {``    ``return` `"hello"``;``  ``}``}
```

　　输出结果为false。这里面虽然将b用final修饰了，但是由于其赋值是通过方法调用返回的，那么它的值只能在运行期间确定，因此a和c指向的不是同一个对象。

5.下面这段代码的输出结果是什么？

```
public` `class` `Main {``  ``public` `static` `void` `main(String[] args) {``    ``String a = ``"hello"``;``    ``String b = ``new` `String(``"hello"``);``    ``String c = ``new` `String(``"hello"``);``    ``String d = b.intern();``    ` `    ``System.out.println(a==b);``    ``System.out.println(b==c);``    ``System.out.println(b==d);``    ``System.out.println(a==d);``  ``}``}
```

　　输出结果为（JDK版本 JDK6)：

　　![img](https://images0.cnblogs.com/i/288799/201406/091536144056475.jpg)

　　这里面涉及到的是String.intern方法的使用。在String类中，intern方法是一个本地方法，在JAVA SE6之前，intern方法会在运行时常量池中查找是否存在内容相同的字符串，如果存在则返回指向该字符串的引用，如果不存在，则会将该字符串入池，并返回一个指向该字符串的引用。因此，a和d指向的是同一个对象。

6.String str = new String("abc")创建了多少个对象？

　　这个问题在很多书籍上都有说到比如《Java程序员面试宝典》，包括很多国内大公司笔试面试题都会遇到，大部分网上流传的以及一些面试书籍上都说是2个对象，这种说法是片面的。

　　如果有不懂得地方可以参考这篇帖子：

　　http://rednaxelafx.iteye.com/blog/774673/

　　首先必须弄清楚创建对象的含义，创建是什么时候创建的？这段代码在运行期间会创建2个对象么？毫无疑问不可能，用javap -c反编译即可得到JVM执行的字节码内容：

　　![img](https://images0.cnblogs.com/i/288799/201406/091709344832053.jpg)

　　很显然，new只调用了一次，也就是说只创建了一个对象。

　　而这道题目让人混淆的地方就是这里，这段代码在运行期间确实只创建了一个对象，即在堆上创建了"abc"对象。而为什么大家都在说是2个对象呢，这里面要澄清一个概念 该段代码执行过程和类的加载过程是有区别的。在类加载的过程中，确实在运行时常量池中创建了一个"abc"对象，而在代码执行过程中确实只创建了一个String对象。

　　因此，这个问题如果换成 String str = new String("abc")涉及到几个String对象？合理的解释是2个。

　　个人觉得在面试的时候如果遇到这个问题，可以向面试官询问清楚”是这段代码执行过程中创建了多少个对象还是涉及到多少个对象“再根据具体的来进行回答。

7.下面这段代码1）和2）的区别是什么？

```
public` `class` `Main {``  ``public` `static` `void` `main(String[] args) {``    ``String str1 = ``"I"``;``    ``//str1 += "love"+"java";    1)``    ``str1 = str1+``"love"``+``"java"``;   ``//2)``    ` `  ``}``}
```

　　1）的效率比2）的效率要高，1）中的"love"+"java"在编译期间会被优化成"lovejava"，而2）中的不会被优化。下面是两种方式的字节码：

　　1）的字节码：

　　![img](https://images0.cnblogs.com/i/288799/201406/092017165925249.jpg)

　　2）的字节码：

　　![img](https://images0.cnblogs.com/i/288799/201406/092017552494106.jpg)

　　可以看出，在1）中只进行了一次append操作，而在2）中进行了两次append操作。

---

参考：

https://www.cnblogs.com/dolphin0520/p/3778589.html

https://www.runoob.com/java/java-stringbuffer.html

