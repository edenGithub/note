# 泛型

## 泛型入门

```
简单泛型使用示例：
    Map<String, Integer> map = new LinkedHashMap<>();
    map.put("1", 1);
    map.put("2", 2);
    map.put("3", 3);
    map.forEach((key, value) -> System.out.println(key + " -> " + value));
```

## 从泛型类派生子类

```
注：
在静态方法、静态初始化块或者静态变量的声明和初始化中不允许使用泛型声明
下面代码是错误而的
static T info;

public static coid info(T msg) {}

instanceof运算符后不能使用泛型
下面代码是错误的
a instanceof java.util.ArrayList<String>
```

## 类型通配符

```
public void test(List<?> list){}
```

设置类型通配符的上限制

```
public void draw(List<? extends Shape> shapes) {}

但是无法向这个集合中加入数据，因为系统只知道是Shape或其子类，并不知道具体是哪个类，所以下面代码是错误的
public void add(List<? extends Shape> shapes) {
	//引发编译错误
	shapes.add(new Circle());
}

```

一种更极端的情况：
程序需要为泛型设置多个上限

```
public class Apple<T extends Number & java.io.Serializable>
```

## 泛型方法

```
public static <T> arrayToCollection(T[] a, Collection<T> c) {
	for (T o : a) {
		c.add(o);
	}
}
```





