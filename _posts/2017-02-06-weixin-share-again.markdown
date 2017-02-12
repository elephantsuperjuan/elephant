---
layout: post
#标题配置
title:  微信二次转发经验分享
#时间配置
date:   2017-02-06 13:47:00 +0800
#大类配置
categories: document
#小类配置
tag: 教程
---

### 1. 背景	
分享到微信可以调用webview自带的分享功能，集成了微信sdk；但是再次转发时，当前页面并没有集成微信sdk的功能，为此，结合微信转发和分享的默认配置，设置再次转发时的默认title和默认图标。

### 2. 解决方案

**标题**：会取当前页面title里面的内容。    
**图片**：会取当前页面body内最前面的一张符合条件的图片。   
**简介**：暂时没有办法，默认为访问地址   
**图片规格有要求**：    
尺寸必须大于： 300px × 300px  
把符合以上两个条件的图片放到<img>里，放到页面<body>内的最前面。
这样分享时就会取这张图作为缩略图了。    

> ### tip1: ios的标题使用document.title = "标题"，并不会起作用，以下可解决。 

	function mySetTitle(title) {
	    document.title = title;  
	
	    if($rootScope.os.iphone && $rootScope.os.weixin){
	        var i = document.createElement('iframe');
	        i.src = '/favicon.ico';
	        i.style.display = 'none';
	        i.onload = function() {
	            setTimeout(function(){
	                i.remove();
	            }, 9)
	        };
	        document.body.appendChild(i);
	    }
	}

> ### tip2. 设置默认图片相关代码

	// template添加默认图标	
	<div style='display:none'>
		<img id='wx_logo' src="\{\{share.wxImg}}" />
	</div>

	// 预加载该图标
	var wxImg = require('./res/logo-300.png');
	var mod = angular.module('app.shareCtrl', []);
	mod.controller('shareCtrl', shareCtrl);
	mod.value('wxImg', wxImg);
	
	// 给该图标src赋值
	module.exports = /*@ngInject*/function (wxImg) {
		vm.wxImg = wxImg;
	}
