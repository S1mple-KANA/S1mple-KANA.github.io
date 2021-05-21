---
layout: post
title: 这是一篇博客文章模板
date: 2015-3-02
categories: blog
tags: [标签一,标签二]
description: 文章金句。
---

# **1. 基础**

## 1. Java基础知识

### 1.1 重载和重写的区别

**重载（overload）：**发生在同一类中，方法名必须相同，参数类型不同，个数不同，顺序不同，方法返回值和访问修饰符可以不同，发生在编译时。

**重写（override）：**发生在父子类中，方法名、参数列表必须相同，返回值范围小于等于父类，抛出的异常范围小于父类，访问修饰符范围大于等于父类；如果父类方法访问修饰符为private，则子类不能重写父类该方法。

###  1.2 String，StringBuffer和StringBuilder的区别是什么？为什么String是不可变的？

**可变性**

简单的来说：String类中使用final关键字字符数组保存字符串，private final char value[]，所以String对象是不可变的。而StringBuilder与StringBuffer都继承自AbstractStringBuilder类，在AbstractStringBuilder中也是使用字符数字保存字符串char[]value但是没有用final关键字修饰，所以这两种对象都是可变的。

StringBuilder与StringBuffer的构造方法都是调用父类构造方法，也就是AbstractStringBuilder实现的，大家可以自行查阅源码。

```java
AbstractStringBuilder.java
abstract class AbstractStringBuilder implements Appendable, CharSequence
{ char[] value;
int count;
AbstractStringBuilder() {
}
AbstractStringBuilder(int capacity)
{ value = new char[capacity];
}
```



**线程安全性**

String中的对象是不可变的，也可以理解为常量，线程安全。

AbstractStringBuilder是StringBuilder与StringBuffer的公共父类，定义了一些字符串的基本操作，如expandCapacity.append.insert.indexOf等公共方法。StringBuffer对方法加了同步锁或者对调用的



### 如何在不使用外键的情况下保证数据的统一性

使用后台程序启动事务的模式保证数据的一致性，以前使用外键只是为把原本程序做的事情，改为数据库做。而互联网尤其多数业务场景下，没有必要保持这样的数据一致性，而且通过后台程序+数据库事务即可，同时减少外键的使用，可以减少死锁的发生概率，提高数据库的并发处理能力。

# 插入

centOS7下redis 6379端口开放却无法通过telnet进行外部连接？

1、首先确认配置信息，bind默认为127.0.0.1。更改为0.0.0.0或者用#号注释掉。

![image-20210521154429210](新建文件夹\image-20210521154429210.png)

2、protected-mode 默认为yes。更改为no即可通过外部进行连接。

![image-20210521151604103](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210521151604103.png)

3、此语句可为redis添加密码，如若不想要密码可以不设置。

![image-20210521151745034](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210521151745034.png)

4、wq保存并退出

![image-20210521152000953](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210521152000953.png)

5、外部telnet连接centOS7

![image-20210521152217484](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210521152217484.png)

6、查看redis服务是否启动，redis已经启动，占用地址是127.0.0.1.外部无法连接

![image-20210521153145522](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210521153145522.png)

7、登录redis客户端，输入密码，关闭已启动redis服务

![image-20210521153501196](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210521153501196.png)

8、查看服务状态，服务已断开

![image-20210521153618147](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210521153618147.png)

9、重启redis服务并查看IP与端口，此时IP更改为0.0.0.0。配置生效

![image-20210521153838510](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210521153838510.png)

10、打开控制台重新进行连接

![image-20210521154222163](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210521154222163.png)

11、输入auth 123456并回车，出现如下图。密码的输入过程不显示。

![image-20210521154309035](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210521154309035.png)