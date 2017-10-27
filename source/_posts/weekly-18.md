---
title: 大前端周刊 第18期 （本期小编：包京京）
date: 2017-10-27 10:24:12
tags:
---

## Show me the code

### 用Javascript学习数据结构之栈(Stack)

栈(Stack)是一种遵循后进先出（LIFO）的有序集合，较新的元素会靠近顶部，较旧的元素会在栈的底部。
接下来我们正式开始实现栈（Stack）。首先，建立一个Stack类：


``` javascript
function Stack() {
    // 类内部定义Stack的属性和方法
}
```
#### 属性：
1. let items = []; //使用array来存储栈内的元素

#### 方法：
1. push(elements): 新增一个或者多个元素到栈的顶部
2. pop(): 移除栈顶部元素，同时返回被移除的元素
3. peek()或top(): 仅返回stack元素，不做任何修改
4. isEmpty(): 检查栈是否为空？若无任何元素则返回true，反之返回false
5. clear(): 清空栈内的所有元素
6. size(): 返回栈的元素个数

#### 1.push(elements)和pop()
由于我们使用array当做stack的存储方式，所以我们可以使用array内建的push(element)和pop()方式来实现LIFO的特性，让元素的新增和删除只能发生在尾端。
``` javascript
function Stack() {
    let items = [];
    this.push = function(element) {
        items.push(element);
    }
    this.pop = function() {
        return items.pop();
    }
}
```

#### 2.peek()：
若是我们想知道栈中的最后一个元素（最顶端的元素），我们可以实现peek()方法，返回顶部元素
``` javascript
function Stack() {
    let items = [];
    this.peek = function() {
        return items[items.length - 1];
    }
}
```
#### 3.isEmpty()：
若我们想知道栈内是否还有元素，我们可以使用isEmpty()来判断
``` javascript
function Stack() {
    let items = [];
    this.isEmpty = function() {
        return items.length === 0;
    }
}
```
#### 4.clear()：
若我们想清空栈的话，可以使用clear()方法，将所有元素删除
``` javascript
function Stack() {
    let items = [];
    this.clear = function() {
        items = [];
    }
}
```
#### 5.size()：
通过size()方法我们可以取得栈的大小（共有几个元素）
``` javascript
function Stack() {
    let items = [];
    this.size = function() {
        return items.length;
    }
}
```
#### 完整代码：
把上面各种方法放到一起
``` javascript
function Stack() {
    var items = [];
    this.push = function(element) {
        items.push(element);
    }
    this.pop = function() {
        return items.pop();
    }
    this.peek = function() {
        return items[items.length - 1];
    }
    this.isEmpty = function() {
        return items.length === 0;
    }
    this.clear = function() {
        items = [];
    }
    this.size = function() {
        return items.length;
    }
    // 加入打印方法
    this.print = function() {
        console.log(items.toString());
    }
}
```
## 插件推荐

- [PhantomJS](http://phantomjs.org/)
PhantomJS可以应用于下面这几个典型场景：无需浏览器的web测试，页面自动化操作，屏幕截图和网络监控等

## 文章推荐
- [Node.js的事件轮询Event Loop原理解释](http://www.jdon.com/idea/nodejs/event-loop.html)
Event Loop是理解Node实现事件驱动、异步高并发服务的关键。这篇文章中解释了下面几个容易被忽略的点： 1. Node.js的底层其实也是有一个线程池的，用来执行各种堵塞操作。2. 一个Event loop的三个基本组件：事件队列、读取事件的轮询线程、以及线程池。3. 各个事件的回调函数是如何激活并执行的。

- [jsonp原理详解](http://www.qdfuns.com/notes/16738/1b6ad6125747d28592a53a960b44c6f4.html)
jsonp不是ajax的一个特例，哪怕jquery等巨头把jsonp封装进了ajax，也不能改变这一点！

- [this , apply , call , bind详解](https://juejin.im/post/59bfe84351882531b730bac2)
几个ES5 的坑，this是其中经常搞晕的一个，上一篇通俗且易理解的文章

- [深入理解 Node.js Stream 内部机制](http://taobaofed.org/blog/2017/08/31/nodejs-stream/)
知其然知其所以然，来了解一下nodejs stream内部机制。

- [基于 Electron 开发客户端产品的体验](https://segmentfault.com/a/1190000011699304)
基于 Electron 开发的产品非常多，文章主要是针对于如何入门 Electron，可以说是作者开发的总结；非常适合计划使用 Electron的开发者阅读。

- [babel到底该如何配置？](https://juejin.im/post/59ec657ef265da431b6c5b03)
大家都知道js作为宿主语言，很依赖执行的环境（浏览器、node等），不同环境对js语法的支持不尽相同，特别是ES6之后，ECMAScrip对版本的更新已经到了一年一次的节奏，虽然每年更新的幅度不大，但是每年的提案可不少。babel的出现就是为了解决这个问题，把那些使用新标准编写的代码转译为当前环境可运行的代码，简单点说就是把ES6代码转译（转码+编译）到ES5。

- [CSS 新的长度单位 fr 你知道么？](https://zhuanlan.zhihu.com/p/27502596)
本文介绍了 CSS Grid 规范中引入的一个新的长度单位 fr，我们一起来看看到底是怎么回事吧！

- [使用 webpack 优化资源](https://qiutc.me/post/resource-optimization-webpack.html)
本片文章中主要是基于 webpack 打包，以 React、vue 等生态开发的单页面应用来举例说明如何从 webpack 打包的层面去处理资源以及缓存，其中主要我们需要做的是对 webpack 进行配置的优化，同时涉及少量的业务代码的更改。

- [SASS用法指南](http://www.ruanyifeng.com/blog/2012/06/sass.html)
今年TalkingData团队将 CSS 预处理器切换到了 SASS，代码层面只是简单直接的做了风格转换，还没有挖掘出 SASS 更深入的能力。本周推荐一篇 SASS “基础”内容，推荐大家阅读和实践，以提升大家在 CSS 方面的编程能力。

- [VirtualDOM与diff(Vue实现)](https://zhuanlan.zhihu.com/p/29450092)
我们是不是可以把真实DOM树抽象成一棵以JavaScript对象构成的抽象树，在修改抽象树数据后将抽象树转化成真实DOM重绘到页面上呢？于是虚拟DOM出现了，它是真实DOM的一层抽象，用属性描述真实DOM的各个特性。当它发生变化的时候，就会去修改视图。

- [多“维”优化——前端高并发策略的更深层思考](http://wetest.qq.com/lab/view/316.html)
一项指标的变好，总少不了相应优化策略的实施。优化并不是简单的一蹴而就，而是个不断迭代与推翻的过程。更深层的优化方案，往往是在某种思维策略之下，对问题场景和基本策略优缺的深刻理解后做出的当下最优的权衡结果——作者导读。

- [Egg 源码解析之 egg-cluster](https://juejin.im/entry/59bcce1b5188257e82676b53)
Node.js 进程只能运行在一个 CPU 上，而 egg 采用多进程模型，使多核 CPU 的性能发挥到极致，最大程度地榨干服务器资源，进而解决了该问题。egg-cluster 是用于 egg 多进程管理的基础模块，负责底层的 IPC 通道的建立以及处理各进程的通信，本文解析了实现原理，值得一看。

## 招聘
TalkingData DTU 可视化团队招聘：
* 资深前端工程师

简历投递：
``` javascript
const email = 'xiang.wang#tendcloud.com'.replace('#', '@');
console.log(email);
```