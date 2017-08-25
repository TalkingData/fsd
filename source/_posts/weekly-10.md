---
title: 大前端周刊 第10期 （本期小编：王祥）
date: 2017-08-25 10:30:30
tags: [weekly,工程化实践,Vuex,Webpack,PWA,持续部署]
---
## Show me the code
ES 6 中引入了很多让代码看起来更简洁的新特性，比如展开运算符 (spread operator)。下面的三段代码，展示了 ES6 更简洁的对象拷贝、数组复制和可变参数的写法。

* 对象拷贝

```javascript
// very bad
const original = { a: 1, b: 2 };
const copy = Object.assign(original, { c: 3 }); // this mutates `original` ಠ_ಠ
delete copy.a; // so does this

// bad
const original = { a: 1, b: 2 };
const copy = Object.assign({}, original, { c: 3 }); // copy => { a: 1, b: 2, c: 3 }

// good
const original = { a: 1, b: 2 };
const copy = { ...original, c: 3 }; // copy => { a: 1, b: 2, c: 3 }

const { a, ...noA } = copy; // noA => { b: 2, c: 3 }
```

* 数组复制 (copy arrays)

```javascript
// bad
const len = items.length;
const itemsCopy = [];
let i;

for (i = 0; i < len; i += 1) {
  itemsCopy[i] = items[i];
}

// good
const itemsCopy = [...items];
```

* 可变函数 (variadic function)

```javascript
// bad
const x = [1, 2, 3, 4, 5];
console.log.apply(console, x);

// good
const x = [1, 2, 3, 4, 5];
console.log(...x);

// bad
new (Function.prototype.bind.apply(Date, [null, 2016, 8, 5]));

// good
new Date(...[2016, 8, 5]);
```

## 工具和模块
推荐一个 Markdown 生成 Word 文档工具 pandoc。

1. 使用 pandoc 将 Markdown 文件转换为 Word 文档。
``` bash
$ pandoc -f markdown -t docx front-end-engineering-practice.md -o mydoc.docx
```
2. 安装 pandoc ( Mac )
``` bash
$ brew install pandoc
```

## 文章推荐
* [10 个基于 JavaScript 的机器学习实例](https://zhuanlan.zhihu.com/p/26709518)

虽然，大多数 JavaScript 机器学习库都是“新轮子”，有的甚至还在研发中，但并不会影响你的使用。在这篇文章中，我们将与你分享这些库，以及一些很酷的 AI Web 应用程序实例，帮助你开启机器学习之旅。

* [通俗大白话来理解TCP协议的三次握手和四次分手](https://github.com/jawil/blog/issues/14)

前端工程师也需要了解HTTP方面的一些知识，本篇文章用通俗易懂的方式讲解了平时经常听到的三次握手和四次分手究竟是什么。

* [测试框架 Mocha 实例教程](http://www.ruanyifeng.com/blog/2015/12/a-mocha-tutorial-of-examples.html)

Mocha 是目前最流行的测试框架之一，支持浏览器端和 Node 端的单元测试。这篇文章非常全面地介绍如何使用Mocha，让你轻松上手。
* [前后端分离的思考与实践](https://www.kancloud.cn/kancloud/midway/48192)

本文是阿里某前端团队，在探索一套基于NodeJS的前后端分离方案的过程中，对于前后端分离的一些认识以及思考。

* Mac [Charles 从入门到精通](http://blog.devtang.com/2015/11/14/charles-introduction/)
  PC [Fiddler 抓包工具总结](http://blog.csdn.net/qq_21445563/article/details/51017605)

在PC Web端开发的时候，我们能很方便的从浏览器开发者工具里进行网络接口调试。
在移动端开发是面对这样的需求，我们可以通过抓包工具来解决这个问题。
在Mac系统常用的抓包工具是Charles，Windows系统中常用的抓包工具是Fiddler。
下面的文章分别对Charles和Fiddler进行介绍，并图文显示了使用方法。

* [微信小程序开发教程](https://github.com/zce/weapp-demo/tree/tutorial)

由易到难介绍小程序开发的流程，讲解比较层次化，比较细致，可以让人很快进行上手开发

* [JavaScript Error 指南](https://github.com/Jocs/jocs.github.io/issues/1)

深度的剖析了错误信息和追溯栈，从错误捕获、剖析追溯栈、不同浏览器对于追溯栈格式上的差异等等，讲解相当详细也很透彻。

* [浏览器是怎么看闭包的](http://ifanqi.me/2017/07/25/you-can-understand-closure/)

关于闭包的解释有很多，很多只是从“行”上去解读，理解 JavaScript 闭包绕不开一个问题：闭包是如何实现变量保留在内存中呢？这涉及到浏览器对内存的分配与回收，本文从这个点展开图文详实的解读。拓展阅读：[可视化分析js的内存分配与回收](http://ifanqi.me/2017/07/28/js-variable-memory/)。

* [剖析Promise内部结构](https://github.com/xieranmaya/blog/issues/3)

一步一步实现一个完整的、能通过所有Test case的Promise类。文章由构造简单的promise对象开始，逐步完善逻辑。抛出问题，介绍思路，给出代码示例，比较清晰合理。自己实现已有的轮子，对于编码能力提升还是很有帮助的。

## 招聘
TalkingData DTU 可视化团队招聘：
* 资深前端工程师
* 前端实习生

简历投递：
``` javascript
const email = 'xiang.wang#tendcloud.com'.replace('#', '@');
console.log(email);
```
