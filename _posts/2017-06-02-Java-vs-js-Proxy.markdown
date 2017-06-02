---
layout: post
title:  "Proxy代理：java vs javascript"
date:   2017-06-02 15:00:00
categories: 阅读心得
---


## 概念
* Proxy 用于修改某些操作的默认行为，等同于在语言层面做出修改，所以属于一种“元编程”（meta programming），即对编程语言进行编程。Proxy 可以理解成，在目标对象之前架设一层“拦截”，外界对该对象的访问，都必须先通过这层拦截，因此提供了一种机制，可以对外界的访问进行过滤和改写。
* 利用代理可以在运行时创建一个实现了一组给定接口的新类。这种功能只有在编译时无法确定需要实现哪个接口时才有必要使用。

## 语言场景
* ES6 原生提供 Proxy 构造函数，用来生成 Proxy 实例。
* Java SE 1.3 新增加的特性。代理类是在程序运行过程中创建的。一单创建，就编程了常规类，与虚拟机中的任何其他类没有区别。代理类一定是public和final的,有接口、实现类、代理类三种身份，参见[代理模式Proxy][3]

## 实现方式
* js: ES6介绍了一个get set方法调用前拦截的例子，set前先检查是否可改，get判断该属性是否存在。参考[ES6 Proxy][1] 创建Proxy示例，需要实现handler，介绍了13中代理的实例方法。其中拦截函数的调用用apply——类比invoke。
* Java: Proxy.newProxyInstance(…),JAVA核心技术上I介绍了一个二分查找Integer数组的例子，元素由代理实现<code>Comparable.class</code>,于是在调用<code>Array.binarySearch(elements,key);</code>时,会调用该代理内invoke语句前的打印语句，包括输出时<code>System.out.println(result);</code>也会调用toString在该代理前的打印功能。参考[java核心技术卷I][2]
* 设计模式：以上两个例子均为动态代理（invoke/apply），静态代理（三类身份一看便知）——自己去csdn吧。

## 总结
* 对比一下，是不是又殊途同归了呢。

> [1]: http://es6.ruanyifeng.com/#docs/proxy "阮一峰 Proxy"
> [2]: java核心技术卷I，第9版 "java core I"
> [3]: http://blog.csdn.net/hguisu/article/details/7542143 " 设计模式（十一）代理模式Proxy（结构型）"
