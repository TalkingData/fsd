---
title: 大前端周刊 第15期 （本期小编：郭俊兵）
date: 2017-09-29 16:23:27
tags: [动画, Node, Babels, 渲染性能, this关键字, http/2升级, CSS黑魔法]
---
## Show me the code

* 对象数组排序

概念：javascript实现多维数组、对象数组排序，其实用的就是原生的sort()方法，用于对数组的元素进行排序。

语法：arr.sort(by('xx'))

- 参数介绍：
  - function, key
  使用回调函数，处理需要排序的对象key。

- 返回值
  排序以后的数组。

  针对于偶尔需要前端排序的情况，可以使用该方式。

```
  // 回调函数
  function by(name) {
    return function(o, p) {
      let a;
      let b;
      if (typeof o === 'object' && typeof p === 'object' && o && p) {
        a = o[name];
        b = p[name];
        if (a === b) {
          return 0;
        }
        if (typeof a === typeof b) {
          return a < b ? -1 : 1;
        }
        return typeof a < typeof b ? -1 : 1;
      }
    };
  }
```
  需要排序的 Array：
```
  const employees = [{
    name: 'George',
    age: 32,
    retiredate: 'March 12, 2014'
  }, {
    name: 'Edward',
    age: 17,
    retiredate: 'June 2, 2023'
  }, {
    name: 'Christine',
    age: 58,
    retiredate: 'December 20, 2036'
  }, {
    name: 'Sarah',
    age: 62,
    retiredate: 'April 30, 2020'
  }];
```
  通过 age 排序：
```
  employees.sort(by('age'));
```
  结果：
```
  [{"name":"Edward","age":17,"retiredate":"June 2, 2023"},
  {"name":"George","age":32,"retiredate":"March 12, 2014"},
  {"name":"Christine","age":58,"retiredate":"December 20, 2036"},
  {"name":"Sarah","age":62,"retiredate":"April 30, 2020"}]
```
  到这里，对象数组排序就算基本实现了。那如何实现多个键值排序呢？意思就是先是对age排序，如果age相同，再比较name。
	这时，我们可以进一步修改by函数，让其可以接受第二个参数，当主要的键值产生一个匹配的时候，另一个compare方法将被调用以决出高下:
```
  // by函数接受一个成员名字符串和一个可选的次要比较函数做为参数
  // 并返回一个可以用来包含该成员的对象数组进行排序的比较函数
  // 当o[age]和 p[age] 相等时， 次要比较函数被用来决出高下
  function by(name, minor) {
    return function(o, p) {
      let a;
      let b;
      if (o && p && typeof o === 'object' && typeof p === 'object') {
        a = o[name];
        b = p[name];
        if (a === b) {
          return typeof minor === 'function' ? minor(o, p) : 0;
        }
        if (typeof a === typeof b) {
          return a < b ? -1 : 1;
        }
        return typeof a < typeof b ? -1 : 1;
      } else {
        thro("error");
      }
    }
  }
```
  待排序数组：
```
  const employees = [{
    name: 'George',
    age: 32,
    retiredate: 'March 12, 2014'
  }, {
    name: 'Edward',
    age: 17,
    retiredate: 'June 2, 2023'
  }, {
    name: 'Christine',
    age: 32,
    retiredate: 'December 20, 2036'
  }, {
    name: 'Sarah',
    age: 62,
    retiredate: 'April 30, 2020'
  }];
  // 排序操作
  employees.sort(by('age', by('name')))
```
  结果：
```
	[{"name":"Edward","age":17,"retiredate":"June 2, 2023"},
	{"name":"George","age":32,"retiredate":"March 12, 2014"},
	{"name":"Sarah","age":32,"retiredate":"April 30, 2020"},
	{"name":"Christine","age":58,"retiredate":"December 20, 2036"}]
```

## 插件推荐
- [jsoneditor JOSN格式编辑器](https://github.com/josdejong/jsoneditor/)
  #### 安装 
```
  npm install jsoneditor
```

  #### 引入 
```
  import JSONEditor from 'jsoneditor/dist/jsoneditor';
  const container = document.getElementById('jsonEdit');
  container.innerHTML = '';
  const options = {
    mode: 'code',
  };
  const editor = new JSONEditor(container, options);
  // 添加数据
  editor.set(JSON);
  // 获取数据
  editor.get();
```

## 文章推荐

- [实现达到 60FPS 的高性能交互动画](https://mp.weixin.qq.com/s?__biz=MzAwNTAzMjcxNg==&mid=2651425040&idx=1&sn=523695a371f87ce6f4f1c003ef937f0b&chksm=80dff773b7a87e65fa93ce9f059d3b1f6af1c2115c3bf5356357f25fab730cab4f8ae67cb70d&mpshare=1&scene=1&srcid=0929ZyVAlRQeJ9EX6qEuuq5C#rd)
	对于页面优化而言，开发者往往会花大量精力在优化首屏加载，为了几毫秒锱铢必较，但忽略了页面交互动画所带来的性能问题。本文从浏览器渲染原理的角度，给出了实现60FPS交互动画的方法。

- [Node.js cluster 踩坑小结](https://zhuanlan.zhihu.com/p/27069865)
	推荐大家深入阅读这篇来自饿了么 Node 大神黄鼎恒的文章，内容深入介绍了进程与 process 对象、子进程 和 IPC ，负载实现等知识点和踩过的坑。

- [你真的会用 Babel 吗](https://juejin.im/post/59b9ffa8f265da06710d8e89)
	对于 babel 的使用，大部分同学一直停留在与 webpack 结合使用，以及在浏览器开发环境下。导致很多 babel 的包，都不清楚他们是干嘛的。本篇文章可以当个入门来读

- [JavaScript 数组的演进及其性能](http://www.zcfy.cc/article/diving-deep-into-javascript-array-8211-evolution-038-performance-void-canvas-4202.html?t=new)
[MDN JavaScript typed arrays](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Typed_arrays)
	文章通过数组与类型化数组（Typed Arrays）进行对比，从创建，插入，读取等方面进行性能比较；从而直观的介绍类型化数组的，并没有深入Typed Arrays。

- [RAIL 性能模型](http://web.jobbole.com/86941/)
	资源加载之后的性能，因为大多数用户关注的不是应用如何加载而是具体的使用。所以要快速响应用户，尤其是无线端，我们有必要了解浏览器渲染性能。

- [CSS 黑魔法小技巧，让你少写不必要的JS，代码更优雅](https://segmentfault.com/a/1190000011354975)
	[这些JavaScript编程黑科技，装逼指南，高逼格代码，让你惊叹不已](https://github.com/jawil/blog/issues/24)
	很有意思的两篇代码小技巧，几行代码实现让人惊诧的功能、效果。思路清奇，仔细阅读代码相信会沉淀不少有用的东西。

- [javascript 函数中的 this 的四种绑定形式](http://web.jobbole.com/92207/)
 	javascript中的this和函数息息相关，谈到this很多让人晕晕乎乎的抽象概念就跑出来了，这里只说最核心的一点——函数中的this总指向调用它的对象

- [怎样把网站升级到http/2](https://fed.renren.com/2017/09/23/http2/)
	为何升级http/2理由[在这里](https://fed.renren.com/2017/09/03/upgrade-to-https/)，本文是实践部分。http/2给前端优化带来了[新的机遇与挑战](https://imququ.com/post/http2-new-opportunities-and-challenges.html)，有兴趣的小伙伴可以了解下。

- [JavaScript 开发者所需要知道的 V8（一）：V8 In NodeJS](https://segmentfault.com/a/1190000007484357)
	V8做为Javascript引擎，使用范围已经越来越广泛。文中简单介绍了V8引擎在NodeJS的中运用。

## 招聘
TalkingData DTU 可视化团队招聘：
* 资深前端工程师
* 前端实习生

简历投递：
``` javascript
const email = 'xiang.wang#tendcloud.com'.replace('#', '@');
console.log(email);
```