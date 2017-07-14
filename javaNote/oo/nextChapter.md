# 面向对象


## 包装类及其用法

* 包装类的概念

基本类型 - 包装类

|基本数据类型    |     包装类    |
|:------------:|:------------:|
|byte          |Byte          |
|short         |short         |
|int           |Integer       |
|long          |Long          |
|char          |Character     |
|float         |Float         |
|double        |Double        |
|boolean       |Boolean       |

* 包装类与基本类型的转换

`注：除了Character类之外，都可以通过传入字符串参数来构建包装类对象。 `

* **包装类**实现了基本类型和字符串之间的转换

```
//基本类型转字符串
public static String valueOf(int i) {
    return Integer.toString(i);
}
```

* 包装类的比较

1.包装类与数值可以直接比较

```
Character c = 'A';
System.out.println(c > 4);
```

2.两个包装类比较

```
public static int compare(int x, int y) {
    return (x < y) ? -1 : ((x == y) ? 0 : 1);
}
```

## 处理对象


