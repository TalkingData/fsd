---
title: 大前端周刊 第17期 （本期小编：耿少真）
date: 2017-10-20 10:24:12
tags:
---

## Show me the code   
      
### 柯里化

柯里化就是函数和参数值结合产生一个新的函数，如下代码，假设有一个curry的函数：


``` javascript
function add(a, b) {
    return a + b;
}

let add1 = add.curry(1);
console.log(add1(5)); // 6
console.log(add1(2)); // 3
```

怎么实现这样一个curry的函数？它的重点是要返回一个函数，这个函数有一些闭包的变量记录了创建时的默认参数，然后执行这个返回函数的时候，把新传进来的参数和默认参数拼一下变成完整参数列表去调原本的函数，所以有了以下代码：
``` javascript
Function.prototype.curry = function() {
    let defaultArgs = arguments;
    let that = this;
    return function() {
        return that.apply(this, defaultArgs.concat(arguments));    
        }
    };
```

但是由于参数不是一个数组，没有concat函数，所以需要把伪数组转成一个伪数组，可以用Array.prototype.slice：

``` javascript
Function.prototype.curry = function() {
    let slice = Array.prototype.slice;
    let defaultArgs = slice.call(arguments);
    let that = this;
    return function() {
         return that.apply(this, defaultArgs.concat(slice.call(arguments)));    
        }
    };
```

### 复杂选择器的查DOM

如实现一个document.querySelector：


``` javascript
document.querySelector(".mls-info > div .copyright-content")
```

首先把复杂选择器做一个解析，序列为以下格式：
``` javascript
//把selector解析为
var selectors = [
{relation: "descendant",  matchType: "class", value: "copyright-content"},
{relation: "child",       matchType: "tag",   value: "div"},
{relation: "subSelector", matchType: "class", value: "mls-info"}];

```

从右往左，第一个selector是.copyright-content，它是一个类选择器，所以它的matchType是class，它和第二个选择器是祖先和子孙关系，因此它的relation是descendant；同理第二个选择器的matchType是tag，而relation是child，表示是第三个选择器的直接子结点；第三个选择器也是class，但是它没有下一个选择器了，relation用subSelector表示。

matchType的作用就在于用来比较当前选择器是否match，如下代码所示：

``` javascript
function match(node, selector){
    if(node === document) return false;
    switch(selector.matchType){
        //如果是类选择器
        case "class":
            return node.className.trim().split(/ +/).indexOf(selector.value) >= 0;

        //如果是标签选择器
        case "tag":
            return node.tagName.toLowerCase() === selector.value. toLowerCase();

        default:
            throw "unknown selector match type";
    }
}
```

根据不同的matchType做不同的匹配。

在匹配的时候，从右往左，依次比较每个选择器是否match. 在比较下一个选择器的时候，需要找到相应的DOM结点，如果当前选择器是下一个选择器的子孙时，则需要比较当前选择器所有的祖先结点，一直往上直到document；而如果是直接子元素的关系，则比较它的父结点即可。所以需要有一个找到下一个目标结点的函数：
``` javascript
function nextTarget(node, selector){
    if(!node || node === document) return null;
    switch(selector.relation){
        case "descendant":
            return {node: node.parentNode, hasNext: true};
        case "child":
            return {node: node.parentNode, hasNext: false};
        case "sibling":
            return {node: node.previousSibling, hasNext: true};
        default:
            throw "unknown selector relation type";
          //hasNext表示当前选择器relation是否允许继续找下一个节点
    }
}
```
有了nextTarge和match这两个函数就可以开始遍历DOM，如下代码所示：
``` javascript
function querySelector(node, selectors){
    while(node){ // 遍历节点
        var currentNode = node;
        if(!match(node, selectors[0])){
            node = nextElement(currentNode);
            continue;
        }
        var next = null;
        for(var i = 0;i < selectors.length;i++){
            var matchIt = false;
            do {
                next = nextTarget(node, selectors[i]);
                node = next.node;
                if(!node){
                    break;
                }
                if(match(node, selectors[i+1])){
                    matchIt = true;  // 有一个符合就继续
                    break;
                }
            } while (next.hasNext);
            if(!matchIt) break;
        }
        if(matchIt && i === selectors.length - 1){
            return currentNode; // 全部匹配完
        }
        node = nextElement(currentNode);
    }
    return null;
}
```

最外层的while循环和简单选择器一样，都是要遍历所有DOM结点。对于每个结点，先判断第一个选择器是否match，如果不match的话，则继续下一个结点，如果不是标签选择器，对于绝大多数结点将会在这里判断不通过。如果第一个选择器match了，则根据第一个选择器的relation，找到下一个target，判断下一个targe是否match下一个selector，只要有一个target匹配上了，则退出里层的while循环，继续下一个选择器，如果所有的selector都能匹配上说明匹配成功。如果有一个selecotr的所有target都没有match，则说明匹配失败，退出selector的for循环，直接从头开始对下一个DOM结点进行匹配。


## 插件推荐

- [vue-area-linkage](https://dwqs.github.io/vue-area-linkage/)

Vue Area Linkage: 中国行政区联动选择器，省、市、区、街道联动选择


## 文章推荐
- [换种方式解读this](http://www.cnblogs.com/penghuwan/p/7356210.html) 
文中用一种全新的形式解读this的几种绑定形式，不论是新入门还是大牛都可以看看这种新的解读形式。

- [谈谈 PostCSS](http://web.jobbole.com/92760/)
现在的前端，javascript的发展有目共睹，框架林立。同时，html也是齐头并进，推出了HTML5标准，并且得到了普及。这样的发展却唯独少了一个角色？

- [前端：常见的6种HTML5错误用法](http://geek.csdn.net/news/detail/240600)
人们在标签使用中最常见到的错误之一就是随意将HTML5的<section>等价于<div>——具体地说，就是直接用作替代品(用于样式)。

- [vuejs 路由基础入门实战操作详细指南](https://segmentfault.com/a/1190000011612365)
Vue.js + vue-router 创建单页应用，是非常简单的。使用 Vue.js ，我们已经可以通过组合组件来组成应用程序，当你要把 vue-router 添加进来，我们需要做的是，将组件(components)映射到路由(routes)，然后告诉 vue-router 在哪里渲染它们。

- [JavaScript专题之解读 v8 排序源码](https://segmentfault.com/a/1190000011623637#articleHeader17)
文章对于插入排序与快速排序原理、实现讲解非常详细，并且在 V8排序的源码进行了实例分析。

- [从Vue.js源码看异步更新DOM策略及nextTick](https://juejin.im/post/59c7b25a5188257a125d7a98)
文章以实际问题为引，从源码入手，吸收别人的思路，一步步得到解决问题方案。首先，我觉得作者这种解决问题的方式以及刨根问底的精神首先值得我们学习；其次，文章总结的很到位，配合代码示例，让人清晰理解nextTick的实现。

- [更快速的Web应用程序I / O和流数据操作](https://www.sitepen.com/blog/2017/10/02/a-guide-to-faster-web-app-io-and-data-operations-with-streams/)
使用流更改您读取，写入和处理数据的方式。根据您的用例，代码复杂度可能会增加。然而，流可以实现数据的高效处理，从而导致更好的存储器性能。

- [使用Nuxt.js改善现有项目](https://qianduan.group/posts/59e8be1b0119753d067b40cc)
`SPA` 应用有其天生的问题：搜索引擎爬虫抓不到，无法满足 `SEO` 的需求。这可以可以通过 `SSR` 解决，`Nuxt.js` 是由一对法国的兄弟基于 vue 2.0 提供的 ssr 能力开发的框架，基于恰到好处的约定与配置，可以显著的降低开发者创建服务端渲染 web app 的门槛。

- [浅析nodejs的http模块](http://www.jianshu.com/p/ab2741f78858)
HTTP模块是Node内置的核心模块之一，node入门的课程都会讲，通过createServer就可以得到一个server对象，关于它内部实现的理解，可以帮助你提高技能。本文讲解了HTTP模块的大致流程，对一些关键点进行了充分的分析。

- [数据模拟神器 easy-mock](https://juejin.im/post/59a8f15ef265da246c4a3822)
如何提高前端开发效率？当前端UI及逻辑都写完而后端接口还没有完成，怎样不打断开发进程？  因此一款简单、高效、可视化并能快速生成模拟数据 的在线mock服务诞生。

- [如何使用koa2+es6/7打造高质量Restful API](https://zhuanlan.zhihu.com/p/26216336)
如今nodejs变得越来越火热，采用nodejs实现前后端分离架构已被多数大公司所采用。在过去，使用nodejs大家首先想到的是express.js，而发展到如今，更轻量，性能更好的koa已然成为主流不仅性能优异，它还支持async/await, 堪称回调地狱的终结者。

## 招聘
TalkingData DTU 可视化团队招聘：
* 资深前端工程师

简历投递：
``` javascript
const email = 'xiang.wang#tendcloud.com'.replace('#', '@');
console.log(email);
```