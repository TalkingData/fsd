---
title: 大前端周刊 第一期 （本期小编：王祥）
date: 2017-06-23 11:18:25
tags: [weekly,全栈,Node]
---

## 基础

* [Promise](http://es6.ruanyifeng.com/#docs/promise)
在Javascript的单线程异步架构下，Promise会是很多异步服务的核心知识点，Node 8.X已经可以方便的将回调方式转换为Promise。

* [异步函数async](http://es6.ruanyifeng.com/#docs/async)
使用异步函数可以实现“用同步的写法，完成异步的事情”，Node 8.X已经在编译器层面对async做了优化。
* [语义化版本 2.0.0](http://semver.org/lang/zh-CN/)
玩开源项目的基础，组件发布的约定。
* [package.json规则](https://docs.npmjs.com/files/package.json)
项目的依赖列表，区别开发环境、生产环境、面向的平台和组件的规范（CMD、AMD和UMD）等。

## 单元测试工具
Web 应用中的单元测试更加重要，在 Web 产品快速迭代的时期，每个测试用例都给应用的稳定性提供了一层保障。 API 升级，测试用例可以很好地检查代码是否向下兼容。 对于各种可能的输入，一旦测试覆盖，都能明确它的输出。 代码改动后，可以通过测试结果判断代码的改动是否影响已确定的结果。

* [mocha单元测试](https://mochajs.org/)
NPM里每天有25W的下载量，同时支持Node、浏览器多平台的测试用例的执行。

* [power-assert断言库](https://www.npmjs.com/package/power-assert)
power-assert可以零学习成本，直观的展示出判断条件和结果。

```
1) Array #indexOf() should return index when the value is present:
     AssertionError: # path/to/test/mocha_node.js:10

  assert(ary.indexOf(zero) === two)
         |   |       |     |   |
         |   |       |     |   2
         |   -1      0     false
         [1,2,3]

  [number] two
  => 2
  [number] ary.indexOf(zero)
  => -1
```

## 文章

* [JavaScript专题之跟着underscore学防抖](https://github.com/mqyqingfeng/Blog/issues/22)
对防抖的原理介绍的很清晰，从最简单的实现版本一步一步讲解到实现复杂的版本。
让我对防抖有了重新的认识。

* [从前端开发看面向未来的敏捷学习法](http://www.jianshu.com/p/fd7055705c62)
授人以鱼不如授人以渔
前端技术更新速度很快，快速学习已经成了每个工程师必备技能。
除了掌握技术知识，解决问题的能力在实际项目中也很重要，文中以实际案例给出分解思路和系统敏捷学习新知识思路。

* [前端工程师做事的三重境界：我的进阶之路](https://zhuanlan.zhihu.com/p/26660510)
从程序员到工程师的进阶之路，精益求精才能称得上是工程师。作者认为这三个单词（Programmer、Developer、Enginner）对应不用的境界。

* [浏览器缓存机制剖析](http://louiszhai.github.io/2017/04/07/http-cache/)
正如文中所述“缓存一直是前端优化的主战场, 利用好缓存就成功了一半”，利用好缓存在前端优化地位中举足轻重，本文能够带领大家对浏览器缓存机制有一个初步了解。

* [vue-mixins使用注意事项和高级用法](https://www.deboy.cn/Vue-mixins-advance-tips.html)
在项目开发中经常会碰到两个组件的业务逻辑有所相似，可能共享相同的底层业务逻辑；此时需要考虑如何来合理地划分代码，即避免冗余代码，也不能过度抽象。

* [也谈JavaScript数组去重](https://www.toobug.net/article/array_unique_in_javascript.html)
去重，首先要思考什么是相等，从最初的循环，到Set集合。

* [大前端公共知识梳理：这些知识你都掌握了吗？](https://mp.weixin.qq.com/s?__biz=MzIwNjQwMzUwMQ==&mid=2247485277&idx=1&sn=82703e13febb1e7947cc18d1f57fc375&key=6b0fbfcb936d93fa91a745202d0f37bffff65fd2cba5ff2cfa25618c8d03951944ae6eb2f4db18aaf1c8893ddaeffb404684dbd7f6159925dbab9411094f960daba3c6f46c1f93d34f9a6d476104fc63&ascene=0&uin=MTQwNzQzODYwMA%3D%3D&version=12020810&nettype=WIFI&fontScale=100&pass_ticket=xJ0pJsFuIsM3Ce35cuVqghSLUWaqU91w%2FEgBgn2%2BhouemlzbFvOIXP3KmJlioe0D)
文章覆盖非常全面，所介绍基础知识、技术栈、能力、领域有很多都是目前我所欠缺的，介于此推荐给大家。。。看完最直观的感受就是自己是个假前端

* [重温ES6核心概念和基本用法](https://segmentfault.com/a/1190000009885614)
文章梳理了ES6核心概念及基础用法，推荐给大家。
