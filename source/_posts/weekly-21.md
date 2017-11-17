---
title: 大前端周刊 第21期 （本期小编：李凡）
date: 2017-11-17 12:52:13
tags:
---
## Show me the code

### 关于Promise对象容易忽视的几个问题

1.resolve后的执行情况

无论是 resolve, reject，都会将函数剩余的代码执行完
``` javascript
const promise = new Promise((resolve, reject) => {
    console.log('mark 1');
    resolve('hello world');     // reject('hello world');
    console.log('mark 2');
});

promise.then(result => {
    console.log(result);
}).catch(err => {
    console.log(err);
});
```
2.调用 then 方法返回新的 Promise 对象
``` javascript
let promise1 = new Promise((resolve) => {
    resolve('Hello world')
})

let promise2 = promise1.then()

console.log(promise1 === promise2)    // false
console.log(promise1 instanceof Promise)  // true
console.log(promise2 instanceof Promise)  // true
```
3.串行执行和并行执行
- 串行执行：有一堆 Promise 对象，它们的执行顺序是固定的，前一个 promise 执行完后，后一个 promise 才开始执行，比如数据库查询，它们往往有前后的因果关系。
- 并行执行：有一堆 Promise 对象，它们的执行顺序是不固定的，没有前后因果关系，可以并发地去执行。


```javascript
//串行方式一
const datum = [];
for(let i = 0; i < 10; i++) {
    datum.push(i);
}

let serial = Promise.resolve();

for(let i of datum) {
    serial = serial.then(data => {
        console.log(data);
	return new Promise((resolve, reject) => {
	    setTimeout(() => {
		console.log(i * 200 + " ms 后执行结束");
		resolve("第 " + (i + 1) + " 个 Promise 执行结束");
	    }, i * 200);
	})	
    });
}

//串行方式二  使用reduce
const datum = [];
for(let i = 0; i < 10; i++) {
    datum.push(i);
}

datum.reduce((prev, cur) => {
    return prev.then(data => {
	console.log(data);
	return new Promise((resolve, reject) => {
	    setTimeout(() => {
		console.log(cur * 200 + " ms 后执行结束");
		resolve("第 " + (cur + 1) + " 个 Promise 执行结束");
	    }, cur * 200);
	})	
    })
}, Promise.resolve(true));
```
并行执行很好解决，在 Promise中有 all 这个函数支持, Promise.all 方法用于将多个 Promise 实例，包装成一个新的 Promise 实例。当多个 Promise 实例执行完后才去执行最后新的 Promise 实例。
```javascript
const datum = [];
for(let i = 0; i < 10; i++) {
    datum.push(i);
}

Promise.all(datum.map(i => {
    return new Promise((resolve, reject) => {
	setTimeout(() => {
	    console.log(i * 200 + " ms 后执行结束");
	    resolve("第 " + (i + 1) + " 个 Promise 执行结束");
	}, i * 200);
    })
})).then((data) => {
    console.log(data);
});

```
如果不使用 Promise.all 这个方法的话，你也可以使用像 ES7 的 async/await

```javascript
const asyncFun = async () => {
    const datum = []
    for(let i = 0; i < 10; i++) {
        datum.push(new Promise((resolve, reject) => {
            setTimeout(() => {
                console.log(i * 200 + 'ms 后执行结束')
                resolve('第 ' + (i + 1) + ' 个 Promise 执行结束')
            }, i * 200)
        }))
    }
    const result = []
    for(let promise of datum) {
        result.push(await promise)
    }
    console.log(result)
}
asyncFun()
```

4 . 结合 async/await 编写同步代码
-  async/await 函数可以帮助我们彻底摆脱回调地狱的烦恼，用一种同步的方式来编写异步函数。
- await 后面可以接数值，如果是异步请求的话可以接 Thunk 函数和 Promise 对象。

```javascript
const timeout = (ms) => {
    return new Promise((resolve) => {
        setTimeout(() => {
            resolve(ms + ' passed')
        }, ms)
    })
}

const asyncFunc =  async () => {
    const value1 = await timeout(2000)
    console.log(value1)
    const value2 = await timeout(2000)
    console.log(value2)
}

asyncFunc()
console.log('now')
```
5  .resolved 状态的 Promise 不会立即执行

```javascript
let i = 0;
Promise.resolve('resolved promise').then(() => {
    i += 2
})
console.log(i)  // 0
```


## 文章推荐
* [TypeScript 入门指南](http://www.oschina.net/question/12_72250)
  TypeScript入门指南，适合入门了解。



* [别再拿奇技淫巧搬砖了](https://juejin.im/post/5a0b29756fb9a045167cb643)
技巧性的知识大家都有掌握，使用场景及方式是否合理也是个问题。
文章总结了一些常见的编程技巧的利弊，希望对大家有所帮助。



* [抓住数据的小尾巴 - JS浮点数陷阱及解法](https://zhuanlan.zhihu.com/p/30703042?utm_medium=social&amp;utm_source=wechat_session)
推荐：众所周知，JavaScript 浮点数运算时经常遇到会 0.000000001 和 0.999999999 这样奇怪的结果，如 0.1+0.2=0.30000000000000004、1-0.9=0.09999999999999998，很多人知道这是浮点数误差问题，但具体原因就说不清楚了。本文帮你理清这背后的原理以及解决方案，还会向你解释JS中的大数危机和四则运算中会遇到的坑。



* [打造自己的JavaScript武器库](https://juejin.im/post/5a091afe6fb9a044ff30f402)
作为战斗在业务一线的前端，要想少加班，就要想办法提高工作效率。这里提一个小点，我们在业务开发过程中，经常会重复用到日期格式化、url参数转对象、浏览器类型判断、节流函数等一类函数，这些工具类函数，基本上在每个项目都会用到，为避免不同项目多次复制粘贴的麻烦，我们可以统一封装，发布到npm，以提高开发效率。



* [浏览器渲染引擎](https://juejin.im/post/59f5bbdb6fb9a0451968d851)
浏览器基础是前端知识网中的一个小分支，也是前端开发人员必须掌握的基础知识点。他贯穿着前端的整个网络体系，项目优化也是围绕着浏览器进行的。



* [美化表单的CSS高级技巧](https://www.w3cplus.com/css/advanced-css-form-styling.html)
	通常前端业务离不开表单，而其本身的UI确实不太美观，文章通过一些选择器实现常用表单的美化，相信对有定制化表单需求的小伙伴有所帮助。



* [websocket服务器监控](http://blog.fens.me/nodejs-websocket-monitor/)
	这篇文章解释了一个简单的例子，用NodeJS搭建一个服务器监控程序，核心是socket.io实现的real time通信，另外还有node.js的child_process模块来实现进程管理。从这个简单而有用的例子出发，可以去研究socket.io和child_process的深层用法。



* [Web应用程序和Git的双向同步](https://ponyfoo.com/articles/two-way-synchronization-for-a-web-app-and-git)
通过钩子函数实现数据库与git仓库之间的双向同步，当数据库发生变化时，git仓库也进行相应同步操作。

## 招聘
TalkingData DTU 可视化团队招聘：
* 资深前端工程师

简历投递：
``` javascript
const email = 'xiang.wang#tendcloud.com'.replace('#', '@');
console.log(email);
```
