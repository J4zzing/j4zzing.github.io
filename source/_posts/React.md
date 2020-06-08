---
title: React
date: 2020-05-22 17:47:41
tags:
- React
---

# React 学习笔记

### 要点摘录：

> React elements are [immutable](https://en.wikipedia.org/wiki/Immutable_object). Once you create an element, you can’t change its children or attributes. An element is like a single frame in a movie: it represents the UI at a certain point in time.

> React DOM compares the element and its children to the previous one, and only applies the DOM updates necessary to bring the DOM to the desired state.

> React may batch multiple `setState()` calls into a single update for performance.
>
> Because `this.props` and `this.state` may be updated [asynchronously](https://reactjs.org/docs/state-and-lifecycle.html#state-updates-may-be-asynchronous), you should not rely on their values for calculating the next state.



### 继续学习：

[代码分块，懒加载](https://reactjs.org/docs/code-splitting.html)

https://reactjs.org/docs/introducing-jsx.html#jsx-prevents-injection-attacks

[深入JSX](https://reactjs.org/docs/jsx-in-depth.html)

### 思考

#### Tradeoff

与其把性能花费在监听/订阅状态等数据上，React把性能花费在创建新的Immutable Collection上。



同时Immutable实现了memoization的性能优化，

### 提问：

React如何确保这段代码是更新原来的元素而不是渲染多个元素？

https://reactjs.org/docs/rendering-elements.html#updating-the-rendered-element

如果是用Key，那么为什么有些元素需要key属性，另一些不需要？

https://reactjs.org/docs/lists-and-keys.html#keyss



### Immutable



## 练手项目

### 入门

#### MERN

https://codingthesmartway.com/the-mern-stack-tutorial-building-a-react-crud-application-from-start-to-finish-part-1/

###　入门后





## 特技

#### 点击文档跳出爱心❤

考虑对document设置click的EventListener。了解下js canvas，配合border-radius、CSS动画之类的。应在一定时间后清除那些隐藏的元素。

参考资料：
https://www.quirksmode.org/js/events_order.html#link4

#### Hexo 主题开发

参考下列主题

https://github.com/probberechts/hexo-theme-cactus

https://theme-next.js.org/

https://www.yunyoujun.cn/

优秀博客

https://dnocm.com/articles/beechnut/hexo-next-injects/

https://blog.oniuo.com/