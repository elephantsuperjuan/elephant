---
layout: post
title:  "阅读清单-前端"
date:   2016-06-16 16:00:20
categories: 技术贴
image: 'img/html5.jpg'
---

### 阅读清单-前端
 - [webpack中文](#webpack) [http://webpackdoc.com/development.html](http://webpackdoc.com/development.html) 【2016-06-16】
 - [react native](#react_native)  [http://reactnative.cn/](http://reactnative.cn/)
 - [angularJS 2.0](#angularjs_2.0)  [http://www.angular.live/docs/ts/latest/](http://www.angular.live/docs/ts/latest/)
 - [angular material](#angular_material)  [https://github.com/angular/material/](https://github.com/angular/material)
 - [gulp](#gulp)  [http://www.gulpjs.com.cn/](http://www.gulpjs.com.cn/)

<h2 id="webpack">webpack</h2>
### webpack 模块打包器

    $ npm install webpack -g
    # 进入项目目录
    # 确定已经有 package.json，没有就通过 npm init 创建
    # 安装 webpack 依赖
    $ npm install webpack --save-dev

    # 查看 webpack 版本信息
    $ npm info webpack
    # 安装指定版本的 webpack
    $ npm install webpack@1.12.x --save-dev

    # 需要使用 Webpack 开发工具，要单独安装：
    $ npm install webpack-dev-server --save-dev

    # 安装 loader：
    $ npm install css-loader style-loader

    // 配置package.json
      "devDependencies": {
        "css-loader": "^0.21.0",
        "style-loader": "^0.13.0",
        "webpack": "^1.12.2"
      }
    // webpack.config.js
    module.exports = {
        entry: './js/activity.js',
        output: {
            path: './bin',
            filename: 'app.bundle.js'
        },
        module: {
            loaders: [
                { test: /\.\/css$/, loader: "style!css" }
            ]
        }
     };
     // 载入 css
     require("!style!css!../css/activity.css")
     
     # webpack打包
     $ webpack

<h2 id="react_native">react native</h2>

###react native 





<h2 id="angularjs_2.0">angularJS 2.0</h2>

### angularJS 2.0




<h2 id="angular_material">Angular Material</h2>

### Angular Material



<h2 id="gulp">gulp</h2>

### gulp
