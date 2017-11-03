---
title: 大前端周刊 第19期 （本期小编：段扬帅）
date: 2017-11-03 11:08:59
tags:
---

## Show me the code

### HTML5 桌面通知(Notification API)

HTML5新增的桌面通知API：Notification API是用于向用户推送通知消息的API。
值得注意的是，该通知不管用户在不在当前标签页都会进行推送

#### 权限

该API需要用户明确授权同意推送后，才能进行推送！
那么怎么才能知道用户有没有同意呢？

``` javascript
Notification.permission
```
返回值：granted（用户同意） 、 denied（用户拒绝） 、 default（用户还没有选择）

#### 获取权限

Notification 对象提供了requestPermission():

``` javascript
Notification.requestPermission().then(function(permission) {
    console.log(permission)  // 返回用户的选择
});
```
#### 推送

得到用户的许可后，就可以愉快的进行推送了

``` javascript
new Notification(title, options)
```

参数说明：
title:  通知的标题。 必传
options：通知的设置选项。 可选：
- dir：默认值是auto, 可以是ltr或rtl，表示提示主体内容的水平书写顺序。
- body：通知的内容。
- tag：代表通知的唯一标识，相同tag时只会打开同一个通知窗口。
- icon：要在通知中显示的图标的URL。
- data：想要和通知关联的数据。
- requireInteraction：通知保持有效不自动关闭，默认为false。
- vibrate: 通知显示时候，设备震动硬件需要的振动模式。所谓振动模式，指的是一个描述交替时间的数组，分别表示振动和不振动的毫秒数，一直交替下去,例如[200, 100, 200]表示设备振动200毫秒，然后停止100毫秒，再振动200毫秒。
- renotify: 布尔值。新通知出现的时候是否替换之前的。如果设为true，则表示替换，表示当前标记的通知只会出现一个。
- silent: 布尔值。通知出现的时候，是否要有声音。默认false, 表示无声。
- sound: 字符串。音频地址。表示通知出现要播放的声音资源。
- noscreen: 布尔值。是否不再屏幕上显示通知信息。默认false, 表示要在屏幕上显示通知内容。
- sticky: 布尔值。是否通知具有粘性，这样用户不太容易清除通知。默认false, 表示没有粘性。


#### 关闭

Notification.close() 关闭通知

#### 支持事件

onclick 点击触发
onerror 显示异常触发
onclose 消息关闭时触发
onshow  消息显示的时候触发

#### 兼容性
移动端几乎都不支持，PC端大部分都支持，IE需要14.0版本以上

## 插件推荐

- [gpu.js](https://github.com/gpujs/gpu.js/tree/develop)
gpu.js这个库会把你写的js编译成GLSL然后在GPU上执行，以达到加速的效果。并且，如果电脑不支持GPU，它还会当成普通的js执行。

## 文章推荐
- [探索nodeJS事件机制源码 打造属于自己的事件发布订阅系统](https://zhuanlan.zhihu.com/p/26300877)
本文探索并解析了nodejs的event实现和设计原理，解释了“事件发布订阅模式”，详细介绍了eventEmitter的一些核心属性和方法。另外，还基于ES6语法，DIY了一个简单的事件订阅发布系统。

- [http请求的理解](https://blog.souche.com/jie-kou-ce-shi-zhi-httpqing-qiu-de-li-jie/)
从tcp到http，从计算机网络来看一个http请求，理解前后端网络通讯

- [深入认识vue-cli：能做的不仅仅是初始化vue工程](https://segmentfault.com/a/1190000011643581?_ea=2709729)
有许多同学没有搞清楚vue-cli和vue工程之间的关系，导致没有充分发挥vue-cli的功能。在这篇文章中，我将从底层原理开始并结合几个例子，告诉大家vue-cli还能这样用

- [CSS Modules 用法教程](http://www.ruanyifeng.com/blog/2016/06/css_modules.html)
在前端模块化大行其道的今天，开发者发布的开源模块，如何避免 CSS 样式被宿主页面的样式所覆盖是非常重要的问题。CSS Modules 加入了局部作用域和模块依赖，这恰恰是网页组件最急需的功能。

- [JavaScript 中的对象拷贝](https://scotch.io/bar-talk/copying-objects-in-javascript#toc-the-naive-way-of-copying-objects)
在 JavaScript 中拷贝一个对象可能会碰到各种各样的问题，本文详细描述了各种拷贝的方法及注意点

- [Vue 2.0 的数据依赖实现原理简析](https://github.com/DDFE/DDFE-blog/issues/17)
源码解析，一步一步讲解 vue 的响应式是如何实现的，信息量比较大。

- [在js里写SQL](http://zzfe.org/#/detail/59e42c3b91d3e35ba880fd0e)
在日新月异的前端领域中，前端工程师能做的事情越来越多，前端页面可能出现一些数据逻辑复杂的页面，传统的js逻辑处理起来比较复杂，因此需要引入新的东西来简化逻辑。

- [ES6 模块系统](http://www.zcfy.cc/article/es6-modules-in-depth-4436.html?t=new)
对于ES6的模块系统，文章首先是对严格模式的一些总结，然后是对export 和 import 展开总结性的说明了各种绑定方式。

- [Vue 项目架构设计与工程化实践 ](https://github.com/berwin/Blog/issues/14)
作者详述了自己Vue搭建项目的过程：技术选型(Vue全家桶)->架构设计(不同层面的职责)->发布上线。整个过程较为详细，举例项目遇到的问题及解决方案，对于搭建项目有一定的参考价值。

- [深入探讨前端组件化开发](http://web.jobbole.com/92879/)
这几年，从陷入 “React、Vue 和 Angular 哪个性能好？”的争论，到现在的各个框架（库）的生态越来越完善，讨论性能差距已经没有价值了。而国内的前端娱乐圈，最火的就是 React 和 Vue 了，而 Angular 由于历史原因，在国内的占有率确实不高。

- [打造丝般顺滑的 H5 翻页库](http://fex.baidu.com/blog/2017/10/build-a-silky-smooth-slide-library/)
翻页组件实现起来并不难，本文在此基础上进一步尝试打造丝般顺滑的效果，各种优化手段值得学习。

- [使用Node+Koa2+Mysql搭建简易博客](http://blog.csdn.net/wclimb/article/details/77890793)
Koa2使用实例，从Koa安装到项目建立模版使用，代码很详细的项目实例。

## 招聘
TalkingData DTU 可视化团队招聘：
* 资深前端工程师

简历投递：
``` javascript
const email = 'xiang.wang#tendcloud.com'.replace('#', '@');
console.log(email);
```