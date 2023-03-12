# IPC机制

## 1、介绍

IPC的简写：Inter-Process Communication，即：进程间通信，具体指两个进程之间进行数据交换的过程。



- 进程：按照操作系统的描述，进程通常指一个执行单元，在PC或者移动设备上指一个程序或者一个应用。
- 线程：CPU调度的最小单元，也是一种有限的系统资源。

一个进程中可以包含多个线程，最简单的时候：一个进程只有一个进程，即：主线程。Android里面主线程也叫UI线程，不能把好使操作放在主线程中，否则会引起ANR。



Binder是Android中最具特色进程间通信方式。



## 2、Android中的多进程模式

### 2.1、开启多进程模式

通常，在Android中多进程是指一个应用中存在多个进程的情况。

Android中使用多进程的方法只有一个，即：给四大组件在Manifest文件中指定`android:process`属性

非常规方法：通过JNI在native层面去fork一个新的进程，暂时不考虑。









# 参考

[Android开发艺术探索](https://github.com/baijiangLai/Books/blob/master/Android/Android开发艺术探索.pdf)

