---
title: 大前端周刊 第10期 （本期小编：王祥）
date: 2017-08-25 10:30:30
tags: [weekly,工程化实践,Vuex,Webpack,PWA,持续部署]
---
## Show me the code
### 展开运算符 (spread operator)
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
1. 使用 pandoc 将 Markdown 文件转换为 Word 文档。
``` bash
$ pandoc -f markdown -t docx front-end-engineering-practice.md -o mydoc.docx
```
2. Mac 下安装 pandoc
```
$ brew install pandoc
```

## 文章推荐
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

## 招聘
* 资深前端工程师
* 前端实习生

简历投递：xiang.wang@tendcloud.com
