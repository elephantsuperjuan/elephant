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
3. 使用ng-table代码更清晰些

### 2. 关键字
angular ng-table $q.defer

### 3. 解决方案
1. 尝试用全局的 var defer = $q.defer来解决，结果点击页数时，只能请求两次，再点就没有调用后台接口了；
2. 需要每次新建defer对象


	  		module.exports = function ($scope, $filter, NgTableParams, CONFIG, API, rest, $q) {
	
		    'use strict';
		    var vm = this;
		    vm.getTableInfo = getTableInfo;
	
		    //初始化页面参数
		    init();
		
		    function init() {
		        //自定义分页查询参数
		        vm.searchFields = {
		            pageIndex: 0,     	// 重要,区分第一次网络请求
		            pageSize: 10,
		            type: "",
		            name: ""
		        };
		    }
			// 方式一
		    function getTableInfo1(currentPage) {
		        var defer = $q.defer();
		
		        vm.searchFields.pageIndex = currentPage;
		        rest.post4Data(API.url, vm.searchFields, API.method, function (data) {
		            defer.resolve(data);
		        });
		
		        defer.promise.then(function (data) {
		            vm.pageTable = new NgTableParams({
		                page: vm.searchFields.pageIndex,
		                count: 10
		            }, {
		                counts: [],     //不可删，也可配置[5,10,20]
		                getData: function (params) {
		                    if(vm.searchFields.pageIndex != params.page()){
		                        //点击页码时，判断是否要重新load数据
		                        getTableInfo(params.page());
		                    }else {
		                        //其他非点击页码时，只需要展示数据即可
		                        params.total(data.count);
		                    	return params.sorting ? $filter('orderBy')(data.list, params.orderBy()) : data.list;
		                    }
		                }
		            });
		        })
		    }

		    // 方式二（推荐，不会新建table对象，也不会重复网络请求）
		    function getTableInfo() {
		        var defer;
		
		        vm.pageTable = new NgTableParams({
		            page: 1,    //首次加载的默认页数
		            count: 10   //首次加载默认的条数
		        }, {
		            counts: [],     //不可删，也可配置[5,10,20]
		            getData: function (params) {
		                if(vm.searchFields.pageIndex != params.page()){
		                    //需要new一个新的defer对象，重新请求
		                    defer = $q.defer();
		
		                    vm.searchFields.pageIndex = params.page();
		                    rest.post4Data(API.url, vm.searchFields, API.method, function (data) {
		                        defer.resolve(data);
		                    });
		                }
		
		                //返回当前有效defer的请求数据
		                return defer.promise.then(function (data) {
		                    //其他非点击页码时，只需要展示数据即可
		                    params.total(data.count);
		                    return params.sorting ? $filter('orderBy')(data.list, params.orderBy()) : data.list;
		                });
		
		            }
		        });
		
		    }
