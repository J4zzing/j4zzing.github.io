---
title: js event loop 和 node.js event loop
date: 2020-05-29 17:20:41
tags:
- JavaScript
---

## 什么是event loop

event loop为事件循环，

https://www.youtube.com/watch?v=8aGhZQkoFbQ

## JavaScript event loop

![Event Loop](https://javascript.info/article/event-loop/eventLoop-full.svg)

参考资料：https://developer.mozilla.org/en-US/docs/Web/JavaScript/EventLoop#Run-to-completion

event loop 是在js运行时（runtime）的一种并发模型，负责执行代码，收集、处理事件和执行队列中的子任务。

![运行时概念](https://mdn.mozillademos.org/files/17124/The_Javascript_Runtime_Environment_Example.svg)

#### Stack

调用函数会形成栈的结构，即调用栈。栈中的每一项称为frame。

#### Queue

message queue是由message组成的队列。

##### message又是什么?

##### message如何被处理？

在event loop的某个阶段，运行时会开始处理message队列。根据队列FIFO的定义，运行时从最先进入队列的那一项处理，此时与message关联的回调函数会被调用，而message则作为该函数的参数使用，之后该message会被移除。

同样的，调用回调函数时会在栈中创建一个新的frame，直到栈空，运行时开始处理下一个message。

##### 什么时候会创建message?

1. 每当一个拥有对应事件监听器（event listener）的事件发生。比如点击拥有click事件监听器的元素会添加一个message到队列。
2. setTimeout函数。setTimeout接受的第2个参数为时延，从添加message到队列开始算起。注意，只有当队列里没有其他message在前并且栈空，该message在才会在时延后被执行。所以这个时延参数为**最短时延**，它并不能aAQZ保证在准确的时间后执行。



#### Heap

heap指的是一大块内存区域，js对象会分配到heap中。

## Node.js event loop

参考资料：https://nodejs.org/en/docs/guides/event-loop-timers-and-nexttick/