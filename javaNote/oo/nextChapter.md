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

* toString()方法
* ==和equals()方法

1.当使用==来判断两个变量是否相等时，如果两个变量是基本类型变量，且都是数值类型，只要两个变量的值相等就返回true；但对于引用类型的变量，只有他们指向同一个对象才返回true

```
int a = 65;
float f = 65.0F;
//将会输出true
System.out.println(a == f);
```

`当Java程序直接使用形如"hello"的字符串直接量（包括可以在编译时就计算出来的字符串值）时，JVM会使用常量池来管理这些字符串；当使用new String("hello")时，JVM会先使用常量池来管理"hello"直接量，再调用String类的构造器来创建新的String对象，新创建的String对象被保存在堆内存中。`

## 类成员

* 理解类成员（static）
* 单例类（Singleton）

## final修饰符

1.final修饰成员变量

```
注：final修饰的成员变量必须由程序员显式地指定初始值
类变量：必须在静态初始化块中或声明该变量时指定初始值
实例变量：必须在非静态初始化块、声明该实例变量或构造器中指定初始值
```

2.final修饰局部变量

`注：final修饰形参时，由系统根据传入的实参来初始化`

3.final修饰基本类型变量和引用类型变量

`注：对于引用类型变量而言，仅仅保存一个引用，final只保证这个引用类型变量所引用的地址不会改变，即一直引用同一个对象，但这个被引用对象本身是可以改变的`

4.宏变量

* 使用final修饰符修饰
* 在定义变量时指定初始值
* 该初始值在编译时就可以确定下来

```
String s = "ab";
String s1 = "a";
String s2 = "b";
String s4 = s1 + s2;
//输出false(如果想输出true，可以考虑使用宏变量)
System.out.println(s == s4);
``` 

5.final方法

6.final类

final修饰的类不可以有子类

7.不可变类

创建该类的实例后，该实例的实例变量是不可改变的。

```
使用private和final修饰符来修饰该类的成员变量
提供带参数的构造器，用于根据传入参数来初始化类的成员变量
仅为该类的成员变量提供getter方法，不要提供setter方法，因为普通方法无法修改final修饰的成员变量
如果有必要，重写Object类的hashCode()和equals()方法
```

## 抽象类

## 接口

`注：接口之间的继承支持多继承，这里与类是有区别的`

## 内部类

* 非静态内部类

`注：在非静态内部类里可以直接访问外部类的private成员，因为在非静态内部类对象里，保存了一个外部类对象的引用`

```
在内部类里访问外部类实例变量 = OutClass.this.propName
访问非静态内部类实例变量 = this.propName
如果外部类需要访问非静态内部类的成员，则必须显式创建非静态内部类对象
注：可以把非静态内部类看做外部类的一种实例成员
```

* 静态内部类

静态内部类可以包含静态成员，也可以包含非静态成员，静态内部类不能访问外部类的实例成员，即使是静态内部类的实例方法也不能访问外部类的实例成员

* 使用内部类

1.在外部类以外的地方定义内部类变量的语法格式： OuterClass.InnerClass varNmae
2.由于非静态内部类对象必须寄生在外部类的对象里，因此在创建非静态内部类对象之前，必须先创建外部类对象：new OuterClass().new InnerClass()

* 局部内部类

`注：这种语法很“鸡肋”，因为这种类的作用域太小，只能在当钱方法内使用`

* 匿名内部类

## Lambda表达式

Lambda表达式允许使用更加简洁的语法创建函数式接口的实例

* 方法引用和构造器引用

如果Lambda表达式的代码块只有一条代码，还可以在代码块中使用方法引用和构造器引用

|种类|实例|说明|对应的Lambda表达式|
|:------:|:------:|:------:|:------:|
|引用类方法|类名::类方法|被实现方法的全部参数传给该类方法作为参数|(a, b) -> 类名.类方法(a, b)|
|引用特定对象的实例方法|特定对象::实例方法|被实现方法的全部参数传给该方法作为参数|(a, b) -> 特定对象.实例方法(a, b)|
|引用某类对象的实例方法|类名::实例方法|第一个参数作为调用者，后面全部参数传给该方法作为参数|(a, b) -> a.实例方法(b)|
|引用构造器|类名::new|函数式接口中被实现方法的全部参数传给该构造器作为参数|(a, b) -> new 类名(a, b)|

```
引用类方法：
@FunctionalInterface
interface Converter{
    Integer conver(String form);
}

Converter con = form -> Integer.valueOf(form);

Converter con = Integer::valueOf;
```

```
引用特定对象的实例方法：
@FunctionalInterface
interface Converter{
	int conver(String form);
}

Converter con = form -> "Jiabinhe".indexOf(form);

Converter con = "Jiabinhe"::indexOf;
```

```
引用某类对象的实例方法：
@FunctionalInterface
interface Converter{
    String conver(String a, int b, int c);
}

Converter con = (a, b, c) -> a.subString(b, c);

Converter con = String::subString;
```

```
引用构造器：
@FunctionalInterface
interface Converter{
    JFrame win(String title);
}

Converter con = title -> new JFrame(title);

Converter con = JFrame::new; 
```

## 枚举类


















