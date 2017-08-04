---
title: 大前端周刊 第七期 （本期小编：张成斌）
date: 2017-08-04 10:32:34
tags: [weekly,模块,node,Vue,函数式]
---
## 基础

* [exports、module.exports 和 export、export default 到底是咋回事](https://juejin.im/post/597ec55a51882556a234fcef)
**模块引入方式的一个梳理**

* [Node.js 实践教程](https://juejin.im/post/597ec55a51882556a234fcef)
**饿了么出的一个Node实践教程，还在施工中，有兴趣的小伙伴可以关注一下。前提背景是[如何通过饿了么 Node.js 面试](https://github.com/ElemeFE/node-interview/tree/master/sections/zh-cn)**

* [浏览器是怎么看闭包的](https://juejin.im/post/5979b5755188253df1067397)
**换个角度来理解闭包，从内存分配与回收的角度阐述，希望能帮助大家真正消化掉所看到的闭包知识**

## 文章
* [深入理解 JavaScript 数据双向绑定](https://mp.weixin.qq.com/s?__biz=MzIyMjYyMzg3MA==&mid=2247484289&idx=2&sn=e1d9664d24d7b44bcece7464318a8369&chksm=e82be290df5c6b86f08fa80a5b33e4a3d46daa1093290610d63b47f86f5bdd7d21151b91dd8f&mpshare=1&scene=1&srcid=0804TnxBJbqO63wtfhcXPBra&pass_ticket=lctb96bPZ%2BUbaZfdgO9Bxo8p62cFUW61TN3xhm1p6zgF%2FxcmdmZtIzWeDN%2F7BnNZ#rd)
<small>*推荐人：包京京*</small>
首先讲解一下数据双向绑定的基本原理，介绍对比一下三大框架的不同实现方式，同时会一步步完成一个简单的mvvm示例。

* [前端开发者指南（2017）](https://juejin.im/post/592faca42f301e006bc791e0)
<small>*推荐人：郭俊兵*</small>
内容偏向于 WEB 技术（HTML、CSS、DOM、JavaScript）和以这些技术为根基直接构建而成的开源技术。书中引用和讨论的材料要么就是同类翘楚，要么就是解决问题的流行方案。

* [关于 Vue App 开发的一些思考](https://juejin.im/post/592faca42f301e006bc791e0)
<small>*推荐人：张成斌*</small>
TalkingData实习生写的一篇文章。作者回顾了自己经历三个项目的开发历程，发现了很多问题，也产生了很多思考。该文章有很多值得借鉴的地方。

* [JavaScript专题之jQuery通用遍历方法each的实现](https://segmentfault.com/a/1190000010480396)
<br>[系列目录地址](https://github.com/mqyqingfeng/Blog)
<small>*推荐人：陶明*</small>
文章从each 的功能实现入手不断完善，整体实现思路清晰，对于问题及解决也有详细的代码实现与解释。这是一个系列内容涵盖防抖、节流、去重、类型判断等。

* [JavaScript 数据类型和数据结构](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Data_structures)
<small>*推荐人：李丽娇*</small>
作为js权威文档之一，mozilla网站除了对基础只是的介绍，还会有一些总结性的文章和使用注意事项。
这篇文章总结性地介绍了Javascript的数据类型和数据结构，并有一些使用中的注意事项。

* [函数式编程初探](http://www.ruanyifeng.com/blog/2012/04/functional_programming.html)
<br>[函数式编程入门教程](http://www.ruanyifeng.com/blog/2017/02/fp-tutorial.html)
<small>*推荐人：王祥*</small>
推荐阮一峰老师的两篇函数式入门文章，大家可能无意识的使用函数式编程一段时间了。读这两篇文章，可以将思维里零散的函数式编码习惯系串联起来。

* [Vue 全站服务器渲染 SSR 实践](http://gitbook.cn/m/mazi/article/5900675d2fde0e5078d4ed5e?readArticle=yes)
<small>*推荐人：胡国伟*</small>
掘金分享了`vue`实现SSR的实践，目前来看性能问题依然很严重，仅供大家参考。

* [Vue开发常见问题集锦](http://mp.weixin.qq.com/s/fgFOvWBC_P78hG154gyXYQ)
<small>*推荐人：王俐*</small>
附：[换个思路理解Javascript中的this](http://mp.weixin.qq.com/s/fgFOvWBC_P78hG154gyXYQ)实际开发中会遇到的问题，主要涉及技术栈： Vue-CLI、 Element UI、 Pug(Jade)、 Less、ES6；
1、涉及问题：ES6语法转换建议使用babel-polyfill；
2、对于let和const的使用
3、自定义路径别名的设置
4、 在使用 Moment.js 遇到一些问题
5、CSS 作用域与模块

* [详解 Vue 2.4.0 带来的 4 个重大变化](https://mp.weixin.qq.com/s/qRAdgYxOfBW6xmQUdZcu_A)
<small>*推荐人：李志伟*</small>
“异步组件”让你的应用代码分离，使非必要组件在首页加载后延迟加载， 从而让用户更快的看到主页；组件内新增实现“属性继承”，使你的在每个中间组件属性定义变得相当简洁；异步组件支持webpack3，vue-loaderv13.0.0将.vue文件作为ES模块输出，这使得vue能够享受新的变量提升带来的便利；保留HTML注释，咳咳...聊胜于无。

* [异步编程之async](https://i.jakeyu.top/2017/03/15/async/)
<small>*推荐人：耿少真*</small>
对async方法的深入理解。
