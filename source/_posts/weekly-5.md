---
title: 大前端周刊 第5期 （本期小编：陶明）
date: 2017-07-21 14:21:43
tags: [weekly,three.js,Zepto,ES6,Vue,事件驱动]
---

## 基础
* [JS中关于this](https://kongchenglc.github.io/blog/%E5%85%B3%E4%BA%8Ethis20170716/)
**关于this的几种绑定规则以及优先级**

* [跨域资源共享 CORS](http://www.ruanyifeng.com/blog/2016/04/cors.html)
**一个option请求引发的疑惑**

* [表单脚本的基础知识](http://www.jianshu.com/p/fc2017f18525)
**详细的总结了表单的属性、方法及事件**

## 文章
* [五种事件驱动的API架构](https://talkingdata.github.io/fsd/2017/07/21/5-protocols-for-event-driven-api-architectures/)
<small>*推荐人：王祥*</small>
本文会介绍 5 种事件驱动的 API 架构：WebSockets、WebHooks、REST Hooks、Pub-Sub， 以及 Server Sent Events，并分别介绍这几种架构的基础功能、使用方式以及各自的优缺点。
对于 Node.js 开发者来说，我们天生就在使用事件驱动的架构，业界也越来越认可事件驱动架构和异步系统的优势，了解本文介绍的 5 种事件驱动API 架构。

* [推荐一篇Three.js入门文章](https://zhuanlan.zhihu.com/p/27296011)
<small>*推荐人：张成斌*</small>
文章把学习Three.js需要掌握的基本概念和知识点讲解的很详细。并且结合代码实现了一个demo。对于Three.js有兴趣的同学，是一篇不错的入门文章。

* [推荐一篇介绍RESTful API的文章](https://segmentfault.com/a/1190000010261115)
<small>*推荐人：李丽娇*</small>
介绍了RESTful API的实现思想，并从http请求方式和相应内容等方面给出详细示例。
在项目接口设计和接口对接中可做实质性参考。

* [读 Zepto 源码之 Event 模块](https://juejin.im/post/596d45d96fb9a06ba2688e44/?utm_source=weixinqun&utm_medium=feZeptoEvent)
<small>*推荐人：胡国伟*</small>
如何自己实现事件处理，本文通过深入浅出解读 Zepto Event 模块源码，给我们提供了很好的答案。

* [深入探究 eventloop 与浏览器渲染的时序问题](https://www.404forest.com/2017/07/18/how-javascript-actually-works-eventloop-and-uirendering/)
<small>*推荐人：陶明*</small>
文章通过对那些『延迟』执行的函数思考，深入的对event loop和task进行了拆分讲解，通过实例与图示详细讲解了整个执行渲染过程。

* [vue的Virtual Dom实现- snabbdom解密](http://www.cnblogs.com/xuntu/p/6800547.html)
<small>*推荐人：李志伟*</small>
文章通过详细的图文对照、算法代码解析讲述了虚拟dom的实现，Virtual Node作为纯数据对象，patch创建或者更新DOM树，diff算法用来比较同层级，然后通过钩子和扩展模块创建有attribute、props、eventlistener的复杂dom。

* [ES6数组的扩展(rest参数和扩展运算符)](https://github.com/ruanyf/es6tutorial/blob/8c8be74712a9e0d1a5dbcc855fe3e574b9fd4e6b/docs/array.md)
<small>*推荐人：耿少真*</small>
rest参数和扩展运算符都是ES6新增的特性。
rest参数的形式为：...变量名；扩展运算符是三个点（...）。

 ##### rest参数:
  - rest参数用于获取函数的多余参数，这样就不需要使用arguments对象了, rest参数搭配的变量是一个数组，该变量将多余的参数放入数组中

 ##### 扩展运算符:
  - 扩展运算符可以看做是 rest 参数的逆运算，将一个数组转为用逗号分隔的参数序列

* [程序员如何快速学习新的框架](https://mp.weixin.qq.com/s?__biz=MjM5Mjg4NDMwMA==&mid=2652975196&idx=1&sn=7775588a3e5a9cd44090f379766d2354&chksm=bd4ae37f8a3d6a69d00df95143c477440c4c494df56a101e4e076911a615e75f5b194cd4e182&mpshare=1&scene=1&srcid=0720soS6N4MjqELSisDoyamI#rd)
<small>*推荐人：郭俊兵*</small>
前端框架丰富多彩的今天，快速学习新的框架是每个前端程序员的必备技能。

* [4种使用webpack提升vue应用的方式](https://mp.weixin.qq.com/s?__biz=MjM5MTA1MjAxMQ==&mid=2651226710&idx=1&sn=3c6848e002aabeb55d6e9456b646d03d&chksm=bd495bd28a3ed2c43c34afb19a4fb0aedfb489b847f5e27348b9a021242e115d6ddb158c9e32&mpshare=1&scene=1&srcid=0721vFmgm9iqGHwNUyqboDb3&pass_ticket=E7F2%2BBqX9jvbMHf320yfzDVuT2rXz5tmHzjKDL3CgheMLCPvEi2MI8tlg%2FO3xRtu#rd)
<small>*推荐人：包京京*</small>
本篇文章所提到的几个措施大家可能都曾经在项目里用过，但是就如作者所言：你只是在用，并不知道为什么用，本文最大的价值在于提供了系统的优化方案并解释了原因

## 其他
* [pell](https://github.com/jaredreich/pell)
**一个非常轻的开源WYSIWYG 编辑器**
* [three.js](https://threejs.org/examples/#webgl_animation_cloth)
**three.js的Demo**
