---
title: 大前端周刊 第11期 （本期小编：胡国伟）
date: 2017-09-01 17:00:00
tags: [weekly,开发工具,测试工具,Vue,ES6,设计模式]
---
## Show me the code

#### 截流(throttle)

概念理解：固定函数执行的速率。
使用场景：DOM 事件绑定，短时间内触发多次绑定事件造成性能问题，如 `onresize`,`onscroll`等，使用节流函数可确保在指定时间内只触发一次。
简单实现：
```javascript
let throttle = (func, wait) => {
	let context, args;
	let previous = 0;

	return function () {
		let now = +new Date();
		context = this;
		args = arguments;
		if (now - previous > wait) {
			func.apply(context, args);
			previous = now;
		}
	};
};
```

#### 防抖(debounce)

概念理解：强制一个函数在某个连续时间段内只执行一次，哪怕它本来会被调用多次。
使用场景：
1. 表单远程搜索，键盘多次输入取最后一次输入值作为查询关键词。
2. 下拉菜单的延时消失。

简单实现：
```javascript
let debounce = (func, wait) => {
	let timeout;
  	return function () {
    	let context = this;
    	let args = arguments;
    	clearTimeout(timeout);
    	timeout = setTimeout(function () {
      		func.apply(context, args)
    	}, wait);
    };
};
```

## 工具和模块

推荐功能强大的`HTTP`抓包调试工具：Fiddler。假如有这样一个场景，线上突然出现bug，而你正在休假、手头有没有源码，但又急需你参与问题排查，怎么办？Fiddler 便是你的救活利器。

1. 官网：http://www.telerik.com/fiddler
2. 插件（官方&第三方）：http://www.telerik.com/fiddler/add-ons
3. 快速上手：[十分钟学会 Fiddler](https://www.qcloud.com/community/article/115124?fromSource=gwzcw.93596.93596.93596)
4. 视频教程：http://www.imooc.com/learn/37
5. 系列文章
   - [【HTTP】Fiddler（一） - Fiddler简介](http://blog.csdn.net/ohmygirl/article/details/17846199)
   - [【HTTP】Fiddler（二） - 使用Fiddler做抓包分析](http://blog.csdn.net/ohmygirl/article/details/17849983)
   - [【HTTP】Fiddler（三）- Fiddler命令行和HTTP断点调试](http://blog.csdn.net/ohmygirl/article/details/17855031)


## 文章推荐

- [代码覆盖率工具 Istanbul 入门教程](http://www.ruanyifeng.com/blog/2015/06/istanbul.html)
  使用 Mocha 进行单元测试时，还需要了解测试的覆盖程度，这个指标就叫做"代码覆盖率"（code coverage）。这篇文章非常全面地介绍了Istanbul，让你轻松上手。深入了解：[nyc](https://github.com/istanbuljs/nyc)

- [深入浅出浏览器渲染原理](https://mp.weixin.qq.com/s?__biz=MzIyMjYyMzg3MA==&mid=2247484408&idx=2&sn=456405dd36fd679dea1470b131924980&chksm=e82be2e9df5c6bff70912d297d535bfb747e2598a129641ea3409cedd88f2eac22e2d77dc98b&mpshare=1&scene=1&srcid=0901XT4SSeVjxiKd3Pj6IOvv&pass_ticket=%2BCgbmXT%2FgYy2AZSB%2B2tlPOm2ZM34W2NpPc%2F1G3ifFff91PXQRXcYFvt%2BSdaP7QjU#rd)
  对于 HTTP 协议和浏览器渲染原理都是理解容易但不好讲明白，那么为什么不采用 Node.js 来阐述呢？以实践的方式、最简单的方式来向你展示不好讲的东西，对于 Node.js 开发者和大前端开发来说都是非常实用的。

- [剖析Vue实现原理 - 如何实现双向绑定mvvm](https://github.com/DMQ/mvvm)
  1. 了解vue的双向数据绑定原理以及核心代码模块
  2. 了解如何实现双向绑定

- [不用call和apply方法模拟实现ES5的bind方法](https://github.com/jawil/blog/issues/16)
  这个问题是对JavaScript基本功很好的一个检测，看JavaScript掌握的怎么样以及平时有没有去深入研究一些方法的实现，简而言之，就是有没有折腾精神。

- [通过ES6 Generator函数实现异步操作](https://github.com/Jocs/jocs.github.io/issues/11)
  文章对 Generator函数实现异步进行了深入的讲解，最后使用 promise和 generator这样的模式实现异步操作，对于实现的过程进行深入细致的分析。

- [你了解CSS设计模式吗？](http://mp.weixin.qq.com/s?__biz=MzI2MTY0NTEyMA==&amp;mid=2247483871&amp;idx=1&amp;sn=f717d3c787626d997c410117a1cd7fb9&amp;chksm=ea5677f0dd21fee6c7853b60b7e32d744af1abb183903ce8523954e093263a8c375895f0f193&amp;mpshare=1&amp;scene=1&amp;srcid=06289q8vqWAQUGuqdrMsqEzq#)
  简单来了解下CSS设计模式：
  1. BEM全称（block、element、modifier）是Yandex 团队提出的CSS Class命名法
  2. OOCSS全称（Object Oriented CSS）由Nicole Sullivan提出的css理论
  3. SMACSS是Jonathan Snook的一个CSS框架
  4. Atomic Design，原子设计


 - [我接触过的前端数据结构与算法](http://fed.renren.com/2017/07/02/algorithm/)
     作者总结了前端常常碰到的算法，主要涉及递归、节流、数组去重、栈和堆、图像处理等。代码示例较为清晰，对于初学者还是很有帮助的，比较赞同作者的观点：算法的目的是用最小的时间和最小的空间解决问题。但是有时候不用太拘泥于一定要最优的答案，能够合适地解决问题就是好方法，而且对于不同的应用场景可能要采取不同的策略。

- [JavaScript 中 4 种常见的内存泄露陷阱](http://web.jobbole.com/88463/)
  虽然Javascript有内存自动回收机制，但这并不以为着js开发使完全不用关心内存管理。文中详细介绍了什么是内存泄漏和js中容易引起内存泄漏的点，并提供了使用Chrome分析内存的方法。

## 招聘
TalkingData DTU 可视化团队招聘：
* 资深前端工程师
* 前端实习生

简历投递：
``` javascript
const email = 'xiang.wang#tendcloud.com'.replace('#', '@');
console.log(email);
```