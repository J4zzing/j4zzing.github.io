---
title: Web前端面试题整理
date: 2020-06-18 20:08:18
tags:
- Web前端
---

以下总结可能来自于

https://www.jianshu.com/p/07b24b4baa35

https://segmentfault.com/a/1190000022211870

http://47.98.159.95/my_blog/nav/#html%E9%83%A8%E5%88%86

## CSS

### 布局 -- 如何同时水平居中并垂直居中一个元素

- 父元素line-height配合内联子元素vertical-align: middle垂直对齐，父元素text-align: center居中对齐

- position: absolute; top: 50% - 元素高度; left: 50% - 元素宽度
- flexbox的content-justify和align-items设为center
- grid layout
- margin: 0 auto水平居中，padding垂直居中

## JavaScript

### 讲一下闭包

是什么

用在什么地方

### 讲一讲事件委托

好处都有啥：

- 节约性能或内存消耗
- 删除一个元素时不必用removeListener去解绑事件

### null的数据类型是对象吗

不是，null是JS七种原始数据类型之一。之所以`typeof null === "object"`是因为JS把所有二进制开头为000的数据都当成object类型，而null的二进制全是0。

~~而这个bug到现在还没修复。~~

https://stackoverflow.com/questions/801032/why-is-null-an-object-and-whats-the-difference-between-null-and-undefined



## DOM

### Element和Node的区别



## Promise，Event Loop，macrotask，microtask



## polyfills

https://en.wikipedia.org/wiki/Polyfill_(programming)



## React

### 讲一下生命周期



### 什么是高阶组件

### 合成事件和原生事件有什么不同

### Redux有了解吗

核心概念state, action 说一下

## Webpack

### Webpack都可以做什么

- 打包文件

- 