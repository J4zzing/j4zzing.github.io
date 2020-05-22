---
title: React
date: 2020-05-22 17:47:41
tags:
---

# React 学习笔记

### 要点摘录：

> React elements are [immutable](https://en.wikipedia.org/wiki/Immutable_object). Once you create an element, you can’t change its children or attributes. An element is like a single frame in a movie: it represents the UI at a certain point in time.

> React DOM compares the element and its children to the previous one, and only applies the DOM updates necessary to bring the DOM to the desired state.

> React may batch multiple `setState()` calls into a single update for performance.
>
> Because `this.props` and `this.state` may be updated [asynchronously](https://reactjs.org/docs/state-and-lifecycle.html#state-updates-may-be-asynchronous), you should not rely on their values for calculating the next state.



### 高级：

[代码分块，懒加载](https://reactjs.org/docs/code-splitting.html)



[深入JSX](https://reactjs.org/docs/jsx-in-depth.html)

### 提问：

React如何确保这段代码是更新原来的元素而不是渲染多个元素？

https://reactjs.org/docs/rendering-elements.html#updating-the-rendered-element

如果是用Key，那么为什么有些元素需要key属性，另一些不需要？

https://reactjs.org/docs/lists-and-keys.html#keyss