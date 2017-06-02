---
layout: post
title:  "Reflect反射：java vs javascript"
date:   2017-06-01 14:00:00
categories: 阅读心得
---

1. 概念
    * wiki：在计算机科学中，反射是指计算机程序在运行时（Run time）可以访问、检测和修改它本身状态或行为的一种能力。用比喻来说，那种程序能够“观察”并且修改自己的行为。
	* 百度百科：反射，一种计算机处理方式。是程序可以访问、检测和修改它本身状态或行为的一种能力。
	* 能够分析类能力的程序成为反射 [java核心技术卷I][2]
2. 语言场景
	* Javascript
		* 反射的概念比较强的语言像java和go。因为他们都是静态语言。缺乏很多动态特性。他们是只有通过一大堆api才能反射。所以才会有比较强反射的概念。
		* 是一个基于原型继承的面向对象的函数语言。反射无处不在。（当一个概念无处不在的时候，那么设个概念也就渐渐地淡化了。）
	* [Java的反射中一些重要的方法][1]
		* JAVA反射机制是在运行状态中，对于任意一个类，都能够知道这个类的所有属性和方法；对于任意一个对象，都能够调用它的任意一个方法和属性；这种动态获取的信息以及动态调用对象的方法的功能称为java语言的反射机制。
		* Java中有个Object 类，是所有Java 类的继承根源，其内声明了数个应该在所有Java 类中被改写的方法：hashCode()、equals()、clone()、toString()、getClass()等。其中getClass()返回一个Class对象。Class对象十分特殊。他是Java中所有类的实例，借助它可以实现对一个对象的操作。
3. 实现方式
	* javascript实现方法-关键词
		* js中eval的使用可以达到java反射的效果——对应于java，通过类名forName能够调用任意方法。
		* js可以通过for(var p in obj)来实现反射，遍历obj对象的所有属性和方法，遇到属性则弹出它的值，遇到方法则立刻执行。
		* call/apply
		* ES6中新增了Reflect类（属于语言内部的方法），将for(var p in obj)的行为变成函数式行为；Reflect.has(obj, name)和Reflect.deleteProperty(obj, name)让它们变成了函数行为。包含13个静态方法，其中有Reflect.apply用来执行方法，set/get修改属性值，define/deleteProperty定义属性。参考[ES6 Reflect][3]
	* JAVA反射实现方法-关键词 [java核心技术卷I][2]
		* 反射机制最重要的内容——检查类的结构。java.lang.reflect包中有三个类Field、Method和Construct。
		* Method有一个invoke方法，它允许调用包装在method对象中的方法，反射机制允许你调用任意方法。
		* class类，通过*.getClass()获得，或Class.forName("java.util.Date")
		* Class类中的getFields、getMethods、getConstructors、getDeclaredFields、getDeclaredMethods、getDeclaredContructors将返回类中声明的域、方法和构造器。
4. 总结
	> 所以看了这么多，感觉ES6把js与java对反射的实现机制统一起来了呢；但是对于这种改进，功过自有人评说，不做详解。反射也就这么回事。


> [1]: https://segmentfault.com/a/1190000004326040 "Java的反射中一些重要的方法"
> [2]: java核心技术卷I，第9版 "java core I"
> [3]: http://es6.ruanyifeng.com/#docs/reflect "阮一峰 Reflect"
