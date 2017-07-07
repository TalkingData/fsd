---
title: 大前端周刊 第三期 （本期小编：李志伟）
date: 2017-07-07 13:10:51
tags: [weekly,es6,vue,算法,工具,必备技能]
---

## 基础
* [JavaScript系列](https://juejin.im/post/59278e312f301e006c2e1510)
相信作为“前端程序猿(媛)”的你一定了解作用域、原型、原型链、继承、闭包……在前端框架的盛行之下，却让初学者忽略了JS基础的学习，但基础不稳必然限制你的发展空间，当你了解了底层，就能很轻松明白框架的原理。

* [排序算法](https://juejin.im/post/57dcd394a22b9d00610c5ec8)
什么？在这个“用数据说话”的时代，你不懂排序算法？那你算什么男人~算什么男人~ 不对不对 算什么猿人~算什么猿人...咳咳，言归正传，平时开发我们常用的快速排序、冒泡排序、选择排序你是否了解其利弊。除此之外还有什么排序算法呢？快来一起学习吧。

* [Iterator 遍历器](http://es6.ruanyifeng.com/#docs/iterator)
Iterator为各种不同的数据结构提供了统一的访问机制。它可以提供统一的、简便的接口，使得数据结构的成员按某种次序排列，而es6新增for...of循环，就是由Iterator接口提供消费的。

* [TCP协议简介](http://www.ruanyifeng.com/blog/2017/06/tcp-protocol.html)
TCP作为互联网核心协议之一，“三次握手”“四次挥手”你是否有所了解？快来完善自己的知识体系吧。
ps:详解请参考[这里](http://www.jianshu.com/p/ef892323e68f)

* [正则表达式](http://www.jianshu.com/p/e7bb97218946)
业务中有很多复杂的逻辑判断？常常嵌套多个if？快来这里学习下吧，熟练掌握正则表达式会使得你的开发效率得到极大提升。

## 资源整理
* [前端知识点大百科全书](https://github.com/Wscats/Good-text-Share)
* [前端资源汇集](http://www.jianshu.com/p/c3dae0951f74)
如此之全的知识整理、资源汇集，都掌握的话你可以神挡杀神佛挡杀佛了。

## 文章

* [一劳永逸的搞定flex布局](https://juejin.im/post/58e3a5a0a0bb9f0069fc16bb)
你是否还在使用浮动布局？写各种line-height实现居中？不妨试试flexBox布局，它简单易用的写法可以轻松实现各种布局，让你的布局更快速高效。

* [Vue的数据依赖实现原理简析](https://segmentfault.com/a/1190000010014281)
主要从初始化的数据层面上分析了Vue是如何管理依赖来到达数据的动态响应。
initState的过程中，将props,computed,data等属性通过Object.defineProperty来改造其getter/setter属性，并为每一个响应式属性实例化一个observer观察者。这个observer内部dep记录了这个响应式属性的所有依赖。
当响应式属性调用setter函数时，通过dep.notify()方法去遍历所有的依赖，调用watcher.update()去完成数据的动态响应。

* [靠谱程序员必备技能——重构](https://mp.weixin.qq.com/s?__biz=MzIyNjE4NjI2Nw==&mid=2652558943&idx=1&sn=1516afcf876b9fb4a17ce048c5ade58d)
当项目变得难以维护，重构便便迫在眉睫，但很多所谓重构仅仅算是重写，随着时间推移，项目再次变得难以维护，周而复始，陷入怪圈。如何避免重构变成重写，本文给了一些很好的建议。

* [我接触过的前端数据结构与算法](https://zhuanlan.zhihu.com/p/27659059)
只要是工程师就必须学好计算机基础，只有这样才能适应计算机技术的快速发展，前端工程师更是如此。

* [Vuex 通俗版教程](https://yeaseonzhang.github.io/2017/03/16/Vuex-%E9%80%9A%E4%BF%97%E7%89%88/)
Vuex 类似 Redux 的状态管理器，用来管理Vue的所有组件状态。
一般在你开发大型单页应用（SPA），会出现多个视图组件依赖同一个状态，来自不同视图的行为需要变更同一个状态。
遇到以上情况时候，可以考虑使用Vuex，它能把组件的共享状态抽取出来，当做一个全局单例模式进行管理。这样不管你在何处改变状态，都会通知使用该状态的组件做出相应修改。

* [学习Vue.js源码](https://stffe.github.io/vue/2017/03/03/%E5%AD%A6%E4%B9%A0Vue%E6%BA%90%E7%A0%81.html)
文中介绍了vue项目目录结构和数据绑定实现，没有太深入，但可以作为初步了解。

* [GitHub —— 你不得不上的交友网站](https://segmentfault.com/a/1190000009985489#articleHeader9)
文章整理了GitHub入门，搭建发布个人博客及个人项目发布，还介绍了一些工具，插件及开源项目；内容比较丰富。

* [彻底搞清楚javascript中的require、import和export](http://meiminjun.github.io/import%E5%92%8Cexport%E7%AC%94%E8%AE%B0/)
通过介绍CMD、AMD、ES6的模块规范，来引申出平时业务中经常用到require、import和export的用法以及含义。

* [工具推荐](https://github.com/istanbuljs/nyc)
覆盖率工具 istanbul 替换为 nyc，多进程覆盖率的测试速度提升了几倍。都是同一作者的作品，后者目前活跃度高，并支持前端很多新特性。

```
$ npm i nyc --save-dev
$ ./node_modules/.bin/nyc ./node_modules/.bin/mocha
```
执行单元测试命令后，还会直观的给出代码覆盖率报告，以[Flclover](http://flcloverjs.org/)为例：
```
------------------------------------|----------|----------|----------|----------|----------------|
File                                |  % Stmts | % Branch |  % Funcs |  % Lines |Uncovered Lines |
------------------------------------|----------|----------|----------|----------|----------------|
All files                           |    79.41 |    66.67 |    61.11 |    81.82 |                |
 flclover                           |      100 |      100 |      100 |      100 |                |
  index.js                          |      100 |      100 |      100 |      100 |                |
 flclover/lib                       |    88.52 |    82.35 |    81.82 |    88.52 |                |
  application.js                    |      100 |      100 |      100 |      100 |                |
  flclover.js                       |       30 |        0 |        0 |       30 |... 13,14,17,19 |
 flclover/lib/middleware/bodyparser |      100 |      100 |      100 |      100 |                |
  index.js                          |      100 |      100 |      100 |      100 |                |
 flclover/lib/middleware/logger     |    55.56 |       50 |       50 |    55.56 |                |
  index.js                          |    55.56 |       50 |       50 |    55.56 |... 39,42,45,48 |
 flclover/lib/utils                 |    71.43 |    33.33 |        0 |    83.33 |                |
  index.js                          |    81.25 |    33.33 |        0 |      100 |           7,10 |
  logger.js                         |       40 |      100 |        0 |       40 |         4,9,13 |
------------------------------------|----------|----------|----------|----------|----------------|
```