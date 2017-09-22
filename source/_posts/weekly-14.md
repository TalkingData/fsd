---
title: 大前端周刊 第14期 （本期小编：陶明）
date: 2017-09-22 15:56:42
tags: [内存管理, 散点图, 正则, AR, Webpack, IOT, 虚拟DOM]
---
## Show me the code

* Set

语法：new Set([iterable])

- 参数介绍：
  - iterable
  如果传递一个可迭代对象，它的所有元素将被添加到新的 Set中。如果不指定此参数或其值为null，则新的 Set为空。

- 返回值
  一个新的Set对象。

  简单说一下为什么要用 Set，因为 Set中的值具有唯一性（划重点！！！）。
  唯一性！
  所以，我就用它来去重。
  嗯，对。
  只用来数组去重！！！

```
  const arr = [1, 2, 3, 4, 5, 5, 4, 3, 2, 0];
  const ArraySet = new Set(arr);

  Array.from(ArraySet); // [1, 2, 3, 4, 5, 0]
  [...ArraySet]; // [1, 2, 3, 4, 5, 0]

  const emoji = ['↖', '💎', '↗', '♠', '↖', '😏', '💎', '😍', '😏',];
  const emojiSet = new Set(arr);
  
  Array.from(emojiSet) // ["↖", "💎", "↗", "♠", "😏", "😍"]
  [...emojiSet] // ["↖", "💎", "↗", "♠", "😏", "😍"]
```
  只能 Array？
```
  const text = 'prototype';
  new Set(text); // Set {"p", "r", "o", "t", "y", "e"} 我是 String Set的
```
  上面说到它的返回值是一个对象
  So, 它有自己属性及方法。
```
  const arr = [1, 2, 3, 4, 5, 5, 4, 3, 2, 0];
  const mySet = new Set(arr);
  
  mySet.size; // 6 剩 6 个了
  mySet.length; // undefined
```
  都叫 'size'了，当然是它的个数啊,
  没 length（手动痴呆脸）我就试试看而已...
```
  const arr = [1, 2, 3, 4, 5, 5, 4, 3, 2, 0];
  const mySet = new Set(arr);

  /* 我要加个 10 */
  mySet.add(10) // [1, 2, 3, 4, 5, 0, 10] 加上了！

  /* 我要加个 1 */
  mySet.add(1) // [1, 2, 3, 4, 5, 0] 233 加不上！说了 Set有唯一性了！

  /* 我不要 0 了 */
  mySet.clear(0) // undefined !!!
  mySet.clear() // undefined !!!
```
  刷出来算我输...
  Set.prototype.clear()，没参数，调用就清空啦.

  当然是可以删除了，开了一个好冷的笑话（故作镇定接着写...）
```
  const arr = [1, 2, 3, 4, 5, 5, 4, 3, 2, 0];
  const mySet = new Set(arr);
  
  /* 我不要 0 了  */
  mySet.delete(0) // [1, 2, 3, 4, 5] 删掉了！

  /* 有 1 吗？ */
  mySet.has(1); // true 有的！

  /* 有 2 吗？ */
  mySet.has(2); // true 有的！

  /* 有 0 吗？ */
  mySet.has(0); // false 没有！刚才删了！
```
  其实还有几个方法，
  这里只是简单的说一下这个 Set 而已
  你以为我结束了？
  我再说最后一个！
  嗯！
  最后一个！
  我保证！
```
  /* 用 forEach 能干点什么？ */
  mySet.forEach(function(value) {
    // use value do something ...
  });
```
  OK，能力有限...

## 插件推荐

- [消息气泡拖拽插件, 基于vue实现的仿QQ消息气泡拖拽插件](https://github.com/lucefer/vue-bubble)
  #### 安装 
```
  npm install vue-bubble
```

  #### 引入 
```
  const vueBubble from 'vue-bubble'
  Vue.use(vueBubble)
```

## 文章推荐

- [JavaScript 工作原理：内存管理与常见内存泄露分析](https://segmentfault.com/a/1190000011229300)
  本系列文章皆着眼于深度解析 JavaScript 内部运行原理，而本文则重点讨论编程语言中常见的内存管理问题；并且还提出了对于处理常见的内存泄露的建议。

- [可视化基础之散点图介绍](https://antv.alipay.com/vis/doc/chart/details/scatter-plot.html)
  这篇文章介绍了散点图的科学意义，推荐大家阅读学习。可视化是前端发展的一个大方向，可视化工程师除了技术实现之外，还应该学习各种图表所能表达的科学含义。感谢蚂蚁金服体验技术部同学们，整理了一整套科学规范的可视化图表“字典”，让大家详细了解每种图表背后的含义。扩展阅读：[可视化基础](https://antv.alipay.com/vis/doc/chart/classify/compare.html)

- [JS正则表达式完整教程](https://juejin.im/post/5965943ff265da6c30653879)
  非常详细的介绍了JS中和正则相关的知识，文章很长，适合慢慢研读

- [webpack：从入门到真实项目配置](https://juejin.im/post/59bb37fa6fb9a00a554f89d2)
  文章主要介绍webpack配置，由简入繁、逐步优化，从简单的打包为一个bundle到分离代码、抽离共同代码、按需加载代码、自动刷新，每一步都非常详细，适合初学者快速入门。

- [AR.js 初探](https://zhuanlan.zhihu.com/p/26364493)
  AR技术（增强现实技术Augmented Reality，简称 AR），AR技术在Native中已经兴起了，并且市场上有许多成功的APP，但是对于JavaScript怎么来玩转AR呢？下面我来简单的给大家演示两个不同版本，不同场景的AR小例子。

- [史上最全面、最透彻的BFC原理剖析](https://github.com/zuopf769/notebook/blob/master/fe/BFC%E5%8E%9F%E7%90%86%E5%89%96%E6%9E%90/README.md)
  介绍FC的概念是什么； BFC的约束规则；咋样才能触发生成新的BFC；BFC在布局中的应用：防止margin重叠(塌陷,以最大的为准)； 清除内部浮动；自适应两（多）栏布局。 

- [JS遇上IOT](https://zhuanlan.zhihu.com/p/29137921)
  IOT是 Internet of Things 的缩写，字面翻译是“物体组成的因特网”，准确的翻译应该为“物联网”。凡是可以用 JavaScript 来写的应用，最终都会用 JavaScript ——Atwood 定律。逃不出这个定律，JavaScript 也能用于物联网开发了。本文介绍了使用 JavaScript 在 ruff 开发平台上的小实例，有树莓派的小伙伴可以尝试把玩一下。

- [上手 Webpack ? 这篇就够了！](https://segmentfault.com/a/1190000010921801)
  文章系统的概述了 Webpack 从安装到配置以及插件等等；讲述的还是比较全面。对于使用 Webpack 来说，完全可以说是够用。

- [实现一个简单的虚拟DOM](http://www.cnblogs.com/giggle/p/7538533.html)
  现在的流行框架，无论React还是Vue，都采用虚拟DOM。文中介绍了虚拟DOM的实现原理，能帮助更好理解双向绑定实现。

## 招聘
TalkingData DTU 可视化团队招聘：
* 资深前端工程师
* 前端实习生

简历投递：
``` javascript
const email = 'xiang.wang#tendcloud.com'.replace('#', '@');
console.log(email);
```
