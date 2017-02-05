---
layout: post
#标题配置
title:  Markdown语法示例快速上手
#时间配置
date:   2017-01-19 01:08:00 +0800
#大类配置
categories: document
#小类配置
tag: 教程
---

Markdown语法示例快速上手
====================
##### 1/19/2017 2:06:12 PM 

### 1. 标题 (#)
	# Header 1
	## Header 2
	### Header 3（依次类推，1~6）

# Header 1
## Header 2
### Header 3（依次类推，1~6）

### 2. 区块（>）; 段落（换行加空行或`<br\/>`）； 修辞（`*`）和强调(`**`)	
	> Some of these words *are emphasized*.
	<br/>
	> Use two asterisks for **strong emphasis**.
	> 

> Some of these words *are emphasized*.
<br/>
> Use two asterisks for **strong emphasis**.
> 

###3. 无序列表(*,+,-)，有序列表（1. ）、
	> 1. elephant
	> 2. winkle
	
	* Candy.
	+ Candy.
	- Gum.
	
	> * A list item.
	> <br/>With multiple paragraphs.
	> * Another item in the list.
	
> 1. elephant
> 2. winkle

* Candy.
+ Candy.
- Gum.

> * A list item.
> <br/>With multiple paragraphs.
> * Another item in the list.

### 4. 链接
	This is an [example link](http://example.com/ "With a Title").
	
	> 参考文献的方式
	> <br/>
	> I get 10 times more traffic from [Google][1] than from
	[Yahoo][2] or [MSN][3].
	
	> [1]: http://google.com/ "Google"
	> [2]: http://search.yahoo.com/ "Yahoo Search"
	> [3]: http://search.msn.com/ "MSN Search"


This is an [example link](http://example.com/ "With a Title").

> 参考文献的方式
> <br/>
> I get 10 times more traffic from [Google][1] than from
[Yahoo][2] or [MSN][3].

> [1]: http://google.com/ "Google"
> [2]: http://search.yahoo.com/ "Yahoo Search"
> [3]: http://search.msn.com/ "MSN Search"

### 5. 图片
	![图片示例](../img/resume.png "resume")
	
	
	> 参考文献的方式
	> <br/>
	> ![alt text][id]
	
	> [1]: http://google.com/ "Google"
	> [2]: http://search.yahoo.com/ "Yahoo Search"
	> [3]: http://search.msn.com/ "MSN Search"

![图片示例](../img/resume.png "resume")


> 参考文献的方式
> <br/>
> ![alt text][id]

> [1]: http://google.com/ "Google"
> [2]: http://search.yahoo.com/ "Yahoo Search"
> [3]: http://search.msn.com/ "MSN Search"


### 6. 代码区块 (``), 代码段（tab）

	`<blink>` 或 `&nsbp`
	
		#include <iostream>;
		using namespace

`<blink>` 或 `&nsbp`

	#include <iostream>;
	using namespace

