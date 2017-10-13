---
title: 大前端周刊 第16期 （本期小编：张成斌）
date: 2017-10-13 10:24:12
tags:
---

## Show me the code

### ES6中的`class`语法

JavaScript 语言中，生成实例对象的传统方法是通过构造函数。这种写法跟传统的面向对象语言（比如 C++ 和 Java）差异很大。ES6 提供了更接近传统语言的写法，引入了 Class（类）这个概念，作为对象的模板。通过class关键字，可以定义类。基本上，ES6 的class可以看作只是一个语法糖，它的绝大部分功能，ES5 都可以做到，新的class写法只是让对象原型的写法更加清晰、更像面向对象编程的语法而已。

#### Class Definition

ES6语法

``` javascript
class Shape {
    constructor (id, x, y) {
        this.id = id;
        this.move(x, y);
    }
    move (x, y) {
        this.x = x;
        this.y = y;
    }
}
```

ES5语法
``` javascript
var Shape = function (id, x, y) {
    this.id = id;
    this.move(x, y);
};
Shape.prototype.move = function (x, y) {
    this.x = x;
    this.y = y;
};
```

上面ES6代码定义了一个“类”，可以看到里面有一个constructor方法，这就是构造方法，而this关键字则代表实例对象。也就是说，ES5 的构造函数Shape，对应 ES6 的Shape类的构造方法。Shape类除了构造方法，还定义了一个move方法。注意，定义“类”的方法的时候，前面不需要加上function这个关键字，直接把函数定义放进去了就可以了。另外，方法之间不需要逗号分隔，加了会报错。

#### Class Inheritance

ES6语法

``` javascript
class Shape {
    constructor (id, x, y) {
        this.id = id;
        this.move(x, y);
    }
    move (x, y) {
        this.x = x;
        this.y = y;
    }
}
class Rectangle extends Shape {
    constructor (id, x, y, width, height) {
        super(id, x, y);
        this.width  = width;
        this.height = height;
    }
}
class Circle extends Shape {
    constructor (id, x, y, radius) {
        super(id, x, y);
        this.radius = radius;
    }
}
```

ES5语法
``` javascript
var Shape = function (id, x, y) {
    this.id = id;
    this.move(x, y);
};
Shape.prototype.move = function (x, y) {
    this.x = x;
    this.y = y;
};
var Rectangle = function (id, x, y, width, height) {
    Shape.call(this, id, x, y);
    this.width  = width;
    this.height = height;
};
Rectangle.prototype = Object.create(Shape.prototype);
Rectangle.prototype.constructor = Rectangle;
var Circle = function (id, x, y, radius) {
    Shape.call(this, id, x, y);
    this.radius = radius;
};
Circle.prototype = Object.create(Shape.prototype);
Circle.prototype.constructor = Circle;
```

上面的ES6代码定义了一个Rectangle类和一个Circle类，它们通过extends关键字，继承了Shape类的所有属性和方法。子类里都出现了super关键字，它在这里表示父类的构造函数，用来新建父类的this对象。子类必须在constructor方法中调用super方法，否则新建实例时会报错。这是因为子类没有自己的this对象，而是继承父类的this对象，然后对其进行加工。如果不调用super方法，子类就得不到this对象。对照ES5语法我们可以发现使用class语法更简洁明了。

## 插件推荐

- [whatruns](https://www.whatruns.com/)

这个chrome插件可以查看网站，包括但不限于web框架、web服务器、js框架、js图表插件、字体、CDN。可以很方便的查看你感兴趣的网站所使用的技术。直接在chrome扩展商店里面搜whatruns就能安装。

## 文章推荐
- [美团外卖前端可视化界面组装平台](https://zhuanlan.zhihu.com/p/27288444) 
前端如何才能提高生产效率，普遍的共识是要做到组件化开发，很多团队已经这样做了。虽然很多的产品已经实现了组件化开发，但不同产品间依然存在很多重复的劳动，比如登录框、导航等等。这里推荐一篇美团外卖在效率方面尝试的一个解决方案。

- [如何处理 JavaScript 内存泄露](https://mp.weixin.qq.com/s?__biz=MzA4NjE3MDg4OQ==&amp;mid=2650965216&amp;idx=1&amp;sn=758f45497eb1755c84de7c4afbd494eb&amp;chksm=843ae886b34d6190e9c720c495952b8c7e045e6af40b35c5192d1f0450856f4d44c2536a970d&amp;mpshare=1&amp;scene=1&amp;srcid=1001pdkcvIK6jOSK62fc15aq#)

讨论开发者容易忽视的重要主题 ：内存管理。文章也提供一些关于如何处理JavaScript内存泄露的技巧。在SessionStack，我们需要确保不会造成内存泄露或者不会增加我们集成的Web应用的内存消耗。

- [反击爬虫，前端工程师的脑洞可以有多大？](https://juejin.im/entry/59deb55951882578c2084a63)
关于反击爬虫，本文给了很多前端反爬虫例子；
真的感叹为了反爬虫，前段工程师真的费尽心思，脑洞大开！

- [Promise 异步流程控制](http://web.jobbole.com/92605/)
网页中预加载20张图片资源，分步加载，一次加载10张，两次完成，怎么控制图片请求的并发，怎样感知当前异步请求是否已完成？

- [设计模式之观察者模式](http://www.cnblogs.com/TomXu/archive/2012/03/02/2355128.html)
观察者模式是一种常用的设置模式。文中提供了多种实现观察者模式的方式，并带有调用方式。可作为实现观察者模式的源码和研究观察者模式使用。

- [用 threejs 制作一款简单的赛车游戏](http://www.alloyteam.com/2017/09/13139/)
通过学习本教程，可以熟悉 `webgl` 和 `threejs` 相关的知识。

- [使用 SRI 增强 localStorage 代码安全](https://imququ.com/post/enhance-security-for-ls-code.html)
大部分 Web 应用从 localStorage 中获取缓存代码后，没有任何检测机制，直接执行。而 localStorage 是跨页面的，同域下任何页面有 XSS 漏洞，就可以被攻击者用来往 localStorage 写入恶意代码，可以使用 SRI 增强 localStorage 代码安全。

- [浏览器缓存机制小结](http://mp.weixin.qq.com/s/a7UtcAUnifrNCzegfDYaig)
本文总结了浏览器缓存的基本机制，将各种情况分为：强缓存和协商缓存两种方式。对三组核心的HTTP请求以及响应头参数：cache-control和expire， last-modified和if-modified-since，etag和if-none-matched，做了清晰的解释，很好理解它们之间的区别、优先级等关系。

- [HTTP 缓存机制一二三](https://zhuanlan.zhihu.com/p/29750583)
作为前端，常与请求打交道，HTTP缓存应该作为基本知识储备。文章介绍了强缓存和协商缓存，响应头各个字段的含义简单了解下，具体业务需要后端配合设置。

## 招聘
TalkingData DTU 可视化团队招聘：
* 资深前端工程师

简历投递：
``` javascript
const email = 'xiang.wang#tendcloud.com'.replace('#', '@');
console.log(email);
```