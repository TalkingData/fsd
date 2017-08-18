---
title: 大前端周刊 第九期 （本期小编：包京京）
date: 2017-08-18 14:57:34
tags: [weekly,工程化实践,Vuex,Webpack,PWA,持续部署]
---
## 基础

* [javascript数据结构](http://blog.benoitvallon.com/data-structures-in-javascript/data-structures-in-javascript/)
**用javascript创建并分析各种常见数据结构**

* [理解Service Worker](https://mp.weixin.qq.com/s?__biz=MjM5MTA1MjAxMQ==&mid=2651226809&idx=1&sn=514ca88902bc91840f363348d6c86c39&chksm=bd495b3d8a3ed22bcf78801f96ae5c8d9555792d599004a7dc47a5a528185b9734f78af565fb&mpshare=1&scene=1&srcid=08182YSPaUr4JxGj4iID40gs&pass_ticket=0Et24OmYtRSLgA6Geno1MGBk5RujsQrVbaq%2FwZJ%2BzwtD%2F%2FbnV8lCXfDaw3Z5FpPr#rd)
**PWA是最近前端最火热的一个概念之一，Service Worker是支持PWA的核心技术之一**

* [常见排序算法之JavaScript实现](https://mp.weixin.qq.com/s?__biz=MjM5MTA1MjAxMQ==&mid=2651226816&idx=1&sn=5c2de943a3ff61de10466bfe21f973c2&chksm=bd495b448a3ed2529d674d66eab367d3b2c9c1516f70206ea36aaa5439703288168a6305d48f&mpshare=1&scene=1&srcid=0818znt16EAbHf0IGrXO1guY&pass_ticket=0Et24OmYtRSLgA6Geno1MGBk5RujsQrVbaq%2FwZJ%2BzwtD%2F%2FbnV8lCXfDaw3Z5FpPr#rd)
**排序算法是基础算法。本文用javascript和算法可视化工具将各种排序算法实现了一遍**


## 文章
* [饿了么的 PWA 升级实践](https://zhuanlan.zhihu.com/p/27853228)
<small>*推荐人: 胡国伟*</small>
饿了吗本次分享了基于 vue.js 的升级实践，踩坑跳坑的过程非常精彩。阅读完本文之余也可了解下Lavas：百度推出的基于 Vue 的 PWA 解决方案，其号称帮助开发者快速搭建 PWA 应用，解决接入 PWA 的各种问题。

* [Vuex框架原理与源码分析](https://tech.meituan.com/vuex-code-analysis.html)
<small>*推荐人：李志伟*</small>
文章首先抛出5个核心问题，然后介绍各模块核心流程，结合图解、代码示例更利于理解。理清store构造方法你也就大致明白Vuex的实现了。

* [每个JavaScript开发者都该懂的Unicode](https://mp.weixin.qq.com/s?__biz=MzAxODE2MjM1MA==&mid=2651552440&idx=1&sn=01bdb132ed0383a47993d711120b4283&chksm=8025ad79b752246fef6761482dbace0d9899ac00982a238063749400e4b0aed38140005ac869&mpshare=1&scene=1&srcid=0809B7Mm0d6x7DCLtBzpQKer#)
<small>*推荐人：郭俊兵*</small>
如果你觉得理解Unicode很难，那么是时候来面对它了！其实它没你想的那么难。让我们进入抽象概念、字符、星光平面(辅助平面)和代理对的世界。

* [Webpack 性能优化 （一）](http://code.oneapm.com/javascript/2015/07/07/webpack_performance_1/)
<small>*推荐人：陶明*</small>
文章通过项目打包场景，介绍了 resolve.alias 即利用别名做重定向的方法，在此基础上，配合module.noParse 忽略对某些模块的解析可以进一步加快速度。

* [分享一篇介绍JS调试技巧的文章](http://web.jobbole.com/85503/)
<small>*推荐人：李丽娇*</small>
据说程序员不是在改bug就是在写bug的路上，由此可见调试问题这个技能的重要性。文中介绍了多种JS的调试工具和方法，并配有GIF图演示。快GET起来吧！

* [Koa2进阶学习笔记](https://chenshenhai.github.io/koa2-note/)
<small>*推荐人：耿少真*</small>
基于async/await实现中间体系的koa2框架将会是是node.js web开发方向大势所趋的普及框架。基于generator/yield的koa1将会逐渐被koa2替代，毕竟使用co.js来处理generator是一种过渡的方式，虽然有其特定的应用场景，但是用async/await会更加优雅地实现同步写法。

* [前端开发持续集成/持续部署(CI/CD)实例](http://annn.me/frontend-ci-cd/)
<small>*推荐人：包京京*</small>
近几年，前端项目也引入了编译，构建，单元测试等现代软件工程化的标准环节。这样大提高了前端的开发效率和业务交付能力。在项目部署阶段，我们还需要引入 CI / CD 等现代化的软件开发实践，来减少风险，自动化重复操作，节省我们的时间。本文主要分享一下如何基于 gitlab 、 jenkins 让 CI/CD 跑起来。

* [滴滴 webapp 5.0 Vue 2.0 重构经验分享](https://github.com/DDFE/DDFE-blog/issues/13)
<small>*推荐人：张成斌*</small>
滴滴的 webapp 是运行在微信、支付宝、手 Q 以及其它第三方渠道的打车软件。借着产品层面的功能和视觉升级，我们用 Vue 2.0 对它进行了一次技术重构；本文即是本次重构中的经验分享。

* [前端工程化实践](http://wxnet.me/2017/08/18/%E5%89%8D%E7%AB%AF%E5%B7%A5%E7%A8%8B%E5%8C%96%E5%AE%9E%E8%B7%B5/)
<small>*推荐人：王祥*</small>
第一篇原创文章，总结了TalkingData DTU可视化团队，在2017年上半年的实践和尝试。内容包括git工作流、代码规范和大前端的目标确定，总结过往，才能更好的迎接未来。


