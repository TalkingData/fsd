---
title: 大前端周刊 第八期 （本期小编：耿少真）
date: 2017-08-11 14:57:34
tags: [weekly,模块,node,Vue,API设计，单元测试]
---
## 基础

* [掌握Chrome开发工具](http://www.zcfy.cc/article/mastering-chrome-developer-tools-next-level-front-end-development-techniques-3722.html?t=selection)
**熟悉Chrome开发工具的基本功能: DOM检查器、样式面板和JavaScript控制台和一些不太为人所知的特性**

* [JS函数式编程指南](https://www.gitbook.com/book/llh911001/mostly-adequate-guide-chinese/details)
**对函数式编程的目的有一个初步认识，对一个程序之所以是函数式程序的原因有一定了解**

* [HTTP协议详解](https://mp.weixin.qq.com/s/27zpNIGhVbx-on9FDs_6dw)
**Web服务器是基于HTTP（HyperText Transfer Protocol）协议实现的，所以要实现一个Web服务器就必须了解HTTP协议，本章主要介绍HTTP协议的相关知识，让我们对HTTP协议有个理性的认识。**

## 资源整理
* [编程书单](http://blog.didiaoyuan.com/2017/04/18/%E6%80%BB%E6%9C%89%E4%BD%A0%E8%A6%81%E7%9A%84%E7%BC%96%E7%A8%8B%E4%B9%A6%E5%8D%95%EF%BC%88GitHub-%EF%BC%89/)
**一些 GitHub 上不错的文章或电子书列表与大家分享。不乏有不少经典，可以收起来慢慢阅览。**

* [Web前端导航网站](http://www.alloyteam.com/nav/)
**收录了前端开发需要的大部分网站，可以快速找到自己需要的网站**

## 文章
* [彻底弄懂CommonJS和AMD/CMD](http://www.cnblogs.com/chenguangliang/p/5856701.html)
<small>*推荐人：李丽娇*</small>
经常说的CommonJS、AMD、CMD规范具体指什么？实现原理是什么？这些规范有哪些具体实现？来看这篇文章找答案。

* [使用Node.js实现文件流转存服务](https://zhuanlan.zhihu.com/p/25367269)
<small>*推荐人：李志伟*</small>
文章介绍了基于node实现分片上传大型文件，通过灵活使用Promise和递归，实现非异步模型看起来很复杂的事情。另外文章附有较为完整的单元测试，覆盖分片的缓存与切割、上传前后的md5值。

* [API设计原则](http://coolshell.cn/articles/18024.html)
<small>*推荐人：胡国伟*</small>
我们平时在编写组件或者后端接口的时候都避免不了API 设计，你的API越容易使用，那么就会有越多的人去用它。那么问题来了，怎样才能设计出优秀的 API ？本文是虽然是以`C++`为例， 其中设计原则和思考是具有普适性的，是关于API设计一篇难得的好文章

* [一道JS面试题所引发的"血案"，透过现象寻本质，再从本质看现象](https://github.com/jawil/blog/issues/3)
<small>*推荐人：张成斌*</small>
对this、执行环境、作用域等概念进行了系统的讲解。加深对于这些易混淆概念的理解。

* [karma+webpack搭建vue单元测试环境](http://www.jianshu.com/p/a515fbbdd1b2)
<small>*推荐人：耿少真*</small>
karma+webpack搭建vue单元测试环境介绍了vue单元测试环境搭建及查看源文件的测试覆盖覆盖率。
[Vue单元测试case写法](http://www.jianshu.com/p/45e8c2b26309)
测试环境搭建完成后，在此基础上vue单元测试思路介绍和case的写法。测试框架使用jasmine。

* [【源码拾遗】axios —— 极简封装的艺术](https://zhuanlan.zhihu.com/p/28396592)
<small>*推荐人：陶明*</small>
本文通过axios 功能的使用及源码分析详细说明了axios 对于功能的实现。
axios是基于Promise的方式封装，所以分析axios源码也是对Promise的深入学习。

* [Intro to Frontend Ops](https://rupl.github.io/frontend-ops/#/)
<small>*推荐人：包京京*</small>
Frontend Ops是这篇文章作者自己定义的一个概念，业界应该还没有统一这种叫法，不过文章作者的意思是，随着前端项目复杂程度的增加，需要类似于DevOps的工程化能力，来进行持续发布、自动化测试等等流程（本文是英文的材料，暂无译文）。

* [Koa 框架教程](http://www.ruanyifeng.com/blog/2017/08/koa.html)
<small>*推荐人：王祥*</small>
本文从零开始，循序渐进，教会你如何使用 Koa 写出自己的 Web 应用。每一步都有简洁易懂的示例，希望让大家一看就懂。

* [一行 JavaScript 代码的逆向工程](https://juejin.im/post/5988411251882526185d634a)
<small>*推荐人：郭俊兵*</small>
这一行代码会被渲染成一个矩阵效果，通过一次代码解读，享受理解它的过程。
`<pre id=p><script>n=setInterval("for(n+=7,i=k,P='p.\\n';i-=1/k;P+=P[i%2?(i%2*j-j+n/k^j)&1:2])j=k/i;p.innerHTML=P",k=64)</script>`

