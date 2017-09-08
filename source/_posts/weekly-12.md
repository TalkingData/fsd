---
title: 大前端周刊 第12期 （本期小编：李志伟）
date: 2017-09-08 14:55:47
tags: [weekly,webpack,koa,web安全,ES6,http]
---
## Show me the code

* 回调地狱

需求：异步读取多个文件，等到所有文件读取完毕执行特定操作。
简单实现：
```javascript
// bad
fs.readFile('./config/test.txt'), (err, data) => {
  if (err) throw err
    fs.readFile('./config/test1.txt'), (err, data1) => {
      if (err) throw err
      fs.readFile('./config/test2.txt'), (err, data2) => {
        if (err) throw err
        fs.readFile('./config/test3.txt'), (err, data3) => {
          if (err) throw err
          console.log('success');
        }
      }
    }
}

// good
function asyncReadFile (filePath, options) {
  return new Promise((resolve, reject) => {
    fs.readFile(filePath, options, (err, data) => {
      if (err) reject(err);
      resolve(data);
    });
  });
}

asyncReadFile('./config/test.txt').then(data => {
  return asyncReadFile('./config/test1.txt');
}).then(data => {
  return asyncReadFile('./config/test2.txt');
}).then(data => {
  return asyncReadFile('./config/test3.txt');
});
```

小结：Promise 是一种对异步操作的封装，在异步操作执行成功或者失败时执行指定方法。将横向的异步调用转换为纵向，因此更符合人类的思维方式。

* async和await

小小面试题：每隔一秒输出一个数字，顺序是：0 -> 1 -> 2 -> 3 -> 4 -> 5

简单实现：
```javascript
// 你首先想到的可能是这样
for (var i = 0; i < 5; i++) {
  (function(j) {  // j = i
    setTimeout(function() {
      console.log(new Date, j);
    }, 1000);
  })(i);
}
console.log(new Date, i);

// 利用es7的async和await 你还可以这样
const sleep = (timeountMS) => new Promise((resolve) => {
  setTimeout(resolve, timeountMS);
});

(async () => {  // 声明即执行的 async 函数表达式
  for (var i = 0; i < 5; i++) {
    await sleep(1000);
    console.log(new Date, i);
  }

  await sleep(1000);
  console.log(new Date, i);
})();
```

## 工具和模块

推荐简单易用的git客户端管理工具——Source Tree，支持创建、克隆、提交、push、pull 和合并等操作，其最大优点是拥有可视化界面，大大简化了开发者与代码库之间的Git操作方式，这对于那些不熟悉Git命令的开发者来说非常实用。

1. 官网：https://www.sourcetreeapp.com/

2. git学习教程：https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000


## 文章推荐

- [从攻击看防御-前端视野下的web安全思考](https://mp.weixin.qq.com/s/mblUhRMgyWUBhtIOaN6bGg)
  文章基于笔者对自身业务的web安全梳理，引起对web安全的一定思考。因其岗位视野以web前端为主，在对web安全的思考上，难免会有一定的局限性，故题目加上了“前端视野下”这样的修饰词。

- [高性能滚动 scroll 及页面渲染优化](http://www.cnblogs.com/coco1s/p/5499469.html)
  本文算是对上一期关于函数节流与防抖的实际场景中的实践，阅读本文以助于更好好的理解函数节流与防抖，并且本文也提供了一些其他的优化思路。

- [基于koajs的前后端分离实践](http://cnodejs.org/topic/57b062ed144011da12ff4183)
  要实现前后端分离框架，无非要满足这样几点：
  更便捷地创建路由、更高效地代理数据请求、更灵活地环境部署

- [深入理解CSS时序函数](https://segmentfault.com/a/1190000011019534)
  本文非常详细的介绍制作动画时所使用的时序函数，对于动画的实现有详细的demo和说明。总之对于CSS动画来说，还是要看大家怎么玩这些属性了。

- [Webpack 的静态资源持久缓存](https://mp.weixin.qq.com/s?__biz=MjM5MTA1MjAxMQ==&mid=2651225513&idx=1&sn=d247881a71f06e75478611e40b3d4e01&chksm=bd49a42d8a3e2d3bc783fc1b75672b3e2069b48c1add29f64dd626b0b8d4c5c6c1bdb09e2565&mpshare=1&scene=1&srcid=09081NPEMSgj7Z8J7G4807ps#rd)
  代码每次更新->服务器重新部署->客户端重新下载资源，显然低效。所以这就是浏览器会缓存静态资源的原因，但存在缺陷：文件不修改文件名，浏览器会认为没有更新，就会使用缓存中的版本。文章介绍webpack如何配置以开启静态资源的持久缓存，内置详细代码示例，易懂易用。

- [js 深拷贝 vs 浅拷贝](https://juejin.im/post/59ac1c4ef265da248e75892b)
  主要讲一下 js 的基本数据类型以及一些堆和栈的知识和什么是深拷贝、什么是浅拷贝、深拷贝与浅拷贝的区别，以及怎么进行深拷贝和怎么进行浅拷贝。

- [关于HTTP协议](http://www.jianshu.com/p/80e25cb1d81a)
  http协议作为连接浏览器和服务器之间的协议，有着重要的作用，为前端开发必了解内容之一。
  下文介绍了http的概要，偏理论，可作为了解。

- [前端校招面试该考察什么？](https://zhuanlan.zhihu.com/p/29010060)
  文章总结了腾讯的校招流程和校招（实习生）对候选人技能的侧重方面。除了招聘，文章还对前端工程师的技术栈做了非常全面的总结。

## 招聘
TalkingData DTU 可视化团队招聘：
* 资深前端工程师
* 前端实习生

简历投递：
``` javascript
const email = 'xiang.wang#tendcloud.com'.replace('#', '@');
console.log(email);
```
