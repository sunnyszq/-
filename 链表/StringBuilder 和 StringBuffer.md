#### String、StringBuilder 和 StringBuffer常见用法



当对字符串进行修改的时候，需要使用 StringBuffer 和 StringBuilder 类。

和 String 类不同的是，StringBuffer 和 StringBuilder 类的对象能够被多次的修改，并且不产生新的未使用对象。

StringBuilder 类在 Java 5 中被提出，它和 StringBuffer 之间的最大不同在于 StringBuilder 的方法不是线程安全的（不能同步访问）。

由于 StringBuilder 相较于 StringBuffer 有速度优势，所以多数情况下建议使用 StringBuilder 类。然而在应用程序要求线程安全的情况下，则必须使用 StringBuffer 类。

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

二、 StringBuffer常用方法

```java
    /***StringBuffer        是一个容器，长度可变，可以直接操作字符串，用toString方法变为字符串 **/
1.存储
        1)append(); //将指定数据加在容器末尾,返回值也是StringBuffer
        eg:
        StringBuffer sb = new StringBuffer(//可以加str);
        StringBuffer sb1=ab.append(数据） //数据可以任何基本数据类型
    注：此时sb == sb1他们是同一对象，意思是可以不用新建sb1直接 sb.append(数据) 使用时之后接使用sb
		2)insert();// 插入
   		 sb.insert(index ,数据);
3.获取
    char c = sb.charAt(index);//获取index上的字符
    int i = sb.indexOf(char)://获取char字符出现的第一次位置
    //与 String 中的获取方法一致参考前面
 
4.修改                  String类中无次操作方法
    sb =sb.replace(start,end,string)//将从start开始到end的字符串替换为string；
    sb.setCharAr(index ,char);//将index位置的字符变为新的char
 
5.反转     sb.reverse();//将sb倒序
6. getChars(int srcBegin,int srcEnd,char[] ch,int chBegin)
//将StringBuffer缓冲区中的指定数据存储到指定数组中
```

三、StringBuilder 
StringBuilder 和 StringBuffer 方法和功能完全一致只是一个是早期版本（StringBuffer)是线程安全的，由于发现利用多线程堆同一String数据操作的情况是很少的，为了提高效率idk1.5以后有StringBuilder 类。意思是多线程操作同一字符串的时候用StringBuffer 安全，现在一般用StringBuilder



参考：

https://www.cnblogs.com/dolphin0520/p/3778589.html

https://www.runoob.com/java/java-stringbuffer.html