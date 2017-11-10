---
title: 大前端周刊 第20期 （本期小编：杨齐）
date: 2017-11-10 15:08:59
tags:
---

## Show me the code

### 前端工程化工具 Dawn (来自阿里云开源)

阿里云内部的前端构建和工程化工具，现已完全开源。它通过 pipeline 和 middleware 将开发过程抽象为相对固定的阶段和有限的操作，简化并统一了开发人员的日常构建与开发相关的工作。

#### 特点

采用中间件技术，封装常用功能，易于扩展，方便重用
支持 pipeline 让多个 task 协同完成构建任务
简单、一致的命令行接口，易于开发人员使用
支持基于「中心服务」管理中件间和工程模板
支持搭建私有中心服务，并统一下发构建规则，易于团队统一管理

#### 安装

``` javascript
$ npm install dawn -g
```

#### 使用

``` javascript
# 1. 创建 & 初始化
$ dn init -t front

# 2. 开发 & 实时编译
$ dn dev

# 3. 语法检查 & 测试
$ dn test

# 4. 构建 & 打包
$ dn build
```

#### 示例

``` javascript
# 启动开发服务
dev:
  - name: webpack
    entry: ./src/.js
    template: ./assets/.html
    watch: true
  - name: server
    port: 8001

# 直接构建
buid:
  - name: webpack
    entry: ./src/.js
    template: ./assets/.html

```
#### 文档

使用入门：  [getting-started](https://user-gold-cdn.xitu.io/2017/11/2/68184fa8fc078832871f8ef138b9a8bf)

配置Pipeline： [pipeline.md](https://github.com/alibaba/dawn/blob/master/docs/markdowns/pipeline.md)


## 插件推荐

- [Frontend Tracker](https://github.com/Pgyer/frontend-tracker)
Frontend Tracker 可以发现前端页面的错误，并且用户察觉错误前将错误发送至指定服务器。

## 文章推荐
- [Node.js加密算法库Crypto](http://blog.fens.me/nodejs-crypto/)
用Node做web服务进行用户认证的场合下，经常需要对用户密码进行加密和解码的操作。Crypto是NodeJS的内置库，提供了必要的功能，值得学习收藏。

- [Web 应用内存分析与内存泄漏定位](https://github.com/wxyyxc1992/Web-Development-And-Engineering-Practices/blob/master/Modern-Web-Engineering-Practices/%E8%B0%83%E8%AF%95/%E5%86%85%E5%AD%98%E5%88%86%E6%9E%90%E4%B8%8E%E5%86%85%E5%AD%98%E6%B3%84%E9%9C%B2%E5%AE%9A%E4%BD%8D.md)
无论是分布式计算系统、服务端应用程序还是 iOS、Android 原生应用都会存在内存泄漏问题，Web 应用自然也不可避免地存在着类似的问题。虽然因为网页往往都是即用即走，较少地存在某个网页长期运行的问题，即使存在内存泄漏可能表现地也不明显；但是在某些数据展示型的，需要长期运行的页面上，如果不及时解决内存泄漏可能会导致网页占据过大地内存，不仅影响页面性能，还可能导致整个系统的崩溃。

- [前端状态管理请三思](https://juejin.im/post/59fd94475188254115703461)
有关前端状态管理的一篇文章，结合实际中的问题，实现一个好用的状态机。

- [前端API备忘录](https://juejin.im/entry/5a0149a9f265da431f4a7999)
好脑筋不如烂笔头，平时还是要多写，多记，推荐一个比较常用的前端API合集，忘得时候查一下，很方便

- [性能优化之组件懒加载](https://zhuanlan.zhihu.com/p/29433875)
文章首先抛出实际场景遇到的性能问题，给出现象，然后分析问题，提出两个解决思路，最后梳理优化并产出通用的Vue 2.x 组件级懒加载解决方案（Vue Lazy Component ）。

- [JavaScript 在 V8 中的元素种类及性能优化](https://segmentfault.com/a/1190000011303679)
JavaScript 对象可以具有与它们相关联的任意属性。对象属性的名称可以包含任何字符。JavaScript 引擎可以进行优化的一个有趣的例子是当属性名是纯数字时，一个特例就是数组索引的属性。

- [Webpack 热更新实现原理分析](https://zhuanlan.zhihu.com/p/30623057?utm_medium=social&utm_source=wechat_session)
在使用 Webpack 构建开发期时，Webpack 提供热更新功能为开发带来良好的体验和开发效率，该文分析关于webpack热更新技术的实现原理。

- [JavaScript Event Loop 机制详解与 Vue.js 中实践应用](https://segmentfault.com/a/1190000011044242)
依次介绍了函数调用栈、MacroTask 与 MicroTask 执行顺序、浅析 Vue.js 中 nextTick 实现等内容

- [从Chrome源码看浏览器如何加载资源](https://fed.renren.com/2017/10/29/chrome-fetch-resource/)
本文通过源码层面解释了浏览器如何加载资源，解决了前端对浏览器加载资源有很多不确定性的困惑，非常实用。

- [sass语法总结](http://www.jianshu.com/p/e139d449f5bb)
CSS 本身是非常强大的，但随着样式表变大，变复杂，维护 CSS 变得越来越难。这时候预处理就有用了。Sass 是一种预处理，它能让你使用一些 CSS 中没有的特性，比如：变量，嵌套（nesting），混入（mixins），继承等。这些特性能让 CSS 变的容易维护。

- [HTTP中GET与POST的区别](http://bbs.thankbabe.com/topic/72/99-%E7%9A%84%E4%BA%BA%E9%83%BD%E7%90%86%E8%A7%A3%E9%94%99%E4%BA%86http%E4%B8%ADget%E4%B8%8Epost%E7%9A%84%E5%8C%BA%E5%88%AB)
看这霸气的文章标题！快来看看和自己理解的是否一致吧


## 招聘
TalkingData DTU 可视化团队招聘：
* 资深前端工程师

简历投递：
``` javascript
const email = 'xiang.wang#tendcloud.com'.replace('#', '@');
console.log(email);
```
