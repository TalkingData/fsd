---
title: 大前端周刊 第六期 （本期小编：郭俊兵）
date: 2017-07-28 12:09:40
tags: [weekly,Vuex,node,WebSocket,http,Vue,iView,Git]
---

## 基础
* [CSS 样式书写规范](https://mp.weixin.qq.com/s?__biz=MzAxODE2MjM1MA==&mid=2651552360&idx=1&sn=8d2bc092405fc23379a786a6b7a36274&chksm=8025ada9b75224bfd372ce168cb0f9cb6959255e2a7e94556eacea5d1d8e4b559dd494704ae5&mpshare=1&scene=1&srcid=0720bFFOVROJ90Pe2ZutzpQz#rd)
**不同的规范都有各自的长处与缺陷，对待所谓的规范最好的方式不是人云亦云，拿来就用，而是应该结合实际情况及需求，取长补短，取其精华去其糟粕。**

* [bfc初探](https://segmentfault.com/a/1190000010150841)
**bfc全称是块级格式化上下文（block formating context），是web可视化css渲染的一部分，它是块级盒子的布局发生，浮动互相交互的部分。**

* [es6精简学习](https://segmentfault.com/a/1190000010279009)
**秉着二八原则，掌握好常用的，有用的这个可以让我们快速起飞**

## 文章
* [推荐一个Vuex的介绍文章](https://github.com/chenbin92/blog/issues/1)
<small>*推荐人：张成斌*</small>
使用Vue做项目时，Vuex的使用与否和怎么使用始终是回避不了的一个问题。这篇文章或许能给你一些灵感。

* [当我们学习 Node.js 时，我们在学习什么？](https://mp.weixin.qq.com/s?__biz=MzIyMjYyMzg3MA==&mid=2247484289&idx=1&sn=9e7f6c0c5e6707c8b3d0a73b36bc00c1&chksm=e82be290df5c6b86e2be66f2eea6ee88be1449c3b40d8ebf40932798f95e651fbaf49ca698d0&mpshare=1&scene=1&srcid=0728VrhaVGLU4L9ednVFlmev&pass_ticket=UuoqCxRu07cu1Iw3Eo8nDcUi6ufOxbjgwdd0cRPXNFEztRXx6J2qpa2gAXxKir5f#rd)
<small>*推荐人：包京京*</small>
大家都说学 Node.js 学 Node.js，到底是学它的什么呢？是学 JavaScript 这门语言，还是学 Node.js 的 API？还是学 Node.js 各种三方库？

* [推荐一篇关于WebSocket 的教程](http://www.ruanyifeng.com/blog/2017/05/websocket.html)
<small>*推荐人：陶明*</small>
文章介绍了WebSocket 的特性及与HTTP对比在服务器推送上的优势，通过一个简单的示例介绍了WebSocket 部分API。

* [推荐一篇介绍git工作流程的文章](http://www.cnblogs.com/cnblogsfans/p/5075073.html)
<small>*推荐人：李丽娇*</small>
git成为现在最火的代码管理工具，文中详细介绍了git在团队中的使用流程，这种思路在团队协作中很是受用。同时文中介绍了gitflow使用的方法。

* [理解 async/await](https://juejin.im/post/596e142d5188254b532ce2da)
<small>*推荐人：耿少真*</small>
async 函数是 Generator 函数的语法糖。使用 关键字 async 来表示，在函数内部使用 await 来表示异步。

* [http协议简介](http://www.jianshu.com/p/80e25cb1d81a)
<small>*推荐人：郭俊兵*</small>
大致了解下http协议相关内容，有利于了解前端开发时，调用后台接口，请求做了什么。

* [Vue2.0 源码阅读：响应式原理](http://zhouweicsu.github.io/blog/2017/03/07/vue-2-0-reactivity/)
<small>*推荐人：李志伟*</small>
文章深入Vue源码，详细地解析了响应式原理。其原理大致可总结为：当数据发生改变后，相应的 setter 函数被触发，然后执行 notify 函数通知订阅者（Watcher）去更新相关视图，也会对新的数据重新 observe，更新相关的依赖关系。

* [HTTP/2 Server Push 详解(原文)](https://www.smashingmagazine.com/2017/04/guide-http2-server-push/)
<small>*推荐人：胡国伟*</small>
Server Push可以将静态资源推送给客户端，实现多路复用，是HTTP/2众多协议优化中最令人振奋的特性，它大大降低了网络延迟对性能的影响。
##### 翻译：
  - [HTTP/2 Server Push 详解（上）](http://www.alloyteam.com/2017/04/guide-http2-server-push-part1/)
  - [HTTP/2 Server Push 详解（下）](http://www.alloyteam.com/2017/04/guide-http2-server-push-part2/)

* [深入vue2.0底层思想–模板渲染](http://mp.weixin.qq.com/s/L5VK5v3fmzdjLdT6Z6w-rA)
<small>*推荐人：王俐*</small>
Vue 2.0 中模板渲染与 Vue 1.0的区别，1.0 中采用的 DocumentFragment （想了解可以观看这篇文章），而 2.0 中借鉴 React 的 Virtual DOM。基于 Virtual DOM，2.0 还可以支持服务端渲染（SSR），也支持 JSX 语法。

* [iView 一周年了，同时发布了 2.0 正式版](https://zhuanlan.zhihu.com/p/28090879)
<small>*推荐人：王祥*</small>
一周年，两个大版本，很值得称赞的成绩！能跟梁灏这样优秀的前端生态贡献者共事，我感到非常荣幸！
正如标题所言，2.0正式版将会是一个全新的开始，她将随着Vue社区的进步而快速迭代。
期待vue社区和iView能有更好的发展，iView不会止于组件库，更期待iView deign、iView mobile…和更多优秀的开发者参与到开源生态的共建！