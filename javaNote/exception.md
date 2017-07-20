# 异常

## Java7提供的多异常捕获

捕获多种异常时，异常变量有隐式的final修饰，不可以对该变量重新赋值

```
try {
	//可能发生异常的代码
} catch (IndexOutOfBoundsException | NumberFormatException e) {
	//下面代码会出错
	e = new RuntimeException();
}
```

## Java7提供的自动回收资源的try-catch语句

```
try (
        BufferedReader br = new BufferedReader(new FileReader("notExistFile.java"))
    )
{
    System.out.println(br.readLine());
} catch (Exception e) {
    e.printStackTrace();
}
```



