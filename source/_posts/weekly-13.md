---
title: 大前端周刊 第13期 （本期小编：李丽娇）
date: 2017-09-15 14:55:47
tags: [weekly,Trackingjs,flex,postman,神经网络,DOM,Nodejs,Web Worker,GitHub插件,人脸识别,流体排版]
---
## Show me the code

* 剩余参数

概念：剩余参数（rest parameter）语法允许我们将一个不定数量的参数表示为一个数组。
使用场景：在不确定参数个数的函数中，设置部分行参。
语法：
```
function(a, b, ...restArgs) {
  // ...
}
```
示例：
```
function multiply(multiplier, ...theArgs) {
  return theArgs.map(function (element) {
    return multiplier * element;
  });
}

var arr = multiply(2, 1, 2, 3); 
console.log(arr);  // [2, 4, 6]
```
说明：
剩余参数和 arguments 对象的区别：
1. 剩余参数只包含那些没有对应形参的实参，而 arguments 对象包含了传给函数的所有实参。
2. arguments 对象不是一个真实的数组,而剩余参数是真实的 Array实例，也就是说你能够在它上面直接使用所有的数组方法，比如 sort，map，forEach，pop。
3. arguments 对象对象还有一些附加的属性 (比如callee属性)。


* 逗号操作符

概念：逗号操作符  对它的每个操作数求值（从左到右），并返回最后一个操作数的值。
语法：expr1, expr2, expr3...
示例：
```
function a(num) {
  console.log(num);
}

function b(num) {
  console.log(num * 2);
}

a(1), b(1); // 1  2
b(1), a(1); // 2  1
```
小结：
逗号表达式最常用的地方是是用一句代码定义多个变量的场景。在许多大厂的源码中也被用在如上示例的函数调用。


## 解决方案

* Trackingjs

js实现人脸识别，看这里：[https://trackingjs.com](https://trackingjs.com/)，文章推荐板块中有成功的实践案例。

* 图片渐进式加载

需求：在网速不好的情况下，网站上的某张图片用上向下一点点加载，用户体现不友好。希望先显示整张图片然后渐渐变清晰。
方案：使用渐进式加载的图片，详情见文章：[渐进式jpeg(progressive jpeg)图片](http://www.zhangxinxu.com/wordpress/2013/01/progressive-jpeg-image-and-so-on/)。


* Flex布局

自从有了flex布局，处女座的设计师再也不用担心内容没有中间对其或上下对齐了。图文详解flex语法，戳下文：[Flex 布局教程－语法篇](http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html)

## 工具和模块

作为前端童鞋，平时开发免不了和接口打交道，拿到接口后需要测试一下接口返回是否正常，这时最后有一款支持各种请求方式的模拟Http请求工具。现在来介绍一些一款解决这个问题的工具－Postman，Postman支持各种请求方式，支持添加各个请求头参数。对写接口或用接口的同学来说都是利器。

1. 官网：[https://www.getpostman.com/](https://www.getpostman.com/)

2. 推荐文章：[Postman用法简介](http://blog.csdn.net/flowerspring/article/details/52774399)


## 文章推荐

- [面向 Web 开发者的 VR 指南](https://www.smashingmagazine.com/2017/09/guide-virtual-reality-web-developers/?utm_source=frontendfocus&utm_medium=email)
  近日来，越来越多的浏览器添加了对于 VR 特性的支持，本文即是盘点下目前浏览器中 VR 技术发展的现状，并且对可用的 WebVR 相关 API 进行简要介绍。

- [深入浅出基于“依赖收集”的响应式原理](https://segmentfault.com/a/1190000011153487)
  文章很透彻的解析了对于使用Object.defineProperty()实现的响应式原理；从一个简单的实例逐步分析响应式原理的具体思路。讲解响应式原理的文章很多，这篇还是很形象的。

- [30 行 JavaScript 代码搭建神经网络](https://zhuanlan.zhihu.com/p/28653993)
  数据科学部的同学推荐的一篇神经网络入门实践文章，这篇文章图文并茂的介绍了神经网络的基础知识：神经元、神经网络等。深入阅读：[神经网络入门](http://www.ruanyifeng.com/blog/2017/07/neural-network.html)

- [深入浅出DOM基础——《DOM探索之基础详解篇》学习笔记](https://github.com/jawil/blog/issues/9)
  文章稍长，本文只论述DOM基础概念，不涉及DOM的一些事件原理机制，页面元素的操作和常用API的讲解以及兼容性事项，所以概念性东西比较多，稍微有点抽象。

- [编写可维护代码之“中间件模式”](https://zhuanlan.zhihu.com/p/26063036)
  中间件可以介入请求和相应的处理,是一个轻量级的模块,每个中间负责完成某个特定的功能。

- [当我们学习 Node.js 时，我们在学习什么？](http://mp.weixin.qq.com/s?__biz=MzIyMjYyMzg3MA==&mid=2247484289&idx=1&sn=9e7f6c0c5e6707c8b3d0a73b36bc00c1&chksm=e82be290df5c6b86e2be66f2eea6ee88be1449c3b40d8ebf40932798f95e651fbaf49ca698d0&mpshare=1&scene=1&srcid=0727KaC7tg9V5Sa1mhiVeInx#rd)
  大家都说学 Node.js 学 Node.js，到底是学它的什么呢？是学 JavaScript 这门语言，还是学 Node.js 的 API？还是学 Node.js 各种三方库？

- [石墨表格之 Web Worker 应用实战](https://zhuanlan.zhihu.com/p/29165800)
  JavaScript 执行是单线程的，如运行 CPU 密集型任务会阻塞线程，此时浏览器会被卡住。解决该问题的办法之一就是引入Web Worker。Web Worker 为前端带来了后台计算的能力，可以实现主 UI 线程与复杂计运算线程的分离，从而极大减轻了因计算量大而造成 UI 阻塞而出现的界面渲染卡、掉帧的情况，从而更大程度地的提高我们的页面性能。

- [那些你不能错过的 GitHub 插件和工具](https://juejin.im/post/59ade28051882538fd72fa2c)
  既然 GitHub 这么重要，又被我们使用得这么频繁，那关于 GitHub 的一些优秀浏览器插件或者其他工具，我们就一定不可错过啦。本文就来整理一些，都是我平常使用最得心应手的东西，全都倾力推荐出来，绝对干货！

- [纯前端实现人脸识别-提取-合成](http://refined-x.com/2017/09/06/%E7%BA%AF%E5%89%8D%E7%AB%AF%E5%AE%9E%E7%8E%B0%E4%BA%BA%E8%84%B8%E8%AF%86%E5%88%AB-%E6%8F%90%E5%8F%96-%E5%90%88%E6%88%90/)
  前段时间火遍朋友圈的军装照竟然是用纯前段实现的！
  实现原理已在文中揭秘，速度get起来～

- [实现精准的流体排版原理](http://www.w3cplus.com/css/css-polyfluidsizing-using-calc-vw-breakpoints-and-linear-equations.html)
  文章介绍了如何实现精准的流式排版。其中原理非常的简单，通过CSS的Viewport单位和calc()配合一些数学公式，较为精准的实现随着视窗改变，能较为精准的改变font-size的大小，甚至只要是带有长度单位的属性都可以通过这样方式，达到精准的值。


## 招聘
TalkingData DTU 可视化团队招聘：
* 资深前端工程师
* 前端实习生

简历投递：
``` javascript
const email = 'xiang.wang#tendcloud.com'.replace('#', '@');
console.log(email);
```
