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




