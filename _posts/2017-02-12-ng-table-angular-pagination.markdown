---
layout: post
#标题配置
title:  ng-table分页，post数据，后台分页
#时间配置
date:   2017-02-06 13:47:00 +0800
#大类配置
categories: document
#小类配置
tag: 教程
---

### 1. 背景
angular使用bootstrap的原生分页与ng-table的区别，
1. 需要自己生成分页的数组
2. 不能排序
3. 代码清晰些

### 2. 关键字
angular ng-table $defer

### 3. 解决方案
1. 尝试用全局的 var defer = $q.defer来解决，结果点击页数时，只能请求两次，再点就没有调用后台接口了；(这个问题之前晨哥应该也遇到了，至于后来怎么解决，我再看看代码)
2. 
http://www.cnblogs.com/hutuzhu/p/4465109.html