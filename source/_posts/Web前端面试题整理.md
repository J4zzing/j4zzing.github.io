---
title: Web前端面试题整理
date: 2020-06-18 20:08:18
tags:
- Web前端
---

## 通用心得

回答问题时要有发散思维，要善于引导面试官到自己擅长的内容。

毕竟面试时，双方的信息不对称，虽然都是开发者，但是各自钻研的方向也不尽相同。所以说要尽可能的展示自己的长处。

简历上写的内容要吃透。

好的项目要有难点或亮点。



以下内容可能来自于

亲身经历

互联网

## 算法与数据结构

冒泡排序

递归

二叉树遍历



## 计算机网络

### HTTP

**Q：HTTP有几种请求方法**

GET, HEAD, POST, PUT, DELETE, CONNECT, OPTIONS, TRACE, PATCH

**Q：Options请求的使用场景**

1. 确认服务器支持的请求方法

2. preflight request in CORS（重点）

——申引出CORS

https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/OPTIONS#Preflighted_requests_in_CORS

Q：GET和POST请求发送数据的优劣势

使用GET请求发送数据的

劣势：

1. 数据长度。使用GET发送数据时，数据会被添加到URL查询字符串，URL的长度限制为2048字符
2. 数据类型。因为数据是通过URL的方式发送，所以使用GET请求发送数据只支持ASCII字符
3. 安全性。因为数据是通过URL的方式发送，所以数据对任何可以看到URL的人可见

优势：

1. 实现更简单。
2. 通过分享链接，操作可以重现。

https://www.w3schools.com/tags/ref_httpmethods.asp

#### 泛问题 - 考察了解程度和细节把握

**Q：在浏览器输入URL后发生了什么**

https://zhuanlan.zhihu.com/p/43369093

1. DNS域名解析
2. 建立TCP连接
3. 发送HTTP请求
4. 服务器处理请求并响应
5. 关闭TCP连接
6. 浏览器解析HTML
7. 浏览器布局渲染

**Q：了解哪些HTTP首部**

随缘作答

#### HTTP缓存

**Q：Post请求能被缓存吗**

不能，GET支持缓存。

***Hot* Q：介绍一下HTTP缓存的几种方法**

Cache-Control, Expires首部

E-Tag

#### HTTP跨源

**Q：讲一下跨源**

#### HTTP安全

***Hot* Q：XSS与CSRF防范**

#### Websockets



### 传输层

***Hot* Q：HTTPS和HTTP的区别**

具体讲TSL



## HTML

Q：H5新标签

Q：HTML语义化

**Q：HTML表单编码类型**

application/x-www-form-urlencoded or multipart/form-data. 

Use multipart encoding for binary data



## CSS

***Hot* Q：花式居中一个元素**

https://www.smashingmagazine.com/2013/08/absolute-horizontal-vertical-centering-css/

http://jsfiddle.net/mBBJM/1/

```css
.Absolute-Center {
  margin: auto;
  position: absolute;
  top: 0; left: 0; bottom: 0; right: 0;
}
```

- 父元素line-height配合内联子元素vertical-align: middle垂直对齐，父元素text-align: center居中对齐
- position: absolute; top: 50% - 元素高度; left: 50% - 元素宽度
- flexbox的content-justify和align-items设为center
- grid layout
- margin: 0 auto水平居中，padding垂直居中
- padding % https://stackoverflow.com/questions/11535827/responsive-height-proportional-to-width

例题：

1. 居中一个宽高均为100px的元素。

2. 窗口居中一个未知大小的元素。

#### 响应式设计

**Q：怎么实现响应式设计的**

1. @media

2. 现代布局。flex和grid对响应式支持好

3. 相对长度单位

**Q：rem和em的区别**

rem表示根元素的字体大小（通常是html），em表示该元素的字体大小。

如果em用在自身的font-size大小上，那么它的大小将继承父元素。

https://developer.mozilla.org/en-US/docs/Web/CSS/length



## JavaScript

**Q：Js一共有多少种数据类型（纯记忆）**

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures

九种，包括6种原始数据类型：number, boolean, string, undefined, BigInt, Symbol

与null, Object, Function

**Q：null的数据类型是对象吗**

不是，null是一种特殊的原始类型。之所以`typeof null === "object"`是因为JS把所有二进制开头为000的数据都当成object类型，而null的二进制全是0。

~~而这个bug到现在还没修复。~~

https://stackoverflow.com/questions/801032/why-is-null-an-object-and-whats-the-difference-between-null-and-undefined

**Q：for...in和for...of的区别**



**Q：ES6/ES7的新特性**

#### this指向类



**Q：讲一下闭包**

闭包时一个函数能够访问其父函数的变量，即使这个父函数已经执行完毕。

用在什么地方？

**Q：讲一讲事件委托**

好处都有啥：

- 节约性能或内存消耗
- ~~删除一个元素时不用removeListener去解绑事件~~

#### 原型与继承类

**Q：讲一讲原型链**

Q：未完成，请忽略

```javascript
Class A {
    constructor(num=1)
    fn1(num=2)
    fn2(num=3)
}
Class B extends A {
    fn1(num=4)
}
const b = new B();
b.fn2();
b.fn1();
```

1. 输出结果
2. 不使用console.log函数实现输出A5

**Q：设计一个EventEmitter，包含on, off, emit方法。**

#### DOM

Q：Element和Node的区别

#### Promise

**Q：promise是在什么时候执行的**

事件循环，宏任务，微任务

Event Loop，macrotask，microtask

**Q：Async/awaits 是如何实现的**



#### polyfills

https://en.wikipedia.org/wiki/Polyfill_(programming)

**Q：实现function.prototype.bind**



## React

#### 生命周期

http://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/

**Q：生命周期都有哪些**



**Q：组件更新时会触发哪些生命周期**



Q：key



**Q：什么是高阶组件（HOC），它的作用、缺点及解决方案**

一个返回新组件的组件。

HOC提高代码复用性。

缺点是会导致嵌套地狱。

缺点是会导致嵌套地狱

hooks出现的原因之一就是为了解决这个问题。

**比较render props**

**Q：合成事件和原生事件有什么不同**

合成事件是React实现的一个模块，它包裹了原生事件，解决了浏览器兼容的问题。

#### React生态

**Q: Redux有了解吗**

核心概念reducer，state，action， 说一下



## Webpack

**Q：Webpack都可以做什么**

- 打包并支持模组化。
- 通过插件或loaders转义（transpile）代码
- 性能优化：代码分块等
- 提高开发效率：检测改动自动打包，Webpack开发服务器等

**Q：都用过Webpack的那些插件**

- 代码分块插件 - SplitChunkPlugin
- 生成HTML插件 - HtmlWebpackPlugin
- 清理输出文件夹 - CleanWebpackPlugin



## 其他

***Hot* Q：有哪些优化性能的方法？**

[代码分块](https://webpack.js.org/guides/code-splitting/) Webpack, optimization.splitChunks

懒加载

- 图片延迟加载

文件最小化minified

https://webpack.js.org/plugins/mini-css-extract-plugin/#minimizing-for-production

**Q：前后端分离用户认证的方法**

HTTP Basic Authentication

Cookie或Session

JWT Token



## 拓展阅读

https://www.jianshu.com/p/07b24b4baa35

https://segmentfault.com/a/1190000022211870

http://47.98.159.95/my_blog/nav/#html%E9%83%A8%E5%88%86