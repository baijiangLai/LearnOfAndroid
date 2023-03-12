# so加载流程
## 前言：

为什么需要了解？
只要使用到Java进行开发，或多或少都会知道`native`关键字，由于Java无法与一些操作系统的东西直接打交道，因此只能委托`JNI`，但是JVM如何加载`So`，可能很少了解



## System.load&loadLibrary()

System 提供的` load() `用于指定 so 的`完整的路径名且带文件后缀`并加载，等同于调用 Runtime 类提供的 load()。

比如：

```java
System.load("/sdcard/xxx/xx.so")
```

1. 通过反射获取调用来源的Class实例
2. 调用Runtime的`load0()`实现



`load0()`:

`load0()` 首先获取系统的 SecurityManager。当 SecurityManager 存在的话检查目标 so 文件的访问权限。

	1. 权限不足的话打印拒绝信息、抛出 SecurityException ，如果 name 参数为空，抛出 NullPointerException。
	1. 如果 so 文件名非绝对路径的话，并不支持，并抛出 UnsatisfiedLinkError，message 为：

```
Expectiong ad absolute path of the library: xxx
```

只有当以上两步完成后，才会继续调用`ClassLoader`的loadLibrary()实现

# 参考
[一文了解 Java 中 so 文件的加载原理](https://mp.weixin.qq.com/s/HVQvjDhhUuCrkBuOP8PJZw)