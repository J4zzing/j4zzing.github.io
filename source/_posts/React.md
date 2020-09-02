---
title: React 学习笔记
date: 2020-05-22 17:47:41
tags:
- React
---

# React 学习笔记

## React

### 要点摘录：

> React elements are [immutable](https://en.wikipedia.org/wiki/Immutable_object). Once you create an element, you can’t change its children or attributes. An element is like a single frame in a movie: it represents the UI at a certain point in time.

> React DOM compares the element and its children to the previous one, and only applies the DOM updates necessary to bring the DOM to the desired state.

> React may batch multiple `setState()` calls into a single update for performance.
>
> Because `this.props` and `this.state` may be updated [asynchronously](https://reactjs.org/docs/state-and-lifecycle.html#state-updates-may-be-asynchronous), you should not rely on their values for calculating the next state.



### 思考

#### Tradeoff

与其把性能花费在监听/订阅状态等数据上，React把性能花费在创建新的Immutable Collection上。



同时Immutable实现了memoization的性能优化，

### 提问：

React如何确保这段代码是更新原来的元素而不是渲染多个元素？

https://reactjs.org/docs/rendering-elements.html#updating-the-rendered-element



### Immutable

### 类型检查

#### TypeScript-React

https://github.com/Microsoft/TypeScript-React-Starter#typescript-react-starter

https://www.staging-typescript.org/docs/handbook/jsx.html

#### PropTypes

## React-Router

## Redux





## 练手项目

### 原生练习

https://codepen.io/

#### MERN

https://codingthesmartway.com/the-mern-stack-tutorial-building-a-react-crud-application-from-start-to-finish-part-1/

### 全方位项目 Spectrum

https://github.com/withspectrum/spectrum

## 怀旧

http://www.ruanyifeng.com/blog/2015/03/react.html

React.createClass()

Flux

https://blog.andrewray.me/flux-for-stupid-people/