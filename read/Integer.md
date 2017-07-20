# Integer

## A

继承了Number类，Number类声明了intValue、longValue、floatValue、doubleValue四个抽象方法，但是byteValue、shortValue方法被声明为普通方法 <mark>为什么？</mark>

`小白理解`：通过看byteValue、shortValue两个方法的具体实现，Number类中，是先转化为int值再转化为byte或short；但是在Integer、Long、Float、Double四个包装类里重写了这两个方法，且实现都是通过把包装类的值直接强制转化为byte或short，本人试了几个数值，想看看两次转化和一次转化有什么不同，但是并没有发现结果。

## B

Integer实现了Comparable<Integer>接口，并重写了compareTo方法

Java8提供了一个无符号比较的抽象方法：compareUnsigned(int x, int y），相当于比较两个数的绝对值，底层实现是比较 **x + Integer.MIN_VALUE** 和 **y + Integer.MIN_VALUE**

`注：Integer.MIN_VALUE - 1 = Integer.MAX_VALUE`

## C

Integer使用两个类变量`MIN_VALUE` 和 `MAX_VALUE` 来分别表示int类型可以保存的最小值和最大值
使用 `TYPE` 类变量表示 int基本类型代表的类对象 `Class<Integer>`

使用char数组 `digits`来存储表示一个整型数据所有可能使用到的字符 

## D












