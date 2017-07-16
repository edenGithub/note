# 集合

## 使用Lambda表达式遍历集合

```
public static void main(String[] args) {
    List<Integer> list = new ArrayList<>();
    list.add(1);
    list.add(2);
    list.add(3);
    list.add(4);
    list.forEach(ele -> System.out.println("当前元素：" + ele));
}
```

## Iterator遍历集合元素

* 传统遍历
* Lambda表达式遍历

```
Iterator<Integer> it = list.iterator();
it.forEachRemaining(ele -> System.out.println("当前元素：" + ele));
```

## 使用Java8新增的Predicate操作集合

```
使用Predicate过滤集合
List<String> list = new ArrayList<>();
    list.add("轻量级JavaEE 企业应用实战");
    list.add("疯狂Java讲义");
    list.add("疯狂IOS讲义");
    list.add("疯狂Ajax讲义");
    list.removeIf(ele -> ele.length() > 10);
```

## Stream操作集合

* Collection提供了一个stram()方法来获取流

```
步骤：
	1.使用Stream或者XXXStream的builder()类方法创建Buildr
	2.重复调用Builder的add()方法向该流添加多个元素
	3.调用builder的build()方法获取对应的Stream
	4.调用Stream的聚集方法
```

```
实例：
IntStream is = IntStream.builder()
                .add(20)
                .add(13)
                .add(-2)
                .add(18)
                .build();
//        以下调用聚集方法的代码每次只能执行一行
//        System.out.println("最大元素 " + is.max().getAsInt());
//        System.out.println("元素总和 " + is.count());
    System.out.println(is.allMatch(ele -> ele * ele > 20));
    System.out.println(is.anyMatch(ele -> ele * ele > 20));
    IntStream newIs = is.map(ele -> ele * 20 + 2);
    newIs.forEach(System.out::println);
}
```

## <a name="Set"></a>Set

* HashSet类

```
特点：
1.无序
2.不是同步的，如果多个线程同时访问一个HashSet，必须通过代码来保证其同步
3.集合元素值可以是null
```

* LinkedHashSet类 

```
LinkedHashSet使用链表记录集合元素的添加顺序，但是LinkedHashSet依然是HashSet，不允许集合元素重复
```

* TreeSet类

`注：元素必须实现Comparable接口`

1.自然排序

2.定制排序

`TreeSet set = new TreeSet((o1, o2) -> o1 -o2)`

* EnumSet类

`注：EnumSet类元素是有序的，以枚举值的定义顺序来决定集合的顺序，且不允许添加null元素`

总结：各类Set的性能分析

1.HashSet的性能总是比TreeSet好，因为TreeSet需要额外的红黑树算法来维护集合的次序

2.LinkedHashSet对于插入删除操作，要略慢于HashSet，这是由于维护链表造成的开销，但是遍历会快

3.EnumSet是性能最好的，但是它只能保存一个枚举类里的枚举值

4.以上介绍的Set都是线程不安全的


## List

# ArrayList和Vector类

```
ArrayList和Vector的显著区别：
1.ArrayList是线程不安全的，Vector是线程安全的
2.Vector提供了一个Stack子类，它用于模拟“栈”数据结构
3.Vector是比较古老的类，性能比较差，不推荐使用，推荐使用ArrayDeque
```

* 固定长度的List

```
List<String> fixedList = Arrays.asList("a", "b", "c");
//    将输出Arrays$ArrayList
System.out.println(fixedList.getClass());
fixedList.forEach(System.out::println);
//    此List不可增、删，只能遍历访问元素，故以下代码会产生异常
//    fixedList.add("d");
//    fixedList.remove("e");
```

## Queue集合

Queue用于模拟队列这种数据结构，队列通常是指“先进先出”的容器。

* PriorityQueue实现类

```
PriorityQueue是一个比较标准的队列实现，而绝不是标准的队列实现，因为PriorityQueue保存元素的顺序并不是按照加入队列的顺序，而是按照元素的大小重新排序
```

排序规则参考TreeSet [goto **Set**](#Set)

* Deque接口与ArrayDeque实现类

Deque代表一个双端队列

Deque接口的典型实现类：ArrayDeque类，既可以作为“栈”，也可以作为“队列”

* LinkedList实现类

LinkedList实现类非常强大，既可以作为List集合，也可以作为“栈”，也可以作为“队列”

## Java增强的Map集合

* HashMap和Hashtable实现类

Hashtable类似于Vector，是一个比较古老的类，不推荐使用

```
区别： 
1. Hashtable是线程安全的；HashMap是线程不安全的
2. Hashtable不允许使用null作为key和value；HashMap允许使用null作为key和value
```

## LinkedHashMap实现类

## Properties读写属性文件

## SortedMap接口和TreeMap实现类

## WeakHashMap实现类

```
HashMap保留了key对象的强引用，但是WeakHashMap只保留了key对象的弱引用
```

## IdentityHashMap实现类

这个Map实现类的实现机制与HashMap基本相似，但是它在处理两个key相等时比较独特：在IdentityHashMap中，当且仅当两个key严格相等(key1 == key2)时，才认为两个key相等；而HashMap只要key1与key2的equals和hashCode值相等即可

## EnumMap实现类

## 操作集合的工具类-Collections





















